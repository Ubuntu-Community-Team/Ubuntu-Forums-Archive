---
title: "Logitech C615 not fully recognized."
date: 2012-10-18
forum: New to Ubuntu
---

### Post by Gnawnsense on 2012-10-18
Hello all! Brand new to Linux, running 12.4, ran into a little snag earlier. Long story short, I have a Logitech C615 camera that appears to be supported. I checked the LSUSB and it is listed. Works on various websites used for checking webcam functionality.

So the next thing I did after checking to make sure it appeared to be working was downloading cam software for it. I downloaded Cheese after doing a bit of reading. I downloaded it from the software center, launched it, and the camera was not recognized within the program.

I downloaded guvcview to see if it would show there, and surprisingly, it did. Tried Cheese again, still nothing. Rebooted, nothing. So at this point, I uninstalled Cheese and decided to stick with guvcview.

But I use my cam for a lot of work related activities. I'd like to identify what could be the problem with Cheese, just in case I have further issues with supported software that should appear to be working.

---

### Post by newb85 on 2012-10-18
Did you check to see if your webcam could be selected as the device under Cheese preferences?

---

### Post by Gnawnsense on 2012-10-18
> **newb85 said:**
> Did you check to see if your webcam could be selected as the device under Cheese preferences?

I wasn't able to. When I open up Cheese, the canvas area that would show my cam picture is a black screen, and all the options below are gray'd out. The options at the top of the program are also are gray'd out, except the help screen and the close button.

I just assumed it was acting like there was no detected cam hardware connected to my computer, thus not even letting me get to the preferences dialogue. That's where most of my confusion comes from.

When I fire up guvcview, it recognizes it from the get-go. It's cool if Cheese won't work, but I've been reading most recent Logitech cams (mine included) should work with relative ease on my current system.

---

### Post by newb85 on 2012-10-19
Your camera's not being recognized shouldn't prevent you from going to Edit>Preferences.  Perhaps reinstalling would help?

---

### Post by Gnawnsense on 2012-10-19
> **newb85 said:**
> Your camera's not being recognized shouldn't prevent you from going to Edit>Preferences.  Perhaps reinstalling would help?

That was my assumption, as well. But sure enough, every option (literally) except to close the program and the help menu are gray'd out. Definitely cannot click on preferences as it's included in the gray'd out area.

I uninstalled and reinstalled and still had the same problem, as well.

---

### Post by newb85 on 2012-10-19
Seems this is a bug that has already been reported.  If you haven't already, you should mark it as affecting you.

[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930671]("https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930671")

---

### Post by Gnawnsense on 2012-10-20
> **newb85 said:**
> Seems this is a bug that has already been reported.  If you haven't already, you should mark it as affecting you.

[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930671]("https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930671")

Good find. I should probably get familiar with Launchpad and the way bugs are reported.

Will definitely chime in and mark it as affecting me.

Once again, thanks for the assistance!

---

