---
title: "[OpenGL] Add perspective projection"
date: 2012-10-20
forum: Programming Talk
---

### Post by bird1500 on 2012-10-20
Hi,
Can anyone please add perspective projection into the code below?
I learned how to multiply matrices, vectors, what dot/cross products are, etc except how to setup a perspective projection matrix and use it - just can't get it.

[PHP]
#include <GL/glew.h>
#include <GL/freeglut.h>
#include <stdio.h>

GLuint app, buf;
GLint locPos, locColor;
const GLfloat data[] = {
    -0.5f, -0.5f,
    1.0f, 0.0f, 0.0f,
    
    0.5f, -0.5f,
    0.0f, 1.0f, 0.0f,
    
    0.0f, 0.5f,
    0.0f, 0.0f, 1.0f
};

GLuint CreateShaderType(const GLenum type, const GLchar *src, const char *progName) {
    GLuint shader = glCreateShader(type);
    if(shader == 0) {
        return 0;
    }
    
    glShaderSource(shader, 1, &src, NULL);
    glCompileShader(shader);
    
    GLint status;
    glGetShaderiv(shader, GL_COMPILE_STATUS, &status);
    if(status != GL_FALSE) {
        return shader;
    }
    
    GLint len;
    glGetShaderiv(shader, GL_INFO_LOG_LENGTH, &len);
    if(len > 0) {
        char *log = new char[len];
        glGetShaderInfoLog(shader, len, NULL, log);
        const char *szType;
        if(type == GL_VERTEX_SHADER) {
            szType = "vertex";
        } else if(type == GL_FRAGMENT_SHADER) {
            szType = "fragment";
        } else {
            szType = "unknown";
        }
        printf("Error compiling %s shader of %s: %s\n", szType, progName, log);
        delete[] log;
    }
    glDeleteShader(shader);
    return 0;
}

GLuint CreateShader(const GLchar *vertSrc, const GLchar *fragSrc, const char *progName) {
    GLuint vertShader = CreateShaderType(GL_VERTEX_SHADER, vertSrc, progName);
    if(vertShader == 0) {
        return 0;
    }
    
    GLuint fragShader = CreateShaderType(GL_FRAGMENT_SHADER, fragSrc, progName);
    if(fragShader == 0) {
        glDeleteShader(vertShader);
        return 0;
    }
    
    GLuint prog = glCreateProgram();
    glAttachShader(prog, vertShader);
    glAttachShader(prog, fragShader);
    glLinkProgram(prog);
    glDeleteShader(vertShader);
    glDeleteShader(fragShader);
    
    GLint status;
    glGetProgramiv(prog, GL_LINK_STATUS, &status);
    if(status != GL_FALSE) {
        return prog;
    }
    
    GLint len;
    glGetProgramiv(prog, GL_INFO_LOG_LENGTH, &len);
    if(len > 0) {
        char *log = new char[len];
        glGetProgramInfoLog(prog, len, NULL, log);
        printf("Error linking %s program: %s\n", progName, log);
        delete[] log;
    }
    glDeleteProgram(prog);
    return 0;
}

bool
AppSetup() {
    glClearColor(0.0f, 0.0f, 0.0f, 1.0f);
    
    glGenBuffers(1, &buf);
    glBindBuffer(GL_ARRAY_BUFFER, buf);
    glBufferData(GL_ARRAY_BUFFER, sizeof(data), data, GL_STATIC_DRAW);
    glBindBuffer(GL_ARRAY_BUFFER, 0);
    
    const GLchar *vertSrc =
    "#version 330\n"
    "in vec2 vPos;\n"
    "in vec3 vColor;\n"
    "out vec3 vPassColor;\n"
    "void main() {\n"
    "    vPassColor = vColor;\n"
    "    gl_Position = vec4(vPos, 0.0f, 1.0f);\n"
    "}\n";
    
    const GLchar *fragSrc =
    "#version 330\n"
    "in vec3 vPassColor;\n"
    "out vec4 vOutColor;\n"
    "void main() {\n"
    "    vOutColor = vec4(vPassColor, 1.0f);\n"
    "}\n";
    
    app = CreateShader(vertSrc, fragSrc, "Main shader");
    if(app == 0) {
        return false;
    }
    
    locPos = glGetAttribLocation(app, "vPos");
    locColor = glGetAttribLocation(app, "vColor");
    
    
    return true;
}

void
WinClose() {
    if(app != 0) {
        glDeleteProgram(app);
    }
}

void
WinDraw() {
    glClear(GL_COLOR_BUFFER_BIT);
    
    glUseProgram(app);
    
    glBindBuffer(GL_ARRAY_BUFFER, buf);
    glEnableVertexAttribArray(locPos);
    glEnableVertexAttribArray(locColor);
    
    glVertexAttribPointer(locPos, 2, GL_FLOAT, GL_FALSE, sizeof(GLfloat)*5, 0);
    glVertexAttribPointer(locColor, 3, GL_FLOAT, GL_FALSE, sizeof(GLfloat)*5, (void*) (sizeof(GLfloat)*2));
    
    glDrawArrays(GL_TRIANGLES, 0, 3);
    
    glDisableVertexAttribArray(locPos);
    glDisableVertexAttribArray(locColor);
    glBindBuffer(GL_ARRAY_BUFFER, 0);
    
    glutSwapBuffers();
}

void
WinResize(int w, int h) {
    glViewport(0, 0, w, h);
}


int main(int argc, char *argv[]) {
    
    glutInit(&argc, argv);
    glutInitDisplayMode(GLUT_RGBA | GLUT_DOUBLE | GLUT_DEPTH);
    glutInitWindowSize(800, 500);
    glutCreateWindow("GL 3.3");
    
    glutDisplayFunc(WinDraw);
    glutReshapeFunc(WinResize);
    glutCloseFunc(WinClose);
    
    GLenum status = glewInit();
    if(status != GLEW_OK) {
        printf("Glew init failed %s\n", glewGetErrorString(status));
        return 0;
    }
    
    if(!AppSetup()) {
        return 0;
    }
    
    glutMainLoop();
    return 0;
}
[/PHP]

EDIT: I'll try out [this]("http://www.geeks3d.com/20090729/howto-perspective-projection-matrix-in-opengl/") and see if it works.

---

