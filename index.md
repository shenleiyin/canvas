<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <title></title>
</head>
<body>
    <canvas id="canvas" width="120" height="40"></canvas>
    <script>
        var canvas = document.getElementById("canvas");//获取到canvas对象，演员
        var context = canvas.getContext("2d");//获取到canvas的绘图环境，演员表演的舞台
        draw();
        canvas.onclick = function () {
            context.clearRect(0, 0, 120, 40);//清除画布
            draw();
        }
        //获取到随机的颜色值
        function getColor() {
            var red = Math.floor(Math.random() * 256);
            var green = Math.floor(Math.random() * 256);
            var blue = Math.floor(Math.random() * 256);
            return "rgb(" + red + "," + green + "," + blue + ")";
        }

        function draw() {
            context.strokeRect(0, 0, 120, 40);//绘制矩形框
            var aCode = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l'];
            for (var i = 0; i < 4; i++) {
                var x = 20 + 20 * i;
                var y = 20 + Math.random() * 10;
                var index = Math.floor(Math.random() * aCode.length);//获取到随机的索引值
                var str = aCode[index];//获取到随机的内容
                context.font = "bold 20px 微软雅黑";//设置字体
                context.fillStyle = getColor();//设置字体的颜色

                context.translate(x, y);
                var deg = Math.random() * 120 * Math.PI / 180;
                context.rotate(deg);
                context.fillText(str, 0, 0);//把文字写到canvas上面
                context.rotate(-deg);
                context.translate(-x, -y);
            }
            //做干扰线
            for (var i = 0; i < 8; i++) {
                context.beginPath();//声明开始一个路径
                context.moveTo(Math.random() * 120, Math.random() * 40);//设置起点
                context.lineTo(Math.random() * 120, Math.random() * 40);//设置终点
                context.strokeStyle = getColor();//设置线的颜色
                context.stroke();//开始绘制直线
            }
            //做干扰点
            for (var i = 0; i < 20; i++) {
                context.beginPath();//声明开始一个路径
                var x = Math.random() * 120;
                var y = Math.random() * 40;
                context.moveTo(x, y);//设置起点
                context.lineTo(x + 1, y + 1);//设置终点
                context.strokeStyle = getColor();//设置线的颜色
                context.stroke();//开始绘制直线
            }
        }
       
    </script>
</body>
</html>
