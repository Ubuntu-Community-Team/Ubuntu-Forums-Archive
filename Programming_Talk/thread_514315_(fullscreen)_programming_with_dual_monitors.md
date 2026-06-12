---
title: "(fullscreen) programming with dual monitors"
date: 2007-07-31
forum: Programming Talk
---

### Post by Angry on 2007-07-31
I was wondering if there were any available resources that could point me in the right direction in regards to programming with multiple monitors.

I am playing around with C++/SDL/OpenGL and have Beryl running.  Currently, going fullscreen causes my rendered scene to be placed half and half in both monitors, and subsequently bordered by black space.  I can  turn off Beryl and eliminate it as a potential failure point - but the end result remains the same.

I suppose my question is both a) how can I go fullscreen in a single monitor?  And then b) go fullscreen utilizing both montors as a single rendering space?

Thanks in advance.

---

### Post by brooksbp on 2007-08-01
Sounds like a vid driver bug.  You should look into that for your specific graphics card.  As for going fullscreen utilizing both monitors, you have to check your drivers again.  You can always drag the window by yourself.

Short term response: don't maximize, resize manually to close to full screen??  I assume you're a big boy/girl.

---

### Post by Angry on 2007-08-02
Ok...

```

	// set sdl surface depth to system depth
	const SDL_VideoInfo* video = SDL_GetVideoInfo();
	int depth = video->vfmt->BitsPerPixel;

	int vf;						// video flag(s)
	vf	 = SDL_OPENGL;			// using OpenGL
	vf	|= SDL_GL_DOUBLEBUFFER;	// enable double buffering
	vf	|= SDL_HWPALETTE;		// store palette in hardware
	vf	|= (this->_settings->fullscreen()) ? SDL_FULLSCREEN : SDL_RESIZABLE;

	// store surface in video or system memory, based on hardware availability
	vf	|= (video->hw_available ? SDL_HWSURFACE : SDL_SWSURFACE);

	// use hardware acceleration if hardware blits available
	if (video->blit_hw) vf |= SDL_HWACCEL;

	// set sdl video mode
	if(!SDL_SetVideoMode(width, height, depth, vf))
		throw sys_error(std::string("could not set sdl surface.  SDL returned:\n") += SDL_GetError()); 

```

now, if I choose SDL_FULLSCREEN, I don't have anything to drag or maximize.  And I am a big boy.

---

