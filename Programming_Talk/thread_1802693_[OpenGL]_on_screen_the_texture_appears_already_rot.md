---
title: "[OpenGL] on screen the texture appears already rotated"
date: 2011-07-12
forum: Programming Talk
---

### Post by t1497f35 on 2011-07-12
Hi,
See attached video,
the Earth texture appears already rotated on the globe, though I haven't done any rotation, anyone knows why?

Here's the source code and the vert and frag shaders, texture attached.

Earth.cpp:

[PHP]
#include <GLTools.h>
#include <GLMatrixStack.h>
#include <GLGeometryTransform.h>
#include <GLFrame.h>
#include <GLFrustum.h>
#include <StopWatch.h>
#include <GLTriangleBatch.h>
#include <iostream>

#ifdef __APPLE__
#include <glut/glut.h>
#else
#include <GL/glut.h>
#endif

GLMatrixStack mvMatStack, projMatStack;
GLGeometryTransform transformPipe;
GLFrame cameraFrame;
GLFrustum viewFrustum;
GLTriangleBatch sphereBatch;
GLuint earthSh, texId;
GLint locAmbientColor, locDiffuseColor, locNormalMat, locMvMat, locMvpMat, locLightPos, locTexUnit;

bool LoadTGATexture(const char *name, GLenum minFilter, GLenum magFilter, GLenum wrapMode) {
    int width, height, openglFormat;
    GLenum imageFormat;
    GLbyte *pBytes = gltReadTGABits(name, &width, &height, &openglFormat, &imageFormat);
    if(pBytes == NULL) {
        std::cerr << __PRETTY_FUNCTION__ << " Can't load texture " << name << std::endl;
        return false;
    }
    
    glPixelStorei(GL_UNPACK_ALIGNMENT, 1);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, minFilter);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, magFilter);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, wrapMode);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, wrapMode);
    
    glTexImage2D(GL_TEXTURE_2D, 0, openglFormat, width, height, 0, imageFormat, GL_UNSIGNED_BYTE, pBytes);
    free(pBytes);
    
    if(minFilter == GL_LINEAR_MIPMAP_LINEAR ||
        minFilter == GL_LINEAR_MIPMAP_NEAREST ||
        minFilter == GL_NEAREST_MIPMAP_NEAREST ||
        minFilter == GL_NEAREST_MIPMAP_NEAREST) {
        glGenerateMipmap(GL_TEXTURE_2D);
    }
    
    return true;
}

void ChangeSize(int w, int h) {
    glViewport(0, 0, w, h);
    viewFrustum.SetPerspective(35.0f, float(w)/float(h), 0.01f, 100.0f);
    projMatStack.LoadMatrix(viewFrustum.GetProjectionMatrix());
    transformPipe.SetMatrixStacks(mvMatStack, projMatStack);
}

void RenderScene() {
    glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT);
    static CStopWatch stopWatch;
    const float fNum = 0.2f;
    GLfloat vAmbientColor[] = {fNum, fNum, fNum, 1.0f};
    GLfloat vDiffuseColor[] = {1.0f, 1.0f, 1.0f, 1.0f};
    GLfloat vLightPos[] = {-100.0f, 100.0f, 100.0f};
    
    M3DMatrix44f cameraMat;
    cameraFrame.GetCameraMatrix(cameraMat);
    
    mvMatStack.PushMatrix();
        mvMatStack.MultMatrix(cameraMat);
        mvMatStack.Rotate(stopWatch.GetElapsedSeconds() * 20.0f, 0.0f, 1.0f, 0.0f);
        glUseProgram(earthSh);
            glUniform1i(locTexUnit, 0);
            glUniform4fv(locAmbientColor, 1, vAmbientColor);
            glUniform4fv(locDiffuseColor, 1, vDiffuseColor);
            glUniform3fv(locLightPos, 1, vLightPos);
            glUniformMatrix3fv(locNormalMat, 1, GL_FALSE, transformPipe.GetNormalMatrix());
            glUniformMatrix4fv(locMvMat, 1, GL_FALSE, transformPipe.GetModelViewMatrix());
            glUniformMatrix4fv(locMvpMat, 1, GL_FALSE, transformPipe.GetModelViewProjectionMatrix());
        sphereBatch.Draw();
    mvMatStack.PopMatrix();
    
    glutSwapBuffers();
}

bool SetupRC() {
    glClearColor(0.0f, 0.0f, 0.0f, 1.0f);
    glEnable(GL_DEPTH_TEST);
    glEnable(GL_CULL_FACE);
    
    glGenTextures(1, &texId);
    glActiveTexture(GL_TEXTURE0);
    glBindTexture(GL_TEXTURE_2D, texId);
    if(!LoadTGATexture("Earth.tga", GL_LINEAR_MIPMAP_LINEAR, GL_LINEAR, GL_CLAMP_TO_EDGE)) {
        return false;
    }
    
    gltMakeSphere(sphereBatch, 1.0f, 50, 50);
    earthSh = gltLoadShaderPairWithAttributes("Earth.vert", "Earth.frag", 3, GLT_ATTRIBUTE_VERTEX, "vVertex",
            GLT_ATTRIBUTE_NORMAL, "vNormal", GLT_ATTRIBUTE_TEXTURE0, "vCoords");
    
    locAmbientColor = glGetUniformLocation(earthSh, "ambientColor");
    locDiffuseColor = glGetUniformLocation(earthSh, "diffuseColor");
    locNormalMat = glGetUniformLocation(earthSh, "normalMatrix");
    locMvMat = glGetUniformLocation(earthSh, "mvMatrix");
    locMvpMat = glGetUniformLocation(earthSh, "mvpMatrix");
    locLightPos = glGetUniformLocation(earthSh, "vLightPosition");
    locTexUnit = glGetUniformLocation(earthSh, "texUnit");
    
    cameraFrame.MoveForward(-4.0f);
    return true;
}

void ShutdownRC() {
    glDeleteTextures(1, &texId);
    glDeleteProgram(earthSh);
}

int main(int argc, char *argv[]) {
    gltSetWorkingDirectory(argv[0]);
    
    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGBA | GLUT_DEPTH);
    glutInitWindowSize(800, 600);
    glutCreateWindow("Rotating Earth");
    glutDisplayFunc(RenderScene);
    glutReshapeFunc(ChangeSize);
    
    GLenum result = glewInit();
    if(result != GLEW_OK) {
        std::cout << __PRETTY_FUNCTION__ << glewGetErrorString(result) << std::endl;
        return result;
    }
    
    if(!SetupRC()) {
        std::cout << "setup rc failed, returning" << std::endl;
        return 1;
    }
    atexit(ShutdownRC);
    glutTimerFunc(50, gltRepaintScene, 30);
    glutMainLoop();
    return 0;
}
[/PHP]Vert shader:
[PHP]
#version 330

in vec4 vVertex;
in vec3 vNormal;
in vec2 vCoords;

uniform mat4 mvpMatrix;
uniform mat4 mvMatrix;
uniform mat3 normalMatrix;
uniform vec3 vLightPosition;

out vec3 vVaryingNormal;
out vec3 vVaryingLightDir;
out vec2 vPassCoords;

void main() {
    vPassCoords = vCoords;
    vVaryingNormal = normalMatrix * vNormal;
    
    vec4 vEyePos4 = mvMatrix * vVertex;
    vec3 vEyePos3 = vEyePos4.xyz / vEyePos4.w;
    vVaryingLightDir = vLightPosition - vEyePos3;
    
    gl_Position = mvpMatrix * vVertex;
}
[/PHP]Frag shader:
[PHP]
#version 330

uniform vec4 ambientColor;
uniform vec4 diffuseColor;
uniform sampler2D texUnit;

in vec3 vVaryingLightDir;
in vec3 vVaryingNormal;
in vec2 vPassCoords;

out vec4 vFinalColor;

void main() {
    vec3 vNormal = normalize(vVaryingNormal);
    vec3 vLightDir = normalize(vVaryingLightDir);
    
    float fIntensity = max(0.0, dot(vNormal, vLightDir));
    vFinalColor = diffuseColor * fIntensity;
    vFinalColor += ambientColor;
    
    vFinalColor *= texture(texUnit, vPassCoords);
    
    vec3 vReflection = reflect(-vLightDir, vNormal);
    fIntensity = max(0.0, dot(vNormal, vReflection));
    if(fIntensity > 0.0f) {
        float fPow = pow(fIntensity, 128.0f);
        vFinalColor.rgb += vec3(fPow, fPow, fPow);
    }
}
[/PHP]
Makefile:
[PHP]
MAIN = Earth
SRCPATH = ../../../Src/Chapter06/$(MAIN)/
SHAREDPATH = ../../../Src/GLTools/src/
SHAREDINCPATH = ../../../Src/GLTools/include/
LIBDIRS = -L/usr/X11R6/lib -L/usr/X11R6/lib64 -L/usr/local/lib
INCDIRS = -I/usr/include -I/usr/local/include -I/usr/include/GL -I$(SHAREDINCPATH)  -I$(SHAREDINCPATH)GL

CC = g++
CFLAGS = $(COMPILERFLAGS) -g $(INCDIRS)
LIBS = -lX11 -lglut -lGL -lGLU -lm

prog : $(MAIN)

$(MAIN).o : $(SRCPATH)$(MAIN).cpp
glew.o    : $(SHAREDPATH)glew.c
GLTools.o    : $(SHAREDPATH)GLTools.cpp
GLBatch.o    : $(SHAREDPATH)GLBatch.cpp
GLTriangleBatch.o    : $(SHAREDPATH)GLTriangleBatch.cpp
GLShaderManager.o    : $(SHAREDPATH)GLShaderManager.cpp
math3d.o    : $(SHAREDPATH)math3d.cpp

$(MAIN) : $(MAIN).o glew.o
    $(CC) $(CFLAGS) -o $(MAIN) $(LIBDIRS) $(SRCPATH)$(MAIN).cpp $(SHAREDPATH)glew.c $(SHAREDPATH)GLTools.cpp $(SHAREDPATH)GLBatch.cpp $(SHAREDPATH)GLTriangleBatch.cpp $(SHAREDPATH)GLShaderManager.cpp $(SHAREDPATH)math3d.cpp $(LIBS)

clean:
    rm -f *.o
[/PHP]
Example derived from the OpenGL Superbible 5th ed.

---

