---
title: "SDL and Removing things"
date: 2011-01-20
forum: Programming Talk
---

### Post by Ravenshade on 2011-01-20
Hi peeps. 

Now, I've been experimenting with key strokes and voila, the system recognizes them but I've come up against a curious problem to which I am not aware of the syntax, yet. 

Any how... using SDL, I press a key and associate with it a message to be displayed. When I press that key, the message is displayed on the screen using TTF. 

Then I apply it to the surface, and SDL_Flip to update the screen. 

Now. Something isn't quite right. 

...meh... here's the code. 
[PHP]//If message needs to be displayed
		if( keyPressedMessage != NULL )
		{
			
			apply_surface( 150, 300, keyPressedMessage, screen );
			keyPressedMessage = NULL; //Reset the surface. 
			//was there a problem sending it to the screen? update!
			if( SDL_Flip( screen ) == -1 )
			{
				return 1;
			}
				
		}[/PHP]

I am trying to figure out a way to reset the surface...or clear the text that seems to remain. I set it to Null and I didn't expect that to work and updated the screen as you can see above. 

I've also tried Clearing the surface...turns out that's a bad idea >.>; So anyone got a tip as to how I can do this? Or rather...I only want the message to appear for a short time...

---

### Post by Mach1723 on 2011-01-20
I don't quite understand your post, but it seems like you would call [SDL_delay(to keep the text on screen for however long)]("http://wiki.libsdl.org/moin.cgi/SDL_Delay?highlight=%28%5CbCategoryTimer%5Cb%29%7C%28CategoryStruct%29%7C%28CategoryEnum%29") and then use the [SDL_RenderClear]("http://wiki.libsdl.org/moin.cgi/SDL_RenderClear?highlight=%28%5CbCategoryVideo%5Cb%29%7C%28CategoryEnum%29%7C%28CategoryStruct%29") function.

Though I haven't meddled with SDL in a while, and I might be wrong.

---

### Post by fct on 2011-01-21
I'm also not sure what the post means.

Normally, a videogame flow goes:

1.- Check input, change state accordingly
2.- Perform needed calculations based on state
3.- Update screen, play sound, etc.
4.- Go to 1

If you want messages on screen, you normally would set up some messaging system, with a list of messages to be displayed and each one with a limited timespan that decreases with time.

Also, "keyPressedMessage = NULL" frees no memory, so you have a memory leak there.

---

### Post by worksofcraft on 2011-01-21
IDK anything about SDL but in general if you want to remove something from the screen you have to redraw that part of the image without the bit that you wanted to remove. So to remove the text you not only set to NULL (to stop it from being redrawn), but also redraw the rest of what was there before.

A lot of graphics packages simply generate the new image in memory and then "blit" it to the screen.

Best performance is achieved using what is known as "double buffering". What that means is the software produces an image in one buffer while the blitting hardware transfers the other one to the screen and then the buffers are swapped so that you don't get jumpy transitions and the software never has to wait for the hardware to catch up or vice versa.

Now I have heard that advanced generation graphics cards have integral high performance processors that can do a lot of these operations independently... even animating full 3D models,

Thus in theory they having potential to relieve your main processor from phenomenal work load :shock: OTOH I have also heard that on many systems the software don't come even remotely close to realizing that potential of the hardware :(

---

### Post by Simian Man on 2011-01-21
fct is right, you need a little bit more structure.  You should have one rendering loop and only call SDL_Flip once per scene.  Something like this (pseudocode):

```


SDL_Surface* message = SDL_TTF_Whatever(...);
bool show_message = false;

while(SDL_PollEvent(&event)) {
    if(whatever key you want to check) {
        show_message = true;
    } else {
        show_message;
    }

    /* clear the screen */

    /* render stuff */
    if(show_message) {
        apply_surface(150, 300, message, screen); 
    }

    /* now flip */
    SDL_Flip(screen);
}

```

If you only ever clear the screen, render and flip buffers once, it becomes much more manageable to make changes to your scene.

---

