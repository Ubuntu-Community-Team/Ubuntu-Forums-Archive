---
title: "Any column Matrix math?"
date: 2012-11-23
forum: Programming Talk
---

### Post by bird1500 on 2012-11-23
Hi,
Is there any (OpenGL) math code I can look at that both:
1) Uses 4x4 _**column-major**_ **matrices**, not row matrices which get transposed before sending to OpenGL.
2) The 4x4 _**column**_-major **matrices** are defined as an array of 16 floats.

Hence (logically and programmatically) e.g. matrix[2] should be the element at row 3 column 1, not row 1 column 3.

So far I only found code that despite teaching OpenGL uses row matrix notation and transposes it before usage, or where a matrix is an array of arrays.

EDIT: I did it myself, source code below.

glm.h:
[PHP]
#ifndef GLM_H
#define GLM_H

#include <GL/glew.h>
#include <string.h>
#include <stdio.h>
#include <stdlib.h>

class mat4 {
public:
    mat4();
    virtual ~mat4();
    
    void
    ident();
    
    void
    mult(const mat4&);
    
    void
    perspSymm(float r, float t, float n, float f);
    
    void
    print(const char*);
    
    void
    transl(float xOff, float yOff, float zOff);
    
    float m[16];
};

#endif
[/PHP]glm.cpp:
[PHP]
#include "glm.h"
#include <math.h>
#include <time.h>
#include <stdio.h>
#include <string.h>


mat4::mat4() {}
mat4::~mat4() {}

void
mat4::ident() {
    memset(m, 0, sizeof(m));
    m[0] = m[5] = m[10] = m[15] = 1.0f;
}

//I am the matrix on the left
void
mat4::mult(const mat4 &rMat) {
    const float *r = rMat.m;
    float buf[16];
    
    buf[0] = m[0]*r[0] + m[4]*r[1] + m[8]*r[2] + m[12]*r[3];
    buf[1] = m[1]*r[0] + m[5]*r[1] + m[9]*r[2] + m[13]*r[3];
    buf[2] = m[2]*r[0] + m[6]*r[1] + m[10]*r[2] + m[14]*r[3];
    buf[3] = m[3]*r[0] + m[7]*r[1] + m[11]*r[2] + m[15]*r[3];
    
    buf[4] = m[0]*r[4] + m[4]*r[5] + m[8]*r[6] + m[12]*r[7];
    buf[5] = m[1]*r[4] + m[5]*r[5] + m[9]*r[6] + m[13]*r[7];
    buf[6] = m[2]*r[4] + m[6]*r[5] + m[10]*r[6] + m[14]*r[7];
    buf[7] = m[3]*r[4] + m[7]*r[5] + m[11]*r[6] + m[15]*r[7];
    
    buf[8] = m[0]*r[8] + m[4]*r[9] + m[8]*r[10] + m[12]*r[11];
    buf[9] = m[1]*r[8] + m[5]*r[9] + m[9]*r[10] + m[13]*r[11];
    buf[10] = m[2]*r[8] + m[6]*r[9] + m[10]*r[10] + m[14]*r[11];
    buf[11] = m[3]*r[8] + m[7]*r[9] + m[11]*r[10] + m[15]*r[11];
    
    buf[12] = m[0]*r[12] + m[4]*r[13] + m[8]*r[14] + m[12]*r[15];
    buf[13] = m[1]*r[12] + m[5]*r[13] + m[9]*r[14] + m[13]*r[15];
    buf[14] = m[2]*r[12] + m[6]*r[13] + m[10]*r[14] + m[14]*r[15];
    buf[15] = m[3]*r[12] + m[7]*r[13] + m[11]*r[14] + m[15]*r[15];
    
    memcpy(m, buf, sizeof(buf));
}

void
mat4::perspSymm(float r, float t, float n, float f) {
    memset(m, 0, sizeof(m));
    
    //1st col
    m[0] = n/r;
    
    //2nd col
    m[5] = n/t;
    
    //3rd col
    m[10] = (-f-n)/(f-n);
    m[11] = (-2*f*n)/(f-n);
    
    //4th col
    m[14] = -1.0f;
}

void
mat4::print(const char *sz) {
    
    if(sz != NULL) {
        printf("%s\n", sz);
    }
    
    const float *f = m;
    printf("%.3f %.3f %.3f %.3f\n", f[0], f[4], f[8], f[12]);
    printf("%.3f %.3f %.3f %.3f\n", f[1], f[5], f[9], f[13]);
    printf("%.3f %.3f %.3f %.3f\n", f[2], f[6], f[10], f[14]);
    printf("%.3f %.3f %.3f %.3f\n", f[3], f[7], f[11], f[15]);
    
    printf("\n");
}

void
mat4::transl(float xOff, float yOff, float zOff) {
    memset(m, 0, sizeof(m));
    m[0] = m[5] =  m[10] = m[15] = 1.0f;
    m[12] = xOff;
    m[13] = yOff;
    m[14] = zOff;   
}
[/PHP]

---

