---
title: "Tip (with a how-to): GRUB Splashimages for widescreen users!"
date: 2007-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by DEMONIIIK on 2007-09-05
So, you just figured out how to install a GRUB splash image, and GRUB is actually fun to stare at. Or would be, if it wasn't so stretched out. You are muttering under your breath at how idiotic the widescreen movement is, and wish you had just gotten a nice, big, 4:3 monitor, like all the other not-losers-anymore have. You are even considering taking off the splash image, because you would prefer black and white over some distorted image, and everyone knows there is no way to fix this, because GRUB can't load your graphics drivers and therefore can't display anything higher/wider than 640x480 pixels at 14-bit color. Stupid GRUB.

OK, several things wrong with what you are thinking. First off, if you are actually obsessing over the splash image that much... you may wish to see your therapist :p. Second off, you are right about not being able to change the resolution displayed... but you CAN change the image.

So, now that I've got you interested in tricking that mean ol' GRand Unified Bootloader into thinking it's torturing you with distorted images, lets begin. (This tip guide will be written under the assumption that you are making your own image or editing a raw image not already at said resolution..)

**Time for my tip! Yay!**
(If you want to just see the concept explained and do it all yourself... skip to "Step whatever-number-we-are-on:")

First and foremost, MAKE A BACKUP COPY OF YOUR PICTURE (if you are editing one), and if you are making your image, MAKE A BACKUP COPY OF IT AFTER YOU FINISH IT! Editing anything always seems to mess something up, or at least for me, (especially when your cat runs across the keyboard after the flashlight... in broad daylight... when your flashlight isn't even at your house... :roll:), so even if you don't have a cracked-up cat to mess you up, save a backup anyway. It might save you 2 days worth of additional pain and agony over losing a cool creation (or however long it took you to make it).


If you have a 16:9 aspect ratio and know this, just set the image size to 768x480 and you can skip this next step. Jump to "If you were making [...]."

Now, for the actual making of your image. You will first want to know your aspect ratio OR the resolution your final picture will be at. To do this the easy way, open up your favorite editor (I'm using Photoshop) and quite simply, set the size of this blank, new picture, at your optimal desktop resolution, or, if you know it, your monitor's native resolution (usually they are the same thing, and if not, your desktop probably looks funky, just like that darn GRUB screen). Then, resize the image with the aspect ratio locked so that the second value is 480 pixels. For example, I would open up a new image and set my image size to 1440x900 pixels. (PIXELS! Yards would be........ big. Seriously, remember to select pixels (px) as your unit... this might save you from a program/computer crash, hehehe) Then, I would resize the image to be <not touching this value>x480, and because 'preserve aspect ratio' was enabled, the result of changing the one value made my image 768x480.

If you were making your own image, go ahead and draw away (you may either draw in 14 bit color from the start or make your own super cool image and change the coloring to 14-bit when done and retouch, whichever floats your boat!). If you were editing a pre-made image, go ahead and crop/resize/etc and do whatever you need to get this image down to your resolution (Ax480).

You done? You have a super cool image that's ready to go? Good.

Step whatever-number-we-are-on: Resize the image again, this time WITHOUT aspect ratio preservation. You want to force your image to be 640x480 now (at 14-bit color, did you remember that part?). Yes, it looks skinny and distorted, but this is how we are tricking GRUB. GRUB can only show at 640x480, so if it's on a widescreen monitor, it will stretch it out to fill your screen. What we did is make an image that would look undistorted when stretched (because it was at the same aspect ratio) and simply squished it together so it would still comply with GRUB. GRUB stretches the image out, and voila, undistortion!

You are done. Save the image in .xpm format, gzip it, and move it to your /boot/grub/ directory using ```
sudo cp <old location> /boot/grub/
``` (you don't have to move it, but it's good practice, since a broken link in splashimage can prevent you from booting). Edit your menu.lst file as necessary to point to the new splash image (I'm assuming you know what you need to edit and how).

Badabing. Save, do whatever else you need to do, reboot, and check out the undistortion. You can be happy again, and peacefully stare at GRUB now.


By the way, if you got as far as saving the image, but are clueless as to what all that rubbish about editing a menu.lst file, or you flat-out don't know what to edit and how, look [here]("http://users.bigpond.net.au/hermanzone/p15.htm"). It's not an official Ubuntu page, but the guy wrote a pretty decent walkthrough on GRUB (and is an Ubuntu user, so you can stop scratching your head).

---

