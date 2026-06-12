---
title: "Tablet support for an odd make..."
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Cantua on 2008-08-21
Hello all!  First things first - I'm MJ, and I recently switched to Linux because of Vista.  I'd always wanted to switch - I love the Linux ethos - but I'm not terribly technical, and I lived in rural Japan, and knew nobody who would be prepared to help with tech support.  Well, right before leaving, I found a beautifully tiny tablet, a Kohjinsha SH, on sale second-hand and had to have it.  Unfortunately, it not only had Vista pre-installed, it had JAPANESE Vista.  My technical Japanese is decent, but deciphering the kanji for pages upon pages of installation instructions is like a nightmare wrapped around a headache wrapped around a large gold brick.  To make matters worse, I've never used Vista before, and the computer is not QUITE good enough to handle it well.  So, I installed the latest Ubuntu to dual-boot, thinking that I might just use it occasionally to browse the internet a little more quickly.  That was maybe two weeks ago, and I've only opened up Windows once since.  I can't even remember what for.

So now that I feel I'll be using Ubuntu for pretty much everything from now on, I do have one small unresolved issue.  The computer is a tablet with a screen that swings around and all that (and looks like nothing so much as a large, old-style Nintendo DS), and I would love to be able to use the tablet features.  It does register properly when I touch the screen - a tap is a click, a dragging motion drags - but the pointer executes these motions far away from where the screen is actually touched.  On Vista, there is also a small keyboard-map that pops up when you click in a text field so that you don't have to open the computer to type, and I consider that a luxury I probably don't really need, but it would be nice to be able to draw and click on the screen.  Is there some kind of program that I might be able to download that would help me easily configure the touch-screen mouse features?

MJ

---

### Post by Pro-reason on 2008-08-21
The manufacturer's website ([http://www.kohjinsha.com.sg/products/drivers.htm](http://www.kohjinsha.com.sg/products/drivers.htm)) has Linux drivers to download for the touchscreen, but they don't seem very user friendly.  You'll probably need help installing them, and I don't have access to your hardware to know whether stuff works.

You may find some basic drivers available in the Synaptic package manager.  I know there is a package (confusingly) called “synaptics” which deals with touchpads and suchlike.  It may help.  It's difficult for me to say more.

---

### Post by Shiruban on 2008-11-06
Now I am writing from my kohjinsha SH8 installed with intrepid...  I kept windows only for the one seg TV, meaning I never use it!
If you search this forum with kohjinsha you will found some post concerning this little computer.
For the touchscreen, from what you say you may be using hardy or intrepid? please tell which one.
If intrepid no luck for now, it's still under investigation and we may have to wait from the people of penmount.com (the maker of the touchscreen for a new driver).
If you are using hardy, just go to the website penmount.com, download the driver, run the installer (sudo sh ./install.sh) your touchscreen is a usb interface 6000, i think you will like stream mode, me i put 800ms for the right click, and that should be all. After you disable compiz (metacity --replace) and you go system>preference>calibration, you chose the number of calibration points, you touch accurately the point that appears and you are done!
Good luck with your kohjinsha and GNU/linux !
if you need some more help...yoroshiku

---

