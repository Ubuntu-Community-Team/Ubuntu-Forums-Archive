---
title: "HOWTO: Composite and GLX"
date: 2005-01-16
forum: Outdated Tutorials &amp; Tips
---

### Post by jetta92 on 2005-01-16
add this line to /etc/X11/xorg.conf under your video card options and you will be able to have glxgears work again along with OpenGl games and apps...

Option      "AllowGLXWithComposite" "true"   

If your using an ATI card add :

Option      "backingstore" "true"

It is used to enable the server's support for backing store, a mechanism by which pixel data for occluded window regions is remembered by the server thereby alleviating the need to send expose events to X clients when the data needs to be redisplayed.       

that also works for all cards and seems to draw windows faster and smoother....

I know this works with nvidia geforce 4 mx440 but your mileage may vary ...

have fun

---

### Post by oddabe19 on 2005-01-17
[QUOTE=jetta92]add this line to /etc/X11/xorg.conf under your video card options and you will be able to have glxgears work again along with OpenGl games and apps...

Option      "AllowGLXWithComposite" "true"   

If your using an ATI card add :

Option      "backingstore" "true"

It is used to enable the server's support for backing store, a mechanism by which pixel data for occluded window regions is remembered by the server thereby alleviating the need to send expose events to X clients when the data needs to be redisplayed.       

that also works for all cards and seems to draw windows faster and smoother....

I know this works with nvidia geforce 4 mx440 but you mileage may vary ...

have fun[/QUOTE]
 also

Option "RenderAccel" "true"

should be there too for nvidia

---

### Post by jetta92 on 2005-01-17
Yeah I didn't post that because I thought that one was kinda obvious because It's all over the forums and probably assumed most people knew that one but hey well If you don't know then now ya do ....lol :-#

---

### Post by oddabe19 on 2005-01-17
[QUOTE=jetta92]Yeah I didn't post that because I thought that one was kinda obvious because It's all over the forums and probably assumed most people knew that one but hey well If you don't know then now ya do ....lol :-#[/QUOTE]
 FYI: a how-to should consist of all steps... please don't leave one out... it's really frustrating to people like my roomate who are on the fringe of changing to linux, but find documentation that skips steps.

Just a friendly reminder :-)

---

### Post by jetta92 on 2005-01-17
I wrote a HOWTO for enabling glx to working properly with Composite because many people had the problem I didn't write a HOWTO for Composite, or else I would have included all steps..... The purpose was to tell people how to have composite and glx/opengl play nice again NOT to tell them how to configure Composite.... If you'd like I can write one because It seems noone has but then again if I'm gonna get flamed I'll just  not bother wasting my time ..... 

thanx

---

### Post by Rotarychainsaw on 2005-01-17
What if I still cant use some OpenGl stuff? Glxgears seems to work, but any of the OGL screensavers or That 3d pool game crash X.

---

### Post by jetta92 on 2005-01-17
What video card are you using ...... If it's an nvidia, and as you'll see in one of the above posts you should add...

Option   "RenderAccel" "true" 
 
in your video card section and that may help but if not, then it is either an issue with metacity or just the plain fact that Composite is still very buggy and not quite ready .... You may want to look into compiling Metacity and disabling RENDER in the config,  that seems to have worked for a few but I do know that I have heard claims that there are problems with Ubuntu and Metacity but I could be wrong ....

---

### Post by theh0g on 2005-03-08
Same here, whatever I do, screensaver crashes X if I use xcompmgr. Weird.

---

### Post by shimon on 2005-03-23
Move this to the Hoary section

---

### Post by kuleali on 2005-04-12
thak's this really helped

---

