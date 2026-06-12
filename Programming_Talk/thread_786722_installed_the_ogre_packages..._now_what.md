---
title: "installed the ogre packages... now what?"
date: 2008-05-08
forum: Programming Talk
---

### Post by Choad on 2008-05-08
to clarify, c++ isn't my strong point. i am just trying to get to the point where i can compile an example app.

bla.cpp
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
        MessageBox( NULL, e.what(), "An exception has occurred!", MB_OK | MB_ICONERROR | MB_TASKMODAL);
#else
        fprintf(stderr, "An exception has occurred: %s\n",
                e.what());
#endif
    }

    return 0;
}
```

makefile
```
DEFINES =
LIBS = OGRE
CXX = g++
CXXFLAGS = $(shell pkg-config --cflags $(LIBS)) $(DEFINES)
LD = g++
LDFLAGS = $(shell pkg-config --libs $(LIBS))

all:
	$(CXX) $(CXXFLAGS) $(LDFLAGS) -o bla bla.cpp

clean:
	rm -f bla

```

terminal output
```

make
g++ -DOGRE_GUI_GLX -DOGRE_CONFIG_LITTLE_ENDIAN -I/usr/include/OGRE    -lOgreMain   -o bla bla.cpp
bla.cpp:1:32: error: ExampleApplication.h: No such file or directory
bla.cpp:22:21: error: windows.h: No such file or directory
bla.cpp:4: error: expected class-name before &#8216;{&#8217; token
bla.cpp:24: error: &#8216;INT&#8217; does not name a type
make: *** [all] Error 1

```

any help? gotta set up some environment variables? does the packaged ogre not come with this file?

---

### Post by Zugzwang on 2008-05-08
It appears as if you forgot to copy the "ExampleApplication.h" header file from your tutorial (into the same directory as your code file).

Hint: Always look at the *first* error the compiler produces. The rest might be caused by the first one, so fix it first. In this case, it is:
```

bla.cpp:1:32: error: ExampleApplication.h: No such file or directory

```

---

### Post by Choad on 2008-05-08
i'm pretty sure that stuff is part of ogre tho. well anyway...

ok so i downloaded the source to get a copy of exampleApplication.h 

stuck it in and then...

```
richard@richard-laptop:~/Desktop/ogre$ make
g++ -DOGRE_GUI_GLX -DOGRE_CONFIG_LITTLE_ENDIAN -I/usr/include/OGRE    -lOgreMain   -o bla bla.cpp
In file included from ExampleApplication.h:26,
                 from bla.cpp:1:
ExampleFrameListener.h:45:21: error: OIS/OIS.h: No such file or directory
In file included from ExampleApplication.h:26,
                 from bla.cpp:1:
ExampleFrameListener.h:386: error: &#8216;OIS&#8217; has not been declared
ExampleFrameListener.h:386: error: ISO C++ forbids declaration of &#8216;InputManager&#8217; with no type
ExampleFrameListener.h:386: error: expected &#8216;;&#8217; before &#8216;*&#8217; token

<snip>

ExampleFrameListener.h:388: error: &#8216;OIS&#8217; has not been declared
ExampleFrameListener.h:388: error: ISO C++ forbids declaration of &#8216;Keyboard&#8217; with no 
ExampleFrameListener.h:323: error: &#8216;mJoy&#8217; was not declared in this scope
make: *** [all] Error 1
richard@richard-laptop:~/Desktop/ogre$ 
```

??

i'm guessing i now need ois/ois.h

i have simply never been able to get my head around c++ development. :(

with python, you type import <module> and it works. do the same in c++ and you spend the next week trying to figure out what the hell is going wrong! (i do want to learn tho)

---

### Post by Choad on 2008-05-08
well ok i got bored of trying to find out wtf OIS is called in synaptic so i just compiled it from source.

now i get a slightly different error but it's still talking about OIS

```
richard@richard-laptop:~/Desktop/ogre$ make
g++ -DOGRE_GUI_GLX -DOGRE_CONFIG_LITTLE_ENDIAN -I/usr/include/OGRE    -lOgreMain   -o bla bla.cpp
/tmp/ccAQR8Ai.o: In function `ExampleFrameListener::windowClosed(Ogre::RenderWindow*)':
bla.cpp:(.text._ZN20ExampleFrameListener12windowClosedEPN4Ogre12RenderWindowE[ExampleFrameListener::windowClosed(Ogre::RenderWindow*)]+0x39): undefined reference to `OIS::InputManager::destroyInputObject(OIS::Object*)'
bla.cpp:(.text._ZN20ExampleFrameListener12windowClosedEPN4Ogre12RenderWindowE[ExampleFrameListener::windowClosed(Ogre::RenderWindow*)]+0x53): undefined reference to `OIS::InputManager::destroyInputObject(OIS::Object*)'
bla.cpp:(.text._ZN20ExampleFrameListener12windowClosedEPN4Ogre12RenderWindowE[ExampleFrameListener::windowClosed(Ogre::RenderWindow*)]+0x6d): undefined reference to `OIS::InputManager::destroyInputObject(OIS::Object*)'
bla.cpp:(.text._ZN20ExampleFrameListener12windowClosedEPN4Ogre12RenderWindowE[ExampleFrameListener::windowClosed(Ogre::RenderWindow*)]+0x7b): undefined reference to `OIS::InputManager::destroyInputSystem(OIS::InputManager*)'
/tmp/ccAQR8Ai.o: In function `ExampleFrameListener::ExampleFrameListener(Ogre::RenderWindow*, Ogre::Camera*, bool, bool, bool)':
bla.cpp:(.text._ZN20ExampleFrameListenerC1EPN4Ogre12RenderWindowEPNS0_6CameraEbbb[ExampleFrameListener::ExampleFrameListener(Ogre::RenderWindow*, Ogre::Camera*, bool, bool, bool)]+0x4f3): undefined reference to `OIS::InputManager::createInputSystem(std::multimap<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::less<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::allocator<std::pair<std::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >&)'
bla.cpp:(.text._ZN20ExampleFrameListenerC1EPN4Ogre12RenderWindowEPNS0_6CameraEbbb[ExampleFrameListener::ExampleFrameListener(Ogre::RenderWindow*, Ogre::Camera*, bool, bool, bool)]+0x548): undefined reference to `OIS::InputManager::createInputObject(OIS::Type, bool, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
bla.cpp:(.text._ZN20ExampleFrameListenerC1EPN4Ogre12RenderWindowEPNS0_6CameraEbbb[ExampleFrameListener::ExampleFrameListener(Ogre::RenderWindow*, Ogre::Camera*, bool, bool, bool)]+0x5f8): undefined reference to `OIS::InputManager::createInputObject(OIS::Type, bool, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
bla.cpp:(.text._ZN20ExampleFrameListenerC1EPN4Ogre12RenderWindowEPNS0_6CameraEbbb[ExampleFrameListener::ExampleFrameListener(Ogre::RenderWindow*, Ogre::Camera*, bool, bool, bool)]+0x6a8): undefined reference to `OIS::InputManager::createInputObject(OIS::Type, bool, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
collect2: ld returned 1 exit status
make: *** [all] Error 1
richard@richard-laptop:~/Desktop/ogre$ 
```

---

