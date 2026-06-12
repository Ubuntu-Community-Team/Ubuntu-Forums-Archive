---
title: "[OpenGL] GLFW doesn't work with core profile"
date: 2012-10-23
forum: Programming Talk
---

### Post by bird1500 on 2012-10-23
Hi,
I'm using GLFW to create a window showing a triangle in persp projection.
It works fine, but when I set GLFW to use the OpenGL Core profile and GL version 3.3 (uncomment the 3 lines below) then it doesn't show up the triangle anymore, just a blank (black) window.
Any ideas why? I think I'm not using legacy APIs here.

The relevant code,
main() - sets the core profile - those 3 lines are commented out:
[PHP]
int
main(int argc, char *argv[]) {
    
    if(!glfwInit()) {
        exit(1);
    }
    
    glfwDisable(GLFW_AUTO_POLL_EVENTS);
    /*
    glfwOpenWindowHint(GLFW_OPENGL_VERSION_MAJOR, 3);
    glfwOpenWindowHint(GLFW_OPENGL_VERSION_MINOR, 3);
    glfwOpenWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);
    */
    if(!glfwOpenWindow(winw, winh, 0, 0, 0, 0, 32, 0, GLFW_WINDOW)) {
        glfwTerminate();
        return 1;
    }
    
    glfwSetWindowRefreshCallback(WinDraw);
    glfwSetWindowSizeCallback(&WinResize);
    
    GLenum status = glewInit();
    if(status != GLEW_OK) {
        printf("Can't init glew: %s\n", glewGetErrorString(status));
        return 1;
    }
    
    if(!AppSetup()) {
        printf("AppSetup() failed\n");
        return 1;
    }
    
    while(true) {
        glfwWaitEvents();
        if(glfwGetKey(GLFW_KEY_ESC) || !glfwGetWindowParam(GLFW_OPENED)) {
            break;
        }
    }
    
    glfwTerminate();
    delete pManager;
    return 0;
}
[/PHP]The setup func:
[PHP]
bool
AppSetup() {
    
    const GLfloat data[] = {
        -0.5f, -0.5f,
        1.0f, 0.0f, 0.0f,
        
        0.5f, -0.5f,
        0.0f, 1.0f, 0.0f,
        
        0.0f, 0.5f,
        0.0f, 0.0f, 1.0f
    };
    
    glClearColor(0.0f, 0.0f, 0.0f, 1.0f);
    
    glGenBuffers(1, &buf);
    glBindBuffer(GL_ARRAY_BUFFER, buf);
    glBufferData(GL_ARRAY_BUFFER, sizeof(data), data, GL_STATIC_DRAW);
    glBindBuffer(GL_ARRAY_BUFFER, 0);
    
    pManager = new Manager();
    app = pManager->loadProgram("../display.vert", "../display.frag");
    if(app == 0) {
        return false;
    }
    
    locPos = glGetAttribLocation(app, "vPos");
    locColor = glGetAttribLocation(app, "vColor");
    locMvp = glGetUniformLocation(app, "mvp");
    
    if(locPos == -1 || locColor == -1 || locMvp == -1) {
        printf("Can't get attribs\n");
        return false;
    }
    return true;
}
[/PHP]And the rendering func:
[PHP]
void
WinDraw() {
    glClear(GL_COLOR_BUFFER_BIT);
    glUseProgram(app);
    
    Matrix3D translMat;
    Oglm::SetTranslation(translMat, 0.0f, 0.0f, -7.0f);
    Matrix3D projMat;
    Oglm::SetPerspProj(projMat, 45.0f, 1.0f, 0.1f, 100.0f);
    Matrix3D mvp;
    Oglm::Multiply(projMat, translMat, mvp);
    glUniformMatrix4fv(locMvp, 1, GL_FALSE, mvp);
    
    glBindBuffer(GL_ARRAY_BUFFER, buf);
    glEnableVertexAttribArray(locPos);
    glEnableVertexAttribArray(locColor);
    
    glVertexAttribPointer(locPos, 2, GL_FLOAT, GL_FALSE, sizeof(GLfloat)*5, 0);
    glVertexAttribPointer(locColor, 3, GL_FLOAT, GL_FALSE, sizeof(GLfloat)*5,
        (void*) (sizeof(GLfloat)*2));

    glDrawArrays(GL_TRIANGLES, 0, 3);
    
    glDisableVertexAttribArray(locPos);
    glDisableVertexAttribArray(locColor);
    glBindBuffer(GL_ARRAY_BUFFER, 0);

    glfwSwapBuffers();
}
[/PHP]The whole little project is attached.
I'm using Nvidia's driver which advertises OpenGL 4.x

---

### Post by capnramses on 2012-12-27
you're missing a vertex array object. it's like a meta-buffer that tells opengl which vertex buffers to draw. the glenableattribute() calls and attributepointer() calls actually set up the currently bound vertex array object, not the currently bound vertex buffer. you just need to generate one and bind it. then when drawing, instead of binding a vertex buffer you bind the vertex array. if you want a working example [http://antongerdelan.net/opengl4/vertexbuffers.html](http://antongerdelan.net/opengl4/vertexbuffers.html)

---

