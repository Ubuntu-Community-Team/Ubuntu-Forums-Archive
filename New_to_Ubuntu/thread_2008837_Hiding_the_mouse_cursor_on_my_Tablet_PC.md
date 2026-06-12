---
title: "Hiding the mouse cursor on my Tablet PC"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by FragMonkey90 on 2012-06-23
I wish to hide my mouse cursor when using my stylus on my tablet PC. I find the mouse cursor itself to be very distracting.

I have researched solutions for this, but many of them require heavy editing of some code file somewhere and not much explanation is provided how to even go about doing that.

Here is an apparent working solution I found:
[http://www.linuxquestions.org/questions/linux-general-1/manually-setting-x-cursor-or-theme-doesnt-work-no-errors-700965/](http://www.linuxquestions.org/questions/linux-general-1/manually-setting-x-cursor-or-theme-doesnt-work-no-errors-700965/)

The fix the user posts references many applications and files and it is not the easiest to follow for me, as I literally just picked up a linux distro for the first time and haven't wrapped my head around the file system yet.

What solutions are there?

---

### Post by FragMonkey90 on 2012-06-23
I would imagine by now such a thing would exist for ubuntu. Is there a way to change my mouse pointer theme to transparent? Haven't had much luck, my googlefu fails me

---

### Post by Stunts on 2012-06-23
Hi there,
Yes, what you suggest would be a nice workaround - getting an invisible cursor theme.
However I don't think one exists.
But that shouldn't be a problem. Here's what I would do:
1. Get an icon theme that looks complete (such as this one) [http://gnome-look.org/content/show.php/DMZ-Red?content=140570](http://gnome-look.org/content/show.php/DMZ-Red?content=140570)

2. Extract the archive and place it under ~/.icons
3. Replace all the files that are not links with an empty .png file (as in a 48x48 transparent image)
4. Enjoy your invisible cursor.

Let us know how it worked out for you.

---

### Post by FragMonkey90 on 2012-06-23
Alright that method did the trick.

I couldn't simply make a transparent .png to replace the files with though. I had to get a GIMP plugin that opens X Cursor files, and I edited the relevant files and turned them into transparencies, which did the trick.

---

### Post by Stunts on 2012-06-24
I'm glad I could be of assistance.
And thank you for sharing that gimp plugin information. I really didn't know that.
Anyway, you should mark the thread as [solved] in case someone else stumbles upon this issue.
Enjoy your new invisible cursors!

---

