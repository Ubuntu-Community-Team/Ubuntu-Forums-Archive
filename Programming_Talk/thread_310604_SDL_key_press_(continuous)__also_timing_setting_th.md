---
title: "SDL key press (continuous) ?? also timing/ setting the frame rate"
date: 2006-12-01
forum: Programming Talk
---

### Post by Choad on 2006-12-01
is there an event for the key being down (as opposed to the key just being pressed, which only ticks 1 time)

or should i set up a boolean variable that turns on/off on key down/up and work it like that?

also, how do i set the frame rate with sdl? i think someone told me before but i didnt use it and cant find it

need to set it to 40 fps or whatever

cheers

---

### Post by Mickeysofine1972 on 2006-12-01
Hi Choad

The problem lies in the use of two while loops in your input loop.

ditch while(SDL_PollEvent(&event)) bit like this:

```

while(done != true)	{// new input processing loop based on the input 
		SDL_PollEvent(&event);
                .. then process the rest of the events

```

just put one while loop in and follow it with a switch or set of ifs to process the events.

This will give continuous input as you wanted and not event based polling.

Also on the frame rate thing you can use FPSmanager which is part of the SDL_gfx library. however, you will need to install this package through your package manager before you using it.

```

const int FPS = 100;

int main(void)

{

   SDL_Event event;

   bool done = false;

   FPSmanager fps_manager;

   

   init();  // Initialize everything	



   // Make sure you set the fps_manager after initializing SDL

   SDL_initFramerate( &fps_manager );

   // Set the FramesPerSecond

   SDL_setFramerate( &fps_manager, FPS );   



   // This is the main loop, and it will run until not done :)

   while (!done) { // While not done

      //Draw the scene

      drawScene();  	

      // And poll for events

      SDL_PollEvent(&event);
	 switch (event.type) {

	    case SDL_VIDEORESIZE:

	       /* handle resize event */

     	       screen = SDL_SetVideoMode( event.resize.w, event.resize.h, 16, videoFlags );

	       if ( !screen ){

	          printf("Could not get a surface after resize: %s\n", SDL_GetError( ) );

		  exit( 1 );

	       }

	       resizeWindow( event.resize.w, event.resize.h );

	       break;

            case SDL_KEYDOWN:

		switch(event.key.keysym.sym){ // handle key presses

		   case SDLK_UP:

	             xStep -= 0.1f;

	             break;

	           case SDLK_DOWN:

	             xStep += 0.1f;

	             break;

	           case SDLK_RIGHT:

	             yStep += 0.1f;

	             break;

	           case SDLK_LEFT:

	             yStep -= 0.1f;

	             break;

 	           case SDLK_ESCAPE:

                   case SDLK_q:

 		     done = true;

	             break;

		   default: 

                     break;

                 }

                 break;

	    case SDL_QUIT:

	       done = true;

	       break;

            default:

  	      break;

         }

      

      SDL_framerateDelay( &fps_manager); // this will delay execution for a while

   }





   SDL_FreeSurface(screen);

  

}

```

Mike

---

### Post by dlai on 2006-12-01
You might need the SDL_EnableKeyRepeat(100,SDL_DEFAULT_REPEAT_INTERVAL);, when you initialise SDL??

---

### Post by Mickeysofine1972 on 2006-12-01
I've added some code that was given to me buy hod139 to demonstrate

Mike

---

### Post by VDM on 2006-12-02
If you want something to happen only once when you keep a button pressed, use booleans to check it a/that key was already pressed.

---

### Post by slavik on 2006-12-02
```
Uint8* keyboardmap;

...

while (!done) {
  //poll for events and other stuff
  ...
  keyboardmap = SDL_GetKeyState(NULL);

  //I think this while loop is terrible ...
  while (keyboardmap[SDLK_a]) {
    ... //do more stuff (don't forget to draw here, too
    keyboardmap = SDL_GetKeyState(NULL);
  }
```

---

### Post by Choad on 2006-12-07
> **Mickeysofine1972 said:**
> Hi Choad

The problem lies in the use of two while loops in your input loop.

ditch while(SDL_PollEvent(&event)) bit like this:

```

while(done != true)	{// new input processing loop based on the input 
		SDL_PollEvent(&event);
                .. then process the rest of the events

```

just put one while loop in and follow it with a switch or set of ifs to process the events.

This will give continuous input as you wanted and not event based polling.

Also on the frame rate thing you can use FPSmanager which is part of the SDL_gfx library. however, you will need to install this package through your package manager before you using it.

```

const int FPS = 100;

int main(void)

{

   SDL_Event event;

   bool done = false;

   FPSmanager fps_manager;

   

   init();  // Initialize everything	



   // Make sure you set the fps_manager after initializing SDL

   SDL_initFramerate( &fps_manager );

   // Set the FramesPerSecond

   SDL_setFramerate( &fps_manager, FPS );   



   // This is the main loop, and it will run until not done :)

   while (!done) { // While not done

      //Draw the scene

      drawScene();  	

      // And poll for events

      SDL_PollEvent(&event);
	 switch (event.type) {

	    case SDL_VIDEORESIZE:

	       /* handle resize event */

     	       screen = SDL_SetVideoMode( event.resize.w, event.resize.h, 16, videoFlags );

	       if ( !screen ){

	          printf("Could not get a surface after resize: %s\n", SDL_GetError( ) );

		  exit( 1 );

	       }

	       resizeWindow( event.resize.w, event.resize.h );

	       break;

            case SDL_KEYDOWN:

		switch(event.key.keysym.sym){ // handle key presses

		   case SDLK_UP:

	             xStep -= 0.1f;

	             break;

	           case SDLK_DOWN:

	             xStep += 0.1f;

	             break;

	           case SDLK_RIGHT:

	             yStep += 0.1f;

	             break;

	           case SDLK_LEFT:

	             yStep -= 0.1f;

	             break;

 	           case SDLK_ESCAPE:

                   case SDLK_q:

 		     done = true;

	             break;

		   default: 

                     break;

                 }

                 break;

	    case SDL_QUIT:

	       done = true;

	       break;

            default:

  	      break;

         }

      

      SDL_framerateDelay( &fps_manager); // this will delay execution for a while

   }





   SDL_FreeSurface(screen);

  

}

```

Mike
what are the command line compile options i need to add for this to work?

sorry to bring up a dead thread lol

---

### Post by Choad on 2006-12-07
> **Choad said:**
> what are the command line compile options i need to add for this to work?

sorry to bring up a dead thread lol
never mind, i guessed it!

---

### Post by Mickeysofine1972 on 2006-12-07
I thought you would given time LOL :D 

Mike

---

