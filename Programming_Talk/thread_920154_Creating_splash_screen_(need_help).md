---
title: "Creating splash screen (need help)"
date: 2008-09-15
forum: Programming Talk
---

### Post by MR.UNOWEN on 2008-09-15
Hello,

Back when I had window's I'd always modify the boot screen. So now that I use Ubuntu 99% of time, I thought I'd start learning how to do it for Ubuntu. So I starting looking at some source code and for the most part I could understand a good portion of it, but there's a few thing I'm unclear about. If you could answer the questions below, that would be great.


Here's some source code I've found....
```

/* usplash
 *
 * tux_world-theme.c - definition of tux_world theme
 *
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301 USA
 */

#include <usplash-theme.h>
/* Needed for the custom drawing functions */
#include <usplash_backend.h>

extern struct usplash_pixmap pixmap_tux_world_800_600, pixmap_tux_world_1024_768;
extern struct usplash_pixmap pixmap_throbber_back;
extern struct usplash_pixmap pixmap_throbber_fore;
extern struct usplash_font font_helvB10;

void t_init(struct usplash_theme* theme);
void t_clear_progressbar(struct usplash_theme* theme);
void t_draw_progressbar(struct usplash_theme* theme, int percentage);
void t_animate_step(struct usplash_theme* theme, int pulsating);

struct usplash_theme usplash_theme_1024_768;

/* Theme definition */
struct usplash_theme usplash_theme = {
	.version = THEME_VERSION, /* ALWAYS set this to THEME_VERSION, 
                                 it's a compatibility check */
    .next = &usplash_theme_1024_768,
    .ratio = USPLASH_4_3,

	/* Background and font */
	.pixmap = &pixmap_tux_world_800_600,
	.font   = &font_helvB10,

	/* Palette indexes */
	.background             = 0,
  	.progressbar_background = 5,
  	.progressbar_foreground = 210,
	.text_background        = 0,
	.text_foreground        = 4,
	.text_success           = 2,
	.text_failure           = 1,

	/* Progress bar position and size in pixels */
  	.progressbar_x      = 303,
  	.progressbar_y      = 426,
  	.progressbar_width  = 320,
  	.progressbar_height = 18,

	/* Text box position and size in pixels */
  	.text_x      = 225,
  	.text_y      = 450,
  	.text_width  = 350,
  	.text_height = 150,

	/* Text details */
  	.line_height  = 15,
  	.line_length  = 32,
  	.status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar,
    .draw_progressbar = t_draw_progressbar,
    .animate_step = t_animate_step,
};

struct usplash_theme usplash_theme_1024_768 = {
	.version = THEME_VERSION,
    .next = NULL,
    .ratio = USPLASH_4_3,

	/* Background and font */
	.pixmap = &pixmap_tux_world_1024_768,
	.font   = &font_helvB10,

	/* Palette indexes */
	.background             = 0,
  	.progressbar_background = 5,
  	.progressbar_foreground = 210,
	.text_background        = 0,
	.text_foreground        = 4,
	.text_success           = 2,
	.text_failure           = 1,

	/* Progress bar position and size in pixels */
  	.progressbar_x      = 384, /* 1024/2 - 320/2 */
  	.progressbar_y      = 548,
  	.progressbar_width  = 320,
  	.progressbar_height = 18,

	/* Text box position and size in pixels */
  	.text_x      = 282,
  	.text_y      = 573,
  	.text_width  = 460,
  	.text_height = 195,

	/* Text details */
  	.line_height  = 15,
  	.line_length  = 32,
  	.status_width = 35,

    /* Functions */
    .init = t_init,
    .clear_progressbar = t_clear_progressbar,
    .draw_progressbar = t_draw_progressbar,
    .animate_step = t_animate_step,
};

void t_init(struct usplash_theme *theme) {
    int x, y;
    usplash_getdimensions(&x, &y);
    theme->progressbar_x = (x - theme->pixmap->width)/2 + theme->progressbar_x;
    theme->progressbar_y = (y - theme->pixmap->height)/2 + theme->progressbar_y;
}

void t_clear_progressbar(struct usplash_theme *theme) {
    t_draw_progressbar(theme, 0);
}

void t_draw_progressbar(struct usplash_theme *theme, int percentage) {
    int w = (pixmap_throbber_back.width * percentage / 100);
    usplash_put(theme->progressbar_x, theme->progressbar_y, &pixmap_throbber_back);
    if(percentage == 0)
        return;
    if(percentage < 0)
        usplash_put_part(theme->progressbar_x - w, theme->progressbar_y, pixmap_throbber_back.width + w,
                         pixmap_throbber_back.height, &pixmap_throbber_fore, -w, 0);
    else
        usplash_put_part(theme->progressbar_x, theme->progressbar_y, w, pixmap_throbber_back.height, 
                         &pixmap_throbber_fore, 0, 0);
}

void t_animate_step(struct usplash_theme* theme, int pulsating) {

    static int pulsate_step = 0;
    static int pulse_width = 28;
    static int step_width = 2;
    static int num_steps = (216 - 28)/2;
    int x1;

    if (pulsating) {
        t_draw_progressbar(theme, 0);
    
        if(pulsate_step < num_steps/2+1)
	        x1 = 2 * step_width * pulsate_step;
        else
	        x1 = 216 - pulse_width - 2 * step_width * (pulsate_step - num_steps/2+1);

        usplash_put_part(theme->progressbar_x + x1, theme->progressbar_y, pulse_width,
                         pixmap_throbber_fore.height, &pixmap_throbber_fore, x1, 0);

        pulsate_step = (pulsate_step + 1) % num_steps;
    }
}

```
[B]
The first half is understandable as it just configures the positioning, text color and other stuff.
What I'm having trouble understanding are the functions at the bottom. Some of the variables I don't know where they're coming from or what they're for.[/B]

Also what are my limitations to the images?  I noticed that color are indexed so obviously there are some limitations.
-how many colors can I have?
-what are my screen resolution limitations?

If something goes wrong, what will happen and how do I fix it?

---

### Post by MR.UNOWEN on 2008-09-15
I just revised the topic, hopefully it's clearer now. Please help me.......

---

### Post by MR.UNOWEN on 2008-09-16
Can someone explain how the three functions on the bottom of the code work? Their names explains what they do, but I'm having a hard time understanding how the function works. Also some of the variables I don't know where they're coming from.

BTW what is the maximum number of colors I can have on screen?

---

### Post by dribeas on 2008-09-16
> **MR.UNOWEN said:**
> Can someone explain how the three functions on the bottom of the code work? Their names explains what they do, but I'm having a hard time understanding how the function works. Also some of the variables I don't know where they're coming from.

BTW what is the maximum number of colors I can have on screen?

You are asking about a really particular issue, which I don't know anyone with experience. In my case I am just trying to read the code and understand what it means, but you should really read into the docs where you got this code from

void t_draw_progressbar(struct usplash_theme *theme, int percentage);

This function seems to overwrite just the part of the image dedicated to the progress bar by first clearing it and then painting either from left or right depending on whether the percentage is possitive/negative. Read the docs for usplash_put_part to confirm that this function draws a section of the screen.

void t_animate_step(struct usplash_theme* theme, int pulsating);

You should read usplash_put_part and get what the second to last parameter means. I assume that it is some kind of brightness factor. In that case, just out of assumption, the function calculates that factor and applies it to the progress bar drawing, so that it pulsates.

Then again, as I already said, I have not used that lib, I did not read the docs and I have no time to do it either.

---

### Post by MR.UNOWEN on 2008-09-16
Could you give me the link to the docs?? 
BTW I got the code from gnome-look from an existing splash screen.

Also I'm still not that experienced in c that much. What does "->" in "theme->progressbar_y" mean? If only you could have the splash screen done in Java -_-....

---

### Post by dribeas on 2008-09-17
> **MR.UNOWEN said:**
> Could you give me the link to the docs?? 
BTW I got the code from gnome-look from an existing splash screen.

Also I'm still not that experienced in c that much. What does "->" in "theme->progressbar_y" mean? If only you could have the splash screen done in Java -_-....

I cannot help you with the docs, search for them where you got the code. Then the other question: a->b is a synonim for (*a).b, that is dereference the pointer and access the data.

---

### Post by red_team316 on 2008-09-20
You are limited to 256 colors(you can make amazing looking images in 256 colors, I have for years).
You can code resolutions as high as you want, you should only be limited by your graphics card or monitor max resolutions.
theme->progressbar_y is a pointer to the .progressbar_y value in the theme definition(struct).
It's kind of hard to bork your system from a usplash. Most likely if something goes wrong, you'll just be left without a fancy splash screen. If you are not familiar with installing a usplash manually, then use Usplash-Switcher. Try to stay away from SUM until you are positive you can repair anything it screws up as it can modify GRUB too.

To get the docs:
```

sudo apt-get install libusplash-dev

```
and then go to:
/usr/share/doc/libusplash-dev/examples

---

