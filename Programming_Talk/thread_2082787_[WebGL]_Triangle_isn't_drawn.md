---
title: "[WebGL] Triangle isn't drawn"
date: 2012-11-10
forum: Programming Talk
---

### Post by bird1500 on 2012-11-10
Hi,
this sample should display a yellow triangle on a black background, for some reason it only displays the black background, can anyone spot the bug please?

2 files, the HTML:
[PHP]
<html>
     <head>
          <title>WebGL by hand</title>
          <script type="text/javascript" src="misc.js"></script>
         
          <script type="x-shader/x-vertex" id="vertShader">
                attribute vec2 vPos;
                
                void main() {
                     gl_Position = vec4(vPos, 0.0, 1.0);
                }
          </script>
        
          <script type="x-shader/x-fragment" id="fragShader">
                precision mediump float;
                void main() {
                     gl_FragColor = vec4(1.0, 1.0, 0.0, 1.0);
                }
          </script>
          
     </head>
     <body onload="initGL()">
          <canvas id="f15" style="width:640px; height:480px"></canvas>
     </body>
</html>
[/PHP]and the misc.js file:
[PHP]
var gl, canvas;
var vertBuf;
var prog;
var locVertPos;

function initGL() {
     canvas = document.getElementById("f15");
     gl = canvas.getContext("webgl") || canvas.getContext("experimental-webgl");
     if (!gl) {
          alert("Can't init GL");
          return;
     }
     gl.clearColor(0.0, 0.0, 0.0, 1.0);
     gl.clearDepth(1.0);
     gl.enable(gl.DEPTH_TEST);
     gl.depthFunc(gl.LEQUAL);

     vertBuf = gl.createBuffer();
     gl.bindBuffer(gl.ARRAY_BUFFER, vertBuf);
     var data = [
          -0.5, -0.5,
          0.5, -0.5,
          0.0, 0.5
     ];
     gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(data), gl.STATIC_DRAW);

     prog = createProgram(getScriptText("vertShader"),
          getScriptText("fragShader"));
    if(prog <= 0) {
         alert("Can't create program");
         return;
    }
    locVertPos = gl.getAttribLocation(prog, "vPos");
    setInterval(drawScene, 200);
}

function createProgram(vertSrc, fragSrc) {
     var vertShader = createShader(vertSrc, true);
     var fragShader = createShader(fragSrc, false);

     if (vertShader == null || fragShader == null) {
          return 0;
     }

     prog = gl.createProgram();
     gl.attachShader(prog, vertShader);
     gl.attachShader(prog, fragShader);
     gl.linkProgram(prog);

     if (!gl.getProgramParameter(prog, gl.LINK_STATUS)) {
          alert("Failed to link program");
          return 0;
     }

     return prog;
}

function createShader(src, isVertex) {
     var shader = gl.createShader(isVertex ? gl.VERTEX_SHADER :
          gl.FRAGMENT_SHADER);

     gl.shaderSource(shader, src);
     gl.compileShader(shader);

     if (!gl.getShaderParameter(shader, gl.COMPILE_STATUS)) {
          alert("Error in " + (isVertex ? "vertex" : "fragment") + " shader: " +
                gl.getShaderInfoLog(shader));
          return null;
     }

     return shader;
}

function drawScene() {
     gl.clear(gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT);
     
     gl.useProgram(prog);
     gl.enableVertexAttribArray(locVertPos);
     
     gl.bindBuffer(gl.ARRAY_BUFFER, vertBuffer);
     gl.vertexAttribPointer(locVertPos, 2, gl.FLOAT, false, 0, 0);
     
     gl.drawArrays(gl.TRIANGLES, 0, 3);
}

function getScriptText(id) {
     var shaderScript = document.getElementById(id);

     if (!shaderScript) {
          return null;
     }

     var text = "";
     var currentChild = shaderScript.firstChild;

     while (currentChild) {
          if (currentChild.nodeType == 3) {
                text += currentChild.textContent;
          }

          currentChild = currentChild.nextSibling;
     }

     return text;
}
[/PHP]EDIT: found the reason: vertBuffer -> vertBuf

---

