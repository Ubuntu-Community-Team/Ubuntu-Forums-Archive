---
title: "[WebGL] Is this rotation about Z-axis correct?"
date: 2012-11-12
forum: Programming Talk
---

### Post by bird1500 on 2012-11-12
Hi,
I have a triangle rotating about the Z-axis but it looks like it doesn't only rotate but also bounce around a little, is it true and if so what am I doing wrong?

The relevant code, the drawing function:
[PHP]
function drawScene() {
    gl.clear(gl.COLOR_BUFFER_BIT | gl.DEPTH_BUFFER_BIT);
    gl.useProgram(prog);

    var translMat = new Array(16);
    matTranslate(0.0, 0.0, -1.0, translMat);

    var rotMat = new Array(16);
    angle = (angle + 2) % 360;
    matRotZ(angle, rotMat);

    var viewMat = new Array(16);
    matMultMat(rotMat, translMat, viewMat);

    var projMat = new Array(16);
    var fk = 0.5;
    matPerspSymm(fk, fk, 1.0, 10.0, projMat);

    var mvp = new Array(16);
    matMultMat(projMat, viewMat, mvp);

    gl.uniformMatrix4fv(prog.locMvp, false, mvp);
    
    gl.enableVertexAttribArray(prog.locVertCoords);
    
    gl.bindBuffer(gl.ARRAY_BUFFER, prog.vertBuf);
    gl.vertexAttribPointer(prog.locVertCoords, 2, gl.FLOAT, false, 0, 0);

    gl.drawArrays(gl.TRIANGLES, 0, 3);
}
[/PHP]The rotation matrix:
[PHP]
function matRotZ(angle, m) {
    var theta = angle * MAT_TO_RAD;

    m[0] = Math.cos(theta);
    m[1] = -(Math.sin(theta));
    m[2] = 0.0;
    m[3] = 0.0;

    m[4] = Math.sin(theta);
    m[5] = Math.cos(theta);
    m[6] = 0.0;
    m[7] = 0.0;

    m[8] = 0.0;
    m[9] = 0.0;
    m[10] = 1.0;
    m[11] = 0.0;

    m[12] = 0.0;
    m[13] = 0.0;
    m[14] = 0.0;
    m[15] = 1.0;
}
[/PHP]The full working HTML example is attached.

---

