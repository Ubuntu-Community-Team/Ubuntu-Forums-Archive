---
title: "brightness problem in lenovo z 570"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by himanshu3110 on 2012-04-06
i have installed ubuntu 11.04 in my lenovo z570 laptop.
but there is a problem the brightness always remain maximum.
the fn + arrow keys wont work.
PLEASE HELP

---

### Post by Redblade20XX on 2012-04-06
Hmmm what video driver you have installed?

- Red

---

### Post by himanshu3110 on 2012-04-06
i have just installed ubuntu and nothing else.
where should i find the video driver?

---

### Post by gordintoronto on 2012-04-06
Run Additional Drivers and see if it offers a video driver. I'm not sure anything will appear for your Intel Integrated HD Graphics 3000.

Or try this: open a Terminal, and enter this command:
xgamma -gamma .5
You can try different values than .5, to see what works for you.

---

### Post by kazztan0325 on 2012-04-07
I found the same problem has been asked here:

**"Unable to adjust screen brightness on Ideapad Z570"**
[http://askubuntu.com/questions/102287/unable-to-adjust-screen-brightness-on-ideapad-z570]("http://askubuntu.com/questions/102287/unable-to-adjust-screen-brightness-on-ideapad-z570")

And unfortunately no answer has been posted at present...

---

### Post by himanshu3110 on 2012-04-07
> **gordintoronto said:**
> Run Additional Drivers and see if it offers a video driver. I'm not sure anything will appear for your Intel Integrated HD Graphics 3000.

Or try this: open a Terminal, and enter this command:
xgamma -gamma .5
You can try different values than .5, to see what works for you.


i have this but it didnot work....what to do now??

---

### Post by himanshu3110 on 2012-04-07
> **gordintoronto said:**
> Run Additional Drivers and see if it offers a video driver. I'm not sure anything will appear for your Intel Integrated HD Graphics 3000.

Or try this: open a Terminal, and enter this command:
xgamma -gamma .5
You can try different values than .5, to see what works for you.


i have tried this but it didnot work....what to do now??

---

### Post by himanshu3110 on 2012-04-07
and where to get the additional drivers?

---

### Post by kazztan0325 on 2012-04-07
> **himanshu3110 said:**
> and where to get the additional drivers?

You would be able to open **"Hardware Drivers"** window as below:

Click *System > Administration > Hardware Drivers*

You will find Video Driver which is suitable for video chip on your machine if there would be any Video Driver which is needed to install on your machine.

---

### Post by himanshu3110 on 2012-04-08
i find the 'additional drivers' under 'hardware' and when i open it, it says..."no proprietary drivers are in use on this system"

---

### Post by himanshu3110 on 2012-04-08
i didnot find the path you have mentioned.

---

### Post by s1baker on 2012-04-08
Here is a link to a old post about this using Gnome. You may try to
set your ~/.xsessionrc file to different settings and see if
something works after restarting.

```
http://ubuntuforums.org/showthread.php?t=1283622
```

---

### Post by s1baker on 2012-04-08
also - be sure to make a backup of your original .xsessionrc file
before doing anything to it.

---

### Post by kazztan0325 on 2012-04-09
> **himanshu3110 said:**
> i didnot find the path you have mentioned.

I'm sorry I carelessly confused you.
I should have remembered Unity had already been adopted on 11.04.
I myself don't know why but "gnome menu bar" came into my mind at that time...

---

### Post by himanshu3110 on 2012-04-11
> **s1baker said:**
> Here is a link to a old post about this using Gnome. You may try to
set your ~/.xsessionrc file to different settings and see if
something works after restarting.

```
http://ubuntuforums.org/showthread.php?t=1283622
```


thanks alot ...:)
i m very happy...:) xgamma -gamma 0.6 works...
though i didnot find the [FONT=monospace] [/FONT] ~/.xsessionrc file ..and the gnome stuff which is in the link u have given is not working. i mean it shows me option to decrease or increase the brightness but there is no effect after moving the slider.

and also why i cant use fn+arrow(up/down) to change the brightness though i can control volume using fn+arrow(left/right)..???

---

### Post by s1baker on 2012-04-11
I don't have Ubuntu on a laptop, I am using a desktop, but I had this brightness problem when I first started using Ubuntu. I know other people with laptops have had this same problem also. I thought someone was going to write a script that would allow the rasing or lowering of the brightness, but I don't know where it is.

The .xsessionrc file should be in your home ~/ folder and it is 
hidden from view, thus the '.' in the name .xsessionrc, so to see if this file is in your folder, set the 'view' option on nautilus to show hidden files.
 The only thing that is in my .xsessionrc file is this:

```
xgamma -gamma 0.8
```
and 0.8 seems to work for me.

.xsessionrc will run these settings at boot up so that you don't
have to set them every time. If you don't have a .xsessionrc, do this in the terminal:
```
echo "xgamma -gamma .6" >> ~/.xsessionrc
```
your brightness will always be set at .6 upon bootup.

also you may want to do a search for 'xgamma' and check out some of the earlier posts about this.

---

### Post by himanshu3110 on 2012-04-17
i tried that echo command but now my brightness is fixed.
xgamma -gamma 0.5 has no effect. i cant decrease or  increase it again.

---

### Post by himanshu3110 on 2012-04-17
the screen flickers after executing this command and nothing changed.

---

### Post by kazztan0325 on 2012-04-18
Hi himanshu3110,

Have you ever tried **"Cairo Dock"**?

It has an applet called **"Screen Luminosity"**, and we can adjust gamma with the applet.
The applet "Screen Luminosity" works well in 11.10 on my "Lenovo ThinkPad X200s".

I'm not sure if it also would work well on your Z570, but I think you may try it if you are interested in.

**"cairo-dock"** is available from Ubuntu Repo, and there is an information about latest version of "cairo-dock" here:

**"Cairo-Dock 3.0 has been released!"**
[http://www.unixmen.com/cairo-dock-3-0-has-been-released/]("http://www.unixmen.com/cairo-dock-3-0-has-been-released/")

---

