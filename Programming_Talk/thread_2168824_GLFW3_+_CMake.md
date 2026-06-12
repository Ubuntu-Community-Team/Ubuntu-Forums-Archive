---
title: "GLFW3 + CMake"
date: 2013-08-19
forum: Programming Talk
---

### Post by stevensantosgarcia on 2013-08-19
Hello.  I followed the following post to succesfully compile and run a simple GLFW 3.0 example:
[URL="http://stackoverflow.com/questions/17768008/how-to-build-install-glfw-3-and-use-it-in-a-linux-project"]
http://stackoverflow.com/questions/17768008/how-to-build-install-glfw-3-and-use-it-in-a-linux-project[/URL]

The source for the simple example is found here:

[http://www.glfw.org/docs/3.0/quick.html](http://www.glfw.org/docs/3.0/quick.html)

```

#include <GLFW/glfw3.h>
#include <stdlib.h>
#include <stdio.h>
static void error_callback(int error, const char* description)
{
    fputs(description, stderr);
}
static void key_callback(GLFWwindow* window, int key, int scancode, int action, int mods)
{
    if (key == GLFW_KEY_ESCAPE && action == GLFW_PRESS)
        glfwSetWindowShouldClose(window, GL_TRUE);
}
int main(void)
{
    GLFWwindow* window;
    glfwSetErrorCallback(error_callback);
    if (!glfwInit())
        exit(EXIT_FAILURE);
    window = glfwCreateWindow(640, 480, "Simple example", NULL, NULL);
    if (!window)
    {
        glfwTerminate();
        exit(EXIT_FAILURE);
    }
    glfwMakeContextCurrent(window);
    glfwSetKeyCallback(window, key_callback);
    while (!glfwWindowShouldClose(window))
    {
        float ratio;
        int width, height;
        glfwGetFramebufferSize(window, &width, &height);
        ratio = width / (float) height;
        glViewport(0, 0, width, height);
        glClear(GL_COLOR_BUFFER_BIT);
        glMatrixMode(GL_PROJECTION);
        glLoadIdentity();
        glOrtho(-ratio, ratio, -1.f, 1.f, 1.f, -1.f);
        glMatrixMode(GL_MODELVIEW);
        glLoadIdentity();
        glRotatef((float) glfwGetTime() * 50.f, 0.f, 0.f, 1.f);
        glBegin(GL_TRIANGLES);
        glColor3f(1.f, 0.f, 0.f);
        glVertex3f(-0.6f, -0.4f, 0.f);
        glColor3f(0.f, 1.f, 0.f);
        glVertex3f(0.6f, -0.4f, 0.f);
        glColor3f(0.f, 0.f, 1.f);
        glVertex3f(0.f, 0.6f, 0.f);
        glEnd();
        glfwSwapBuffers(window);
        glfwPollEvents();
    }
    glfwDestroyWindow(window);
    glfwTerminate();
    exit(EXIT_SUCCESS);
}



```

It successfully compiles with:
 
[B]g++ -c main.cpp
[/B]**g++ main.o main.exec -lGL -lGLU -lglfw3 -lX11 -lXxf86vm -lXrandr -lpthread -lXi**

I have since been attempting to build using CMake and have been unsuccessful so far. Here   is my current CMakeLists.txt:
 
```

#----------------------------------------------------------------------
# 
#----------------------------------------------------------------------
cmake_minimum_required(VERSION 2.8)


set(PROJ_NAME hello_glfw)


project(${PROJ_NAME})


#set up linux search paths
set(LIBRARY_SEARCH_PATH
  /usr/local
  /opt/local
  /usr
  /opt
)


set(HEADER_SEARCH_PATH
  /usr/local
  /opt/local
  /usr
  /opt
)


# Find OpenGL
find_package(OpenGL)
find_package(X11)


# Find glfw header
find_path(GLFW_INCLUDE_DIR GLFW/glfw3.h ${HEADER_SEARCH_PATH})


# Find glfw library
find_library(GLFW_LIBRARIES glfw3 ${LIBRARY_SEARCH_PATH})


# gets rid of undefined reference to 'XF86VidModeQueryExtension'
find_library(X11_LIBRARIES X11R6 ${LIBRARY_SEARCH_PATH})


# Include directories for this project
set(INCLUDE_PATH
  ${OPENGL_INCLUDE_DIR}
  ${GLFW_INCLUDE_DIR}
)


# Libraries needed on all platforms for this project
set(LIBRARIES
  ${OPENGL_LIBRARIES}
  ${GLFW_LIBRARIES}
  ${X11_LIBRARIES}
)


# Windows and Linux need GLEW, the OpenGL Extension Wrangler
find_path(GLEW_INCLUDE_DIR GL/glew.h
    ${HEADER_SEARCH_PATH}
)


set(INCLUDE_PATH ${INCUDE_PATH}
    ${GLEW_INCLUDE_DIR} 
)


#set flags
set(CMAKE_CXX_FLAGS "-lGL -lGLU -lglfw3 -lX11 -lXxf86vm -lXrandr -lpthread -lXi")


# Add a target executable
add_executable(${PROJ_NAME}
  main.cpp
)


# Libraries to be linked
target_link_libraries(${PROJ_NAME}
  ${LIBRARIES}
 )


```


While I have been eliminating errors one by one over the past couple days I've been stuck on the latest which is the following:

```

Linking CXX executable hello_glfw
/usr/bin/ld: /usr/local/lib/libglfw3.a(x11_clipboard.c.o): undefined reference to symbol 'XConvertSelection'
/usr/bin/ld: note: 'XConvertSelection' is defined in DSO /usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/libX11.so so try adding it to the linker command line
/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/libX11.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[2]: *** [hello_glfw] Error 1
make[1]: *** [CMakeFiles/hello_glfw.dir/all] Error 2
make: *** [all] Error 2
xxxxxx@ubuntu:~/Documents/hello_glfw/build$ 

```

As you can see in my CMakeLists.txt I have the line:  [B]set(CMAKE_CXX_FLAGS "-lGL -lGLU -lglfw3 -lX11 -lXxf86vm -lXrandr -lpthread -lXi")
[/B]
I am determined to figure this out and I hope someone can give me some insight as to what the problem may be (or perhaps point me to some helpful threads).  Thank you for your time.

Here is my updated CMakeLists.txt:

```

#----------------------------------------------------------------------
# 
#----------------------------------------------------------------------
cmake_minimum_required(VERSION 2.8)


set(PROJ_NAME hello_glfw)


project(${PROJ_NAME})


#set up linux search paths
set(LIBRARY_SEARCH_PATH
  /usr/local
  /opt/local
  /usr
  /opt
)


set(HEADER_SEARCH_PATH
  /usr/local
  /opt/local
  /usr
  /opt
)


# Find OpenGL
find_package(OpenGL)
find_package(X11)


# Find glfw header
find_path(GLFW_INCLUDE_DIR GLFW/glfw3.h ${HEADER_SEARCH_PATH})


# Find glfw library
find_library(GLFW_LIBRARIES glfw3 ${LIBRARY_SEARCH_PATH})


# Set additional libs
set( ADDITIONAL_LIBS 
     -lGLEW
     -lGLU 
     -lglfw3
     -pthread
     -lrt
     -lXinerama
     -lXrandr
     -lXxf86vm
     -lXi
)


# Include directories for this project
set(INCLUDE_PATH
  ${OPENGL_INCLUDE_DIR}
  ${GLFW_INCLUDE_DIR}
)


# Libraries needed on all platforms for this project
set(LIBRARIES
  ${OPENGL_LIBRARIES}
  ${GLFW_LIBRARIES}
  ${X11_LIBRARIES}
  ${ADDITIONAL_LIBS}  
)


# Windows and Linux need GLEW, the OpenGL Extension Wrangler
find_path(GLEW_INCLUDE_DIR GL/glew.h
    ${HEADER_SEARCH_PATH}
)


set(INCLUDE_PATH ${INCUDE_PATH}
    ${GLEW_INCLUDE_DIR} 
)


# Add a target executable
add_executable(${PROJ_NAME}
  main.cpp
)


# Libraries to be linked
target_link_libraries(${PROJ_NAME}
  ${LIBRARIES}
)



```

---

