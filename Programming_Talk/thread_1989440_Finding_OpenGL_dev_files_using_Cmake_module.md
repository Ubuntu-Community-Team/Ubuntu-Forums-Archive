---
title: "Finding OpenGL dev files using Cmake module"
date: 2012-05-28
forum: Programming Talk
---

### Post by Cardale on 2012-05-28
I'm trying to find some opengl dev files and I had it working great in 11.10.  I can just barely move around cmake and kind of wrap my head around linux development.

If anyone can provide a better explanation of how I can solve this problem after upgrades and what I should look for in the future would be a huge help.

Here is one of my cmake modules.

```
INCLUDE (FindPackageHandleStandardArgs)
FIND_PACKAGE(PkgConfig ${gl_FIND_REQUIRED} ${gl_FIND_QUIETLY})
IF (PKG_CONFIG_FOUND)
    SET(PKG_CONFIG_PATH_ENV_VAR $ENV{PKG_CONFIG_PATH})
    IF (NOT PKG_CONFIG_PATH_ENV_VAR)
        IF (gl_FIND_REQUIRED)
            MESSAGE (FATAL_ERROR "Environment variable PKG_CONFIG_PATH not set. Setting this variable is required in order for pkg-config to locate installed software packages.")
        ENDIF (gl_FIND_REQUIRED)
    ENDIF (NOT PKG_CONFIG_PATH_ENV_VAR)
    PKG_CHECK_MODULES (gl gl)
    IF (gl_FOUND)
        SET(gl_LIBRARY ${gl_LIBRARIES})
        SET(gl_INCLUDE_DIR ${gl_INCLUDEDIR})
        SET(gl_LIBRARY_DIR ${gl_LIBRARY_DIRS})
        IF (NOT gl_FIND_QUIETLY)
            MESSAGE(STATUS "    includedir: ${gl_INCLUDE_DIR}")
            MESSAGE(STATUS "    librarydir: ${gl_LIBRARY_DIR}")
        ENDIF (NOT gl_FIND_QUIETLY)
    ENDIF(gl_FOUND)
ENDIF (PKG_CONFIG_FOUND)
FIND_PACKAGE_HANDLE_STANDARD_ARGS(gl DEFAULT_MSG gl_LIBRARY gl_INCLUDE_DIR)
```I have basically the same file for glu and glui.

I am not sure what got screwed up in my dev enviornment, but your help is much appreciated.

The error 
```
 DrawGLScene(): error: undefined reference to 'glutSwapBuffers'
```

---

