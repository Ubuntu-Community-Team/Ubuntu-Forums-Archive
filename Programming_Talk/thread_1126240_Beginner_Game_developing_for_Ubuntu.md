---
title: "Beginner Game developing for Ubuntu"
date: 2009-04-15
forum: Programming Talk
---

### Post by bunyk on 2009-04-15
I migrate to Ubuntu two weeks ago. I am interested in game programming, and graphics. First I used Eclipse, because I hear that is Visual Studio analog for linux, but it was not wery good for C++ and OpenGL. 

Then I use Code::Blocks. Much better IDE. It even have wizards for creating GLUT applications. I created a Rubics Cubic model ([code and screenshot here (ukrainian language!)]("http://bunyk.wordpress.com/2009/04/12/cubik/"). 

But it is very hard to render text using OpenGL, so I decide to find some graphic engine libraries. I download Ogre, but have problems with [compiling ogre tutorials]("http://ubuntuforums.org/showthread.php?t=584907").

Anybody can recommend me some IDE and libraries? Which is best, for game programming, which is simplest to learn? May I learn Python, or C++ is enought?

---

### Post by Neheb on 2009-04-15
Hi, I am in pretty much the same situation as you are, coming from windows/visual studio and currently learning OpenGL.

I tried using code::blocks and KDevelop, but I just didnt like either of them and I have now sort of learnt to use emacs and makefiles.

As for library's I am using SDL, as GLUT is outdated and just a pain to use and because SDL got other game stuff like sound easily implemented. I also think you can use the 2D SDL technique to show text on the screen, but it's probably not the best way.

If you don't want to use SDL I would suggest trying out freeglut instead of glut as it is maintained and have fixed some of the bad stuff in glut.

---

### Post by bunyk on 2009-04-15
Thanks. I will try to use SDL. I am using GLUT because I help girls from my group write homeworks :) , and our teachers teach OpenGL using GLUT.

---

### Post by quaternion on 2009-04-15
I find Java easier to use that C++... Most people do.  If you spend a little time you can figure out how to use JOGL to use OpenGL with Java.  My preferred Editor is Netbeans (made by Sun, and free off their web site).

One of the benefits... although not really easy but easy enough is GUI development with Netbeans(or Eclipse if you prefer).  You can make a frame to contain the OpenGL View and you can interact with GUI controls around the side...  Since you can work in a windowed environment you can cover the OpenGL windows with a text area and output text... or place a text area on the side...

As far as performance goes JOGL is a wrapper to OpenGL, it provides ALL functionality, performance is only slightly slower.  Further your code can be made to execute within a browser as a Java Applet without too much effort.

---

### Post by Neheb on 2009-04-15
The problem with using java instead of c++ for opengl is that most games, especially in the industry, is made using c++. Also, if you are learning opengl at school, I would guess they are teaching it using c++.

But yes, if you just want to use opengl to make games, java is a valid option.

---

### Post by tneva82 on 2009-04-16
> **bunyk said:**
> But it is very hard to render text using OpenGL,

[FTGL]("http://ftgl.wiki.sourceforge.net/") is pretty nice text printing library for openGL. Free&crossplatform. Seems to have tons of features but got basic printing working pretty fast. And you can use your standard font files :) Excelent. Many others I tried required you to have BMP with all the letters there. Too much work for me to create suitable BMP file! I rather just point to existing .ttf file ;-)

Here's simple wrapper I made for printing feature using singleton template to make sure there's only one FTGLPixMapFont used and giving uniform access to it.

print.h

```

#ifndef PRINT_H
#define PRINT_H

#include <FTGL/ftgl.h>
#include <vector>

using namespace std;

class print {
private:

  print(int foo) {  }
  vector<FTGLPixmapFont*> fontList;
public:
  ~print();
  bool addFont(const char *fontFile);
  static print* getInstance();
  void printText(float x, float y, char *string, int font, int size);

  void clearFonts();
};

#endif

```

print.cpp

```

#include "./headers/global.h"
#include "./headers/print.h"

extern "C" {
#include <FTGL/ftgl.h>
}

#include <GL/gl.h>
#include <GL/glu.h>
#include "SDL/SDL.h"
#include <vector>

void print::printText(float x, float y, char *string, int font, int size) {
  glRasterPos2f(x, y);
  fontList[font]->FaceSize(size);
  fontList[font]->Render(string);
}

print::~print() {

 
}

bool print::addFont(const char *fontFile) {
  print::fontList.push_back(new FTGLPixmapFont(fontFile));
  if(print::fontList.back()->Error()) {
    print::fontList.pop_back();
    return false;
  }
  return true;
}
  
print* print::getInstance() {

    static print instance(1);

  return &instance;
}

void print::clearFonts() {
  for(vector<FTGLPixmapFont*>::iterator it=print::fontList.begin();it!=print::fontList.end();it++) {
    if((*it)!=NULL) {
      delete (*it);
    }
  }
  fontList.clear();
}

```

You have to make sure screen is set up for 2d drawing rather than 3d. But then somewhere before printing you do something like this:

```

  if(!print::getInstance()->addFont("./font/verdana.ttf")) {
    printf("Font loading failed!\n");
    exit(1);
  }

```

For any font you wish to use(obviously changing path to one you like :D). Printing then goes:

```
  print::getInstance()->printText(x, y, textLine, 0, 12);
```

(I suppose it would be better to use definitions to identify fonts but since I only use one I haven't seen need to do that).

Finally clear the fonts.

As can be seen FTGL doesn't take that much work. Only reason I created whole print class is to avoid having to pass FTGL class around or creating new FTGL for every class that wishes to print.

Spent long time trying to find suitable text printing library. FTGL filled that perfectly. Maybe it does for you as well?

---

### Post by jacensolo on 2009-04-16
I find [Irrlicht]("http://irrlicht.sourceforge.net/") very easy to use and interact with other modules like physics engines.

---

