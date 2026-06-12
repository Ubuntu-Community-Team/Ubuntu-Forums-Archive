---
title: "Programming Desktop App"
date: 2011-04-23
forum: Programming Talk
---

### Post by hero_bash on 2011-04-23
Hi guys. I'm planning on programming an app that would display random quotes(probably switches randomly per given time interval or something) and also display it on the background in the desktop.

So my question would be what would be the best way to do it. I'm not asking for the step-by-step for it, I'm willing to learn what needs to be but I'm at lost where to start so I'm looking for directions for seceific things I must learn. I know a bit of Python and C++ but haven't done much programming with ubuntu stuff.


Thanks

---

### Post by llanitedave on 2011-04-23
If it's not saving any new data, and acts just as a display applet, you might as well make it a toolbar widget or something similar.  I seem to recall those being done in Javascript, which would work fine for this purpose.

---

### Post by hero_bash on 2011-04-23
do you mean as an applet for the default ubuntu toolbars?

---

### Post by user333 on 2011-04-23
I just thought this might help you:

[http://developer.ubuntu.com/](http://developer.ubuntu.com/)

It's the official place to get started programming in Ubuntu.

---

### Post by StephenF on 2011-04-23
Specifically, the link below shows everything you'll need with respect to text to image conversion. You may want to polish the final result with ImageMagick. Setting the image as wallpaper is specific to your desktop environment.

[http://x11.gp2x.de/personal/google/](http://x11.gp2x.de/personal/google/)

---

### Post by hero_bash on 2011-04-23
I was actually thinking of more in the line of apps like desklets and the likes where the text would be in the background but not exactly the wallpaper itself. but I guess a text-to-image then setting it to wallpaper could work if nothing else.

---

### Post by cipherboy_loc on 2011-04-23
You can achieve the same effect by using Conky and Fortune. I think you can set an update interval in Conky, such that it will stay there for a select period. The thing that this will not be able to do is handle clicks if you want it to change on click. If nothing else, you can look into how conky displays text in the background.


Cipherboy

---

