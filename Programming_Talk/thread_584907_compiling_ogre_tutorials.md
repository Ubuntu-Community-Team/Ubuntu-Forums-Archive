---
title: "compiling ogre tutorials"
date: 2007-10-21
forum: Programming Talk
---

### Post by Choad on 2007-10-21
i have installed the ogre dev packages from the repos, and i would like to start programming some ogre apps in c++. i was going down the python-ogre route but i decided i may as well do c++ instead, as python-ogre support on linux is lacking, and c++ will be more efficient anyway.

sooo...

```
#include "ExampleApplication.h"

class TutorialApplication : public ExampleApplication
{
protected:
public:
    TutorialApplication()
    {
    }

    ~TutorialApplication() 
    {
    }
protected:
    void createScene(void)
    {
    }
};

#if OGRE_PLATFORM == OGRE_PLATFORM_WIN32
#define WIN32_LEAN_AND_MEAN
#include "windows.h"

INT WINAPI WinMain( HINSTANCE hInst, HINSTANCE, LPSTR strCmdLine, INT )
#else
int main(int argc, char **argv)
#endif
{
    // Create application object
    TutorialApplication app;

    try {
        app.go();
    } catch( Exception& e ) {
#if OGRE_PLATFORM == OGRE_PLATFORM_WIN32 
        MessageBox( NULL, e.getFullDescription().c_str(), "An exception has occurred!", MB_OK | MB_ICONERROR | MB_TASKMODAL);
#else
        fprintf(stderr, "An exception has occurred: %s\n",
                e.getFullDescription().c_str());
#endif
    }

    return 0;
}

```

```
richard@richard-laptop:~/Desktop$ gcc ogre.cpp 
ogre.cpp:1:32: error: ExampleApplication.h: No such file or directory
ogre.cpp:22:21: error: windows.h: No such file or directory
ogre.cpp:4: error: expected class-name before ‘{’ token
ogre.cpp:24: error: ‘INT’ does not name a type

```

obviously it can't find exampleApplication.h and the windows stuff, well i am not sure about that... i thought ogre was cross platform.

```

richard@richard-laptop:~/Desktop$ locate ExampleApplication
/home/richard/src/ogrenew/Samples/Common/include/ExampleApplication.h
richard@richard-laptop:~/Desktop$ 

```

that is from when i was trying to compile it from source ages ago... i assume from this that the ubuntu ogre packages don't include the tutorial frameworks...

any hints?

---

### Post by hecato on 2007-10-21
Those exampleApplication.h are inside the source files, dont remember exactly wher, but you should seek in some like Examples/Common

Also I recommend [http://www.ogre3d.org/phpBB2/viewtopic.php?p=232681#232681](http://www.ogre3d.org/phpBB2/viewtopic.php?p=232681#232681)  Im tyoc there, thought I havent been in ogre3d from sometime now, my personal opinion about that way of install it that 1 suguested there is very prety, nice and cute (from my point of view, because you can hav more than 1 ogre version installed in that way and switc one or other... but I have never tryied that lol:guitar:)


Only a side note?? perhaps this also can be from help?[LIST]
[*]A follof up of the anterior way to install it (possible failures when you dont get it) [http://www.ogre3d.org/phpBB2/viewtopic.php?t=33673](http://www.ogre3d.org/phpBB2/viewtopic.php?t=33673)
[*]is it installed? [http://www.ogre3d.org/phpBB2/viewtopic.php?p=233600#233600](http://www.ogre3d.org/phpBB2/viewtopic.php?p=233600#233600)[/LIST]

---

### Post by hecato on 2007-10-21
A yea, havent seen the last part of your post, only watch the first part lol.

Yea, when you do in source distribution make install, it will not "copy" the files needed for demos only the essential files for OGRE3D in fact, ExampleApplication.h Example...h and Example...h (there are 3 of them IIRC are only a "basic framework" that "hide" internal things of ogre like the listeners for frames and things like that, the overlay that shows the ogre logo and FPS info, etc...) they are in a folder inside the source distribution, you need to copy them, where you are compiling the code also because #include "some.h" first search the folder of the file that is compiling in the moment... or the other way, add the path of this files (if you dont want to copy and copy them again and again where you can search for *.h files.

That was long explanation for say only that yes, they are not packaged in the "dev" because if you install like I suguest is a good way in the anterior post, you will see that this problem also raise, because install doesn't use, copy examples. With the suguested way, you will be able to compile the examples.

--------------

Only for be more clear, when you do configure and not dissable demos, they will be build when you do make (it also works like a test suit in some way, they are build IIRC in Examples/Common/bin or some like that), but they will not be copied (to the install location) even that they are build and there when you do make install (that is why they arent included in "dev" package of the distributions, they only include "direct things" of ogre and not samples and helpers like Examplexxxx.h 3 o them IIRC).

---

### Post by bunyk on 2009-04-15
I am using Code::Blocks 8.02, and it's wizard creates project that can't be build.

> **hecato said:**
> That was long explanation for say only that yes, they are not packaged in the "dev" because if you install like I suguest is a good way in the anterior post, you will see that this problem also raise, because install doesn't use, copy examples.

So, solution is to download sources, and copy some files into some directories? I not know all system paths yet :(.

---

