---
title: "OpenGL Mouse Events"
date: 2006-10-28
forum: Programming Talk
---

### Post by richardhp on 2006-10-28
I am writing a Game in SDL/OpenGL and I want the user to be able to place things on the screen by clicking the mouse. I use the 					SDL_GetMouseState(&mouse_x, &mouse_y);
Function to find out where they clicked, but then when I feed these numbers back into the draw function it does not draw where the user clicked.

I know this is because the OpenGL units are different from pixels, but I used the function
       	gluOrtho2D(0, SCREEN_WIDTH, 0, SCREEN_HEIGHT);
which I thought was supposed to change the OpenGL units to pixels but it does not work. Have I done it wrong or is there some clever method I can use to convert between the two?

---

### Post by tpg on 2006-10-28
When you say it does not draw where the user clicked, does it appear a certain distance away every time? i.e. do you just need to do a translation before drawing your objects? 

I'm thinking that the origin of your OpenGL co-ordinates may be in the centre of the window, but SDL_GetMouseState returns co-ordinates from the top left-hand corner.

Hope this helps!:)

---

### Post by richardhp on 2006-10-28
You have highlighted a problem with the code and I have changed it to this:
		DCLib1.additem(mouse_x-(SCREEN_WIDTH/2),mouse_y-(SCREEN_HEIGHT/2));

Where DCLib1.additem adds a polygon to an array that is continuously drawn to the screen to the co-ordinates specified. 

This corrects one of the problems, but the original one still remains. When I click in the centre of the screen, the object is drawn in the centre. But if I click about 10 pixels left of the center, the object is drawn much further away ie - 10 openGl units.

So how do i convert between the two, so that if i move 100 pixels to the left, the object is drawn 100 pixels to the left of the centre, not 100 opengl units to the left (which is off the screen)

---

### Post by tpg on 2006-10-28
I think the easiest thing to do would be to look at this quick program I wrote, that just draws a square under the cursor, and look at the code. It's probably not that great code, but it seems to work!

---

### Post by richardhp on 2006-10-29
thanks alot, that is very much appreciated. i will try and integrate your code into my program.

---

### Post by Jengu on 2006-10-29
You're sort of on the right track. Keep in mind that that gluOrtho2D *changes the 'size' of OpenGL units*. So after you use gluOrtho2D to draw things on the surface of the screen 2D style, *you must switch back to your original 3D perspective*. That is, if you called gluPerspective before, you need to call it again to switch back after gluOrtho2D. Usually in OpenGL you do this by saving the current projection matrix and then pushing it back off. Example:

```

glMatrixMode(GL_PROJECTION);
gluPerspective(0, 10, 0, 10, 45); // Made up values, use your own

// Draw some 3D stuff

glPushMatrix(); // Save current perspective
gluOrtho2D(0, screen_width, 0, screen_height); // Switch to 2D
// Draw some 2D stuff
glPopMatrix(); // Restore old perspective

// Now we can draw 3D stuff again

```

---

