## 개인용으로 사용

라이브러리 URL
* highcharts : https://www.highcharts.com/

## 차트

- [1.0](#1.0) <a name='1.0'></a> 샘플 구조

  ```js
  Highcharts.chart($el, {  // $el 작성 형식 = 'container'
    title: { // 대제목 설정
        text: '대제목'
    },
  
    subtitle: { // 소제목 설정
        text: '소제목'
    },

    yAxis: { // y축 옵션
        title: {
            text: 'y축'
        }
    },
    legend: { // 레전드 설정
        layout: 'vertical',
        align: 'right',
        verticalAlign: 'middle'
    },

    plotOptions: {
        series: {
            label: {
                connectorAllowed: true // 시리즈 라벨. 선으로 연결한 ui제공
            },
            pointStart: 2010 // x 축 시작 값
        }
    },

    series: [{ // 차트 데이터
        name: 'Installation',
        data: [43934, 52503, 57177, 69658, 97031, 119931, 137133, 154175]
    }, {
        name: 'Manufacturing',
        data: [24916, 24064, 29742, 29851, 32490, 30282, 38121, 40434]
    }, {
        name: 'Sales & Distribution',
        data: [11744, 17722, 16005, 19771, 20185, 24377, 32147, 39387]
    }, {
        name: 'Project Development',
        data: [null, null, 7988, 12169, 15112, 22452, 34400, 34227]
    }, {
        name: 'Other',
        data: [12908, 5948, 8105, 11248, 8989, 11816, 18274, 18111]
    }],

    responsive: { //반응형 규칙 설정
      rules: [{
        condition: {
            maxWidth: 500
        },
        chartOptions: {
            legend: {
                layout: 'horizontal',
                align: 'center',
                verticalAlign: 'bottom'
            }
        }  
      }]
    }
  }); 
  ```
  
  
- [2.0](#2.0) <a name='2.0'></a> setOptions 설정

  ```js
  // setOptions
  Highcharts.setOptions({
      colors: ["#e26153", "#e4c24d", "#506485"] // 차트 막대 컬러 설정
      ,lang: {
          decimalPoint: ".", // 숫자형 . 자동 설정
          thousandsSep: ",", // 숫자형 , 자동 설정
          numericSymbols:  ['k', 'M', 'G', 'T', 'P', 'E'], // 숫자 0생략 후 단위 설정
      }
  });
  
  // highcharts
  Highcharts.chart($el, { // $el 작성 형식 = 'container'
    ...
  });
  ```  
  
- [3.0](#3.0) <a name='3.0'></a> chart

  ```js
  //highcharts
  Highcharts.chart($el, {  // $el 작성 형식 = 'container'
    chart: {
      minorTickInterval: 'auto', //보조선 옵션
      type: 'bar', // 차트 타입 :: bar, column, pie, line ...
      height: number, // 세로 사이즈
      width: number, // 가로 사이즈
    },
    
    ...
  });
  ```
  
- [3.1](#3.1) <a name='3.1'></a> title

  ```js
  //highcharts
  Highcharts.chart($el, {  // $el 작성 형식 = 'container'
    title: {
      text: null // 대제목 :: '문구'
    },
    
    ...
  });
  ```
  
- [3.2](#3.2) <a name='3.2'></a> subtitle

  ```js
  //highcharts
  Highcharts.chart($el, {  // $el 작성 형식 = 'container'
    subtitle: {
      text: null // 소제목 :: '문구'
    },
    
    ...
  });
  ```
  
- [3.3](#3.3) <a name='3.3'></a> credits

  ```js
  //highcharts
  Highcharts.chart($el, {  // $el 작성 형식 = 'container'
    credits: {
      enabled: false, // 하단 크레딧 항목 노출 :: true or false
    },
    
    ...
  });
  ```
  
- [3.4](#3.4) <a name='3.4'></a> xAxis

  ```js
  //highcharts
  Highcharts.chart($el, {  // $el 작성 형식 = 'container'
    xAxis: [
      {  
        categories: ['항목1','항목2','항목3']  //  x축의 첫번째 항목
      }
    ],
    
    ...
  });
  ```
  
- [3.5](#3.5) <a name='3.5'></a> yAxis

  ```js
  //highcharts
  Highcharts.chart($el, {  // $el 작성 형식 = 'container'
    yAxis: [
      { // Primary yAxis
        gridLineWidth: 0,
        minorTickInterval: 'auto',//보조선 옵션
        title: {
            text: null // 해당 y축 문구 :: '문구'
        },
        visible: true, // 노출 or 비노출
        opposite: true // true 시 보조축 사용(우측)
      }
    ],
    
    ...
  });
  ```
  
- [3.6](#3.6) <a name='3.6'></a> plotOptions

  ```js
  //highcharts
  Highcharts.chart($el, {  // $el 작성 형식 = 'container'  
    plotOptions: {
      series: {
        dataLabels: { //데이터라벨 :: 범례추가
          enabled:true, // 노출 비노출
          y: -3,  // y축 position
          style: {
            fontWeight: 'normal' // 폰트 굵기
          },
          borderRadius: 2,  // 보더 radius
          backgroundColor: 'rgba(255,255,255,0.7)', // 바탕 색상
          borderWidth: 1,  // 보더 굵기
          borderColor: '#ddd', // 보더 색상
          formatter: function() { // 수정 룰 정하기
            if (this.y === 0) {
                return null;
            } else {
                return this.y.toLocaleString();
            }  
          }
        },
        states: { // columns 오버시 색연하게 만들기 항목 제거
          hover: {
            brightness: 0 // darken
          }
        }
      }
    },
    
    ...
  });
  ```
  
- [3.7](#3.7) <a name='3.7'></a> tooltip

  ```js
  //highcharts
  Highcharts.chart($el, {  // $el 작성 형식 = 'container'  
    tooltip: { 
      borderWidth: 0,  // 보더 굵기
      shadow: false,  // 그림자 노출 비노출
      shared: true,  // 
      backgroundColor: '#FFFFFF',  // 배경 색상
      useHTML: true,  // useHTML 사용시 svg가 아닌 html로 생성
      style:{
        zIndex:'10',  // 태그 zindex
        padding: 0  // 태그 padding
      },
      positioner: function (labelWidth, labelHeight, point) {
        var newPlotX = point.plotX;
        if(newPlotX < 60){
          newPlotX = 30;
          return {
            x: newPlotX,
            y: point.plotY - 60
          };
        }
        return newPosition.call(this, labelWidth, labelHeight, point); },
    },
    
    ...
  });
  ```
  
- [3.8](#3.8) <a name='3.8'></a> series

  ```js
  //highcharts
  Highcharts.chart($el, {  // $el 작성 형식 = 'container'  
     series: [{
       data: [29.9, 216.4, 194.1, 95.6, 54.4]
     }],
    
    ...
  });
  ```