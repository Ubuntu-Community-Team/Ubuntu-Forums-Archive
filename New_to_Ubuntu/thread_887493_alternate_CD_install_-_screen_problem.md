---
title: "alternate CD install - screen problem"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by tgyorgyi on 2008-08-12
I have problems with the Live CD install (at one point it simply stops and returns to the Live CD desktop without an error or any other type of message).

I'm trying now the alternate CD, but here I have another problem.
The screen is split at two thirds, the first section of the screen is on the right, and the second part of the screen is on the left. 
Reading the screen is impossible this way.

I'm trying to install on a Fujitsu-Siemens Amilo L laptop.

---

### Post by decoherence on 2008-08-12
What is the LCD's native screen resolution?

You may be able to fix this by appending a vga= argument to your kernel line. vga=*what* depends on your lcd's native screen resolution.

---

### Post by tgyorgyi on 2008-08-12
Hmm, I think it is 1024x800, at least this is the only resolution with which Ubuntu used to look right before. What would I need to _exactly_ type into the kernel line (noob here, though I know at least how to type into the kernel line of the CD? :) ).

---

### Post by tgyorgyi on 2008-08-12
Meanwhile I tried adding vga= to the kernel and it asked me to specify, which I did, but this only changed the positioning of the script before the bluish install screen, that remained switched like before: the left one third of the screen on the right, and what should be in the middle starting on the left.

---

### Post by decoherence on 2008-08-12
okay, when you start your computer up, watch for a prompt to press ESC to enter GRUB.

Once you're there, select the kernel you normally boot from (the top one, by default) and press 'e'

Select the line that starts with "kernel" and press 'e' again.

You are brought to the end of the kernel line. type a space, followed by vga=761

Press enter, then type 'b'

hopefully that will let you get through the install so X can take over screen resolution.

---

### Post by tgyorgyi on 2008-08-12
I managed to add this. I do not have grub right now, this is the whole issue (Live CD stops the install and grub is most likely not written, I end up with XP-only startup or grub error), but I could add to the kernel line by hitting F6 on the opening screen of the alternate CD. I got a message that this is not a valid value and a list of values to choose from, which I did. But this is not the solution anyway, the new vga settins affected only the next couple of lines while the terminal-style white-on-black communication still lasted. Once I was on the blue install screen of the alternate CD, I still had the same problem of the screen being split into two vertical parts and mixed in the wrong order. :-(

---

### Post by decoherence on 2008-08-13
> **tgyorgyi said:**
> but I could add to the kernel line by hitting F6 on the opening screen of the alternate CD.

That's what I meant. Sorry for not being clearer. Also, sorry for giving you the wrong number. Check out

[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

And try a few likely numbers. You'll note your specific resolution isn't there, so I'd just try a few and see if any work. Particularly 768 and 773.

Doing so *shouldn't* melt your LCD...:wink:

---

