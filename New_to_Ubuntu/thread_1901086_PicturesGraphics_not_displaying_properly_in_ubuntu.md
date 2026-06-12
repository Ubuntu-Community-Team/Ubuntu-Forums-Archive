---
title: "Pictures/Graphics not displaying properly in ubuntu 11.10"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by funkywimble on 2011-12-27
I recently bought a new laptop, I was previously using Ubuntu 10.10 which I absolutely loved, but unfortunately I was unable to get my built in wireless to work with the old ubuntu so I upgraded to 11.10 and it now works fine. Unfortunately I've found that pictures aren't quite displaying properly. I'm a total n00b so I don't know why this is but it's as if the computer is missing some colours, pictures which would usually show a smooth gradient are showing visible lines between the colours. 

I have an intel HD graphics card and there is a driver in use, not sure if I need to change this to get this working? My husband only uses the computer for the internet and so it's not an issue for him but as I use darktable & gimp software for image editing and manipulation, this is really important for me. This wasn't an issue in 10.10.

The only thing I can think which is relevant is when I was trying out the liveCD there was an error message whilst it was booting up which said something like, "wmi interface unsupported".

Not sure if a screenshot will help but I have attached one of my desktop. As you can see where the colours would usually blend in with one another you can almost see the separation of the different shades of blue.

If you need any further information, please just ask.

Thanks,
M (link to screenshot below)

[http://i40.tinypic.com/21jaidf.png](http://i40.tinypic.com/21jaidf.png)

---

### Post by jerrrys on 2011-12-29
I see nothing wrong with your screenshot, which would indicate that you may need a driver or driver settings are wrong.  What kind of video do you have?  Open a terminal and copy and paste:
[FONT=monospace]
[/FONT]lspci | grep VGA

---

### Post by JamButty on 2011-12-29
The coarse color gradients looks like a low resolution/bad compression issue, but I can't tell whether this is an issue on your machine or one with the default resolution on your screen grab. Do high res images opened in GIMP also look this way?

---

### Post by dFlyer on 2011-12-29
If your using ufraw, you will need to following these instructions to get it to work with 11.10.

[https://bugs.launchpad.net/ubuntu/+source/gnome-raw-thumbnailer/+bug/852923](https://bugs.launchpad.net/ubuntu/+source/gnome-raw-thumbnailer/+bug/852923)

---

### Post by wildmanne39 on 2011-12-29
Hi, the > wmi interface unsupportedmessage would not cause that, you said you are using intel graphics it is possible if your computer is old  your card may not be supported in this version of ubuntu as well, posting the output of the command jerrrys asked for will tell us exactly the card you have.
Thanks

---

### Post by Henkdroid on 2011-12-29
It may be a colour depth issue. Please follow the instructions  [here]("http://superuser.com/questions/173123/how-to-change-the-color-depth-in-ubuntu-10-04")

---

