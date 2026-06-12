---
title: "SDL and openGL, same code / program, occasionally refuses to draw anything"
date: 2010-03-11
forum: Programming Talk
---

### Post by weematt on 2010-03-11
Hello Everyone,

Thanks in advance for reading this and any help you may be able to provide.

I have been programming scientific simulations for the past few years using a combination of C++, SDL, and openGL (plus a few other libraries).  Everything works great for the most part, but I have an itermittent bug which I can't figure out...

Sometimes, on a given execution, the program does not draw anything to the window it creates, leaving it blank.  The exact same code will often work, but sometimes not work.  When it doesn't draw anything, I rerun it again and again and eventually it works again.  No error messages are reported.

It seems to me like I'm not initializing something correctly, or that there is some race condition that is messing things up at init.  Any thoughts of what I might try?

Below is the code I use to init SDL.  You'll see at the end, I draw a yellow line from one corner of the screen to another.  This (and all subsequent openGL drawing) sometimes doesn't draw.

Thanks again!

Matthew

Linux kernel: 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
nVidia driver#185.18.36
GPU:Quadro NVS 285 (GPU 0)


```

  void init2DSDL(double left, double right, double bottom, double top) {
  ////////////// INIT SDL
  cout <<"------------------------------------" << endl;
  cout <<"Initializing SDL...";
  if ( SDL_Init ( SDL_INIT_EVERYTHING ) < 0 ) {
    cout <<"Could not initialize SDL:" << SDL_GetError() << endl;
    SDL_Quit();
  }
  else {
    cout << "DONE." <<endl;
  }
  
  SDL_GL_SetAttribute ( SDL_GL_DOUBLEBUFFER, 1);
  SDL_GL_SetAttribute ( SDL_GL_DEPTH_SIZE, 16 );
  SDL_GL_SetAttribute ( SDL_GL_RED_SIZE, 8 );
  SDL_GL_SetAttribute ( SDL_GL_GREEN_SIZE, 8 );
  SDL_GL_SetAttribute ( SDL_GL_BLUE_SIZE, 8 );
  SDL_GL_SetAttribute ( SDL_GL_ALPHA_SIZE, 8 );
  
  SDL_Surface* drawContext;
  Uint32 flags;
  flags = SDL_OPENGL;// | SDL_FULLSCREEN;
  
  int width = WINDOW_WIDTH;
  int height = width/2;
  

  drawContext = SDL_SetVideoMode ( width, height, 0, flags );
  glViewport( 0, 0, width, height); 
  glEnable(GL_BLEND);
  glBlendFunc (GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);

  glEnable( GL_TEXTURE_2D );
  glClearColor( 0.0f, 0.0f, 0.0f, 1.0f );   
  
  glClear( GL_COLOR_BUFFER_BIT );  
  
  glMatrixMode( GL_PROJECTION );
  glLoadIdentity();
  glOrtho(left, right, bottom, top, -1.0f, 1.0f);
  
  glMatrixMode( GL_MODELVIEW );
  glLoadIdentity(); 

  SDL_GL_SwapBuffers(); 

  glColor4d(1,1,0,1);
  glBegin(GL_LINES);
  glVertex2d(left,top);
  glVertex2d(right,bottom);
  glEnd();
  
}  


```

---

### Post by Zugzwang on 2010-03-11
Does it always work if you switched off your desktop effects beforehand? If yes, it's probably not your fault, but a problem with compiz.

---

### Post by weematt on 2010-03-11
> **Zugzwang said:**
> Does it always work if you switched off your desktop effects beforehand? If yes, it's probably not your fault, but a problem with compiz.
Unfortunately, you seem to be right.  I disabled compiz effects, and no sign of the bug.  Too bad, I like compiz.  I wonder if the compiz developers are aware of this bug.

Thanks for your help!

Matt

---

