---
title: "Compiling CEGUI and samples"
date: 2014-09-25
forum: Packaging and Compiling Programs
---

### Post by komarx6 on 2014-09-25
I've downloaded CEGUI source from official site. I tried to compile it. First I installed cegui-mk2* packages, because I read that it's necessary dependencies. After that compilation complited successfully.
But README.md says that in build folder should be bin folder, but in my case there is only lib folder. It also says that if I install (make install) cegui system wide I should be able to run samples just by typeing sample name in terminal. But I can't, and I suppose thats because samples are not even compiled, they should be in bin folder, I suppose.

cmake gives me this output:
> -- Could NOT find MINIZIP (missing:  MINIZIP_LIB MINIZIP_H_PATH) 
-- Could NOT find OpenGL (missing:  OPENGL_gl_LIBRARY) 
-- Could NOT find GLEW (missing:  GLEW_LIB GLEW_H_PATH) 
-- Could NOT find GLM (missing:  GLM_H_PATH) 
-- Could NOT find GLFW (missing:  GLFW_LIB GLFW_H_PATH) 
-- Could NOT find DIRECTXSDK (missing:  DIRECTXSDK_LIB_PATH DIRECTXSDK_H_PATH DIRECTXSDK_MAX_D3D) 
-- Could NOT find D3DX11EFFECTS (missing:  D3DX11EFFECTS_LIB D3DX11EFFECTS_H_PATH) 
-- Could NOT find IRRLICHT (missing:  IRRLICHT_LIB IRRLICHT_H_PATH) 
-- Could NOT find OGRE (missing:  OGRE_LIB OGRE_H_PATH OGRE_H_BUILD_SETTINGS_PATH) 
-- Could NOT find OIS (missing:  OIS_LIB OIS_H_PATH) 
-- Could NOT find DIRECTFB (missing:  DIRECTFB_LIB DIRECTFB_H_PATH) 
-- Could NOT find OPENGLES (missing:  OPENGLES_LIB OPENGLES_H_PATH) 
-- Could NOT find EXPAT (missing:  EXPAT_LIB EXPAT_H_PATH) 
-- Could NOT find XERCESC (missing:  XERCESC_LIB XERCESC_H_PATH) 
-- Could NOT find LibXml2 (missing:  LIBXML2_LIBRARIES LIBXML2_INCLUDE_DIR) 
-- Could NOT find TINYXML (missing:  TINYXML_LIB TINYXML_H_PATH) 
-- Could NOT find RAPIDXML (missing:  RAPIDXML_H_PATH) 
-- Could NOT find SILLY (missing:  SILLY_LIB SILLY_H_PATH) 
-- Could NOT find CORONA (missing:  CORONA_LIB CORONA_H_PATH) 
-- Could NOT find PVRTOOLS (missing:  PVRTOOLS_LIB PVRTOOLS_H_PATH) 
-- Could NOT find PythonLibs (missing:  PYTHON_INCLUDE_DIRS) 
-- Could NOT find Boost
-- Could NOT find Doxygen (missing:  DOXYGEN_EXECUTABLE) 
-- Some or all of the gtk libraries were not found. (missing:  GTK2_GTK_LIBRARY GTK2_GTK_INCLUDE_DIR GTK2_GLIB_INCLUDE_DIR GTK2_GLIBCONFIG_INCLUDE_DIR GTK2_GLIB_LIBRARY GTK2_GDK_INCLUDE_DIR GTK2_GDKCONFIG_INCLUDE_DIR GTK2_GDK_LIBRARY) 
CMake Warning at CMakeLists.txt:340 (message):
  None of the XML parser modules are going to be built.

  You should ensure that CEGUI_OPTION_DEFAULT_XMLPARSER is set to something

  appropriate.


-- Configuring done
-- Generating done
-- Build files have been written to:

But I need EXPAT and lua with cegui. So I installed expat package via apt-get. But still it says that EXPAT is not found. I suppose that I didn't get samples they depend on some of this packages.
How to solve this problem?

Thank you.
Please help.

---

### Post by thibaud-ecarot on 2014-10-23
Hello friend,

it's very strange because Cmake log say that :
> Could NOT find Boost

Can you post your CMakeList.txt ? Or the CMkaeList of CeGUI source ?

Thanks in advance.

---

