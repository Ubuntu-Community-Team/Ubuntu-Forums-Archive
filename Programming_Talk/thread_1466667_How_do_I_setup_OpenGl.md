---
title: "How do I setup OpenGl?"
date: 2010-04-30
forum: Programming Talk
---

### Post by Axilus on 2010-04-30
Hey there,

Recently I have switched over to Linux and have been finding better opensource alternatives to what I used to use on windows, however...

I was recommended to use the Netbeans IDE (I was previously on Visual Studio 2008 ). I used to do a little game programming on DirectX, but now I want to start learning OpenGl.

Does anyone know how to get OpenGl setup with Netbeans? All I could find was how to setup JOGL, but I'm more of a C/C++ programer.

Or any other recommendations for getting started would be nice.

---

### Post by TheBuzzSaw on 2010-04-30
I recommend learning SDL.

---

### Post by phrostbyte on 2010-04-30
I second SDL, but if you are going to do C++ development maybe look into an OO scene graph? I heard Ogre3D is pretty good.

---

### Post by slavik on 2010-04-30
install mesagl, done.

---

### Post by Axilus on 2010-04-30
I'm more into developing 2D games however I have yet to find a tutorial on how to get started developing (good) 2D games in Linux.

I'm not too concerned about the 3D aspects of game development. I just want a easy to setup way of programming good quality games.

---

### Post by phrostbyte on 2010-04-30
SDL is a typical 2D game engine if you are using C/C++

pygame is good with Python

Allegro is another 2D game engine

There are probably many more. Hell you can just draw to a Cairo surface if you like.

---

### Post by Axilus on 2010-04-30
I've been searching around and there doesn't seem to be much support for netbeans for my goals. I'm going to set up SDL with eclispe and see how that works out.

---

### Post by Axilus on 2010-05-02
I got SDL up and running in Netbeans. Eclispe gave me a whole load of trouble, however Netbeans only presented difficulties when trying to figure out how to link to the SDL libraries.

If anyone else who reads this thread would like to setup SDL in Netbeans just send me a message (because there aren't any tutorials for it for some reason... trust me, I've looked.)

---

### Post by weaponx69 on 2010-05-12
Hi,
   I would like to know how to setup Netbeans for SDL if you still do that.

---

### Post by Axilus on 2010-05-12
> **weaponx69 said:**
> Hi,
   I would like to know how to setup Netbeans for SDL if you still do that.

I will try my best to explain my setup process. If you need me to make a complete tutorial (with screenshots) then I can make a new post, but for now I'll just explain it best I can.


[SIZE="2"][COLOR="RoyalBlue"]STEP ONE:[/COLOR][/SIZE]

Firstly I am assuming you have installed Netbeans 6.8 from the Ubuntu repositories. It would also be a good idea to install the 'build-essentials' package by opening up a terminal and pasting the following:

```
gksudo aptitude install build-essential
```

Before you can get programing with SDL you first need to get the C/C++ development plugin (By opening up the Netbeans IDE then 'Tools -> Plugins' and search for and install the C/C++ plugin).

If successful they should ask you to restart the IDE and just click yes.


[SIZE="2"][COLOR="RoyalBlue"]Step Two:[/COLOR][/SIZE]

Next, you must of course install the SDL Development package. You can install this via synaptic package manager and searching for "libsdl1.2-dev" (excluding the quotes) or by using the following code in the terminal:

```
sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev
```


[SIZE="2"][COLOR="RoyalBlue"]Step Three:[/COLOR][/SIZE]

Don't worry all that terminal stuff is all over and done with (at least until you try installing your next program :P ). So now lets move on to actualing linking SDL into your project.

Firstly you must create new a C++ project in Netbeans. I would advise you to just use [[COLOR="DeepSkyBlue"]this visual guide[/COLOR]]("http://verend.com/sdlonubuntu.php") for this part, however I will still explain the process.

Firstly right click on the project and go into the 'Properties -> Build -> C++ compiler'.

Select 'All configurations' in the Configuration drop down menu. Then click the box at the far right of the 'Include Directories'. Select 'Add' and then add the directory:
```
/usr/include/SDL
```

Click 'Ok' and then proceed to the 'Linker' options, and select 'All configurations' again. This time click the box at the far right of  Libraries, and click 'Add Library'. Now you have to navigate to the SDL library called:

```
/usr/lib/libSDL.a
```

Add that library and you should be good to go.

N.B. I had problems with the project compiling (it would compile sometimes, and refuse to compile the same code for no reason at all). Just go to the properties again, then to profile and uncheck the box that says, "Show profile indicators during run."


[SIZE="2"][COLOR="RoyalBlue"]Step Four:[/COLOR][/SIZE]

Now comes the moment of truth...

Paste this code into your main.cpp file and if it runs correctly without errors then pat yourself on the back my friend. If not... welcome to the life of an average programmer (also just tell me whats up and I will see if I can figure it out). Here's the code:

```
#include "SDL/SDL.h"

int main( int argc, char* args[] )
{
    //Start SDL
    SDL_Init( SDL_INIT_EVERYTHING );

    //Quit SDL
    SDL_Quit();

    return 0;
}
```

Good Luck with the wonderful world of SDL/OpenGl programming :D

Here is a good site for learning the basics:
[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

---

