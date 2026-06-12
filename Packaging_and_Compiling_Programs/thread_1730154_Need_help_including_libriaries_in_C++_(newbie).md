---
title: "Need help including libriaries in C++ (newbie)"
date: 2011-04-15
forum: Packaging and Compiling Programs
---

### Post by rob1101 on 2011-04-15
I a lot of experience in higher level languages like java and python, and so far everything for those languages has been pretty straight forward and have just worked. C++ is not bad either until I need to add a non standard library, then I am just lost. 

Everything I have searched for online regarding the subject either simply says add this path to that dialogue (which does not work), or goes way out of the scope for what I am trying to do, I just want to include someones library and be on my way.

I am trying to follow along in this book(5th edition) just to learn some openGL for 'fun'. I can compile and run the first two example programs fine with his supplied make files.

However when I try to recreate the projects in either Eclipse, CodeBlocks, or even moving everything to one folder and changing the paths in the make file they cannot find the required libraries (except for GLTools). No matter what paths i add to the compiler and linker search directories, GLTools is included fine but GLTools.h wishes to include glew.h, which I have added in the same way I did GLTools but the IDEs just complain that it cant be found.

This has been by far the most irritating little problem I have encountered in a while.

If anyone can help, it would be very much appreciated.

---

### Post by SevenMachines on 2011-04-16
If you could include example code of what your trying to do (using the forum ```
 tags) that would make it more clear. 

In general though, when using opengl on linux, you'll find everything in /usr/include/GL.

/usr/include is a system path, the compiler will search for included headers ( using the <> system header brackets ) relative to that directory so...
[CODE]#include <GL/glew.h> 
```would be be found since this equates to /usr/include/GL/glew.h

but..
```
#include <glew.h> 
```will not be found since this equates to /usr/include/glew.h, which doesnt exist.

To get the compiler to find this second examples headers you need to tell it where to look, you do this using the -I (capital i) parameter, eg
```
$ gcc -o hello hello.cpp -I/usr/include/GL
```Now the compiler will search /usr/include/GL and so find glew.h

Note this also works for libraries so, to add directories to the compilers library search path use '-L/some/path/to/library'

In eclipse adding header and library search paths and so on is done in 
project->properties->C/C++ General->Paths and Symbols

Sometimes this doesnt update the include paths correctly for me so be warned if it happens to you, luckily you can update them manually in
project->properties->C/C++ Build->Settings
and add the include directories whatever 'Includes' section you want to

---

### Post by rob1101 on 2011-04-27
Sorry for the delayed response. This is a personal side project that I'm working on in my spare time of which has been quite scarce lately. I really do appreciate your response, it has definitely helped me make progress.

The tutorials I am referring to are from the 5th edition of the [OpenGL Super Bible]("http://www.starstonesoftware.com/OpenGL/"), the full source to all the tutorials can be found on said website.

The book only explains how to set up the tutorials on Windows(Visual Studio) and briefly on OSX(Xcode). I believe the steps describe in the book lead to my confusion as to what was going on. Still being a novice at C++, and having most of my experience in higher level languages I decided to read up a bit more on [header files]("http://www.learncpp.com/cpp-tutorial/19-header-files/") and the [preprocessor]("http://www.learncpp.com/cpp-tutorial/110-a-first-look-at-the-preprocessor/"). (very helpful links, for anyone learning :))

Part of the confusion I had was not realizing that glut is a standard library and installed on my system in the directory you described. The same is not true for Windows, which you must manually add the library through Visual Studio (which is what I tried to do in eclipse). By adding "/usr/include/GL" to the include path glut.h can now be found.

The second library, GLTools is still giving me trouble however. If I understand correctly this is a 3rd partly library provided by the books author(s). The compiled .lib and the .a files are available for windows and OSX bun no linux build :(. However the .cpp source file is included. It seems that I have to build the GLTools library myself, however I am not entirely sure how to do this through eclipse, or make files for that matter which I am starting to read up again. 

I have included the source, to all the files mentioned above.


**Block.cpp** (first tutorial)
```

// Block.cpp
// OpenGL SuperBible, Chapter 1
// Demonstrates an assortment of basic 3D concepts
// Program by Richard S. Wright Jr.

#include <GLTools.h>    // OpenGL toolkit
#include <GLMatrixStack.h>
#include <GLFrame.h>
#include <GLFrustum.h>
#include <GLBatch.h>
#include <GLGeometryTransform.h>

#include <math.h>
#ifdef __APPLE__
#include <glut/glut.h>
#else
#define FREEGLUT_STATIC
#include <GL/glut.h>
#endif

/////////////////////////////////////////////////////////////////////////////////
// An assortment of needed classes
GLShaderManager        shaderManager;
GLMatrixStack        modelViewMatrix;
GLMatrixStack        projectionMatrix;
GLFrame                cameraFrame;
GLFrustum            viewFrustum;
GLBatch                cubeBatch;
GLBatch                floorBatch;
GLBatch                topBlock;
GLBatch                frontBlock;
GLBatch                leftBlock;

GLGeometryTransform    transformPipeline;
M3DMatrix44f        shadowMatrix;


// Keep track of effects step
int nStep = 0;

// Lighting data
GLfloat lightAmbient[] = { 0.2f, 0.2f, 0.2f, 1.0f };
GLfloat lightDiffuse[] = { 0.7f, 0.7f, 0.7f, 1.0f };
GLfloat lightSpecular[] = { 0.9f, 0.9f, 0.9f };
GLfloat vLightPos[] = { -8.0f, 20.0f, 100.0f, 1.0f };

GLuint textures[4];


///////////////////////////////////////////////////////////////////////////////
// Make a cube out of a batch of triangles. Texture coordinates and normals
// are also provided.
void MakeCube(GLBatch& cubeBatch)
    {
    cubeBatch.Begin(GL_TRIANGLES, 36, 1);

    /////////////////////////////////////////////
    // Top of cube
    cubeBatch.Normal3f(0.0f, 1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 1.0f);
    cubeBatch.Vertex3f(1.0f, 1.0f, 1.0f);

    cubeBatch.Normal3f(0.0f, 1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 0.0f);
    cubeBatch.Vertex3f(1.0f, 1.0f, -1.0f);

    cubeBatch.Normal3f(0.0f, 1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f);
    cubeBatch.Vertex3f(-1.0f, 1.0f, -1.0f);

    cubeBatch.Normal3f(0.0f, 1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 1.0f);
    cubeBatch.Vertex3f(1.0f, 1.0f, 1.0f);

    cubeBatch.Normal3f(0.0f, 1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f);
    cubeBatch.Vertex3f(-1.0f, 1.0f, -1.0f);

    cubeBatch.Normal3f(0.0f, 1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 1.0f);
    cubeBatch.Vertex3f(-1.0f, 1.0f, 1.0f);


    ////////////////////////////////////////////
    // Bottom of cube
    cubeBatch.Normal3f(0.0f, -1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f);
    cubeBatch.Vertex3f(-1.0f, -1.0f, -1.0f);

    cubeBatch.Normal3f(0.0f, -1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 0.0f);
    cubeBatch.Vertex3f(1.0f, -1.0f, -1.0f);

    cubeBatch.Normal3f(0.0f, -1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 1.0f);
    cubeBatch.Vertex3f(1.0f, -1.0f, 1.0f);

    cubeBatch.Normal3f(0.0f, -1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 1.0f);
    cubeBatch.Vertex3f(-1.0f, -1.0f, 1.0f);

    cubeBatch.Normal3f(0.0f, -1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f);
    cubeBatch.Vertex3f(-1.0f, -1.0f, -1.0f);

    cubeBatch.Normal3f(0.0f, -1.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 1.0f);
    cubeBatch.Vertex3f(1.0f, -1.0f, 1.0f);

    ///////////////////////////////////////////
    // Left side of cube
    cubeBatch.Normal3f(-1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 1.0f);
    cubeBatch.Vertex3f(-1.0f, 1.0f, 1.0f);

    cubeBatch.Normal3f(-1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 0.0f);
    cubeBatch.Vertex3f(-1.0f, 1.0f, -1.0f);

    cubeBatch.Normal3f(-1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f);
    cubeBatch.Vertex3f(-1.0f, -1.0f, -1.0f);

    cubeBatch.Normal3f(-1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 1.0f);
    cubeBatch.Vertex3f(-1.0f, 1.0f, 1.0f);

    cubeBatch.Normal3f(-1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f);
    cubeBatch.Vertex3f(-1.0f, -1.0f, -1.0f);

    cubeBatch.Normal3f(-1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 1.0f);
    cubeBatch.Vertex3f(-1.0f, -1.0f, 1.0f);

    // Right side of cube
    cubeBatch.Normal3f(1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f);
    cubeBatch.Vertex3f(1.0f, -1.0f, -1.0f);

    cubeBatch.Normal3f(1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 0.0f);
    cubeBatch.Vertex3f(1.0f, 1.0f, -1.0f);

    cubeBatch.Normal3f(1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 1.0f);
    cubeBatch.Vertex3f(1.0f, 1.0f, 1.0f);

    cubeBatch.Normal3f(1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 1.0f);
    cubeBatch.Vertex3f(1.0f, 1.0f, 1.0f);

    cubeBatch.Normal3f(1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 1.0f);
    cubeBatch.Vertex3f(1.0f, -1.0f, 1.0f);

    cubeBatch.Normal3f(1.0f, 0.0f, 0.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f);
    cubeBatch.Vertex3f(1.0f, -1.0f, -1.0f);

    // Front and Back
    // Front
    cubeBatch.Normal3f(0.0f, 0.0f, 1.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 0.0f);
    cubeBatch.Vertex3f(1.0f, -1.0f, 1.0f);

    cubeBatch.Normal3f(0.0f, 0.0f, 1.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 1.0f);
    cubeBatch.Vertex3f(1.0f, 1.0f, 1.0f);

    cubeBatch.Normal3f(0.0f, 0.0f, 1.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 1.0f);
    cubeBatch.Vertex3f(-1.0f, 1.0f, 1.0f);

    cubeBatch.Normal3f(0.0f, 0.0f, 1.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 1.0f);
    cubeBatch.Vertex3f(-1.0f, 1.0f, 1.0f);

    cubeBatch.Normal3f(0.0f, 0.0f, 1.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f);
    cubeBatch.Vertex3f(-1.0f, -1.0f, 1.0f);

    cubeBatch.Normal3f(0.0f, 0.0f, 1.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 0.0f);
    cubeBatch.Vertex3f(1.0f, -1.0f, 1.0f);

    // Back
    cubeBatch.Normal3f(0.0f, 0.0f, -1.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 0.0f);
    cubeBatch.Vertex3f(1.0f, -1.0f, -1.0f);

    cubeBatch.Normal3f(0.0f, 0.0f, -1.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f);
    cubeBatch.Vertex3f(-1.0f, -1.0f, -1.0f);

    cubeBatch.Normal3f(0.0f, 0.0f, -1.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 1.0f);
    cubeBatch.Vertex3f(-1.0f, 1.0f, -1.0f);

    cubeBatch.Normal3f(0.0f, 0.0f, -1.0f);
    cubeBatch.MultiTexCoord2f(0, 0.0f, 1.0f);
    cubeBatch.Vertex3f(-1.0f, 1.0f, -1.0f);

    cubeBatch.Normal3f(0.0f, 0.0f, -1.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 1.0f);
    cubeBatch.Vertex3f(1.0f, 1.0f, -1.0f);

    cubeBatch.Normal3f(0.0f, 0.0f, -1.0f);
    cubeBatch.MultiTexCoord2f(0, 1.0f, 0.0f);
    cubeBatch.Vertex3f(1.0f, -1.0f, -1.0f);

    cubeBatch.End();
    }

/////////////////////////////////////////////////////////////////////////////
// Make the floor, just the verts and texture coordinates, no normals
void MakeFloor(GLBatch& floorBatch)
    {
    GLfloat x = 5.0f;
    GLfloat y = -1.0f;

    floorBatch.Begin(GL_TRIANGLE_FAN, 4, 1);
        floorBatch.MultiTexCoord2f(0, 0.0f, 0.0f);
        floorBatch.Vertex3f(-x, y, x);

        floorBatch.MultiTexCoord2f(0, 1.0f, 0.0f);
        floorBatch.Vertex3f(x, y, x);

        floorBatch.MultiTexCoord2f(0, 1.0f, 1.0f);
        floorBatch.Vertex3f(x, y, -x);

        floorBatch.MultiTexCoord2f(0, 0.0f, 1.0f);
        floorBatch.Vertex3f(-x, y, -x);
    floorBatch.End();
    }


///////////////////////////////////////////////////////////////////////////////
// This function does any needed initialization on the rendering context.
// This is the first opportunity to do any OpenGL related tasks.
void SetupRC()
    {
    GLbyte *pBytes;
    GLint nWidth, nHeight, nComponents;
    GLenum format;

    shaderManager.InitializeStockShaders();

    // Black background
    glClearColor(0.0f, 0.0f, 0.0f, 1.0f );
    glEnable(GL_DEPTH_TEST);
    glLineWidth(2.5f);
    glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);
    glHint(GL_LINE_SMOOTH_HINT, GL_NICEST);

    transformPipeline.SetMatrixStacks(modelViewMatrix, projectionMatrix);

    cameraFrame.MoveForward(-15.0f);
    cameraFrame.MoveUp(6.0f);
    cameraFrame.RotateLocalX(float(m3dDegToRad(20.0f)));

    MakeCube(cubeBatch);
    MakeFloor(floorBatch);

    // Make top
    topBlock.Begin(GL_TRIANGLE_FAN, 4, 1);
        topBlock.Normal3f(0.0f, 1.0f, 0.0f);
        topBlock.MultiTexCoord2f(0, 0.0f, 0.0f);
        topBlock.Vertex3f(-1.0f, 1.0f, 1.0f);

        topBlock.Normal3f(0.0f, 1.0f, 0.0f);
        topBlock.MultiTexCoord2f(0, 1.0f, 0.0f);
        topBlock.Vertex3f(1.0f, 1.0f, 1.0f);

        topBlock.Normal3f(0.0f, 1.0f, 0.0f);
        topBlock.MultiTexCoord2f(0, 1.0f, 1.0f);
        topBlock.Vertex3f(1.0f, 1.0f, -1.0f);

        topBlock.Normal3f(0.0f, 1.0f, 0.0f);
        topBlock.MultiTexCoord2f(0, 0.0f, 1.0f);
        topBlock.Vertex3f(-1.0f, 1.0f, -1.0f);
    topBlock.End();

    // Make Front
    frontBlock.Begin(GL_TRIANGLE_FAN, 4, 1);
        frontBlock.Normal3f(0.0f, 0.0f, 1.0f);
        frontBlock.MultiTexCoord2f(0, 0.0f, 0.0f);
        frontBlock.Vertex3f(-1.0f, -1.0f, 1.0f);

        frontBlock.Normal3f(0.0f, 0.0f, 1.0f);
        frontBlock.MultiTexCoord2f(0, 1.0f, 0.0f);
        frontBlock.Vertex3f(1.0f, -1.0f, 1.0f);

        frontBlock.Normal3f(0.0f, 0.0f, 1.0f);
        frontBlock.MultiTexCoord2f(0, 1.0f, 1.0f);
        frontBlock.Vertex3f(1.0f, 1.0f, 1.0f);

        frontBlock.Normal3f(0.0f, 0.0f, 1.0f);
        frontBlock.MultiTexCoord2f(0, 0.0f, 1.0f);
        frontBlock.Vertex3f(-1.0f, 1.0f, 1.0f);
    frontBlock.End();

    // Make left
    leftBlock.Begin(GL_TRIANGLE_FAN, 4, 1);
        leftBlock.Normal3f(-1.0f, 0.0f, 0.0f);
        leftBlock.MultiTexCoord2f(0, 0.0f, 0.0f);
        leftBlock.Vertex3f(-1.0f, -1.0f, -1.0f);

        leftBlock.Normal3f(-1.0f, 0.0f, 0.0f);
        leftBlock.MultiTexCoord2f(0, 1.0f, 0.0f);
        leftBlock.Vertex3f(-1.0f, -1.0f, 1.0f);

        leftBlock.Normal3f(-1.0f, 0.0f, 0.0f);
        leftBlock.MultiTexCoord2f(0, 1.0f, 1.0f);
        leftBlock.Vertex3f(-1.0f, 1.0f, 1.0f);

        leftBlock.Normal3f(-1.0f, 0.0f, 0.0f);
        leftBlock.MultiTexCoord2f(0, 0.0f, 1.0f);
        leftBlock.Vertex3f(-1.0f, 1.0f, -1.0f);
    leftBlock.End();

    // Create shadow projection matrix
    GLfloat floorPlane[] = { 0.0f, 1.0f, 0.0f, 1.0f};
    m3dMakePlanarShadowMatrix(shadowMatrix, floorPlane, vLightPos);

    // Load up four textures
    glGenTextures(4, textures);

    // Wood floor
    pBytes = gltReadTGABits("floor.tga", &nWidth, &nHeight, &nComponents, &format);
    glBindTexture(GL_TEXTURE_2D, textures[0]);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
    glTexImage2D(GL_TEXTURE_2D,0,nComponents,nWidth, nHeight, 0,
        format, GL_UNSIGNED_BYTE, pBytes);
    free(pBytes);

    // One of the block faces
    pBytes = gltReadTGABits("Block4.tga", &nWidth, &nHeight, &nComponents, &format);
    glBindTexture(GL_TEXTURE_2D, textures[1]);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
    glTexImage2D(GL_TEXTURE_2D,0,nComponents,nWidth, nHeight, 0,
        format, GL_UNSIGNED_BYTE, pBytes);
    free(pBytes);

    // Another block face
    pBytes = gltReadTGABits("Block5.tga", &nWidth, &nHeight, &nComponents, &format);
        glBindTexture(GL_TEXTURE_2D, textures[2]);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
    glTexImage2D(GL_TEXTURE_2D,0,nComponents,nWidth, nHeight, 0,
        format, GL_UNSIGNED_BYTE, pBytes);
    free(pBytes);

    // Yet another block face
    pBytes = gltReadTGABits("Block6.tga", &nWidth, &nHeight, &nComponents, &format);
        glBindTexture(GL_TEXTURE_2D, textures[3]);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_LINEAR);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
    glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
    glTexImage2D(GL_TEXTURE_2D,0,nComponents,nWidth, nHeight, 0,
        format, GL_UNSIGNED_BYTE, pBytes);
    free(pBytes);
    }




///////////////////////////////////////////////////////////////////////////////
// Render the block
void RenderBlock(void)
    {
    GLfloat vRed[] = { 1.0f, 0.0f, 0.0f, 1.0f};
    GLfloat vWhite[] = { 1.0f, 1.0f, 1.0f, 1.0f };

    switch(nStep)
        {
        // Wire frame
        case 0:
            glEnable(GL_BLEND);
            glEnable(GL_LINE_SMOOTH);
            shaderManager.UseStockShader(GLT_SHADER_FLAT, transformPipeline.GetModelViewProjectionMatrix(), vRed);
            glPolygonMode(GL_FRONT_AND_BACK, GL_LINE);
            glDisable(GL_CULL_FACE);

            // Draw the cube
            cubeBatch.Draw();

            break;

        // Wire frame, but not the back side... we also want the block to be in the stencil buffer
        case 1:
            shaderManager.UseStockShader(GLT_SHADER_FLAT, transformPipeline.GetModelViewProjectionMatrix(), vRed);

            // Draw solid block in stencil buffer
            // Back face culling prevents the back sides from showing through
            // The stencil pattern is used to mask when we draw the floor under it
            // to keep it from showing through.
            glPolygonMode(GL_FRONT_AND_BACK, GL_FILL);
            glEnable(GL_STENCIL_TEST);
            glStencilFunc(GL_NEVER, 0, 0);
            glStencilOp(GL_INCR, GL_INCR, GL_INCR);
            cubeBatch.Draw();
            glStencilOp(GL_KEEP, GL_KEEP, GL_KEEP);
            glDisable(GL_STENCIL_TEST);

            glEnable(GL_BLEND);
            glEnable(GL_LINE_SMOOTH);
            glPolygonMode(GL_FRONT_AND_BACK, GL_LINE);

            // Draw the front side cube
            cubeBatch.Draw();
            break;

        // Solid
        case 2:
            shaderManager.UseStockShader(GLT_SHADER_FLAT, transformPipeline.GetModelViewProjectionMatrix(), vRed);

            // Draw the cube
            cubeBatch.Draw();
            break;

        // Lit
        case 3:
            shaderManager.UseStockShader(GLT_SHADER_POINT_LIGHT_DIFF, modelViewMatrix.GetMatrix(),
                projectionMatrix.GetMatrix(), vLightPos, vRed);

            // Draw the cube
            cubeBatch.Draw();
            break;

        // Textured & Lit
        case 4:
        case 5:
        default:
            glBindTexture(GL_TEXTURE_2D, textures[2]);
            shaderManager.UseStockShader(GLT_SHADER_TEXTURE_POINT_LIGHT_DIFF, modelViewMatrix.GetMatrix(),
                projectionMatrix.GetMatrix(), vLightPos, vWhite, 0);

            glBindTexture(GL_TEXTURE_2D, textures[1]);
            topBlock.Draw();
            glBindTexture(GL_TEXTURE_2D, textures[2]);
            frontBlock.Draw();
            glBindTexture(GL_TEXTURE_2D, textures[3]);
            leftBlock.Draw();

            break;
        }

    // Put everything back
    glPolygonMode(GL_FRONT_AND_BACK, GL_FILL);
    glEnable(GL_CULL_FACE);
    glDisable(GL_BLEND);
    glDisable(GL_LINE_SMOOTH);
    glDisable(GL_STENCIL_TEST);
    }

///////////////////////////////////////////////////////////////////////////////
// Render the floor
void RenderFloor(void)
    {
    GLfloat vBrown [] = { 0.55f, 0.292f, 0.09f, 1.0f};
    GLfloat vFloor[] = { 1.0f, 1.0f, 1.0f, 0.6f };

    switch(nStep)
        {
        // Wire frame
        case 0:
            glEnable(GL_BLEND);
            glEnable(GL_LINE_SMOOTH);
            shaderManager.UseStockShader(GLT_SHADER_FLAT, transformPipeline.GetModelViewProjectionMatrix(), vBrown);
            glPolygonMode(GL_FRONT_AND_BACK, GL_LINE);
            glDisable(GL_CULL_FACE);
            break;

        // Wire frame, but not the back side.. and only where stencil == 0
        case 1:
            glEnable(GL_BLEND);
            glEnable(GL_LINE_SMOOTH);

            glEnable(GL_STENCIL_TEST);
            glStencilFunc(GL_EQUAL, 0, 0xff);

            shaderManager.UseStockShader(GLT_SHADER_FLAT, transformPipeline.GetModelViewProjectionMatrix(), vBrown);
            glPolygonMode(GL_FRONT_AND_BACK, GL_LINE);
            break;

        // Solid
        case 2:
        case 3:
            shaderManager.UseStockShader(GLT_SHADER_FLAT, transformPipeline.GetModelViewProjectionMatrix(), vBrown);
            break;

        // Textured
        case 4:
        case 5:
        default:
            glBindTexture(GL_TEXTURE_2D, textures[0]);
            shaderManager.UseStockShader(GLT_SHADER_TEXTURE_MODULATE, transformPipeline.GetModelViewProjectionMatrix(), vFloor, 0);
            break;
        }

    // Draw the floor
    floorBatch.Draw();

    // Put everything back
    glPolygonMode(GL_FRONT_AND_BACK, GL_FILL);
    glEnable(GL_CULL_FACE);
    glDisable(GL_BLEND);
    glDisable(GL_LINE_SMOOTH);
    glDisable(GL_STENCIL_TEST);
    }



///////////////////////////////////////////////////////////////////////////////
// Called to draw scene
void RenderScene(void)
    {
    // Clear the window with current clearing color
    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT | GL_STENCIL_BUFFER_BIT);

    modelViewMatrix.PushMatrix();
        M3DMatrix44f mCamera;
        cameraFrame.GetCameraMatrix(mCamera);
        modelViewMatrix.MultMatrix(mCamera);

        // Reflection step... draw cube upside down, the floor
        // blended on top of it
        if(nStep == 5) {
            glDisable(GL_CULL_FACE);
            modelViewMatrix.PushMatrix();
            modelViewMatrix.Scale(1.0f, -1.0f, 1.0f);
            modelViewMatrix.Translate(0.0f, 2.0f, 0.0f);
            modelViewMatrix.Rotate(35.0f, 0.0f, 1.0f, 0.0f);
            RenderBlock();
            modelViewMatrix.PopMatrix();
            glEnable(GL_BLEND);
            glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);
            RenderFloor();
            glDisable(GL_BLEND);
            }


        modelViewMatrix.PushMatrix();

            // Draw normally
            modelViewMatrix.Rotate(35.0f, 0.0f, 1.0f, 0.0f);
            RenderBlock();
        modelViewMatrix.PopMatrix();


    // If not the reflection pass, draw floor last
    if(nStep != 5)
        RenderFloor();


    modelViewMatrix.PopMatrix();


    // Flush drawing commands
    glutSwapBuffers();
    }


///////////////////////////////////////////////////////////////////////////////
// A normal ASCII key has been pressed.
// In this case, advance the scene when the space bar is pressed
void KeyPressFunc(unsigned char key, int x, int y)
    {
    if(key == 32)
        {
        nStep++;

        if(nStep > 5)
            nStep = 0;
        }

    // Refresh the Window
    glutPostRedisplay();
    }

///////////////////////////////////////////////////////////////////////////////
// Window has changed size, or has just been created. In either case, we need
// to use the window dimensions to set the viewport and the projection matrix.
void ChangeSize(int w, int h)
    {
    glViewport(0, 0, w, h);
    viewFrustum.SetPerspective(35.0f, float(w) / float(h), 1.0f, 500.0f);
    projectionMatrix.LoadMatrix(viewFrustum.GetProjectionMatrix());
    modelViewMatrix.LoadIdentity();
    }

///////////////////////////////////////////////////////////////////////////////
// Main entry point for GLUT based programs
int main(int argc, char* argv[])
    {
    gltSetWorkingDirectory(argv[0]);

    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGBA | GLUT_DEPTH | GLUT_STENCIL);
    glutInitWindowSize(800, 600);
    glutCreateWindow("3D Effects Demo");

    GLenum err = glewInit();
    if (GLEW_OK != err)
        {
        /* Problem: glewInit failed, something is seriously wrong. */
        fprintf(stderr, "Error: %s\n", glewGetErrorString(err));
        return 1;
        }

    glutReshapeFunc(ChangeSize);
    glutKeyboardFunc(KeyPressFunc);
    glutDisplayFunc(RenderScene);

    SetupRC();

    glutMainLoop();
    glDeleteTextures(4,textures);
    return 0;
    }

```

**GLTools.h**
```
// GLTools.h 
// OpenGL SuperBible 
/* Copyright 1998 - 2003 Richard S. Wright Jr. 
All rights reserved. 
 
Redistribution and use in source and binary forms, with or without modification,  
are permitted provided that the following conditions are met: 
 
Redistributions of source code must retain the above copyright notice, this list  
of conditions and the following disclaimer. 
 
Redistributions in binary form must reproduce the above copyright notice, this list  
of conditions and the following disclaimer in the documentation and/or other  
materials provided with the distribution. 
 
Neither the name of Richard S. Wright Jr. nor the names of other contributors may be used  
to endorse or promote products derived from this software without specific prior  
written permission. 
 
THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY  
EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES  
OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT  
SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT,  
INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED  
TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR  
BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN  
CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN  
ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE. 
*/ 
 
#ifndef __GLTOOLS__LIBRARY 
#define __GLTOOLS__LIBRARY 
 
 
// There is a static block allocated for loading shaders to  
// prevent heap fragmentation 
#define MAX_SHADER_LENGTH   8192 
 
 
// Bring in OpenGL  
// Windows 
#ifdef WIN32 
#include <windows.h>        // Must have for Windows platform builds 
#ifndef GLEW_STATIC 
#define GLEW_STATIC 
#endif 
 
#include <gl\glew.h>            // OpenGL Extension "autoloader" 
#include <gl\gl.h>            // Microsoft OpenGL headers (version 1.1 by themselves) 
#endif 
 
// Mac OS X 
#ifdef __APPLE__ 
#include <stdlib.h> 
 
#include <TargetConditionals.h> 
#if TARGET_OS_IPHONE | TARGET_IPHONE_SIMULATOR 
#include <OpenGLES/ES2/gl.h> 
#include <OpenGLES/ES2/glext.h> 
#define OPENGL_ES 
#else 
#include <GL/glew.h> 
#include <OpenGL/gl.h>        // Apple OpenGL haders (version depends on OS X SDK version) 
#endif 
#endif 
 
// Linux 
#ifdef linux 
#define GLEW_STATIC 
#include <glew.h> 
#endif 
 
//////////////////////// TEMPORARY TEMPORARY TEMPORARY - On SnowLeopard this is suppored, but GLEW doens't hook up properly 
//////////////////////// Fixed probably in 10.6.3 
#ifdef __APPLE__ 
#define glGenVertexArrays glGenVertexArraysAPPLE 
#define glDeleteVertexArrays  glDeleteVertexArraysAPPLE 
#define glBindVertexArray    glBindVertexArrayAPPLE 
#ifndef OPENGL_ES 
#define glGenerateMipmap    glGenerateMipmapEXT 
#endif 
#endif 
 
 
// Universal includes 
#include <stdio.h> 
#include <math.h> 
#include <math3d.h> 
#include <GLBatch.h> 
#include <GLTriangleBatch.h> 
 
    
/////////////////////////////////////////////////////// 
// Macros for big/little endian happiness 
// These are intentionally written to be easy to understand what they  
// are doing... no flames please on the inefficiency of these. 
#ifdef __BIG_ENDIAN__ 
/////////////////////////////////////////////////////////// 
// This function says, "this pointer is a little endian value" 
// If the value must be changed it is... otherwise, this 
// function is defined away below (on Intel systems for example) 
inline void LITTLE_ENDIAN_WORD(void *pWord) 
    { 
    unsigned char *pBytes = (unsigned char *)pWord; 
    unsigned char temp; 
     
    temp = pBytes[0]; 
    pBytes[0] = pBytes[1]; 
    pBytes[1] = temp; 
    } 
 
/////////////////////////////////////////////////////////// 
// This function says, "this pointer is a little endian value" 
// If the value must be changed it is... otherwise, this 
// function is defined away below (on Intel systems for example) 
inline void LITTLE_ENDIAN_DWORD(void *pWord) 
    { 
    unsigned char *pBytes = (unsigned char *)pWord; 
    unsigned char temp; 
     
    // Swap outer bytes 
    temp = pBytes[3]; 
    pBytes[3] = pBytes[0]; 
    pBytes[0] = temp; 
     
    // Swap inner bytes 
    temp = pBytes[1]; 
    pBytes[1] = pBytes[2]; 
    pBytes[2] = temp; 
    } 
#else 
 
// Define them away on little endian systems 
#define LITTLE_ENDIAN_WORD  
#define LITTLE_ENDIAN_DWORD  
#endif 
 
 
/////////////////////////////////////////////////////////////////////////////// 
//         THE LIBRARY.... 
/////////////////////////////////////////////////////////////////////////////// 
 
// Get the OpenGL version 
void gltGetOpenGLVersion(GLint &nMajor, GLint &nMinor); 
 
// Check to see if an exension is supported 
int gltIsExtSupported(const char *szExtension); 
 
// Set working directoyr to /Resources on the Mac 
void gltSetWorkingDirectory(const char *szArgv); 
 
/////////////////////////////////////////////////////////////////////////////// 
GLbyte* gltReadBMPBits(const char *szFileName, int *nWidth, int *nHeight); 
 
///////////////////////////////////////////////////////////////////////////////////// 
// Load a .TGA file 
GLbyte *gltReadTGABits(const char *szFileName, GLint *iWidth, GLint *iHeight, GLint *iComponents, GLenum *eFormat, GLbyte *pData = NULL); 
 
// Capture the frame buffer and write it as a .tga 
// Does not work on the iPhone 
#ifndef OPENGL_ES 
GLint gltGrabScreenTGA(const char *szFileName); 
#endif 
 
 
// Make Objects 
void gltMakeTorus(GLTriangleBatch& torusBatch, GLfloat majorRadius, GLfloat minorRadius, GLint numMajor, GLint numMinor); 
void gltMakeSphere(GLTriangleBatch& sphereBatch, GLfloat fRadius, GLint iSlices, GLint iStacks); 
void gltMakeDisk(GLTriangleBatch& diskBatch, GLfloat innerRadius, GLfloat outerRadius, GLint nSlices, GLint nStacks); 
void gltMakeCylinder(GLTriangleBatch& cylinderBatch, GLfloat baseRadius, GLfloat topRadius, GLfloat fLength, GLint numSlices, GLint numStacks); 
void gltMakeCube(GLBatch& cubeBatch, GLfloat fRadius); 
 
// Shader loading support 
void    gltLoadShaderSrc(const char *szShaderSrc, GLuint shader); 
bool    gltLoadShaderFile(const char *szFile, GLuint shader); 
 
GLuint    gltLoadShaderPair(const char *szVertexProg, const char *szFragmentProg); 
GLuint   gltLoadShaderPairWithAttributes(const char *szVertexProg, const char *szFragmentProg, ...); 
GLuint gltLoadShaderTripletWithAttributes(const char *szVertexShader, 
                                          const char *szGeometryShader, 
                                          const char *szFragmentShader, ...); 
 
GLuint gltLoadShaderPairSrc(const char *szVertexSrc, const char *szFragmentSrc); 
GLuint gltLoadShaderPairSrcWithAttributes(const char *szVertexProg, const char *szFragmentProg, ...); 
 
bool gltCheckErrors(GLuint progName = 0); 
void gltGenerateOrtho2DMat(GLuint width, GLuint height, M3DMatrix44f &orthoMatrix, GLBatch &screenQuad); 
 
 
#endif
```

**GLTools.cpp**
```
/* 
 *  gltools.cpp 
 * 
 *  Created by Richard Wright on 10/16/06. 
 *  OpenGL SuperBible, 5th Edition 
 * 
 */ 
/* Copyright (c) 2005-2010, Richard S. Wright Jr. 
All rights reserved. 
 
Redistribution and use in source and binary forms, with or without modification,  
are permitted provided that the following conditions are met: 
 
Redistributions of source code must retain the above copyright notice, this list  
of conditions and the following disclaimer. 
 
Redistributions in binary form must reproduce the above copyright notice, this list  
of conditions and the following disclaimer in the documentation and/or other  
materials provided with the distribution. 
 
Neither the name of Richard S. Wright Jr. nor the names of other contributors may be used  
to endorse or promote products derived from this software without specific prior  
written permission. 
 
THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY  
EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES  
OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT  
SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT,  
INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED  
TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR  
BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN  
CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN  
ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE. 
*/ 
 
#include <GLTools.h> 
#include <math3d.h> 
#include <GLTriangleBatch.h> 
#include <stdio.h> 
#include <assert.h> 
#include <stdarg.h> 
 
#ifdef linux 
#include <cstdlib>  
#endif 
#ifdef __APPLE__ 
#include <unistd.h> 
#endif 
 
/////////////////////////////////////////////////////////////////////////////// 
// Get the OpenGL version number 
void gltGetOpenGLVersion(GLint &nMajor, GLint &nMinor) 
    { 
    #ifndef OPENGL_ES        
    glGetIntegerv(GL_MAJOR_VERSION, &nMajor); 
    glGetIntegerv(GL_MINOR_VERSION, &nMinor); 
    #else 
    const char *szVersionString = (const char *)glGetString(GL_VERSION); 
    if(szVersionString == NULL) 
        { 
        nMajor = 0; 
        nMinor = 0; 
        return; 
        } 
     
    // Get major version number. This stops at the first non numeric character 
    nMajor = atoi(szVersionString); 
     
    // Get minor version number. Start past the first ".", atoi terminates on first non numeric char. 
    nMinor = atoi(strstr(szVersionString, ".")+1); 
    #endif 
    } 
 
/////////////////////////////////////////////////////////////////////////////// 
// This function determines if the named OpenGL Extension is supported 
// Returns 1 or 0 
int gltIsExtSupported(const char *extension) 
    { 
    #ifndef OPENGL_ES        
    GLint nNumExtensions; 
    glGetIntegerv(GL_NUM_EXTENSIONS, &nNumExtensions); 
     
    for(GLint i = 0; i < nNumExtensions; i++) 
        if(strcmp(extension, (const char *)glGetStringi(GL_EXTENSIONS, i)) == 0) 
           return 1; 
    #else 
        GLubyte *extensions = NULL; 
        const GLubyte *start; 
        GLubyte *where, *terminator; 
         
        where = (GLubyte *) strchr(extension, ' '); 
        if (where || *extension == '\0') 
            return 0; 
         
        extensions = (GLubyte *)glGetString(GL_EXTENSIONS); 
         
        start = extensions; 
        for (;;)  
        { 
            where = (GLubyte *) strstr((const char *) start, extension); 
             
            if (!where) 
                break; 
             
            terminator = where + strlen(extension); 
             
            if (where == start || *(where - 1) == ' ')  
            { 
                if (*terminator == ' ' || *terminator == '\0')  
                    return 1; 
            } 
            start = terminator; 
        } 
    #endif 
    return 0; 
    } 
 
///////////////////////////////////////////////////////////////////////////////// 
// No-op on anything other than the Mac, sets the working directory to  
// the /Resources folder 
void gltSetWorkingDirectory(const char *szArgv) 
    { 
    #ifdef __APPLE__ 
    static char szParentDirectory[255];        
 
    ///////////////////////////////////////////////////////////////////////////    
    // Get the directory where the .exe resides 
    char *c; 
    strncpy( szParentDirectory, szArgv, sizeof(szParentDirectory) ); 
    szParentDirectory[254] = '\0'; // Make sure we are NULL terminated 
     
    c = (char*) szParentDirectory; 
 
    while (*c != '\0')     // go to end  
    c++; 
 
    while (*c != '/')      // back up to parent  
    c--; 
 
    *c++ = '\0';           // cut off last part (binary name)  
 
    ///////////////////////////////////////////////////////////////////////////    
    // Change to Resources directory. Any data files need to be placed there  
    chdir(szParentDirectory); 
#ifndef OPENGL_ES 
    chdir("../Resources"); 
#endif 
    #endif 
    } 
 
 
// Draw a torus (doughnut)  at z = fZVal... torus is in xy plane 
void gltMakeTorus(GLTriangleBatch& torusBatch, GLfloat majorRadius, GLfloat minorRadius, GLint numMajor, GLint numMinor) 
    { 
    double majorStep = 2.0f*M3D_PI / numMajor; 
    double minorStep = 2.0f*M3D_PI / numMinor; 
    int i, j; 
     
    torusBatch.BeginMesh(numMajor * (numMinor+1) * 6); 
    for (i=0; i<numMajor; ++i)  
        { 
        double a0 = i * majorStep; 
        double a1 = a0 + majorStep; 
        GLfloat x0 = (GLfloat) cos(a0); 
        GLfloat y0 = (GLfloat) sin(a0); 
        GLfloat x1 = (GLfloat) cos(a1); 
        GLfloat y1 = (GLfloat) sin(a1); 
 
        M3DVector3f vVertex[4]; 
        M3DVector3f vNormal[4]; 
        M3DVector2f vTexture[4]; 
         
        for (j=0; j<=numMinor; ++j)  
            { 
            double b = j * minorStep; 
            GLfloat c = (GLfloat) cos(b); 
            GLfloat r = minorRadius * c + majorRadius; 
            GLfloat z = minorRadius * (GLfloat) sin(b); 
             
            // First point 
            vTexture[0][0] = (float)(i)/(float)(numMajor); 
            vTexture[0][1] = (float)(j)/(float)(numMinor); 
            vNormal[0][0] = x0*c; 
            vNormal[0][1] = y0*c; 
            vNormal[0][2] = z/minorRadius; 
            m3dNormalizeVector3(vNormal[0]); 
            vVertex[0][0] = x0 * r; 
            vVertex[0][1] = y0 * r; 
            vVertex[0][2] = z; 
             
            // Second point 
            vTexture[1][0] = (float)(i+1)/(float)(numMajor); 
            vTexture[1][1] = (float)(j)/(float)(numMinor); 
            vNormal[1][0] = x1*c; 
            vNormal[1][1] = y1*c; 
            vNormal[1][2] = z/minorRadius; 
            m3dNormalizeVector3(vNormal[1]); 
            vVertex[1][0] = x1*r; 
            vVertex[1][1] = y1*r; 
            vVertex[1][2] = z; 
 
            // Next one over 
            b = (j+1) * minorStep; 
            c = (GLfloat) cos(b); 
            r = minorRadius * c + majorRadius; 
            z = minorRadius * (GLfloat) sin(b); 
                         
            // Third (based on first) 
            vTexture[2][0] = (float)(i)/(float)(numMajor); 
            vTexture[2][1] = (float)(j+1)/(float)(numMinor); 
            vNormal[2][0] = x0*c; 
            vNormal[2][1] = y0*c; 
            vNormal[2][2] = z/minorRadius; 
            m3dNormalizeVector3(vNormal[2]); 
            vVertex[2][0] = x0 * r; 
            vVertex[2][1] = y0 * r; 
            vVertex[2][2] = z; 
             
            // Fourth (based on second) 
            vTexture[3][0] = (float)(i+1)/(float)(numMajor); 
            vTexture[3][1] = (float)(j+1)/(float)(numMinor); 
            vNormal[3][0] = x1*c; 
            vNormal[3][1] = y1*c; 
            vNormal[3][2] = z/minorRadius; 
            m3dNormalizeVector3(vNormal[3]); 
            vVertex[3][0] = x1*r; 
            vVertex[3][1] = y1*r; 
            vVertex[3][2] = z; 
 
            torusBatch.AddTriangle(vVertex, vNormal, vTexture);             
             
            // Rearrange for next triangle 
            memcpy(vVertex[0], vVertex[1], sizeof(M3DVector3f)); 
            memcpy(vNormal[0], vNormal[1], sizeof(M3DVector3f)); 
            memcpy(vTexture[0], vTexture[1], sizeof(M3DVector2f)); 
             
            memcpy(vVertex[1], vVertex[3], sizeof(M3DVector3f)); 
            memcpy(vNormal[1], vNormal[3], sizeof(M3DVector3f)); 
            memcpy(vTexture[1], vTexture[3], sizeof(M3DVector2f)); 
                     
            torusBatch.AddTriangle(vVertex, vNormal, vTexture);             
            } 
        } 
    torusBatch.End(); 
    } 
 
///////////////////////////////////////////////////////////////////////////////////////////////// 
// Make a sphere 
void gltMakeSphere(GLTriangleBatch& sphereBatch, GLfloat fRadius, GLint iSlices, GLint iStacks) 
    { 
    GLfloat drho = (GLfloat)(3.141592653589) / (GLfloat) iStacks; 
    GLfloat dtheta = 2.0f * (GLfloat)(3.141592653589) / (GLfloat) iSlices; 
    GLfloat ds = 1.0f / (GLfloat) iSlices; 
    GLfloat dt = 1.0f / (GLfloat) iStacks; 
    GLfloat t = 1.0f;     
    GLfloat s = 0.0f; 
    GLint i, j;     // Looping variables 
     
    sphereBatch.BeginMesh(iSlices * iStacks * 6); 
    for (i = 0; i < iStacks; i++)  
        { 
        GLfloat rho = (GLfloat)i * drho; 
        GLfloat srho = (GLfloat)(sin(rho)); 
        GLfloat crho = (GLfloat)(cos(rho)); 
        GLfloat srhodrho = (GLfloat)(sin(rho + drho)); 
        GLfloat crhodrho = (GLfloat)(cos(rho + drho)); 
         
        // Many sources of OpenGL sphere drawing code uses a triangle fan 
        // for the caps of the sphere. This however introduces texturing  
        // artifacts at the poles on some OpenGL implementations 
        s = 0.0f; 
        M3DVector3f vVertex[4]; 
        M3DVector3f vNormal[4]; 
        M3DVector2f vTexture[4]; 
 
        for ( j = 0; j < iSlices; j++)  
            { 
            GLfloat theta = (j == iSlices) ? 0.0f : j * dtheta; 
            GLfloat stheta = (GLfloat)(-sin(theta)); 
            GLfloat ctheta = (GLfloat)(cos(theta)); 
             
            GLfloat x = stheta * srho; 
            GLfloat y = ctheta * srho; 
            GLfloat z = crho; 
         
            vTexture[0][0] = s; 
            vTexture[0][1] = t; 
            vNormal[0][0] = x; 
            vNormal[0][1] = y; 
            vNormal[0][2] = z; 
            vVertex[0][0] = x * fRadius; 
            vVertex[0][1] = y * fRadius; 
            vVertex[0][2] = z * fRadius; 
             
            x = stheta * srhodrho; 
            y = ctheta * srhodrho; 
            z = crhodrho; 
 
             vTexture[1][0] = s; 
            vTexture[1][1] = t - dt; 
            vNormal[1][0] = x; 
            vNormal[1][1] = y; 
            vNormal[1][2] = z; 
            vVertex[1][0] = x * fRadius; 
            vVertex[1][1] = y * fRadius; 
            vVertex[1][2] = z * fRadius; 
             
 
            theta = ((j+1) == iSlices) ? 0.0f : (j+1) * dtheta; 
            stheta = (GLfloat)(-sin(theta)); 
            ctheta = (GLfloat)(cos(theta)); 
             
            x = stheta * srho; 
            y = ctheta * srho; 
            z = crho; 
         
            s += ds; 
            vTexture[2][0] = s; 
            vTexture[2][1] = t; 
            vNormal[2][0] = x; 
            vNormal[2][1] = y; 
            vNormal[2][2] = z; 
            vVertex[2][0] = x * fRadius; 
            vVertex[2][1] = y * fRadius; 
            vVertex[2][2] = z * fRadius; 
             
            x = stheta * srhodrho; 
            y = ctheta * srhodrho; 
            z = crhodrho; 
 
             vTexture[3][0] = s; 
            vTexture[3][1] = t - dt; 
            vNormal[3][0] = x; 
            vNormal[3][1] = y; 
            vNormal[3][2] = z; 
            vVertex[3][0] = x * fRadius; 
            vVertex[3][1] = y * fRadius; 
            vVertex[3][2] = z * fRadius; 
         
            sphereBatch.AddTriangle(vVertex, vNormal, vTexture);             
             
            // Rearrange for next triangle 
            memcpy(vVertex[0], vVertex[1], sizeof(M3DVector3f)); 
            memcpy(vNormal[0], vNormal[1], sizeof(M3DVector3f)); 
            memcpy(vTexture[0], vTexture[1], sizeof(M3DVector2f)); 
             
            memcpy(vVertex[1], vVertex[3], sizeof(M3DVector3f)); 
            memcpy(vNormal[1], vNormal[3], sizeof(M3DVector3f)); 
            memcpy(vTexture[1], vTexture[3], sizeof(M3DVector2f)); 
                     
            sphereBatch.AddTriangle(vVertex, vNormal, vTexture);             
            } 
        t -= dt; 
        } 
        sphereBatch.End(); 
    } 
     
 
//////////////////////////////////////////////////////////////////////////////////////// 
void gltMakeDisk(GLTriangleBatch& diskBatch, GLfloat innerRadius, GLfloat outerRadius, GLint nSlices, GLint nStacks) 
    { 
    // How much to step out each stack 
    GLfloat fStepSizeRadial = outerRadius - innerRadius; 
    if(fStepSizeRadial < 0.0f)            // Dum dum... 
        fStepSizeRadial *= -1.0f; 
 
    fStepSizeRadial /= float(nStacks); 
     
    GLfloat fStepSizeSlice = (3.1415926536f * 2.0f) / float(nSlices); 
     
    diskBatch.BeginMesh(nSlices * nStacks * 6); 
     
    M3DVector3f vVertex[4]; 
    M3DVector3f vNormal[4]; 
    M3DVector2f vTexture[4]; 
     
    float fRadialScale = 1.0f / outerRadius; 
     
    for(GLint i = 0; i < nStacks; i++)            // Stacks 
        { 
        float theyta; 
        float theytaNext; 
        for(GLint j = 0; j < nSlices; j++)     // Slices 
            { 
            float inner = innerRadius + (float(i)) * fStepSizeRadial; 
            float outer = innerRadius + (float(i+1)) * fStepSizeRadial; 
             
            theyta = fStepSizeSlice * float(j); 
            if(j == (nSlices - 1)) 
                theytaNext = 0.0f; 
            else 
                theytaNext = fStepSizeSlice * (float(j+1)); 
                 
            // Inner First 
            vVertex[0][0] = cos(theyta) * inner;    // X     
            vVertex[0][1] = sin(theyta) * inner;    // Y 
            vVertex[0][2] = 0.0f;                    // Z 
             
            vNormal[0][0] = 0.0f;                    // Surface Normal, same for everybody 
            vNormal[0][1] = 0.0f; 
            vNormal[0][2] = 1.0f; 
             
            vTexture[0][0] = ((vVertex[0][0] * fRadialScale) + 1.0f) * 0.5f;     
            vTexture[0][1] = ((vVertex[0][1] * fRadialScale) + 1.0f) * 0.5f; 
             
            // Outer First 
            vVertex[1][0] = cos(theyta) * outer;    // X     
            vVertex[1][1] = sin(theyta) * outer;    // Y 
            vVertex[1][2] = 0.0f;                    // Z 
             
            vNormal[1][0] = 0.0f;                    // Surface Normal, same for everybody 
            vNormal[1][1] = 0.0f; 
            vNormal[1][2] = 1.0f; 
             
            vTexture[1][0] = ((vVertex[1][0] * fRadialScale) + 1.0f) * 0.5f; 
            vTexture[1][1] = ((vVertex[1][1] * fRadialScale) + 1.0f) * 0.5f; 
             
            // Inner Second 
            vVertex[2][0] = cos(theytaNext) * inner;    // X     
            vVertex[2][1] = sin(theytaNext) * inner;    // Y 
            vVertex[2][2] = 0.0f;                    // Z 
             
            vNormal[2][0] = 0.0f;                    // Surface Normal, same for everybody 
            vNormal[2][1] = 0.0f; 
            vNormal[2][2] = 1.0f; 
             
            vTexture[2][0] = ((vVertex[2][0] * fRadialScale) + 1.0f) * 0.5f; 
            vTexture[2][1] = ((vVertex[2][1] * fRadialScale) + 1.0f) * 0.5f; 
             
             
            // Outer Second 
            vVertex[3][0] = cos(theytaNext) * outer;    // X     
            vVertex[3][1] = sin(theytaNext) * outer;    // Y 
            vVertex[3][2] = 0.0f;                    // Z 
             
            vNormal[3][0] = 0.0f;                    // Surface Normal, same for everybody 
            vNormal[3][1] = 0.0f; 
            vNormal[3][2] = 1.0f; 
             
            vTexture[3][0] = ((vVertex[3][0] * fRadialScale) + 1.0f) * 0.5f; 
            vTexture[3][1] = ((vVertex[3][1] * fRadialScale) + 1.0f) * 0.5f; 
             
            diskBatch.AddTriangle(vVertex, vNormal, vTexture);             
             
            // Rearrange for next triangle 
            memcpy(vVertex[0], vVertex[1], sizeof(M3DVector3f)); 
            memcpy(vNormal[0], vNormal[1], sizeof(M3DVector3f)); 
            memcpy(vTexture[0], vTexture[1], sizeof(M3DVector2f)); 
             
            memcpy(vVertex[1], vVertex[3], sizeof(M3DVector3f)); 
            memcpy(vNormal[1], vNormal[3], sizeof(M3DVector3f)); 
            memcpy(vTexture[1], vTexture[3], sizeof(M3DVector2f)); 
                     
            diskBatch.AddTriangle(vVertex, vNormal, vTexture);             
            } 
        } 
     
    diskBatch.End(); 
    } 
 
// Draw a cylinder. Much like gluCylinder 
void gltMakeCylinder(GLTriangleBatch& cylinderBatch, GLfloat baseRadius, GLfloat topRadius,  
            GLfloat fLength, GLint numSlices, GLint numStacks) 
    {     
    float fRadiusStep = (topRadius - baseRadius) / float(numStacks); 
 
    GLfloat fStepSizeSlice = (3.1415926536f * 2.0f) / float(numSlices); 
 
    M3DVector3f vVertex[4]; 
    M3DVector3f vNormal[4]; 
    M3DVector2f vTexture[4]; 
 
    cylinderBatch.BeginMesh(numSlices * numStacks * 6); 
 
    GLfloat ds = 1.0f / float(numSlices); 
    GLfloat dt = 1.0f / float(numStacks); 
    GLfloat s; 
    GLfloat t; 
 
    for (int i = 0; i < numStacks; i++)  
        { 
        if(i == 0)             
            t = 0.0f; 
        else 
            t = float(i) * dt; 
 
        float tNext; 
        if(i == (numStacks - 1)) 
            tNext = 1.0f; 
        else 
            tNext = float(i+1) * dt; 
     
        float fCurrentRadius = baseRadius + (fRadiusStep * float(i)); 
        float fNextRadius = baseRadius + (fRadiusStep * float(i+1)); 
        float theyta; 
        float theytaNext; 
 
        float fCurrentZ = float(i) * (fLength / float(numStacks));  
        float fNextZ = float(i+1) * (fLength / float(numStacks)); 
         
        float zNormal = 0.0f; 
        if(!m3dCloseEnough(baseRadius - topRadius, 0.0f, 0.00001f)) 
            { 
            // Rise over run... 
            zNormal = (baseRadius - topRadius); 
            } 
         
        for (int j = 0; j < numSlices; j++)  
            {         
            if(j == 0) 
                s = 0.0f; 
            else 
                s = float(j) * ds; 
 
            float sNext; 
            if(j == (numSlices -1)) 
                sNext = 1.0f; 
            else 
                sNext = float(j+1) * ds; 
 
            theyta = fStepSizeSlice * float(j); 
            if(j == (numSlices - 1)) 
                theytaNext = 0.0f; 
            else 
                theytaNext = fStepSizeSlice * (float(j+1)); 
                 
            // Inner First 
            vVertex[1][0] = cos(theyta) * fCurrentRadius;    // X     
            vVertex[1][1] = sin(theyta) * fCurrentRadius;    // Y 
            vVertex[1][2] = fCurrentZ;                        // Z 
             
            vNormal[1][0] = vVertex[1][0];                    // Surface Normal, same for everybody 
            vNormal[1][1] = vVertex[1][1]; 
            vNormal[1][2] = zNormal; 
            m3dNormalizeVector3(vNormal[1]); 
             
            vTexture[1][0] = s;                    // Texture Coordinates, I have no idea... 
            vTexture[1][1] = t; 
     
            // Outer First 
            vVertex[0][0] = cos(theyta) * fNextRadius;    // X     
            vVertex[0][1] = sin(theyta) * fNextRadius;    // Y 
            vVertex[0][2] = fNextZ;                        // Z 
             
            if(!m3dCloseEnough(fNextRadius, 0.0f, 0.00001f)) { 
                vNormal[0][0] = vVertex[0][0];                    // Surface Normal, same for everybody 
                vNormal[0][1] = vVertex[0][1];                    // For cones, tip is tricky 
                vNormal[0][2] = zNormal; 
                m3dNormalizeVector3(vNormal[0]); 
                } 
            else 
                memcpy(vNormal[0], vNormal[1], sizeof(M3DVector3f)); 
         
             
            vTexture[0][0] = s;                    // Texture Coordinates, I have no idea... 
            vTexture[0][1] = tNext; 
             
            // Inner second 
            vVertex[3][0] = cos(theytaNext) * fCurrentRadius;    // X     
            vVertex[3][1] = sin(theytaNext) * fCurrentRadius;    // Y 
            vVertex[3][2] = fCurrentZ;                        // Z 
             
            vNormal[3][0] = vVertex[3][0];                    // Surface Normal, same for everybody 
            vNormal[3][1] = vVertex[3][1]; 
            vNormal[3][2] = zNormal; 
            m3dNormalizeVector3(vNormal[3]); 
 
            vTexture[3][0] = sNext;                    // Texture Coordinates, I have no idea... 
            vTexture[3][1] = t; 
 
            // Outer second 
            vVertex[2][0] = cos(theytaNext) * fNextRadius;    // X     
            vVertex[2][1] = sin(theytaNext) * fNextRadius;    // Y 
            vVertex[2][2] = fNextZ;                        // Z 
             
            if(!m3dCloseEnough(fNextRadius, 0.0f, 0.00001f)) { 
                vNormal[2][0] = vVertex[2][0];                    // Surface Normal, same for everybody 
                vNormal[2][1] = vVertex[2][1]; 
                vNormal[2][2] = zNormal; 
                m3dNormalizeVector3(vNormal[2]); 
                } 
            else 
                memcpy(vNormal[2], vNormal[3], sizeof(M3DVector3f)); 
                 
 
            vTexture[2][0] = sNext;                    // Texture Coordinates, I have no idea... 
            vTexture[2][1] = tNext; 
         
            cylinderBatch.AddTriangle(vVertex, vNormal, vTexture);             
             
            // Rearrange for next triangle 
            memcpy(vVertex[0], vVertex[1], sizeof(M3DVector3f)); 
            memcpy(vNormal[0], vNormal[1], sizeof(M3DVector3f)); 
            memcpy(vTexture[0], vTexture[1], sizeof(M3DVector2f)); 
             
            memcpy(vVertex[1], vVertex[3], sizeof(M3DVector3f)); 
            memcpy(vNormal[1], vNormal[3], sizeof(M3DVector3f)); 
            memcpy(vTexture[1], vTexture[3], sizeof(M3DVector2f)); 
                     
            cylinderBatch.AddTriangle(vVertex, vNormal, vTexture);             
            } 
        } 
    cylinderBatch.End(); 
    } 
     
     
/////////////////////////////////////////////////////////////////////////////////////// 
// Make a cube, centered at the origin, and with a specified "radius" 
void gltMakeCube(GLBatch& cubeBatch, GLfloat fRadius ) 
    { 
    cubeBatch.Begin(GL_TRIANGLES, 36, 1); 
             
    ///////////////////////////////////////////// 
    // Top of cube 
    cubeBatch.Normal3f(0.0f, fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, fRadius); 
    cubeBatch.Vertex3f(fRadius, fRadius, fRadius); 
     
    cubeBatch.Normal3f(0.0f, fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, 0.0f); 
    cubeBatch.Vertex3f(fRadius, fRadius, -fRadius); 
     
    cubeBatch.Normal3f(0.0f, fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f); 
    cubeBatch.Vertex3f(-fRadius, fRadius, -fRadius); 
     
    cubeBatch.Normal3f(0.0f, fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, fRadius); 
    cubeBatch.Vertex3f(fRadius, fRadius, fRadius); 
     
    cubeBatch.Normal3f(0.0f, fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f); 
    cubeBatch.Vertex3f(-fRadius, fRadius, -fRadius); 
     
    cubeBatch.Normal3f(0.0f, fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, fRadius); 
    cubeBatch.Vertex3f(-fRadius, fRadius, fRadius); 
     
     
    //////////////////////////////////////////// 
    // Bottom of cube 
    cubeBatch.Normal3f(0.0f, -fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f); 
    cubeBatch.Vertex3f(-fRadius, -fRadius, -fRadius); 
     
    cubeBatch.Normal3f(0.0f, -fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, 0.0f); 
    cubeBatch.Vertex3f(fRadius, -fRadius, -fRadius); 
     
    cubeBatch.Normal3f(0.0f, -fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, fRadius); 
    cubeBatch.Vertex3f(fRadius, -fRadius, fRadius); 
     
    cubeBatch.Normal3f(0.0f, -fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, fRadius); 
    cubeBatch.Vertex3f(-fRadius, -fRadius, fRadius); 
     
    cubeBatch.Normal3f(0.0f, -fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f); 
    cubeBatch.Vertex3f(-fRadius, -fRadius, -fRadius); 
     
    cubeBatch.Normal3f(0.0f, -fRadius, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, fRadius); 
    cubeBatch.Vertex3f(fRadius, -fRadius, fRadius); 
     
    /////////////////////////////////////////// 
    // Left side of cube 
    cubeBatch.Normal3f(-fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, fRadius); 
    cubeBatch.Vertex3f(-fRadius, fRadius, fRadius); 
     
    cubeBatch.Normal3f(-fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, 0.0f); 
    cubeBatch.Vertex3f(-fRadius, fRadius, -fRadius); 
     
    cubeBatch.Normal3f(-fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f); 
    cubeBatch.Vertex3f(-fRadius, -fRadius, -fRadius); 
     
    cubeBatch.Normal3f(-fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, fRadius); 
    cubeBatch.Vertex3f(-fRadius, fRadius, fRadius); 
     
    cubeBatch.Normal3f(-fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f); 
    cubeBatch.Vertex3f(-fRadius, -fRadius, -fRadius); 
     
    cubeBatch.Normal3f(-fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, fRadius); 
    cubeBatch.Vertex3f(-fRadius, -fRadius, fRadius); 
     
    // Right side of cube 
    cubeBatch.Normal3f(fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f); 
    cubeBatch.Vertex3f(fRadius, -fRadius, -fRadius); 
     
    cubeBatch.Normal3f(fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, 0.0f); 
    cubeBatch.Vertex3f(fRadius, fRadius, -fRadius); 
     
    cubeBatch.Normal3f(fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, fRadius); 
    cubeBatch.Vertex3f(fRadius, fRadius, fRadius); 
     
    cubeBatch.Normal3f(fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, fRadius, fRadius); 
    cubeBatch.Vertex3f(fRadius, fRadius, fRadius); 
     
    cubeBatch.Normal3f(fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, fRadius); 
    cubeBatch.Vertex3f(fRadius, -fRadius, fRadius); 
     
    cubeBatch.Normal3f(fRadius, 0.0f, 0.0f); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f); 
    cubeBatch.Vertex3f(fRadius, -fRadius, -fRadius); 
     
    // Front and Back 
    // Front 
    cubeBatch.Normal3f(0.0f, 0.0f, fRadius); 
    cubeBatch.MultiTexCoord2f(0, fRadius, 0.0f); 
    cubeBatch.Vertex3f(fRadius, -fRadius, fRadius); 
     
    cubeBatch.Normal3f(0.0f, 0.0f, fRadius); 
    cubeBatch.MultiTexCoord2f(0, fRadius, fRadius); 
    cubeBatch.Vertex3f(fRadius, fRadius, fRadius); 
     
    cubeBatch.Normal3f(0.0f, 0.0f, fRadius); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, fRadius); 
    cubeBatch.Vertex3f(-fRadius, fRadius, fRadius); 
     
    cubeBatch.Normal3f(0.0f, 0.0f, fRadius); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, fRadius); 
    cubeBatch.Vertex3f(-fRadius, fRadius, fRadius); 
     
    cubeBatch.Normal3f(0.0f, 0.0f, fRadius); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f); 
    cubeBatch.Vertex3f(-fRadius, -fRadius, fRadius); 
     
    cubeBatch.Normal3f(0.0f, 0.0f, fRadius); 
    cubeBatch.MultiTexCoord2f(0, fRadius, 0.0f); 
    cubeBatch.Vertex3f(fRadius, -fRadius, fRadius); 
     
    // Back 
    cubeBatch.Normal3f(0.0f, 0.0f, -fRadius); 
    cubeBatch.MultiTexCoord2f(0, fRadius, 0.0f); 
    cubeBatch.Vertex3f(fRadius, -fRadius, -fRadius); 
     
    cubeBatch.Normal3f(0.0f, 0.0f, -fRadius); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, 0.0f); 
    cubeBatch.Vertex3f(-fRadius, -fRadius, -fRadius); 
     
    cubeBatch.Normal3f(0.0f, 0.0f, -fRadius); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, fRadius); 
    cubeBatch.Vertex3f(-fRadius, fRadius, -fRadius); 
     
    cubeBatch.Normal3f(0.0f, 0.0f, -fRadius); 
    cubeBatch.MultiTexCoord2f(0, 0.0f, fRadius); 
    cubeBatch.Vertex3f(-fRadius, fRadius, -fRadius); 
     
    cubeBatch.Normal3f(0.0f, 0.0f, -fRadius); 
    cubeBatch.MultiTexCoord2f(0, fRadius, fRadius); 
    cubeBatch.Vertex3f(fRadius, fRadius, -fRadius); 
 
    cubeBatch.Normal3f(0.0f, 0.0f, -fRadius); 
    cubeBatch.MultiTexCoord2f(0, fRadius, 0.0f); 
    cubeBatch.Vertex3f(fRadius, -fRadius, -fRadius);    
    cubeBatch.End(); 
    }     
 
 
 
// Define targa header. This is only used locally. 
#pragma pack(1) 
typedef struct 
{ 
    GLbyte    identsize;              // Size of ID field that follows header (0) 
    GLbyte    colorMapType;           // 0 = None, 1 = paletted 
    GLbyte    imageType;              // 0 = none, 1 = indexed, 2 = rgb, 3 = grey, +8=rle 
    unsigned short    colorMapStart;          // First colour map entry 
    unsigned short    colorMapLength;         // Number of colors 
    unsigned char     colorMapBits;   // bits per palette entry 
    unsigned short    xstart;                 // image x origin 
    unsigned short    ystart;                 // image y origin 
    unsigned short    width;                  // width in pixels 
    unsigned short    height;                 // height in pixels 
    GLbyte    bits;                   // bits per pixel (8 16, 24, 32) 
    GLbyte    descriptor;             // image descriptor 
} TGAHEADER; 
#pragma pack(8) 
 
 
//////////////////////////////////////////////////////////////////// 
// Capture the current viewport and save it as a targa file. 
// Be sure and call SwapBuffers for double buffered contexts or 
// glFinish for single buffered contexts before calling this function. 
// Returns 0 if an error occurs, or 1 on success. 
// Does not work on the iPhone 
#ifndef OPENGL_ES 
GLint gltGrabScreenTGA(const char *szFileName) 
    { 
    FILE *pFile;                // File pointer 
    TGAHEADER tgaHeader;        // TGA file header 
    unsigned long lImageSize;   // Size in bytes of image 
    GLbyte    *pBits = NULL;      // Pointer to bits 
    GLint iViewport[4];         // Viewport in pixels 
    GLenum lastBuffer;          // Storage for the current read buffer setting 
     
    // Get the viewport dimensions 
    glGetIntegerv(GL_VIEWPORT, iViewport); 
     
    // How big is the image going to be (targas are tightly packed) 
    lImageSize = iViewport[2] * 3 * iViewport[3];     
     
    // Allocate block. If this doesn't work, go home 
    pBits = (GLbyte *)malloc(lImageSize); 
    if(pBits == NULL) 
        return 0; 
     
    // Read bits from color buffer 
    glPixelStorei(GL_PACK_ALIGNMENT, 1); 
    glPixelStorei(GL_PACK_ROW_LENGTH, 0); 
    glPixelStorei(GL_PACK_SKIP_ROWS, 0); 
    glPixelStorei(GL_PACK_SKIP_PIXELS, 0); 
     
    // Get the current read buffer setting and save it. Switch to 
    // the front buffer and do the read operation. Finally, restore 
    // the read buffer state 
    glGetIntegerv(GL_READ_BUFFER, (GLint *)&lastBuffer); 
    glReadBuffer(GL_FRONT); 
    glReadPixels(0, 0, iViewport[2], iViewport[3], GL_BGR_EXT, GL_UNSIGNED_BYTE, pBits); 
    glReadBuffer(lastBuffer); 
     
    // Initialize the Targa header 
    tgaHeader.identsize = 0; 
    tgaHeader.colorMapType = 0; 
    tgaHeader.imageType = 2; 
    tgaHeader.colorMapStart = 0; 
    tgaHeader.colorMapLength = 0; 
    tgaHeader.colorMapBits = 0; 
    tgaHeader.xstart = 0; 
    tgaHeader.ystart = 0; 
    tgaHeader.width = iViewport[2]; 
    tgaHeader.height = iViewport[3]; 
    tgaHeader.bits = 24; 
    tgaHeader.descriptor = 0; 
     
    // Do byte swap for big vs little endian 
#ifdef __APPLE__ 
    LITTLE_ENDIAN_WORD(&tgaHeader.colorMapStart); 
    LITTLE_ENDIAN_WORD(&tgaHeader.colorMapLength); 
    LITTLE_ENDIAN_WORD(&tgaHeader.xstart); 
    LITTLE_ENDIAN_WORD(&tgaHeader.ystart); 
    LITTLE_ENDIAN_WORD(&tgaHeader.width); 
    LITTLE_ENDIAN_WORD(&tgaHeader.height); 
#endif 
     
    // Attempt to open the file 
    pFile = fopen(szFileName, "wb"); 
    if(pFile == NULL) 
        { 
        free(pBits);    // Free buffer and return error 
        return 0; 
        } 
     
    // Write the header 
    fwrite(&tgaHeader, sizeof(TGAHEADER), 1, pFile); 
     
    // Write the image data 
    fwrite(pBits, lImageSize, 1, pFile); 
     
    // Free temporary buffer and close the file 
    free(pBits);     
    fclose(pFile); 
     
    // Success! 
    return 1; 
    } 
#endif 
 
 
//////////////////////////////////////////////////////////////////// 
// Allocate memory and load targa bits. Returns pointer to new buffer, 
// height, and width of texture, and the OpenGL format of data. 
// Call free() on buffer when finished! 
// This only works on pretty vanilla targas... 8, 24, or 32 bit color 
// only, no palettes, no RLE encoding. 
// This function also takes an optional final parameter to preallocated  
// storage for loading in the image data. 
GLbyte *gltReadTGABits(const char *szFileName, GLint *iWidth, GLint *iHeight, GLint *iComponents, GLenum *eFormat, GLbyte *pData) 
    { 
    FILE *pFile;            // File pointer 
    TGAHEADER tgaHeader;        // TGA file header 
    unsigned long lImageSize;        // Size in bytes of image 
    short sDepth;            // Pixel depth; 
    GLbyte    *pBits = NULL;          // Pointer to bits 
     
    // Default/Failed values 
    *iWidth = 0; 
    *iHeight = 0; 
    *eFormat = GL_RGB; 
    *iComponents = GL_RGB; 
     
    // Attempt to open the file 
    pFile = fopen(szFileName, "rb"); 
    if(pFile == NULL) 
        return NULL; 
     
    // Read in header (binary) 
    fread(&tgaHeader, 18/* sizeof(TGAHEADER)*/, 1, pFile); 
     
    // Do byte swap for big vs little endian 
#ifdef __APPLE__ 
    LITTLE_ENDIAN_WORD(&tgaHeader.colorMapStart); 
    LITTLE_ENDIAN_WORD(&tgaHeader.colorMapLength); 
    LITTLE_ENDIAN_WORD(&tgaHeader.xstart); 
    LITTLE_ENDIAN_WORD(&tgaHeader.ystart); 
    LITTLE_ENDIAN_WORD(&tgaHeader.width); 
    LITTLE_ENDIAN_WORD(&tgaHeader.height); 
#endif 
     
     
    // Get width, height, and depth of texture 
    *iWidth = tgaHeader.width; 
    *iHeight = tgaHeader.height; 
    sDepth = tgaHeader.bits / 8; 
     
    // Put some validity checks here. Very simply, I only understand 
    // or care about 8, 24, or 32 bit targa's. 
    if(tgaHeader.bits != 8 && tgaHeader.bits != 24 && tgaHeader.bits != 32) 
        return NULL; 
     
    // Calculate size of image buffer 
    lImageSize = tgaHeader.width * tgaHeader.height * sDepth; 
     
    // Allocate memory and check for success 
    if(pData == NULL)  
        pBits = (GLbyte*)malloc(lImageSize * sizeof(GLbyte)); 
    else  
        pBits = pData;  
 
    // Read in the bits 
    // Check for read error. This should catch RLE or other  
    // weird formats that I don't want to recognize 
    if(fread(pBits, lImageSize, 1, pFile) != 1) 
        { 
        if(pBits != NULL) 
            free(pBits); 
        return NULL; 
        } 
     
    // Set OpenGL format expected 
    switch(sDepth) 
        { 
#ifndef OPENGL_ES 
        case 3:     // Most likely case 
            *eFormat = GL_BGR; 
            *iComponents = GL_RGB; 
            break; 
#endif 
        case 4: 
            *eFormat = GL_BGRA; 
            *iComponents = GL_RGBA; 
            break; 
        case 1: 
            *eFormat = GL_LUMINANCE; 
            *iComponents = GL_LUMINANCE; 
            break; 
        default:        // RGB 
            // If on the iPhone, TGA's are BGR, and the iPhone does not  
            // support BGR without alpha, but it does support RGB, 
            // so a simple swizzle of the red and blue bytes will suffice. 
            // For faster iPhone loads however, save your TGA's with an Alpha! 
#ifdef OPENGL_ES 
    for(int i = 0; i < lImageSize; i+=3) 
        { 
        GLbyte temp = pBits[i]; 
        pBits[i] = pBits[i+2]; 
        pBits[i+2] = temp; 
        } 
#endif 
        break; 
        } 
     
    // Done with File 
    fclose(pFile); 
     
    // Return pointer to image data 
    return pBits; 
    } 
 
/////////////////////////////////////////////////////////////////////////////// 
// This function opens the "bitmap" file given (szFileName), verifies that it is 
// a 24bit .BMP file and loads the bitmap bits needed so that it can be used 
// as a texture. The width and height of the bitmap are returned in nWidth and 
// nHeight. The memory block allocated and returned must be deleted with free(); 
// The returned array is an 888 BGR texture 
// These structures match the layout of the equivalent Windows specific structs  
// used by Win32 
#pragma pack(1) 
struct RGB {  
  GLbyte blue; 
  GLbyte green; 
  GLbyte red; 
  GLbyte alpha; 
}; 
 
struct BMPInfoHeader { 
  GLuint    size; 
  GLuint    width; 
  GLuint    height; 
  GLushort  planes; 
  GLushort  bits; 
  GLuint    compression; 
  GLuint    imageSize; 
  GLuint    xScale; 
  GLuint    yScale; 
  GLuint    colors; 
  GLuint    importantColors; 
}; 
 
struct BMPHeader { 
  GLushort    type;  
  GLuint    size;  
  GLushort    unused;  
  GLushort    unused2;  
  GLuint    offset;  
};  
 
struct BMPInfo { 
  BMPInfoHeader        header; 
  RGB                colors[1]; 
}; 
#pragma pack(8) 
 
 
GLbyte* gltReadBMPBits(const char *szFileName, int *nWidth, int *nHeight) 
    { 
    FILE*    pFile; 
    BMPInfo *pBitmapInfo = NULL; 
    unsigned long lInfoSize = 0; 
    unsigned long lBitSize = 0; 
    GLbyte *pBits = NULL;                    // Bitmaps bits 
    BMPHeader    bitmapHeader; 
 
    // Attempt to open the file 
    pFile = fopen(szFileName, "rb"); 
    if(pFile == NULL) 
        return NULL; 
 
    // File is Open. Read in bitmap header information 
    fread(&bitmapHeader, sizeof(BMPHeader), 1, pFile); 
 
    // Read in bitmap information structure 
    lInfoSize = bitmapHeader.offset - sizeof(BMPHeader); 
    pBitmapInfo = (BMPInfo *) malloc(sizeof(GLbyte)*lInfoSize); 
    if(fread(pBitmapInfo, lInfoSize, 1, pFile) != 1) 
        { 
        free(pBitmapInfo); 
        fclose(pFile); 
        return false; 
        } 
 
    // Save the size and dimensions of the bitmap 
    *nWidth = pBitmapInfo->header.width; 
    *nHeight = pBitmapInfo->header.height; 
    lBitSize = pBitmapInfo->header.imageSize; 
 
    // If the size isn't specified, calculate it anyway     
    if(pBitmapInfo->header.bits != 24) 
        { 
        free(pBitmapInfo); 
        return false; 
        } 
 
    if(lBitSize == 0) 
        lBitSize = (*nWidth * 
           pBitmapInfo->header.bits + 7) / 8 * 
            abs(*nHeight); 
 
    // Allocate space for the actual bitmap 
    free(pBitmapInfo); 
    pBits = (GLbyte*)malloc(sizeof(GLbyte)*lBitSize); 
 
    // Read in the pixmap bits, check for corruption 
    if(fread(pBits, lBitSize, 1, pFile) != 1) 
        { 
        free(pBits); 
        pBits = NULL; 
        } 
 
    // Close the bitmap file now that we have all the data we need 
    fclose(pFile); 
 
    return pBits; 
    } 
 
 
// Rather than malloc/free a block everytime a shader must be loaded, 
// I will dedicate a single 4k page for reading in shaders. Thanks to 
// modern OS design, this page will be swapped out to disk later if never 
// used again after program initialization. Where-as mallocing different size 
// shader blocks could lead to heap fragmentation, which would actually be worse. 
//#define MAX_SHADER_LENGTH   8192  -> This is defined in gltools.h 
// BTW... this does make this function unsafe to use in two threads simultaneously 
// BTW BTW... personally.... I do this also to my own texture loading code - RSW 
static GLubyte shaderText[MAX_SHADER_LENGTH]; 
 
////////////////////////////////////////////////////////////////////////// 
// Load the shader from the source text 
void gltLoadShaderSrc(const char *szShaderSrc, GLuint shader) 
    { 
    GLchar *fsStringPtr[1]; 
 
    fsStringPtr[0] = (GLchar *)szShaderSrc; 
    glShaderSource(shader, 1, (const GLchar **)fsStringPtr, NULL); 
    } 
 
 
//////////////////////////////////////////////////////////////// 
// Load the shader from the specified file. Returns false if the 
// shader could not be loaded 
bool gltLoadShaderFile(const char *szFile, GLuint shader) 
    { 
    GLint shaderLength = 0; 
    FILE *fp; 
     
    // Open the shader file 
    fp = fopen(szFile, "r"); 
    if(fp != NULL) 
        { 
        // See how long the file is 
        while (fgetc(fp) != EOF) 
            shaderLength++; 
         
        // Allocate a block of memory to send in the shader 
        assert(shaderLength < MAX_SHADER_LENGTH);   // make me bigger! 
        if(shaderLength > MAX_SHADER_LENGTH) 
            { 
            fclose(fp); 
            return false; 
            } 
         
        // Go back to beginning of file 
        rewind(fp); 
         
        // Read the whole file in 
        if (shaderText != NULL) 
            fread(shaderText, 1, shaderLength, fp); 
         
        // Make sure it is null terminated and close the file 
        shaderText[shaderLength] = '\0'; 
        fclose(fp); 
        } 
    else 
        return false;     
     
    // Load the string 
    gltLoadShaderSrc((const char *)shaderText, shader); 
     
    return true; 
    }    
 
///////////////////////////////////////////////////////////////// 
// Load a pair of shaders, compile, and link together. Specify the complete 
// source text for each shader. After the shader names, specify the number 
// of attributes, followed by the index and attribute name of each attribute 
GLuint gltLoadShaderTripletWithAttributes(const char *szVertexShader, 
                                          const char *szGeometryShader, 
                                          const char *szFragmentShader, ...) 
{ 
    // Temporary Shader objects 
    GLuint hVertexShader = 0; 
    GLuint hGeometryShader = 0; 
    GLuint hFragmentShader = 0; 
    GLuint hReturn = 0; 
    GLint testVal; 
    int iArgCount; 
    va_list attributeList; 
    char *szNextArg = NULL; 
    char infoLog[1024]; 
 
    // Create shader objects 
    hVertexShader = glCreateShader(GL_VERTEX_SHADER); 
    if (gltLoadShaderFile(szVertexShader, hVertexShader) == false) 
        goto failed; 
    glCompileShader(hVertexShader); 
    glGetShaderiv(hVertexShader, GL_COMPILE_STATUS, &testVal); 
    if  (testVal == GL_FALSE) { 
        glGetShaderInfoLog(hVertexShader, 1024, NULL, infoLog); 
        goto failed; 
    } 
 
    // Geometry shader is optional 
    if (szGeometryShader) { 
        hGeometryShader = glCreateShader(GL_GEOMETRY_SHADER); 
        if(gltLoadShaderFile(szGeometryShader, hGeometryShader) == false) 
            goto failed; 
        glCompileShader(hGeometryShader); 
        glGetShaderiv(hGeometryShader, GL_COMPILE_STATUS, &testVal); 
        if  (testVal == GL_FALSE) { 
            glGetShaderInfoLog(hGeometryShader, 1024, NULL, infoLog); 
            goto failed; 
        } 
    } 
 
    // Fragment shader is optional (transform feedback only) 
    if (szFragmentShader) { 
        hFragmentShader = glCreateShader(GL_FRAGMENT_SHADER); 
        if (gltLoadShaderFile(szFragmentShader, hFragmentShader) == false) 
            goto failed; 
        glCompileShader(hFragmentShader); 
        glGetShaderiv(hFragmentShader, GL_COMPILE_STATUS, &testVal); 
        if  (testVal == GL_FALSE) { 
            glGetShaderInfoLog(hFragmentShader, 1024, NULL, infoLog); 
            goto failed; 
        } 
    } 
 
    // Create the final program object, and attach the shaders 
    hReturn = glCreateProgram(); 
    glAttachShader(hReturn, hVertexShader); 
    if (szGeometryShader) 
        glAttachShader(hReturn, hGeometryShader); 
    if (szFragmentShader) 
        glAttachShader(hReturn, hFragmentShader); 
 
    // Now, we need to bind the attribute names to their specific locations 
    // List of attributes 
    va_start(attributeList, szFragmentShader); 
 
    // Iterate over this argument list 
    iArgCount = va_arg(attributeList, int);    // Number of attributes 
    for(int i = 0; i < iArgCount; i++) 
    { 
        int index = va_arg(attributeList, int); 
        szNextArg = va_arg(attributeList, char*); 
        glBindAttribLocation(hReturn, index, szNextArg); 
    } 
    va_end(attributeList); 
 
    // Attempt to link     
    glLinkProgram(hReturn); 
 
    // These are no longer needed 
    glDeleteShader(hVertexShader); 
    glDeleteShader(hGeometryShader); 
    glDeleteShader(hFragmentShader); 
 
    // Make sure link worked too 
    glGetProgramiv(hReturn, GL_LINK_STATUS, &testVal); 
    if(testVal == GL_FALSE) { 
        char infoLog[1024]; 
        glGetProgramInfoLog(hReturn, 1024, NULL, infoLog); 
        fprintf(stderr, infoLog); 
        goto failed; 
    } 
 
    // All done, return our ready to use shader program 
    return hReturn; 
 
failed: 
 
    glDeleteProgram(hReturn); 
    glDeleteShader(hFragmentShader); 
    glDeleteShader(hGeometryShader); 
    glDeleteShader(hVertexShader); 
 
    return 0; 
} 
 
 
///////////////////////////////////////////////////////////////// 
// Load a pair of shaders, compile, and link together. Specify the complete 
// source text for each shader. After the shader names, specify the number 
// of attributes, followed by the index and attribute name of each attribute 
GLuint gltLoadShaderPairWithAttributes(const char *szVertexProg, const char *szFragmentProg, ...) 
    { 
    // Temporary Shader objects 
    GLuint hVertexShader; 
    GLuint hFragmentShader;  
    GLuint hReturn = 0;    
    GLint testVal; 
     
    // Create shader objects 
    hVertexShader = glCreateShader(GL_VERTEX_SHADER); 
    hFragmentShader = glCreateShader(GL_FRAGMENT_SHADER); 
     
    // Load them. If fail clean up and return null 
    // Vertex Program 
    if(gltLoadShaderFile(szVertexProg, hVertexShader) == false) 
        { 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        fprintf(stderr, "The shader at %s could ot be found.\n", szVertexProg); 
        return (GLuint)NULL; 
        } 
     
    // Fragment Program 
    if(gltLoadShaderFile(szFragmentProg, hFragmentShader) == false) 
        { 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        fprintf(stderr,"The shader at %s  could not be found.\n", szFragmentProg); 
        return (GLuint)NULL; 
        } 
     
    // Compile them both 
    glCompileShader(hVertexShader); 
    glCompileShader(hFragmentShader); 
     
    // Check for errors in vertex shader 
    glGetShaderiv(hVertexShader, GL_COMPILE_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        char infoLog[1024]; 
        glGetShaderInfoLog(hVertexShader, 1024, NULL, infoLog); 
        fprintf(stderr, "The shader at %s failed to compile with the following error:\n%s\n", szVertexProg, infoLog); 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        return (GLuint)NULL; 
        } 
     
    // Check for errors in fragment shader 
    glGetShaderiv(hFragmentShader, GL_COMPILE_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        char infoLog[1024]; 
        glGetShaderInfoLog(hFragmentShader, 1024, NULL, infoLog); 
        fprintf(stderr, "The shader at %s failed to compile with the following error:\n%s\n", szFragmentProg, infoLog); 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        return (GLuint)NULL; 
        } 
     
    // Create the final program object, and attach the shaders 
    hReturn = glCreateProgram(); 
    glAttachShader(hReturn, hVertexShader); 
    glAttachShader(hReturn, hFragmentShader); 
 
 
    // Now, we need to bind the attribute names to their specific locations 
    // List of attributes 
    va_list attributeList; 
    va_start(attributeList, szFragmentProg); 
 
    // Iterate over this argument list 
    char *szNextArg; 
    int iArgCount = va_arg(attributeList, int);    // Number of attributes 
    for(int i = 0; i < iArgCount; i++) 
        { 
        int index = va_arg(attributeList, int); 
        szNextArg = va_arg(attributeList, char*); 
        glBindAttribLocation(hReturn, index, szNextArg); 
        } 
    va_end(attributeList); 
 
    // Attempt to link     
    glLinkProgram(hReturn); 
     
    // These are no longer needed 
    glDeleteShader(hVertexShader); 
    glDeleteShader(hFragmentShader);   
     
    // Make sure link worked too 
    glGetProgramiv(hReturn, GL_LINK_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        char infoLog[1024]; 
        glGetProgramInfoLog(hReturn, 1024, NULL, infoLog); 
        fprintf(stderr,"The programs %s and %s failed to link with the following errors:\n%s\n", 
            szVertexProg, szFragmentProg, infoLog); 
        glDeleteProgram(hReturn); 
        return (GLuint)NULL; 
        } 
     
    // All done, return our ready to use shader program 
    return hReturn;   
    }    
 
///////////////////////////////////////////////////////////////// 
// Load a pair of shaders, compile, and link together. Specify the complete 
// file path for each shader. Note, there is no support for 
// just loading say a vertex program... you have to do both. 
GLuint gltLoadShaderPair(const char *szVertexProg, const char *szFragmentProg) 
    { 
    // Temporary Shader objects 
    GLuint hVertexShader; 
    GLuint hFragmentShader;  
    GLuint hReturn = 0;    
    GLint testVal; 
     
    // Create shader objects 
    hVertexShader = glCreateShader(GL_VERTEX_SHADER); 
    hFragmentShader = glCreateShader(GL_FRAGMENT_SHADER); 
     
    // Load them. If fail clean up and return null 
    if(gltLoadShaderFile(szVertexProg, hVertexShader) == false) 
        { 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        return (GLuint)NULL; 
        } 
     
    if(gltLoadShaderFile(szFragmentProg, hFragmentShader) == false) 
        { 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        return (GLuint)NULL; 
        } 
     
    // Compile them 
    glCompileShader(hVertexShader); 
    glCompileShader(hFragmentShader); 
     
    // Check for errors 
    glGetShaderiv(hVertexShader, GL_COMPILE_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        return (GLuint)NULL; 
        } 
     
    glGetShaderiv(hFragmentShader, GL_COMPILE_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        return (GLuint)NULL; 
        } 
     
    // Link them - assuming it works... 
    hReturn = glCreateProgram(); 
    glAttachShader(hReturn, hVertexShader); 
    glAttachShader(hReturn, hFragmentShader); 
 
    glLinkProgram(hReturn); 
     
    // These are no longer needed 
    glDeleteShader(hVertexShader); 
    glDeleteShader(hFragmentShader);   
     
    // Make sure link worked too 
    glGetProgramiv(hReturn, GL_LINK_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        glDeleteProgram(hReturn); 
        return (GLuint)NULL; 
        } 
     
    return hReturn;   
    }    
 
///////////////////////////////////////////////////////////////// 
// Load a set of shaders, compile, and link together. Specify the complete 
// file path for each shader. Note, there is no support for 
// just loading say a vertex program... you have to do all. 
GLuint gltLoadShaderTripletSrc(const char *szVertexSrc, 
                               const char *szGeometrySrc, 
                               const char *szFragmentSrc) 
    { 
    // Temporary Shader objects 
    GLuint hVertexShader = 0; 
    GLuint hGeometryShader = 0; 
    GLuint hFragmentShader = 0; 
    GLuint hReturn = 0;    
    GLint testVal; 
     
    // Create shader objects, load and compile them 
    hVertexShader = glCreateShader(GL_VERTEX_SHADER); 
    gltLoadShaderSrc(szVertexSrc, hVertexShader); 
    glCompileShader(hVertexShader); 
    if (szGeometrySrc) { 
        hGeometryShader = glCreateShader(GL_GEOMETRY_SHADER); 
        gltLoadShaderSrc(szGeometrySrc, hFragmentShader); 
        glCompileShader(hGeometryShader); 
    } 
    hFragmentShader = glCreateShader(GL_FRAGMENT_SHADER); 
    gltLoadShaderSrc(szFragmentSrc, hFragmentShader); 
    glCompileShader(hFragmentShader); 
 
    // Check for errors 
    glGetShaderiv(hVertexShader, GL_COMPILE_STATUS, &testVal); 
    if(testVal == GL_FALSE) { 
        goto failed; 
    } 
 
    if (szGeometrySrc) { 
        glGetShaderiv(hGeometryShader, GL_COMPILE_STATUS, &testVal); 
        if(testVal == GL_FALSE) { 
            goto failed; 
        } 
    } 
 
    glGetShaderiv(hFragmentShader, GL_COMPILE_STATUS, &testVal); 
    if(testVal == GL_FALSE) { 
        goto failed; 
    } 
 
    // Link them - assuming it works... 
    hReturn = glCreateProgram(); 
    glAttachShader(hReturn, hVertexShader); 
    if (szGeometrySrc) 
        glAttachShader(hReturn, hGeometryShader); 
    glAttachShader(hReturn, hFragmentShader); 
    glLinkProgram(hReturn); 
 
    // These are no longer needed 
    glDeleteShader(hVertexShader); 
    glDeleteShader(hGeometryShader); 
    glDeleteShader(hFragmentShader); 
 
    // Make sure link worked too 
    glGetProgramiv(hReturn, GL_LINK_STATUS, &testVal); 
    if(testVal == GL_FALSE) { 
        goto failed; 
    } 
 
    return hReturn; 
 
failed: 
 
    glDeleteProgram(hReturn); 
    glDeleteShader(hFragmentShader); 
    glDeleteShader(hGeometryShader); 
    glDeleteShader(hVertexShader); 
 
    return 0; 
} 
 
 
///////////////////////////////////////////////////////////////// 
// Load a pair of shaders, compile, and link together. Specify the complete 
// file path for each shader. Note, there is no support for 
// just loading say a vertex program... you have to do both. 
GLuint gltLoadShaderPairSrc(const char *szVertexSrc, const char *szFragmentSrc) 
    { 
    // Temporary Shader objects 
    GLuint hVertexShader; 
    GLuint hFragmentShader;  
    GLuint hReturn = 0;    
    GLint testVal; 
     
    // Create shader objects 
    hVertexShader = glCreateShader(GL_VERTEX_SHADER); 
    hFragmentShader = glCreateShader(GL_FRAGMENT_SHADER); 
     
    // Load them.  
    gltLoadShaderSrc(szVertexSrc, hVertexShader); 
    gltLoadShaderSrc(szFragmentSrc, hFragmentShader); 
    
    // Compile them 
    glCompileShader(hVertexShader); 
    glCompileShader(hFragmentShader); 
     
    // Check for errors 
    glGetShaderiv(hVertexShader, GL_COMPILE_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        return (GLuint)NULL; 
        } 
     
    glGetShaderiv(hFragmentShader, GL_COMPILE_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        return (GLuint)NULL; 
        } 
     
    // Link them - assuming it works... 
    hReturn = glCreateProgram(); 
    glAttachShader(hReturn, hVertexShader); 
    glAttachShader(hReturn, hFragmentShader); 
    glLinkProgram(hReturn); 
     
    // These are no longer needed 
    glDeleteShader(hVertexShader); 
    glDeleteShader(hFragmentShader);   
     
    // Make sure link worked too 
    glGetProgramiv(hReturn, GL_LINK_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        glDeleteProgram(hReturn); 
        return (GLuint)NULL; 
        } 
     
    return hReturn;   
    }    
 
///////////////////////////////////////////////////////////////// 
// Load a pair of shaders, compile, and link together. Specify the complete 
// source code text for each shader. Note, there is no support for 
// just loading say a vertex program... you have to do both. 
GLuint gltLoadShaderPairSrcWithAttributes(const char *szVertexSrc, const char *szFragmentSrc, ...) 
    { 
    // Temporary Shader objects 
    GLuint hVertexShader; 
    GLuint hFragmentShader;  
    GLuint hReturn = 0;    
    GLint testVal; 
     
    // Create shader objects 
    hVertexShader = glCreateShader(GL_VERTEX_SHADER); 
    hFragmentShader = glCreateShader(GL_FRAGMENT_SHADER); 
     
    // Load them.  
    gltLoadShaderSrc(szVertexSrc, hVertexShader); 
    gltLoadShaderSrc(szFragmentSrc, hFragmentShader); 
    
    // Compile them 
    glCompileShader(hVertexShader); 
    glCompileShader(hFragmentShader); 
     
    // Check for errors 
    glGetShaderiv(hVertexShader, GL_COMPILE_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        return (GLuint)NULL; 
        } 
     
    glGetShaderiv(hFragmentShader, GL_COMPILE_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        glDeleteShader(hVertexShader); 
        glDeleteShader(hFragmentShader); 
        return (GLuint)NULL; 
        } 
     
    // Link them - assuming it works... 
    hReturn = glCreateProgram(); 
    glAttachShader(hReturn, hVertexShader); 
    glAttachShader(hReturn, hFragmentShader); 
 
    // List of attributes 
    va_list attributeList; 
    va_start(attributeList, szFragmentSrc); 
 
    char *szNextArg; 
    int iArgCount = va_arg(attributeList, int);    // Number of attributes 
    for(int i = 0; i < iArgCount; i++) 
        { 
        int index = va_arg(attributeList, int); 
        szNextArg = va_arg(attributeList, char*); 
        glBindAttribLocation(hReturn, index, szNextArg); 
        } 
    va_end(attributeList); 
 
 
    glLinkProgram(hReturn); 
     
    // These are no longer needed 
    glDeleteShader(hVertexShader); 
    glDeleteShader(hFragmentShader);   
     
    // Make sure link worked too 
    glGetProgramiv(hReturn, GL_LINK_STATUS, &testVal); 
    if(testVal == GL_FALSE) 
        { 
        glDeleteProgram(hReturn); 
        return (GLuint)NULL; 
        } 
     
    return hReturn;   
    }    
 
 
 
 
///////////////////////////////////////////////////////////////// 
// Check for any GL errors that may affect rendering 
// Check the framebuffer, the shader, and general errors 
bool gltCheckErrors(GLuint progName) 
{ 
    bool bFoundError = false; 
    GLenum error = glGetError(); 
         
    if (error != GL_NO_ERROR) 
    { 
        fprintf(stderr, "A GL Error has occured\n"); 
        bFoundError = true; 
    } 
#ifndef OPENGL_ES 
    GLenum fboStatus = glCheckFramebufferStatus(GL_DRAW_FRAMEBUFFER); 
 
    if(fboStatus != GL_FRAMEBUFFER_COMPLETE) 
    { 
        bFoundError = true; 
        fprintf(stderr,"The framebuffer is not complete - "); 
        switch (fboStatus) 
        { 
        case GL_FRAMEBUFFER_UNDEFINED: 
            // Oops, no window exists? 
            fprintf(stderr, "GL_FRAMEBUFFER_UNDEFINED\n"); 
            break; 
        case GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT: 
            // Check the status of each attachment 
            fprintf(stderr, "GL_FRAMEBUFFER_INCOMPLETE_ATTACHMENT\n"); 
            break; 
        case GL_FRAMEBUFFER_INCOMPLETE_MISSING_ATTACHMENT: 
            // Attach at least one buffer to the FBO 
            fprintf(stderr, "GL_FRAMEBUFFER_INCOMPLETE_MISSING_ATTACHMENT\n"); 
            break; 
        case GL_FRAMEBUFFER_INCOMPLETE_DRAW_BUFFER: 
            // Check that all attachments enabled via 
            // glDrawBuffers exist in FBO 
            fprintf(stderr, "GL_FRAMEBUFFER_INCOMPLETE_DRAW_BUFFER\n"); 
            break; 
        case GL_FRAMEBUFFER_INCOMPLETE_READ_BUFFER: 
            // Check that the buffer specified via 
            // glReadBuffer exists in FBO 
            fprintf(stderr, "GL_FRAMEBUFFER_INCOMPLETE_READ_BUFFER\n"); 
            break; 
        case GL_FRAMEBUFFER_UNSUPPORTED: 
            // Reconsider formats used for attached buffers 
            fprintf(stderr, "GL_FRAMEBUFFER_UNSUPPORTED\n"); 
            break; 
        case GL_FRAMEBUFFER_INCOMPLETE_MULTISAMPLE: 
            // Make sure the number of samples for each  
            // attachment is the same  
            fprintf(stderr, "GL_FRAMEBUFFER_INCOMPLETE_MULTISAMPLE\n"); 
            break;  
        case GL_FRAMEBUFFER_INCOMPLETE_LAYER_TARGETS: 
            // Make sure the number of layers for each  
            // attachment is the same  
            fprintf(stderr, "GL_FRAMEBUFFER_INCOMPLETE_LAYER_TARGETS\n"); 
            break; 
        } 
    } 
 
#endif 
 
    if (progName != 0) 
    { 
        glValidateProgram(progName); 
        int iIsProgValid = 0; 
        glGetProgramiv(progName, GL_VALIDATE_STATUS, &iIsProgValid); 
        if(iIsProgValid == 0) 
        { 
            bFoundError = true; 
            fprintf(stderr, "The current program(%d) is not valid\n", progName); 
        } 
    } 
    return bFoundError; 
} 
 
/////////////////////////////////////////////////////////////////////////////////////////////////////// 
// Create a matrix that maps geometry to the screen. 1 unit in the x directionequals one pixel  
// of width, same with the y direction. 
void gltGenerateOrtho2DMat(GLuint screenWidth, GLuint screenHeight,  
                           M3DMatrix44f &orthoMatrix, GLBatch &screenQuad) 
{ 
    float right = (float)screenWidth; 
    float left  = 0.0f; 
    float top = (float)screenHeight; 
    float bottom = 0.0f; 
     
    // set ortho matrix 
    orthoMatrix[0] = (float)(2 / (right - left)); 
    orthoMatrix[1] = 0.0; 
    orthoMatrix[2] = 0.0; 
    orthoMatrix[3] = 0.0; 
 
    orthoMatrix[4] = 0.0; 
    orthoMatrix[5] = (float)(2 / (top - bottom)); 
    orthoMatrix[6] = 0.0; 
    orthoMatrix[7] = 0.0; 
 
    orthoMatrix[8] = 0.0; 
    orthoMatrix[9] = 0.0; 
    orthoMatrix[10] = (float)(-2 / (1.0 - 0.0)); 
    orthoMatrix[11] = 0.0; 
 
    orthoMatrix[12] = -1*(right + left) / (right - left); 
    orthoMatrix[13] = -1*(top + bottom) / (top - bottom); 
    orthoMatrix[14] = -1.0f; 
    orthoMatrix[15] =  1.0; 
 
    // set screen quad vertex array 
    screenQuad.Reset(); 
    screenQuad.Begin(GL_TRIANGLE_STRIP, 4, 1); 
        screenQuad.Color4f(0.0f, 1.0f, 0.0f, 1.0f); 
        screenQuad.MultiTexCoord2f(0, 0.0f, 0.0f);  
        screenQuad.Vertex3f(0.0f, 0.0f, 0.0f); 
 
        screenQuad.Color4f(0.0f, 1.0f, 0.0f, 1.0f); 
        screenQuad.MultiTexCoord2f(0, 1.0f, 0.0f); 
        screenQuad.Vertex3f((float)screenWidth, 0.0f, 0.0f); 
 
        screenQuad.Color4f(0.0f, 1.0f, 0.0f, 1.0f); 
        screenQuad.MultiTexCoord2f(0, 0.0f, 1.0f); 
        screenQuad.Vertex3f(0.0f, (float)screenHeight, 0.0f); 
 
        screenQuad.Color4f(0.0f, 1.0f, 0.0f, 1.0f); 
        screenQuad.MultiTexCoord2f(0, 1.0f, 1.0f); 
        screenQuad.Vertex3f((float)screenWidth, (float)screenHeight, 0.0f); 
    screenQuad.End(); 
}
```

---

### Post by SevenMachines on 2011-04-27
Are you using the linux makefiles? you could set that up in eclipse but for the simple examples on the command line,

* get the example source
[http://www.starstonesoftware.com/files/SB5.zip](http://www.starstonesoftware.com/files/SB5.zip)

then...
```
$ unzip SB5.zip
$ cd SB5/Linux/Chapter01/Block/
$ make 
$ ./Block
```It looks like all the books examples have equivalent linux makefiles so testing out the examples is just 'make' and then run 

Setting up eclipse involves a adding /usr/include/GL and the GLTools/Include paths to the project properties 'paths and symbols' as well as the libraries glut, GL, GLU, maybe more. 
In my opinion, if your making your own simple examples its more straightforward to use the command  line, and also better for learning how to use c++ compilers.
Also, although i'm a fan of eclipse, for small projects its overkill. For small projects the complexity of eclipse dwarves the actual complexity of what you're trying to do, which can be frustrating and confusing when learning.

---

### Post by rob1101 on 2011-05-02
> **SevenMachines said:**
> 
In my opinion, if your making your own simple examples its more straightforward to use the command  line, and also better for learning how to use c++ compilers.
Also, although i'm a fan of eclipse, for small projects its overkill. For small projects the complexity of eclipse dwarves the actual complexity of what you're trying to do, which can be frustrating and confusing when learning.

I have learned a lot more about the compile and linking process as well as a little about make files. But after this ordeal I tend to agree, I am finding that using his framework and tutorials is just adding another layer of complexity at my level, then adding eclipse does not help either. 

However I have had great success with [these tutorials]("http://ubuntu-gamedev.wikispaces.com/3D+HowTos"). They perfect in the fact that it is so simple and straight forward, and got you drawing basic shapes right off the bat. I wish there were more, but this should keep me busy for a little while and has given me a great starting point. 

Anyway thank you all for steering me in the right direction.

PS, Any recommendations on text editors? I like the simplicity of gedit but i cant figure out how to keep it from auto-completing my ),}, or ] or how to navigate to the console plugin with out using the mouse.

---

### Post by sumtaru on 2012-02-15
Hello, You can refer Effective techniques in C++ by scott meyers.
[http://www.cppbasics.com](http://www.cppbasics.com) is also a good resource

---

