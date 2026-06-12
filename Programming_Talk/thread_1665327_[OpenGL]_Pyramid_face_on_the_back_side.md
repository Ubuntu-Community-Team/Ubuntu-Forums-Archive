---
title: "[OpenGL] Pyramid face on the back side"
date: 2011-01-12
forum: Programming Talk
---

### Post by t1497f35 on 2011-01-12
Hi folks,
I got only a pyramid on the scene but it appears as if either the camera is looking at it from behind or as if its sides are flipped. Any ideas what's the matter?

The relevant code - when compiled the texture appears on the back side but it should be on the front side:
```

batch.Begin(GL_TRIANGLES, 18, 1);
    M3DVector3f vApex = {0.0f, 1.0f, 0.0f};
    M3DVector3f vFrontLeft = {-1.0f, -1.0f, 1.0f};
    M3DVector3f vFrontRight = {1.0f, -1.0f, 1.0f};
    M3DVector3f vBackLeft = {-1.0f, -1.0f, -1.0f};
    M3DVector3f vBackRight = {1.0f, -1.0f, -1.0f};
    M3DVector3f n;//normal

    M3DVector3f vTopDown = {0.0f, -1.0f, 0.0f};

// THE FRONT SIDE:
    m3dFindNormal(n, vApex, vFrontLeft, vFrontRight);
    batch.Normal3fv(n);
    batch.MultiTexCoord2f(0, 0.5f, 1.0f);
    batch.Vertex3fv(vApex);

    batch.Normal3fv(n);
    batch.MultiTexCoord2f(0, 0.0f, 0.0f);
    batch.Vertex3fv(vFrontLeft);

    batch.Normal3fv(n);
    batch.MultiTexCoord2f(0, 1.0f, 0.0f);
    batch.Vertex3fv(vFrontRight);
//FRONT SIDE END

```Full source code with texture attached:
[PHP]
#include <GLTools.h>
#include <GLShaderManager.h>
#include <GLMatrixStack.h>
#include <GLGeometryTransform.h>
#include <GLTriangleBatch.h>
#include <GLBatch.h>
#include <GLFrustum.h>
#include <GLFrame.h>

#include <iostream>
#include <math.h>

#ifdef __APPLE__
    #include <glut/glut.h>
#else
    #include <GL/glut.h>
#endif

GLShaderManager shaderManager;
GLMatrixStack projectionMatrix, modelViewMatrix;
GLGeometryTransform pipeline;
GLBatch pyramidBatch;
GLFrustum viewFrustum;
GLFrame cameraFrame, pyramidFrame;
GLuint textureID;

void ChangeSize(int w, int h) {
    glViewport(0, 0, w, h);
    viewFrustum.SetPerspective(35.0f, float(w)/float(h), 0.01f, 100.0f);
    projectionMatrix.LoadMatrix(viewFrustum.GetProjectionMatrix());
    pipeline.SetMatrixStacks(modelViewMatrix, projectionMatrix);
}

void HandleKeys(int key, int x, int y) {
    static const GLfloat step = m3dDegToRad(5.0f);
    if(key == GLUT_KEY_LEFT) {
        pyramidFrame.RotateWorld(-step, 0.0f, 1.0f, 0.0f);
    } else if(key == GLUT_KEY_RIGHT) {
        pyramidFrame.RotateWorld(step, 0.0f, 1.0f, 0.0f);
    } else if(key == GLUT_KEY_UP) {
        pyramidFrame.RotateWorld(step, 1.0f, 0.0f, 0.0f);
    } else if(key == GLUT_KEY_DOWN) {
        pyramidFrame.RotateWorld(-step, 1.0f, 0.0f, 0.0f);
    }
    glutPostRedisplay();
}

void CreatePyramid(GLBatch &batch) {
    batch.Begin(GL_TRIANGLES, 18, 1);
    M3DVector3f vApex = {0.0f, 1.0f, 0.0f};
    M3DVector3f vFrontLeft = {-1.0f, -1.0f, 1.0f};
    M3DVector3f vFrontRight = {1.0f, -1.0f, 1.0f};
    M3DVector3f vBackLeft = {-1.0f, -1.0f, -1.0f};
    M3DVector3f vBackRight = {1.0f, -1.0f, -1.0f};
    M3DVector3f n;//normal

    M3DVector3f vTopDown = {0.0f, -1.0f, 0.0f};

    //floor right side
    batch.Normal3fv(vTopDown);
    batch.MultiTexCoord2f(0, 0.0f, 0.0f);
    batch.Vertex3fv(vBackLeft);

    batch.Normal3fv(vTopDown);
    batch.MultiTexCoord2f(0, 1.0f, 0.0f);
    batch.Vertex3fv(vBackRight);

    batch.Normal3fv(vTopDown);
    batch.MultiTexCoord2f(0, 1.0f, 1.0f);
    batch.Vertex3fv(vFrontRight);

    //floor left side
    batch.Normal3fv(vTopDown);
    batch.Vertex3fv(vFrontLeft);
    batch.Normal3fv(vTopDown);
    batch.Vertex3fv(vBackLeft);
    batch.Normal3fv(vTopDown);
    batch.Vertex3fv(vFrontRight);

    //front side
    m3dFindNormal(n, vApex, vFrontLeft, vFrontRight);
    batch.Normal3fv(n);
    batch.MultiTexCoord2f(0, 0.5f, 1.0f);
    batch.Vertex3fv(vApex);

    batch.Normal3fv(n);
    batch.MultiTexCoord2f(0, 0.0f, 0.0f);
    batch.Vertex3fv(vFrontLeft);

    batch.Normal3fv(n);
    batch.MultiTexCoord2f(0, 1.0f, 0.0f);
    batch.Vertex3fv(vFrontRight);

    //right side
    m3dFindNormal(n, vApex, vFrontRight, vBackRight);
    batch.Normal3fv(n);
    batch.Vertex3fv(vApex);
    batch.Normal3fv(n);
    batch.Vertex3fv(vFrontRight);
    batch.Normal3fv(n);
    batch.Vertex3fv(vBackRight);

    //left side
    m3dFindNormal(n, vApex, vBackLeft, vFrontLeft);
    batch.Normal3fv(n);
    batch.Vertex3fv(vApex);
    batch.Normal3fv(n);
    batch.Vertex3fv(vBackLeft);
    batch.Normal3fv(n);
    batch.Vertex3fv(vFrontLeft);

    //back side
    m3dFindNormal(n, vApex, vBackRight, vBackLeft);
    batch.Normal3fv(n);
    batch.Vertex3fv(vApex);
    batch.Normal3fv(n);
    batch.Vertex3fv(vBackRight);
    batch.Normal3fv(n);
    batch.Vertex3fv(vBackLeft);
    batch.End();
}

bool LoadTGATexture(const char *filename, GLenum minFilter, GLenum magFilter, GLenum wrapMode) {
    int width, height, components;
    GLenum format;
    GLbyte *pBits = gltReadTGABits(filename, &width, &height, &components, &format);
    if(pBits == NULL) {
        return false;
    }

    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, wrapMode);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, wrapMode);

    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, minFilter);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, magFilter);

    glPixelStorei(GL_UNPACK_ALIGNMENT, 1);
    glTexImage2D(GL_TEXTURE_2D, 0, components, width, height, 0, format, GL_UNSIGNED_BYTE, pBits);
    free(pBits);

    if(minFilter == GL_LINEAR_MIPMAP_LINEAR ||
        minFilter == GL_LINEAR_MIPMAP_NEAREST ||
        minFilter == GL_NEAREST_MIPMAP_LINEAR ||
        minFilter == GL_NEAREST_MIPMAP_NEAREST) {
        glGenerateMipmap(GL_TEXTURE_2D);
    }
    return true;
}

void RenderScene() {
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
    static GLfloat vLightPos[] = {0.0f, 10.0f, 1.0f, 1.0f};
    static GLfloat vLightColor[] = {1.0f, 1.0f, 1.0f, 1.0f};
    M3DMatrix44f cameraMatrix, pyramidMatrix;

    modelViewMatrix.PushMatrix();
        cameraFrame.GetCameraMatrix(cameraMatrix);
        modelViewMatrix.MultMatrix(cameraMatrix);
        pyramidFrame.GetMatrix(pyramidMatrix);
        modelViewMatrix.MultMatrix(pyramidMatrix);
        glBindTexture(GL_TEXTURE_2D, textureID);
        shaderManager.UseStockShader(GLT_SHADER_TEXTURE_POINT_LIGHT_DIFF, pipeline.GetModelViewMatrix(),
            pipeline.GetProjectionMatrix(), vLightPos, vLightColor, 0);
        pyramidBatch.Draw();
    modelViewMatrix.PopMatrix();
    glutSwapBuffers();
}

void SetupRC() {
    shaderManager.InitializeStockShaders();
    glClearColor(0.5f, 0.5f, 0.5f, 1.0f);
    glEnable(GL_DEPTH_TEST);
    CreatePyramid(pyramidBatch);
    textureID = 0;
    glGenTextures(1, &textureID);
    glBindTexture(GL_TEXTURE_2D, textureID);
    LoadTGATexture("stone.tga", GL_LINEAR, GL_LINEAR, GL_CLAMP_TO_EDGE);
    cameraFrame.MoveForward(-5.0f);
}

void ShutdownRC() {
    glDeleteTextures(1, &textureID);
}

int main(int argc, char *argv[]) {
    gltSetWorkingDirectory(argv[0]);

    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB | GLUT_DEPTH);
    glutInitWindowSize(1100, 800);
    glutCreateWindow("Pyramid");

    glutDisplayFunc(RenderScene);
    glutReshapeFunc(ChangeSize);
    glutSpecialFunc(HandleKeys);

    GLenum result = glewInit();
    if(result != GLEW_OK) {
        std::cerr << "Glew error: " << glewGetErrorString(result) << std::endl;
        return 1;
    }

    SetupRC();
    glutMainLoop();
    ShutdownRC();
    return 0;
}
[/PHP]

PS: the code is from the [OpenGL SuperBible 5th edition]("http://www.starstonesoftware.com/OpenGL/")

---

