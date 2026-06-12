---
title: "SDL framebuffer"
date: 2010-10-11
forum: Programming Talk
---

### Post by roadkillguy on 2010-10-11
If anyone has experience with SDL, I would be very thankful

My problem is the fact that SDL has a very strange framebuffer.  Whenever my computer get's slow running my application, instead of getting choppy, it buffers all input and gets delayed.  Does anyone know how to implement frame skipping or anything of the likes?  I would rather have choppy, because delayed input is no good, especially for multiplayer applications.

Thanks!

---

### Post by Zugzwang on 2010-10-12
Are you writing a game? As far as I know, SDL by default sets up only a double-buffer, thus you might need to adapt your game update loop to cope with different execution speeds.

As an example, see the following tutorial: [http://shawnmccool.com/game-development-tutorial-1-smooth-time-based-movement/](http://shawnmccool.com/game-development-tutorial-1-smooth-time-based-movement/)

I think that there's also a gamedev.net tutorial on this issue, which you might also want to have a look at, but I don't know the URL - use google if you wish to read it.

---

### Post by roadkillguy on 2010-10-12
Yes, I am writing a game. (I always seem to leave something out)

I'll probably use that time-based movement in the future, once I get this delay solved out.

It seems as though when the game is running slow, it buffers my input for maybe.. 2 seconds.  After the 2 seconds are up, it does the key combination I gave 2 seconds prior.  Maybe I need to flush the input buffer?

---

### Post by TheBuzzSaw on 2010-10-12
> **roadkillguy said:**
> Yes, I am writing a game. (I always seem to leave something out)

I'll probably use that time-based movement in the future, once I get this delay solved out.

It seems as though when the game is running slow, it buffers my input for maybe.. 2 seconds.  After the 2 seconds are up, it does the key combination I gave 2 seconds prior.  Maybe I need to flush the input buffer?

It sounds like you need the time-based movement feature right now.

What exactly does your rendering loop look like right now? There are several parts I would like to see. Your loop should resemble something like this:

[php]
// 40 FPS game logic entails an update every 25ms
Uint32 nextFrame = SDL_GetTicks() + 25;
SDL_event event;

while (running)
{
    while (SDL_PollEvent(&event)) handleEvent(event);

    if (SDL_GetTicks() > nextFrame)
    {
        nextFrame += 25;
        doGameLogicAndUpdates();
    }
    else
    {
        doRendering();
    }

    SDL_Delay(1); // prevent CPU abuse
}
[/php]

---

### Post by roadkillguy on 2010-10-12
```

// Process pending events
bool events()
{
	SDL_Event event;
	if( SDL_PollEvent(&event) )
	{
		int keyNum = event.key.keysym.sym;
		
		if(event.type == SDL_KEYDOWN)
		{
			key[event.key.keysym.sym] = true;
		}
		if(event.type == SDL_KEYUP)
		{
			key[event.key.keysym.sym] = false;
		}
		if(event.type == SDL_MOUSEMOTION)
		{
			if(SDL_WM_GrabInput(SDL_GRAB_QUERY))
			{
				if(ignoreMouseEvent == false)
				{
					float xdiff = event.motion.xrel;
					float ydiff = event.motion.yrel;
					
					lon += xdiff/5;
					lat += ydiff/5;
					//cout << xdiff/5 << endl;
					
					if(lat > 0)
					{
						lat = 0;
					}
					else if(lat < -180)
					{
						lat = -180;
					}
				}
				ignoreMouseEvent = false;
				
				if(event.motion.x > (WINDOW_WIDTH - 2) || event.motion.x < 2 || 
				   event.motion.y > (WINDOW_HEIGHT - 2) || event.motion.y < 2)
				{
					SDL_WarpMouse(WINDOW_WIDTH/2, WINDOW_HEIGHT/2);
					ignoreMouseEvent = true;
				}
			}
		}
		if(event.type == SDL_QUIT)
		{
			return false;
		}
	}
	return true;
}


while( events() )
	{
		glLoadIdentity();
		glRotatef(lat, 1, 0, 0);
		glRotatef(lon, 0, 0, 1);
		glTranslatef(camerax, cameray, cameraz);
		
		glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
		glClearColor(0.9f, 0.9f, 1.0f, 0.0f);

                //OTHER RENDER STUFF GOES HERE

		SDL_GL_SwapBuffers();

		// Check keypresses
		if( key[SDLK_RIGHT] ){ lon += 0.5; }
		if( key[SDLK_LEFT ] ){ lon -= 0.5; }
		if( key[SDLK_UP] ){ lat -= 0.5; }
		if( key[SDLK_DOWN] ){ lat += 0.5; }
		
		//MOVE THE CAMERA
		if(key[SDLK_a])
		{
			camerax += sin((lon + 90)*PI/180)*.05;
			cameray += cos((lon + 90)*PI/180)*.05;
		}
		if(key[SDLK_d])
		{
			camerax += sin((lon - 90)*PI/180)*.05;
			cameray += cos((lon - 90)*PI/180)*.05;
		}
		if(key[SDLK_s])
		{
			camerax += sin((lon)*PI/180)*.05;
			cameray += cos((lon)*PI/180)*.05;
		}
		if(key[SDLK_w])
		{
			camerax += sin((lon + 180)*PI/180)*.05;
			cameray += cos((lon + 180)*PI/180)*.05;
		}
		
		if(key[SDLK_q]){cameraz += .05;}
		if(key[SDLK_e]){cameraz -= .05;}
		
		if(key[SDLK_ESCAPE])
		{
			exit(0);
		}
	}
```

I'm seeing now that it's probably not a good Idea to have the rendering code with the game logic code in the same loop.. Thanks for posting that structure, I'll try to implement that and see what happens.

---

### Post by TheBuzzSaw on 2010-10-12
Yeah, never do updates in the main loop with no timer control. You become slave to the speed of someone's processor rather than uniform across all platforms.

---

### Post by roadkillguy on 2010-10-12
Thanks guys, that helped a bunch. :)
Works perfectly now!

---

### Post by TheBuzzSaw on 2010-10-12
> **roadkillguy said:**
> Thanks guys, that helped a bunch. :)
Works perfectly now!

I'm curious as to what you are working on. :P

If you have any further questions, feel free to ask 'em. I have pretty extensive experience with SDL.

---

### Post by roadkillguy on 2010-10-18
A game I'm working on.  Involving cubes.  Lot's of cubes.

Anyway, now I want to know the best way to render text.  Google searches have only yielded text texture generation, which is in fact not what I want to do.  I want to have a simple fps number in the upper left hand corner, along with some other text.  What do I do?

I don't exactly care if it's a bitmap font or not, and GLUT is out of the picture due to SDL.

---

### Post by Zugzwang on 2010-10-19
> **roadkillguy said:**
> I don't exactly care if it's a bitmap font or not, and GLUT is out of the picture due to SDL.

The following tutorial looks suitable: [http://www.gamedev.net/reference/articles/article1960.asp](http://www.gamedev.net/reference/articles/article1960.asp)

---

### Post by roadkillguy on 2010-10-19
The only problem with that is, it uses sdl surfaces.  If I'm not mistaken those don't work when sdl is in opengl mode.  Am I better off with glut?

---

### Post by Simian Man on 2010-10-19
I spent a *long* time trying to make SDL_Ttf work with OpenGL in an efficient way, and eventually gave it up as a bad job.  I'd recommend using [FTGL]("http://ftgl.sourceforge.net/docs/html/ftgl-tutorial.html") which is just as simple, and works great with OpenGL.

Good luck on your (Minecraft-like?) game!

---

### Post by TheBuzzSaw on 2010-10-19
> **roadkillguy said:**
> Anyway, now I want to know the best way to render text.  Google searches have only yielded text texture generation, which is in fact not what I want to do.  I want to have a simple fps number in the upper left hand corner, along with some other text.  What do I do?

What is wrong with that? You have an irrational fear. Unless you plan on drawing the text with actual OpenGL geometry, loading the text into a texture is the best way to do it. SDL surfaces are *designed* to work with OpenGL. Instead of the 2D mode blitting, you pipe the void* pixels element into texture data. It works great. I'm not sure what you have against that method. Google revealing that one option should have been a hint...

---

### Post by Simian Man on 2010-10-19
> **TheBuzzSaw said:**
> What is wrong with that? You have an irrational fear. Unless you plan on drawing the text with actual OpenGL geometry, loading the text into a texture is the best way to do it. SDL surfaces are *designed* to work with OpenGL. Instead of the 2D mode blitting, you pipe the void* pixels element into texture data. It works great.

Whoa there, that is actually a *terrible* idea, though very easy to implement.  You're proposing that every time the text changes (which for an FPS counter, may as well be every frame), to create an SDL_Surface with that text, create a new OpenGL texture, fill it with data from the SDL_Surface, and render with that texture.  That involves sending all of the pixel data from memory to the graphics card.  Every frame.  This approach will slow your game to a crawl before long.

The right way to do it is to create a texture for each character you want to use and blit them in the right order to construct the text you want.  This removes the horrible inefficiency of creating new textures on the fly.  I tried doing this manually with SDL_Ttf, but I found it more trouble than it was worth and switched to the FTGL library I mentioned earlier which does all of this for you.

And for someone that doesn't know what they're talking about you sure come across like a know-it-all :).

---

### Post by TheBuzzSaw on 2010-10-19
> **Simian Man said:**
> Whoa there, that is actually a *terrible* idea, though very easy to implement.  You're proposing that every time the text changes (which for an FPS counter, may as well be every frame), to create an SDL_Surface with that text, create a new OpenGL texture, fill it with data from the SDL_Surface, and render with that texture.  That involves sending all of the pixel data from memory to the graphics card.  Every frame.  This approach will slow your game to a crawl before long.

The right way to do it is to create a texture for each character you want to use and blit them in the right order to construct the text you want.  This removes the horrible inefficiency of creating new textures on the fly.  I tried doing this manually with SDL_Ttf, but I found it more trouble than it was worth and switched to the FTGL library I mentioned earlier which does all of this for you.

And for someone that doesn't know what they're talking about you sure come across like a know-it-all :).

It's an FPS counter, not some integral part of the game. The amount of data involved is incredibly small. Frankly, you are overplaying the "problem" with creating new surfaces and piping them to the GPU. Also, who would honestly update every single frame? I have my counters update once per second, but that's just me.

Yes, ideally you should be running a text mechanism that optimizes the use of textures, but he just wanted an FPS counter. You act like this absurdly tiny use of memory is the end of the world.

And sure... I don't know what I'm talking about...

*cough*
[http://code.google.com/p/dejarix/](http://code.google.com/p/dejarix/)
[http://code.google.com/p/paroxysm/](http://code.google.com/p/paroxysm/)
[http://www.youtube.com/watch?v=iN1kbcAK6Co](http://www.youtube.com/watch?v=iN1kbcAK6Co)
[http://code.google.com/p/libxpg/](http://code.google.com/p/libxpg/)
[http://code.google.com/p/zero2d/](http://code.google.com/p/zero2d/)
*cough*

In SDL, another clever FPS counter is to simply report the FPS in the window title or something.

---

### Post by Simian Man on 2010-10-19
OK, I'll concede that if the *only* text he wants in his game is the FPS counter, he can get away with the method you described.  But doing anything more than a couple short strings and it would become the rendering bottleneck *very* quickly.  And honestly when have you played a game that didn't have any text on the screen at any point?

And this:
[quote=TheBuzzSaw]Instead of the 2D mode blitting, you pipe the void* pixels element into texture data. It works great. I'm not sure what you have against that method. Google revealing that one option should have been a hint... [/quote]
Implies that your method isn't just something you can sometimes get away with, but the actual right approach which is *not* the case.

---

### Post by TheBuzzSaw on 2010-10-19
You're right. It would be a brutal bottleneck. I was not implying otherwise. :)

Generally, I'm not concerned when people are new to OpenGL. Usually, you will run into much bigger bottlenecks like glBegin. XD

---

### Post by Simian Man on 2010-10-19
> **TheBuzzSaw said:**
> You're right. It would be a brutal bottleneck. I was not implying otherwise. :)

Generally, I'm not concerned when people are new to OpenGL. Usually, you will run into much bigger bottlenecks like glBegin. XD

Fair enough :).  I really like your card table demo BTW!

---

### Post by TheBuzzSaw on 2010-10-19
> **Simian Man said:**
> Fair enough :).  I really like your card table demo BTW!

Thanx. I'm still working on card piles, but I'm busy combating my last semester of school. :(

---

### Post by roadkillguy on 2010-10-19
I think I'm going to go with FTGL.  Thanks for all your help!  It works!

And yes, it is somewhat like minecraft/infiniminer, only I plan on having more reactions between blocks.

---

