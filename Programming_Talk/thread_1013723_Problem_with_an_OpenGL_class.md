---
title: "Problem with an OpenGL class"
date: 2008-12-17
forum: Programming Talk
---

### Post by jyaan on 2008-12-17
I put together a few files which are (hopefully) going to become an OpenGL framework (with SDL) I can base future study on. The problem is... I can't get anything to draw. When I wrote in plain C everything was fine, and the other pieces I've tested so far seem to be okay as well. I modified it (eventually replacing basically _all_ my code) to fit the NeHe tutorial #2, but even after doing this I still have not found the problem. The "rendering" header file (just draws the two shapes) worked fine when substituted into the original NeHe Linux/SDL code. I will attach the whole project. Anyways, here is the implementation file window.cpp for the class...

[PHP]#include <iostream>
#include "window.h"
using namespace std;

// Public
Window::Window(GLint screenHeight, GLint screenWidth, GLint screenBpp) {
	height = screenHeight;
	width = screenWidth;
	bpp = screenBpp;
	fullscreen = 0;
	
	// Attempt to init the SDL Video subsystem. Return error on fail.
	// FIXME Other subsystems need addition when sound, input, etc are added to engine !!
	if (SDL_Init(SDL_INIT_VIDEO) < 0 ) {
		cout << "Unable to init SDL: " << SDL_GetError() << endl;
		SDL_Quit();
	} else cout << "SDL_Init passed.\n";
	
	videoSettings();

	SDL_GL_SetAttribute(SDL_GL_DOUBLEBUFFER, 1);

	if (fullscreen)
		screen = SDL_SetVideoMode(height, width, bpp, videoFlags | SDL_FULLSCREEN); 
	else
		screen = SDL_SetVideoMode(height, width, bpp, videoFlags);
	
	if (!screen) {
		cout << "Failed to set video mode." << SDL_GetError() << endl;
		SDL_Quit();
	}

	if (initGL()) {
		cout << "initGL() failed." << SDL_GetError();
		SDL_Quit();
	} else {
		cout << "initGL() has returned sucessfully." << endl;
	}
}

Window::~Window() {
	SDL_Quit();
}

GLboolean Window::resizeWindow(GLint w, GLint h) {
	width = w;
	height = h;
	
	GLfloat ratio;
	if (height == 0)
		height = 1;
	ratio = (GLfloat) width / (GLfloat)height;
	
	glViewport(0, 0, (GLsizei)height, (GLsizei)width);
	glMatrixMode(GL_PROJECTION);
	glLoadIdentity();
	gluPerspective(45.0f, ratio, 0.1f, 100.0f);
	//glOrtho(0.0f, height, width, 0.0f, -1.0f, 1.0f);
	glMatrixMode(GL_MODELVIEW);
	glLoadIdentity();
	return true;
}

GLvoid Window::toggleFullscreen() {
	SDL_WM_ToggleFullScreen(screen);
}

GLint Window::getHeight() {
	return height;
}

GLint Window::getWidth() {
	return width;
}

// Private
GLint Window::initGL() {
	glShadeModel(GL_SMOOTH);
	glClearColor(0.0f, 0.0f, 0.0f, 0.0f);
	glClearDepth(1.0f);
	glEnable(GL_DEPTH_TEST);
	glDepthFunc(GL_LEQUAL);
	glHint(GL_PERSPECTIVE_CORRECTION_HINT, GL_NICEST);
	return 0;
}

GLvoid Window::videoSettings() {
	videoFlags = SDL_OPENGL; //| SDL_GL_DOUBLEBUFFER | SDL_HWPALETTE | SDL_RESIZABLE;
	// Get info about video card and set accordingly
	const SDL_VideoInfo *videoInfo;
	videoInfo = SDL_GetVideoInfo();
	if (!videoInfo) {
		cout << "Failed to get video information" << SDL_GetError() << endl;
		SDL_Quit();
	}
	if (videoInfo->hw_available) {
		videoFlags |= SDL_HWSURFACE;
		cout << "Using hardware mode" << endl;
	} else {
		videoFlags |= SDL_SWSURFACE;
		cout << "Using software mode" << endl;
	}
	if (videoInfo->blit_hw) {
		videoFlags |= SDL_HWACCEL;
		cout << "Using hardware acceleration" << endl;
	} else {
		cout << "No hardware acceleration!!!" << endl;
	}
}[/PHP]

In the meantime I will be writing a bare-bones version of the class (probably what I should have done in the first place :S I went to far without testing =/) to try and address the issue. Hopefully there are some people skilled in OpenGL / SDL out there!

---

### Post by jyaan on 2008-12-17
I think I found another more up-to-date framework already made here that seems to do what I wanted : [http://nehe.gamedev.net/wiki/NewLesson1.ashx](http://nehe.gamedev.net/wiki/NewLesson1.ashx)

Hopefully this will solve my problems :)

Edit: Ok, it is sort of working now. His Linux version does not compile, but I downloaded the Windows version and simply changed the libraries it links to, and it works. (:S) Still, if anyone could figure out what I did wrong before I would appreciate it. I'm new to a lot of things in C++ (I use mainly Python and C) and don't have 100% grasp on the features yet.

---

### Post by Kazade on 2008-12-17
Yeh please don't use the old lessons... I really need to put a big "DON'T USE THIS" banner on those pages. They are really outdated now.

There will be more "New" lessons coming in the near future, me and the other maintainer of NeHe are currently working on a book on OpenGL 3.0 which should be finished in January. Then we should have more time for NeHe.

---

### Post by jyaan on 2008-12-17
Yea that might not be a bad idea..

If you need any help with anything on the project I'll be glad to contribute. You should also add a README (or a note on the Linux page) indicating that the Makefile was for cmake. I have only used the "normal" makefiles/autoconf and didn't realize what to do with it at first. People with less cli experience probably won't do so well.

---

### Post by jyaan on 2008-12-18
I figured it all out. The viewport / glTranslatef code values were off and I was simply drawing out of viewing area. :lolflag:

Glad I figured this one out; Also glad it wasn't the class.. lol. I just couldn't see what was wrong no matter where I looked, and turned out it was just a single value (Z). My C code had a different viewport settings, which is why it was fine. Of course I didn't notice that until now... :S

---

