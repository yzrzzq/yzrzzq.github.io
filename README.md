<!DOCTYPE html>
<html lang="zh-CN">

<head>
  <meta charset="UTF-8">
  <title>行业产值趋势渐变堆叠面积图</title>
  <!-- 引入 ECharts CDN -->
  <script src="/yzrzzq.github.io/echarts.js"></script>
 <style>
        #chart-container {
             width: 900px;
            height: 500px;
            margin: 30px auto;
        }
         .title {
            text-align: center;
            font-family: "Microsoft YaHei", sans-serif;
            margin-top: 20px;
            color: #333;
        }
    </style>
</head>
<body>
     <h1 class="title">青浦区各产业增速变化趋势 (2019-2024)</h1>
    <div id="chart-container"></div>
    <script>
        // 初始化图表
        var chartDom = document.getElementById('chart-container');
        var myChart = echarts.init(chartDom);
        
        // 数据
         var option = {
            tooltip: {
                trigger: 'axis',
                formatter: function(params) {
                    var result = params[0].axisValue + '年<br/>';
                    params.forEach(function(item) {
                        result += item.marker + ' ' + item.seriesName + ': ' + item.value + '%<br/>';
                    });
                    return result;
                }
            },
            legend: {
                data: ['生产总值增速', '第一产业增速', '第二产业增速', '第三产业增速'],
                top: 30,
                textStyle: {
                    fontFamily: 'Microsoft YaHei'
                }
            },
            toolbox: {
                feature: {
                    saveAsImage: {
                        type: 'svg',
                        title: '保存为SVG'
                    },
                    dataView: { 
                        show: true, 
                        readOnly: false,
                        title: '数据视图'
                    },
                    magicType: { 
                        show: true, 
                        type: ['line', 'bar'],
                        title: {
                            line: '切换为折线图',
                            bar: '切换为柱状图'
                        }
                    },
                    restore: { 
                        show: true,
                        title: '还原'
                    },
                },
                right: 20
            },
            xAxis: {
                type: 'category',
                data: ['2019', '2020', '2021', '2022', '2023', '2024'],
                axisLabel: {
                    fontSize: 12,
                    fontFamily: 'Microsoft YaHei'
                },
                name: '年份',
                nameLocation: 'middle',
                nameGap: 25,
                nameTextStyle: {
                    fontFamily: 'Microsoft YaHei',
                    fontSize: 14
                }
            },
            yAxis: {
                type: 'value',
                name: '增速(%)',
                axisLabel: {
                    formatter: '{value}%',
                    fontFamily: 'Microsoft YaHei'
                },
                nameTextStyle: {
                    fontFamily: 'Microsoft YaHei',
                    fontSize: 14
                }
            },
            series: [
                {
                    name: '生产总值增速',
                    type: 'line',
                    smooth: true,
                    data: [5.8, 3.8, 6.1, -1.9, 5.7, 7.3],
                    lineStyle: {
                        width: 4,
                        color: '#c23531'
                    },
                    symbolSize: 8,
                    itemStyle: {
                        color: '#c23531'
                    }
                },
                {
                    name: '第一产业增速',
                    type: 'line',
                    smooth: true,
                    data: [-14.6, 5.6, 3.7, -0.5, 1.6, -1.1],
                    lineStyle: {
                        width: 3,
                        type: 'dashed',
                        color: '#2f4554'
                    },
                    symbolSize: 6,
                    itemStyle: {
                        color: '#2f4554'
                    }
                },
                {
                    name: '第二产业增速',
                    type: 'line',
                    smooth: true,
                    data: [-2.6, -1.5, 6.2, -9.5, 1.3, 3.7],
                    lineStyle: {
                        width: 3,
                        color: '#61a0a8'
                    },
                    symbolSize: 6,
                    itemStyle: {
                        color: '#61a0a8'
                    }
                },
                {
                    name: '第三产业增速',
                    type: 'line',
                    smooth: true,
                    data: [11.9, 7.1, 6.1, 2.1, 7.8, 9.1],
                    lineStyle: {
                        width: 3,
                        color: '#d48265'
                    },
                    symbolSize: 6,
                    itemStyle: {
                        color: '#d48265'
                    }
                }
            ],
            grid: {
                top: 80,
                bottom: 30,
                left: 60,
                right: 40
            },
            textStyle: {
                fontFamily: 'Microsoft YaHei'
            }
        };
        
        myChart.setOption(option);
        
        window.addEventListener('resize', function() {
            myChart.resize();
        });
  </script>
</body>

</html>
