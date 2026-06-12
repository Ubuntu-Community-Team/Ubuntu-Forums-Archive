---
title: "[How to] make your Ogre3D game on Ubuntu"
date: 2008-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by lingnoi on 2008-05-05
**Note:**

You no longer have to compile your own version of Ogre, I have made my own deb packages [available here]("https://launchpad.net/~andrewfenn/+archive/ogredev").

First add the key

Copy and paste this in the terminal

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6FED7057
```

Then go to System->Administration->Software Sources. Click on the "Third Party Software" Tab and then click the "Add" button.

Replace the word "jaunty" with your version of Ubuntu below and add these repos.

```
deb http://ppa.launchpad.net/andrewfenn/ogredev/ubuntu jaunty main
```
```
deb-src http://ppa.launchpad.net/andrewfenn/ogredev/ubuntu jaunty main
```

After you have done that click close.

You can now get updates for the latest stable release of Ogre and CEGUI.

**If you wish to compile Ogre yourself then keep reading below.**


**Introduction**

Ogre3d and a graphics rendering engine that one can use in either your game or 3d graphics program. It's under a dual license, the source is available under the LGPL but you can also purchase a commercial license for companies do not want to share additions to the Ogre Engine, or need technical support.

This is a newish "how to" on getting everything set up so you can start making your games on Ubuntu using the latest version of Ogre3D and CEGUI. Before you start you might want to have a quick read of the [getting started with Ogre guide]("http://www.ogre3d.org/wiki/index.php/GetStarted") to make sure Ogre3d is the graphics engine you want to use.

**Why compile yourself?**

- Ogre in the repositories is always an old version, this makes any development work difficult especially if you're trying to integrate code for specific versions of packages.
- The package for Ogre is taken from Debian that means they have taken out support for cg which is not recommended. It also builds with support for the old openexr implementation rather then use freeimage support.
- The packages for CEGUI are broken. It is impossible with the packages in Ubuntu to load up ogre's scheme files using CEGUI as they have not been built correctly.

If none of these are problem for you then please go ahead and use the repositories, but I don't feel that's the case for most Ogre uses. The above problems all have bugs filed on launchpad.

**OK, lets do it**

First you're going to want to install the following packages.

```
sudo apt-get install build-essential libois-dev
```

Build-Essential gives you everything you need to compile your programs. libois is the Open Input System which is used in the Ogre and CEGUI samples. If you're not using libOIS in your program then there is no need to install it although you might need to change some options in the ./configure if you don't.

We're going to start by building some packages and then I'll show you a sample makefile at the end you can use.

**Building FreeImage**

First I like to start by adding the latest version of FreeImage as the packages for Ubuntu are always out of date. First go to [FreeImage's website]("http://freeimage.sourceforge.net/"), then go to the download link and get the "Source distribution".

When you have downloaded that, unzip it, cd into the directory and type:

```
make
```

followed afterwards by

```
sudo make install
```

**Building CEGUI**

Next we will install CEGUI. If you're not going to use Crazy Eddies GUI in your program you can skip this step.

The way Ubuntu packages CEGUI is incorrect if you want to use it with Ogre3D's default schemes. To correct this we need to download and build CEGUI ourselves.

For building CEGUI you're going to need to first install the following packages.

```
sudo apt-get install libfreetype6-dev libpcre3-dev
```

Go to the [CEGUI download page]("http://www.cegui.org.uk/wiki/index.php/Downloads") and get the latest stable branch of "CEGUI Library Source Downloads". It will be marked as the one for Linux users.

So unzip it ,cd into the directory and type the following.

```
./configure --with-default-xml-parser=TinyXMLParser --with-default-image-codec=FreeImageImageCodec
```

It will check that you have everything you need then give you the message "Now you can do make && make install.  Good Luck!"

Do what it says, don't forget to add "sudo" to your "make install".

**Building Ogre3d**

To so now we're going to build Ogre3D. Go and [download the version of Ogre]("http://www.ogre3d.org/index.php?option=com_content&task=view&id=412&Itemid=132") you want to use. I suggest the current stable package. Make sure you download the "Linux / OSX" package.

First you're going to need to install a few packages to get Ogre building.
```
sudo apt-get install autoconf automake libtool libzzip-dev libxt-dev libxaw6-dev libxxf86dga-dev libxxf86vm-dev libxrandr-dev nvidia-cg-toolkit libglu1-mesa-dev
```

Again, unzip it, cd into the directory and type the following..

```
./bootstrap
./configure
make
sudo make install
```

After you have compiled and installed Ogre on your system use the following command to make the library you just installed work.

```
sudo ldconfig
```

You should also now be able to run the demos if you built them. They are located in /ogre/samples/common/bin, with "/ogre" being the directory you extracted the source from.

- **Makefile** - So you have done all that and want to start coding.

I suggest you layout your folders directory structure like this..

```
./yourgame/Makefile
./yourgame/src
./yourgame/include
./yourgame/media
./yourgame/bin
./yourgame/cmake/modules
```

You put your .cpp file into the src directory, your .h files will go into include and Ogre's media directory will be put into media. The bin directory will be where your compiled program goes, in that file you're going to need "Ogre.cfg", "plugins.cfg", "resources.cfg" which you can get from an example Ogre app.

If you compiled Ogre yourself you're going to need to change "PluginFolder" in Plugins.cfg to the following..

```
PluginFolder=/usr/local/lib/OGRE/
```

**Compiling your own Ogre programs**

So you've installed your dependencies, maybe you have some code already, how do you compile, link and run it? Well let me introduce you to cmake.

cmake is a program which will generate Makefiles for you, it's actually much more then this. It will generate visual studio programs, code::blocks, xcode, MinGW, whatever compiler or IDE you use to program in it will probably do it and all you have to do is type "cmake ."

To set cmake up you need to write a script for it. 

I suggest looking at [my cmake script]("http://bazaar.launchpad.net/~hardwar/hardwar/trunk/annotate/29?file_id=cmakelists.txt-20080809160108-tahtcmbo0sfzdeu5-1") as well as the [FindOGRE module]("http://bazaar.launchpad.net/~hardwar/hardwar/trunk/files/29?file_id=modules-20080809160058-v3lolt4nm2ufvbmv-3") you will need.

Setting up cmake can be difficult at first, but it's very much worth it for the ease of just typing cmake . to setup your build environment.

Here is a stripped down version of my script. Put this is in ./yourgame/CMakeLists.txt

```
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)



#Change PROJECT_NAME to the name of your project

PROJECT(Project)



# Change to whatever version your project is at

SET( ${PROJECT_NAME}_MAJOR_VERSION 0 ) # < -- Something completely different from old version

SET( ${PROJECT_NAME}_MINOR_VERSION 1 ) # < -- Incompatable with old versions

SET( ${PROJECT_NAME}_PATCH_LEVEL 4 )   # < -- Minor fix



SET( CMAKE_MODULE_PATH    ${CMAKE_MODULE_PATH}

                          ${CMAKE_CURRENT_SOURCE_DIR}/cmake/modules )



SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)



#Declare any external dependencies that your project may have here.

SET(Required_Packages
   OIS

   OGRE

   CEGUI

   CEGUIOGRE

)



# searches for all .cpp and .h files in the current directory and add them 

# to the current project

FILE(GLOB folder_source ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp)

SOURCE_GROUP(${Project} FILES ${folder_source})



INCLUDE_DIRECTORIES(${CMAKE_SOURCE_DIR}/include)


IF (NOT WIN32) # Unix
    # Add compiler warnings ( Warn all, warn unused)

    ADD_DEFINITIONS( "-Wall -Wunused -ansi" )
ENDIF (NOT WIN32)


# create the project (Note WIN32 here will be ignored on linux, it means set to be
# windows application instead of a console application)

ADD_EXECUTABLE(${Project} WIN32 ${folder_source})



#this foreach loads all of the packages that you specified as required.

#It shouldn't need to be modified.

FOREACH(Package ${Required_Packages})

  FIND_PACKAGE(${Package} REQUIRED)

  IF (${Package}_FOUND)

      INCLUDE_DIRECTORIES(${${Package}_INCLUDE_DIR})

      IF (${Package}_LIBRARIES)

         TARGET_LINK_LIBRARIES(hardwar ${${Package}_LIBRARIES})

      ELSE (${Package}_LIBRARIES)

         LINK_DIRECTORIES(${${Package}_LIBRARY_DIRS})

      ENDIF (${Package}_LIBRARIES)

  ELSE (${Package}_FOUND)

      MESSAGE(STATUS "${Package} not found")

  ENDIF(${Package}_FOUND)

ENDFOREACH(Package)
```

**Making a program in Ogre**

To start coding in Ogre3d Check out the [Basic Tutorials]("http://www.ogre3d.org/wiki/index.php/Basic_Tutorial_1") and build your way up from there.

**Further Reading**

Here is some further reading I recommend in coding on Linux using Ogre3d.

[Setting up an application]("http://www.ogre3d.org/wiki/index.php/SettingUpAnApplication") - Deals with setting up your Ogre3d application and compiling it.
[Build FAQ]("http://www.ogre3d.org/wiki/index.php/BuildFAQ") - Deals with some problems people have compiling their programs with Ogre.

**Other Stuff you might want to look at**

[Navi]("http://navi.agelessanime.com/wiki/index.php/Main_Page") - A different User Interface API for Ogre
[FXpression]("http://fxpression.com/") - A particle engine which has a plugin for Ogre
[Bullet]("http://www.bulletphysics.com/Bullet/wordpress/") - A physics engine which can be plugged into Ogre
Optimizing Your C/C++ Applications - [Part 1]("http://developer.amd.com/documentation/articles/pages/6212004126.aspx") and [Part 2]("http://developer.amd.com/documentation/articles/pages/7162004127.aspx")

I hope this helps some people. :)

---

### Post by Gwarkill on 2008-05-09
Ok so I have been relentlessly trying to get this to work but I'm receiving this error:

I get this when trying to make FreeImage:
```

tyler@Tyler-desktop:~/FreeImage$ make
make -f Makefile.gnu 
make[1]: Entering directory `/home/tyler/FreeImage'
g++ -O3 -fPIC -fexceptions -fvisibility=hidden  -Wno-ctor-dtor-privacy -I. -ISource -ISource/Metadata -ISource/FreeImageToolkit -ISource/LibJPEG -ISource/LibMNG -ISource/LibPNG -ISource/LibTIFF -ISource/ZLib -ISource/LibOpenJPEG -ISource/OpenEXR -ISource/OpenEXR/Half -ISource/OpenEXR/Iex -ISource/OpenEXR/IlmImf -ISource/OpenEXR/IlmThread -ISource/OpenEXR/Imath -c Source/FreeImage/PluginBMP.cpp -o Source/FreeImage/PluginBMP.o
Source/FreeImage/PluginBMP.cpp: In function &#8216;BOOL LoadPixelDataRLE4(FreeImageIO*, void*, int, int, FIBITMAP*)&#8217;:
Source/FreeImage/PluginBMP.cpp:227: error: no matching function for call to &#8216;MIN(int&, long int)&#8217;
Source/FreeImage/PluginBMP.cpp:282: error: no matching function for call to &#8216;MIN(int&, long int)&#8217;
make[1]: *** [Source/FreeImage/PluginBMP.o] Error 1
make[1]: Leaving directory `/home/tyler/FreeImage'
make: *** [default] Error 2
tyler@Tyler-desktop:~/FreeImage$ 

```

I get this when trying to configure and make CEGUI:
```

********************************************************************************
* Crazy Eddie's GUI System - Configuration Results Summary
********************************************************************************
* Library Release Version:                              0.6.0
*
* Code options:
*         Building CEGUI in debug mode:                 no
*
* Renderer Modules:
*         Building OpenGL Renderer:                     yes
*         Building Irrlict Renderer:                    no
*
* Image Loading Codec Modules (currently for OpenGL Renderer only):
*         Building Corona Image Codec:                  no
*         Building DevIL Image Codec:                   yes
*         Building FreeImage Image Codec:               yes
*         Building SILLY Image Codec:                   no
*         Building TGA Image Codec:                     yes
*
*         Default Image Codec will be:                  FreeImageImageCodec
*
* XML Parser Modules:
*         Building TinyXMLParser:                       yes
*         Building ExpatParser:                         yes
*         Building LibXMLParser:                        yes
*         Building XercesParser:                        yes
*
*         Default XML Parser is:                        TinyXMLParser
*
* Scripting:
*         Building Lua scripting module:                no
*         Building tolua++cegui generator:              no
*
* Samples Framework:
*         Building Samples:                             yes
*         GTK2 based dialog for renderer selection:     no
*         OpenGL Renderer available in samples:         yes
*         Irrlict Renderer available in samples:        no
*         Ogre3D Renderer available in samples:         yes
********************************************************************************

Now you can do make && make install.  Good Luck!

tyler@Tyler-desktop:~/CEGUI-0.6.0$ make
Making all in .
make[1]: Entering directory `/home/tyler/CEGUI-0.6.0'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/tyler/CEGUI-0.6.0'
Making all in src
make[1]: Entering directory `/home/tyler/CEGUI-0.6.0/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/tyler/CEGUI-0.6.0/src'
Making all in include
make[1]: Entering directory `/home/tyler/CEGUI-0.6.0/include'
make  all-recursive
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/include'
Making all in .
make[3]: Entering directory `/home/tyler/CEGUI-0.6.0/include'
make[3]: Leaving directory `/home/tyler/CEGUI-0.6.0/include'
Making all in elements
make[3]: Entering directory `/home/tyler/CEGUI-0.6.0/include/elements'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/tyler/CEGUI-0.6.0/include/elements'
Making all in falagard
make[3]: Entering directory `/home/tyler/CEGUI-0.6.0/include/falagard'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/tyler/CEGUI-0.6.0/include/falagard'
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/include'
make[1]: Leaving directory `/home/tyler/CEGUI-0.6.0/include'
Making all in XMLParserModules
make[1]: Entering directory `/home/tyler/CEGUI-0.6.0/XMLParserModules'
Making all in .
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/XMLParserModules'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/XMLParserModules'
Making all in XercesParser
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/XMLParserModules/XercesParser'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/XMLParserModules/XercesParser'
Making all in expatParser
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/XMLParserModules/expatParser'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/XMLParserModules/expatParser'
Making all in libxmlParser
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/XMLParserModules/libxmlParser'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/XMLParserModules/libxmlParser'
Making all in TinyXMLParser
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/XMLParserModules/TinyXMLParser'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/XMLParserModules/TinyXMLParser'
make[1]: Leaving directory `/home/tyler/CEGUI-0.6.0/XMLParserModules'
Making all in ImageCodecModules
make[1]: Entering directory `/home/tyler/CEGUI-0.6.0/ImageCodecModules'
Making all in .
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/ImageCodecModules'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/ImageCodecModules'
Making all in DevILImageCodec
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/ImageCodecModules/DevILImageCodec'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/ImageCodecModules/DevILImageCodec'
Making all in FreeImageImageCodec
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/ImageCodecModules/FreeImageImageCodec'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/ImageCodecModules/FreeImageImageCodec'
Making all in TGAImageCodec
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/ImageCodecModules/TGAImageCodec'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/ImageCodecModules/TGAImageCodec'
make[1]: Leaving directory `/home/tyler/CEGUI-0.6.0/ImageCodecModules'
Making all in RendererModules
make[1]: Entering directory `/home/tyler/CEGUI-0.6.0/RendererModules'
Making all in .
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/RendererModules'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/RendererModules'
Making all in OpenGLGUIRenderer
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/RendererModules/OpenGLGUIRenderer'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/RendererModules/OpenGLGUIRenderer'
Making all in directx81GUIRenderer
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/RendererModules/directx81GUIRenderer'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/RendererModules/directx81GUIRenderer'
Making all in directx9GUIRenderer
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/RendererModules/directx9GUIRenderer'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/RendererModules/directx9GUIRenderer'
make[1]: Leaving directory `/home/tyler/CEGUI-0.6.0/RendererModules'
Making all in WindowRendererSets
make[1]: Entering directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets'
Making all in Falagard
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets/Falagard'
Making all in src
make[3]: Entering directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets/Falagard/src'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets/Falagard/src'
Making all in include
make[3]: Entering directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets/Falagard/include'
Making all in .
make[4]: Entering directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets/Falagard/include'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets/Falagard/include'
make[3]: Leaving directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets/Falagard/include'
make[3]: Entering directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets/Falagard'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets/Falagard'
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets/Falagard'
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets'
make[1]: Leaving directory `/home/tyler/CEGUI-0.6.0/WindowRendererSets'
Making all in ScriptingModules
make[1]: Entering directory `/home/tyler/CEGUI-0.6.0/ScriptingModules'
Making all in .
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/ScriptingModules'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/ScriptingModules'
make[1]: Leaving directory `/home/tyler/CEGUI-0.6.0/ScriptingModules'
Making all in Samples
make[1]: Entering directory `/home/tyler/CEGUI-0.6.0/Samples'
Making all in .
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/Samples'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/Samples'
Making all in common
make[2]: Entering directory `/home/tyler/CEGUI-0.6.0/Samples/common'
Making all in include
make[3]: Entering directory `/home/tyler/CEGUI-0.6.0/Samples/common/include'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/tyler/CEGUI-0.6.0/Samples/common/include'
Making all in src
make[3]: Entering directory `/home/tyler/CEGUI-0.6.0/Samples/common/src'
/bin/bash ../../../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I../../../include -I../../../Samples/common/include -I../../../include -I../../.. -DCEGUI_SAMPLE_DATAPATH="\"/usr/local/share/CEGUI"\"  -DOGRE_GUI_GLX -DOGRE_CONFIG_LITTLE_ENDIAN -I/usr/local/include -I/usr/local/include/CEGUI -I/usr/include/OGRE   -I/usr/local/include/OIS -I/usr/local/include       -g -O2 -MT libCEGUISampleHelper_la-CEGuiOgreBaseApplication.lo -MD -MP -MF .deps/libCEGUISampleHelper_la-CEGuiOgreBaseApplication.Tpo -c -o libCEGUISampleHelper_la-CEGuiOgreBaseApplication.lo `test -f 'CEGuiOgreBaseApplication.cpp' || echo './'`CEGuiOgreBaseApplication.cpp
 g++ -DHAVE_CONFIG_H -I. -I../../../include -I../../../Samples/common/include -I../../../include -I../../.. -DCEGUI_SAMPLE_DATAPATH=\"/usr/local/share/CEGUI\" -DOGRE_GUI_GLX -DOGRE_CONFIG_LITTLE_ENDIAN -I/usr/local/include -I/usr/local/include/CEGUI -I/usr/include/OGRE -I/usr/local/include/OIS -I/usr/local/include -g -O2 -MT libCEGUISampleHelper_la-CEGuiOgreBaseApplication.lo -MD -MP -MF .deps/libCEGUISampleHelper_la-CEGuiOgreBaseApplication.Tpo -c CEGuiOgreBaseApplication.cpp  -fPIC -DPIC -o .libs/libCEGUISampleHelper_la-CEGuiOgreBaseApplication.o
CEGuiOgreBaseApplication.cpp: In constructor &#8216;CEGuiDemoFrameListener::CEGuiDemoFrameListener(CEGuiBaseApplication*, Ogre::RenderWindow*, Ogre::Camera*, bool, bool)&#8217;:
CEGuiOgreBaseApplication.cpp:218: error: &#8216;class OIS::InputManager&#8217; has no member named &#8216;numKeyBoards&#8217;
CEGuiOgreBaseApplication.cpp:225: error: &#8216;class OIS::InputManager&#8217; has no member named &#8216;numMice&#8217;
make[3]: *** [libCEGUISampleHelper_la-CEGuiOgreBaseApplication.lo] Error 1
make[3]: Leaving directory `/home/tyler/CEGUI-0.6.0/Samples/common/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tyler/CEGUI-0.6.0/Samples/common'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tyler/CEGUI-0.6.0/Samples'
make: *** [all-recursive] Error 1
```



any clue to why this is occurring:confused:?

---

### Post by lingnoi on 2008-05-10
Do you have build-essential installed? If you can't get FreeImage built then you can use the Ubuntu repository.

```
apt-get install build-essential libfreeimage-dev
```

Your second problem looks like not having OIS installed..

```
apt-get install libois-dev
```

---

### Post by Gwarkill on 2008-05-10
Checked both and they are both the latest version.

---

### Post by lingnoi on 2008-05-11
Try building CEGUI without the samples

```
./configure --with-default-xml-parser=TinyXMLParser --with-default-image-codec=FreeImageImageCodec --disable-samples
```

---

### Post by Gwarkill on 2008-05-11
I think every thing is ok. 

How do i actually run ogre.

---

### Post by lingnoi on 2008-05-12
> **Gwarkill said:**
> I think every thing is ok. 

How do i actually run ogre.

OK, so you compiled Ogre3d and want to do some coding..

I suggest checking the [tutorials]("http://www.ogre3d.org/wiki/index.php/Basic_Tutorial_1") on Ogre's wiki.

I'll write more about it in my first post.

---

### Post by Gwarkill on 2008-05-14
You have been one hell of a help. Thanks bro. 

:)

---

### Post by lingnoi on 2008-05-18
I updated this tutorial. All the packages you need to install to get this compiled have been added, a few extra notes, etc.

If anyone has problems leave a reply or private message me. :)

---

### Post by mbsullivan on 2008-05-20
Thanks! The post was very helpful.

Mike

---

### Post by lingnoi on 2008-05-25
Update: There is an nvidia bug in the new drivers. Use Nvidia-glx instead of nvidia-glx-new package.

```
sudo apt-get install nvidia-glx
```

You will be asked to remove nvidia-glx-new.

Also at the time of writing this the v1-6 branch demos aren't displaying correctly with either drivers, but Ogre's trunk (1.8 ?) seems to be working fine.

---

### Post by lingnoi on 2008-10-19
I have updated this thread as I have added my own packages making it super easy to start hacking on Ogre.

---

### Post by mattgaunt on 2008-11-24
Heya

I'm having some serious problems installing Ogre on Hardy Heron, I keep on getting this output from the ogre Water example

```
$ ./Water 
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
FreeImage version: 3.9.3
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See http://freeimage.sourceforge.net for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi
DDS codec registering
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
Loading library /usr/local/lib/OGRE/RenderSystem_GL.so
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_ParticleFX.so
Installing plugin: ParticleFX
Particle Emitter Type 'Point' registered
Particle Emitter Type 'Box' registered
Particle Emitter Type 'Ellipsoid' registered
Particle Emitter Type 'Cylinder' registered
Particle Emitter Type 'Ring' registered
Particle Emitter Type 'HollowEllipsoid' registered
Particle Affector Type 'LinearForce' registered
Particle Affector Type 'ColourFader' registered
Particle Affector Type 'ColourFader2' registered
Particle Affector Type 'ColourImage' registered
Particle Affector Type 'ColourInterpolator' registered
Particle Affector Type 'Scaler' registered
Particle Affector Type 'Rotator' registered
Particle Affector Type 'DirectionRandomiser' registered
Particle Affector Type 'DeflectorPlane' registered
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_BSPSceneManager.so
Installing plugin: BSP Scene Manager
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_OctreeSceneManager.so
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_CgProgramManager.so
Installing plugin: Cg Program Manager
Plugin successfully installed
*-*-* OGRE Initialising
*-*-* Version 1.6.0 (Shoggoth)
Creating resource group Bootstrap
Added resource location '../../Media/packs/OgreCore.zip' of type 'Zip' to resource group 'Bootstrap'
Added resource location '../../Media' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/fonts' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/materials/programs' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/materials/scripts' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/materials/textures' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/models' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/overlays' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/particle' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/gui' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/DeferredShadingMedia' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/PCZAppMedia' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/packs/cubemap.zip' of type 'Zip' to resource group 'General'
Added resource location '../../Media/packs/cubemapsJS.zip' of type 'Zip' to resource group 'General'
Added resource location '../../Media/packs/dragon.zip' of type 'Zip' to resource group 'General'
Added resource location '../../Media/packs/fresneldemo.zip' of type 'Zip' to resource group 'General'
Added resource location '../../Media/packs/ogretestmap.zip' of type 'Zip' to resource group 'General'
Added resource location '../../Media/packs/skybox.zip' of type 'Zip' to resource group 'General'
*** glibc detected *** ./Water: free(): invalid next size (fast): 0x0835bdc0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7319a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb731d4f0]
/usr/local/lib/libOgreMain-1.6.0.so(_ZN4Ogre4Root16showConfigDialogEv+0x55)[0xb7cf3325]
./Water[0x804dfba]
./Water[0x80523c3]
./Water[0x804cf21]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb72c4450]
./Water(__gxx_personality_v0+0x1d5)[0x804c711]
======= Memory map: ========
08048000-08061000 r-xp 00000000 08:03 664431     /home/matt/Programs/ogre/Samples/Common/bin/Water
08061000-08062000 rw-p 00019000 08:03 664431     /home/matt/Programs/ogre/Samples/Common/bin/Water
08062000-08716000 rw-p 08062000 00:00 0          [heap]
b5700000-b5721000 rw-p b5700000 00:00 0 
b5721000-b5800000 ---p b5721000 00:00 0 
b5847000-b58a7000 rw-s 00000000 00:09 1769497    /SYSV00000000 (deleted)
b58a7000-b58be000 r-xp 00000000 08:03 1540158    /lib/libselinux.so.1
b58be000-b58c0000 rw-p 00016000 08:03 1540158    /lib/libselinux.so.1
b58c0000-b591f000 r-xp 00000000 08:03 1461366    /usr/lib/libgio-2.0.so.0.0.0
b591f000-b5921000 rw-p 0005f000 08:03 1461366    /usr/lib/libgio-2.0.so.0.0.0
b5921000-b5a3b000 r-xp 00000000 08:03 1459142    /usr/lib/libxml2.so.2.6.31
b5a3b000-b5a40000 rw-p 00119000 08:03 1459142    /usr/lib/libxml2.so.2.6.31
b5a40000-b5a41000 rw-p b5a40000 00:00 0 
b5a41000-b5a73000 r-xp 00000000 08:03 1462443    /usr/lib/libcroco-0.6.so.3.0.1
b5a73000-b5a76000 rw-p 00031000 08:03 1462443    /usr/lib/libcroco-0.6.so.3.0.1
b5a76000-b5aa6000 r-xp 00000000 08:03 1462446    /usr/lib/libgsf-1.so.114.0.7
b5aa6000-b5aa9000 rw-p 0002f000 08:03 1462446    /usr/lib/libgsf-1.so.114.0.7
b5aa9000-b5aaa000 rw-p b5aa9000 00:00 0 
b5aaa000-b5b55000 r--p 00000000 08:03 1632553    /usr/share/icons/Tangerine/icon-theme.cache
b5b55000-b5be6000 r--p 00000000 08:03 1753511    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5c64000-b5c73000 r-xp 00000000 08:03 1540222    /lib/libbz2.so.1.0.4
b5c73000-b5c74000 rw-p 0000f000 08:03 1540222    /lib/libbz2.so.1.0.4
b5c74000-b5ca4000 r-xp 00000000 08:03 1462448    /usr/lib/librsvg-2.so.2.22.2
b5ca4000-b5ca5000 rw-p 00030000 08:03 1462448    /usr/lib/librsvg-2.so.2.22.2
b5cae000-b5cb2000 r-xp 00000000 08:03 1516367    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5cb2000-b5cb3000 rw-p 00003000 08:03 1516367    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5cb3000-b5cb4000 r-xp 00000000 08:03 1516470    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5cb4000-b5cb5000 rw-p 00000000 08:03 1516470    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5cb5000-b5cb7000 r-xp 00000000 08:03 1516323    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5cb7000-b5cb8000 rw-p 00001000 08:03 1516323    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5cb8000-b5cbf000 r--s 00000000 08:03 1458754    /usr/lib/gconv/gconv-modules.cache
b5cbf000-b5cc5000 r--s 00000000 08:03 1941555    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5cc5000-b5cc8000 r--s 00000000 08:03 1941572    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b5cc8000-b5cc9000 r--s 00000000 08:03 1941571    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b5cc9000-b5cca000 r--s 00000000 08:03 1941570    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5cca000-b5ccd000 r--s 00000000 08:03 1941569    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b5ccd000-b5cd0000 r--s 00000000 08:03 1941568    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5cd0000-b5cd3000 r--s 00000000 08:03 1941567    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5cd3000-b5cdb000 r--s 00000000 08:03 1941566    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5cdb000-b5ce3000 r--s 00000000 08:03 1941565    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5ce3000-b5ce6000 r--s 00000000 08:03 1941563    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b5ce6000-b5cf7000 r-xp 00000000 08:03 1519189    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b5cf7000-b5cf8000 rw-p 00011000 08:03 1519189    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b5cf8000-b5d01000 r-xp 00000000 08:03 1540129    /lib/tls/i686/cmov/libnss_files-2.7.so
b5d01000-b5d03000 rw-p 00008000 08:03 1540129    /lib/tls/i686/cmov/libnss_files-2.7.so
b5d03000-b5d0b000 r-xp 00000000 08:03 1540131  Aborted

```

Any idea's what the fix might be?

Gaunt

---

### Post by Shorland Hoa on 2008-11-27
I followed the instruction to install Ogre and other things,and everything was ok during installation.But when I tried to run the examples,some thing went wrong.
> hxl@hxl:~/ogre/Samples/Common/bin$ PRE_LOAD_PATH=/usr/local/lib ./BSP 
Creating resource group General
Creating resource group Internal
Creating resource group Autodetect
SceneManagerFactory for type 'DefaultSceneManager' registered.
Registering ResourceManager for type Material
Registering ResourceManager for type Mesh
Registering ResourceManager for type Skeleton
MovableObjectFactory for type 'ParticleSystem' registered.
OverlayElementFactory for type Panel registered.
OverlayElementFactory for type BorderPanel registered.
OverlayElementFactory for type TextArea registered.
Registering ResourceManager for type Font
ArchiveFactory for archive type FileSystem registered.
ArchiveFactory for archive type Zip registered.
FreeImage version: 3.9.3
This program uses FreeImage, a free, open source image library supporting all common bitmap formats. See [http://freeimage.sourceforge.net](http://freeimage.sourceforge.net) for details
Supported formats: bmp,ico,jpg,jif,jpeg,jpe,jng,koa,iff,lbm,mng,pbm,pbm,pcd,pcx,pgm,pgm,png,ppm,ppm,ras,tga,targa,tif,tiff,wap,wbmp,wbm,psd,cut,xbm,xpm,gif,hdr,g3,sgi
DDS codec registering
Registering ResourceManager for type HighLevelGpuProgram
Registering ResourceManager for type Compositor
MovableObjectFactory for type 'Entity' registered.
MovableObjectFactory for type 'Light' registered.
MovableObjectFactory for type 'BillboardSet' registered.
MovableObjectFactory for type 'ManualObject' registered.
MovableObjectFactory for type 'BillboardChain' registered.
MovableObjectFactory for type 'RibbonTrail' registered.
Loading library /usr/local/lib/OGRE/RenderSystem_GL.so
Installing plugin: GL RenderSystem
OpenGL Rendering Subsystem created.
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_ParticleFX.so
Installing plugin: ParticleFX
Particle Emitter Type 'Point' registered
Particle Emitter Type 'Box' registered
Particle Emitter Type 'Ellipsoid' registered
Particle Emitter Type 'Cylinder' registered
Particle Emitter Type 'Ring' registered
Particle Emitter Type 'HollowEllipsoid' registered
Particle Affector Type 'LinearForce' registered
Particle Affector Type 'ColourFader' registered
Particle Affector Type 'ColourFader2' registered
Particle Affector Type 'ColourImage' registered
Particle Affector Type 'ColourInterpolator' registered
Particle Affector Type 'Scaler' registered
Particle Affector Type 'Rotator' registered
Particle Affector Type 'DirectionRandomiser' registered
Particle Affector Type 'DeflectorPlane' registered
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_BSPSceneManager.so
Installing plugin: BSP Scene Manager
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_OctreeSceneManager.so
Installing plugin: Octree & Terrain Scene Manager
Plugin successfully installed
Loading library /usr/local/lib/OGRE/Plugin_CgProgramManager.so
Installing plugin: Cg Program Manager
Plugin successfully installed
*-*-* OGRE Initialising
*-*-* Version 1.6.0 (Shoggoth)
Creating resource group Bootstrap
Added resource location '../../Media/packs/OgreCore.zip' of type 'Zip' to resource group 'Bootstrap'
Added resource location '../../Media' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/fonts' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/materials/programs' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/materials/scripts' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/materials/textures' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/models' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/overlays' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/particle' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/gui' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/DeferredShadingMedia' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/PCZAppMedia' of type 'FileSystem' to resource group 'General'
Added resource location '../../Media/packs/cubemap.zip' of type 'Zip' to resource group 'General'
Added resource location '../../Media/packs/cubemapsJS.zip' of type 'Zip' to resource group 'General'
Added resource location '../../Media/packs/dragon.zip' of type 'Zip' to resource group 'General'
Added resource location '../../Media/packs/fresneldemo.zip' of type 'Zip' to resource group 'General'
Added resource location '../../Media/packs/ogretestmap.zip' of type 'Zip' to resource group 'General'
Added resource location '../../Media/packs/skybox.zip' of type 'Zip' to resource group 'General'
Added resource location '../../Media/packs/chiropteraDM.pk3' of type 'Zip' to resource group 'General' with recursive option
CPU Identifier & Features
-------------------------
 *   CPU ID: GenuineIntel: Intel(R) Celeron(R) CPU 2.13GHz
 *      SSE: yes
 *     SSE2: yes
 *     SSE3: yes
 *      MMX: yes
 *   MMXEXT: yes
 *    3DNOW: no
 * 3DNOWEXT: no
 *     CMOV: yes
 *      TSC: yes
 *      FPU: yes
 *      PRO: yes
 *       HT: yes
-------------------------
******************************
*** Starting GLX Subsystem ***
******************************
GLRenderSystem::_createRenderWindow "OGRE Render Window", 1024x768 fullscreen  miscParams: FSAA=0 displayFrequency=85 MHz gamma= vsync=No 
GLXWindow::create used FBConfigID = 37
GL_VERSION = 1.3 Mesa 7.0.3-rc2
GL_VENDOR = Tungsten Graphics, Inc
GL_RENDERER = Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_window_pos GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_equation_separate GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_cull_vertex GL_EXT_compiled_vertex_array GL_EXT_convolution GL_EXT_copy_texture GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_histogram GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_polygon_offset GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_stencil_wrap GL_EXT_subtexture GL_EXT_texture GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_3DFX_texture_compression_FXT1 GL_APPLE_client_storage GL_APPLE_packed_pixels GL_ATI_blend_equation_separate GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_INGR_blend_func_separate GL_MESA_pack_invert GL_MESA_ycbcr_texture GL_MESA_window_pos GL_NV_blend_square GL_NV_light_max_exponent GL_NV_texture_rectangle GL_NV_texgen_reflection GL_NV_vertex_program GL_NV_vertex_program1_1 GL_OES_read_format GL_SGI_color_matrix GL_SGI_color_table GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
Supported GLX extensions: GLX_ARB_get_proc_address GLX_ARB_multisample GLX_EXT_import_context GLX_EXT_visual_info GLX_EXT_visual_rating GLX_MESA_allocate_memory GLX_MESA_copy_sub_buffer GLX_MESA_swap_control GLX_MESA_swap_frame_usage GLX_OML_swap_method GLX_SGI_make_current_read GLX_SGI_swap_control GLX_SGI_video_sync GLX_SGIS_multisample GLX_SGIX_fbconfig GLX_SGIX_visual_select_group 
***************************
*** GL Renderer Started ***
***************************
Registering ResourceManager for type GpuProgram
GL: Using framebuffer copy for rendering to textures (worst)
GL: Warning: RenderTexture size is restricted to size of framebuffer. If you are on Linux, consider using GLX instead of SDL.
RenderSystem capabilities
-------------------------
RenderSystem Name: OpenGL Rendering Subsystem
GPU Vendor: unknown
Device Name: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
Driver Version: 1.3.0.0
 * Fixed function pipeline: yes
 * Hardware generation of mipmaps: yes
 * Texture blending: yes
 * Anisotropic texture filtering: yes
 * Dot product texture operation: yes
 * Cube mapping: yes
 * Hardware stencil buffer: yes
   - Stencil depth: 8
   - Two sided stencil support: no
   - Wrap stencil values: yes
 * Hardware vertex / index buffers: yes
 * Vertex programs: yes
 * Fragment programs: no
 * Geometry programs: no
 * Supported Shader Profiles: arbvp1
 * Texture Compression: yes
   - DXT: no
   - VTC: no
 * Scissor Rectangle: yes
 * Hardware Occlusion Query: no
 * User clip planes: yes
 * VET_UBYTE4 vertex element type: yes
 * Infinite far plane projection: yes
 * Hardware render-to-texture: no
 * Floating point textures: no
 * Non-power-of-two textures: no
 * Volume textures: yes
 * Multiple Render Targets: 1
   - With different bit depths: no
 * Point Sprites: no
 * Extended point parameters: yes
 * Max Point Size: 255
 * Vertex texture fetch: no
 * Render to Vertex Buffer : no
 * GL 1.5 without VBO workaround: no
 * Frame Buffer objects: no
 * Frame Buffer objects (ARB extension): no
 * Frame Buffer objects (ATI extension): no
 * PBuffer suppport: no
 * GL 1.5 without HW-occlusion workaround: no
Registering ResourceManager for type Texture
ResourceBackgroundQueue - threading disabled
Particle Renderer Type 'billboard' registered
SceneManagerFactory for type 'BspSceneManager' registered.
Registering ResourceManager for type BspLevel
SceneManagerFactory for type 'OctreeSceneManager' registered.
SceneManagerFactory for type 'TerrainSceneManager' registered.
Initialising resource group Bootstrap
Parsing scripts for resource group Bootstrap
Parsing script OgreCore.material
Parsing script OgreProfiler.material
Parsing script Ogre.fontdef
Parsing script OgreDebugPanel.overlay
Texture: New_Ogre_Border_Center.png: Loading 1 faces(PF_A8R8G8B8,256x128x1) with 5 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x128x1.
Texture: New_Ogre_Border.png: Loading 1 faces(PF_A8R8G8B8,256x256x1) with 5 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x256x1.
Texture: New_Ogre_Border_Break.png: Loading 1 faces(PF_A8R8G8B8,32x32x1) with 5 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,32x32x1.
Font BlueHighwayusing texture size 512x512
Info: Freetype returned null for character 127 in font BlueHighway
Info: Freetype returned null for character 128 in font BlueHighway
Info: Freetype returned null for character 129 in font BlueHighway
Info: Freetype returned null for character 130 in font BlueHighway
Info: Freetype returned null for character 131 in font BlueHighway
Info: Freetype returned null for character 132 in font BlueHighway
Info: Freetype returned null for character 133 in font BlueHighway
Info: Freetype returned null for character 134 in font BlueHighway
Info: Freetype returned null for character 135 in font BlueHighway
Info: Freetype returned null for character 136 in font BlueHighway
Info: Freetype returned null for character 137 in font BlueHighway
Info: Freetype returned null for character 138 in font BlueHighway
Info: Freetype returned null for character 139 in font BlueHighway
Info: Freetype returned null for character 140 in font BlueHighway
Info: Freetype returned null for character 141 in font BlueHighway
Info: Freetype returned null for character 142 in font BlueHighway
Info: Freetype returned null for character 143 in font BlueHighway
Info: Freetype returned null for character 144 in font BlueHighway
Info: Freetype returned null for character 145 in font BlueHighway
Info: Freetype returned null for character 146 in font BlueHighway
Info: Freetype returned null for character 147 in font BlueHighway
Info: Freetype returned null for character 148 in font BlueHighway
Info: Freetype returned null for character 149 in font BlueHighway
Info: Freetype returned null for character 150 in font BlueHighway
Info: Freetype returned null for character 151 in font BlueHighway
Info: Freetype returned null for character 152 in font BlueHighway
Info: Freetype returned null for character 153 in font BlueHighway
Info: Freetype returned null for character 154 in font BlueHighway
Info: Freetype returned null for character 155 in font BlueHighway
Info: Freetype returned null for character 156 in font BlueHighway
Info: Freetype returned null for character 157 in font BlueHighway
Info: Freetype returned null for character 158 in font BlueHighway
Info: Freetype returned null for character 159 in font BlueHighway
Info: Freetype returned null for character 160 in font BlueHighway
Texture: BlueHighwayTexture: Loading 1 faces(PF_BYTE_LA,512x512x1) with  hardware generated mipmaps from Image. Internal format is PF_BYTE_LA,512x512x1.
Texture: ogretext.png: Loading 1 faces(PF_A8R8G8B8,256x128x1) with 5 hardware generated mipmaps from Image. Internal format is PF_A8R8G8B8,256x128x1.
Parsing script OgreLoadingPanel.overlay
Finished parsing scripts for resource group Bootstrap
Parsing scripts for resource group Autodetect
Segmentation fault

Can someone give me suggestions?

---

### Post by zedx555 on 2008-12-16
You have an oooold Intel 845G chipset. As it is OGRE does not support intel chipsets. You can try Irrlicht or buy a new GPU.

---

### Post by lingnoi on 2009-01-22
> **mattgaunt said:**
> Heya

I'm having some serious problems installing Ogre on Hardy Heron, I keep on getting this output from the ogre Water example

Do you still get the error? I haven't got this error on the water demo in Hardy.

---

### Post by vichor on 2009-07-18
Hi,

Thanks for your good tutorial.

Even that you now provide a package for Jaunty, I want to compile Ogre myself. Just learning a bit ;). I have a problem though...

When I try to install libxaw6 I get an unknown package error. On the ohter hand, my package manager finds a nice libxaw7 package which seems to install properly... I suppose they are the same (but for the version number).

Regards
Victor

---

