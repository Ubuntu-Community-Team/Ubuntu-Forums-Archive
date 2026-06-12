---
title: "Possible to change resolution at CLI in Hardy?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by ajifans on 2008-05-06
Having issues with Hardy defaulting to a resolution that is not supported by my monitor giving me an 'Out of Range' error message.

I used to be able to either edit the xorg.conf file directly or use dpkg-reconfigure xserver-xorg.

However the meaningful syntax in xorg.conf has been replaced by vague waffle, and the dpkg-reconfigure xerver-xorg is now pretty useless giving only keyboard options.

Is there another option?  Having to borrow someone else's monitor so I can log in and set the correct resolution using the GUI is a bit of a hassle.

Many thanks

---

### Post by 67GTA on 2008-05-06
The short answer is no. The devs didn't see the need for it. I think it was pretty stupid myself. The only way in your case would be to boot into recovery mode and use nano to edit xorg.conf. You could put a modeline in the monitor section.

---

### Post by prshah on 2008-05-06
> **ajifans said:**
> 
I used to be able to either edit the xorg.conf file directly or use dpkg-reconfigure xserver-xorg.


If you have your old xorg.conf file, you can just copy and paste the appropriate sections. Though the (new) xorg.conf file is brutally trimmed, if settings are present, they are not ignored. Just pasting your old sections regarding resolutions and options into it will work fine.

---

### Post by bodhi.zazen on 2008-05-06
You can *try* to copy-paste a previous xorg.conf, but it does not always work.

Additional options include :

```
sudo xfix
```

and 

```
gksu displayconfig-gtk
```

---

### Post by prshah on 2008-05-07
> **bodhi.zazen said:**
> You can *try* to copy-paste a previous xorg.conf, but it does not always work.


Not the entire xconf, just the sections relevant to resolution.

---

### Post by Faud on 2008-05-07
```

gksu displayconfig-gtk

```
Does not work to my knowdledge
and neither does
```

sudo xfix

```
but that is just my personal experience

---

### Post by stream303 on 2008-05-07
No xfix on my Hardy install..

I wonder if anyone has been successful using xrandr, ie

```
xrandr -q
then
xrandr -s 1680x1050
```

I'm not sure if there is a way to force xrandr to use resolutions not already available...

---

### Post by bodhi.zazen on 2008-05-07
gksu displayconfig-gtk works for some people, others no, but it better the being stuck.

Same with xfix. xfix is an option when you boot to recovery mode as well, but in my experience with xfix it is similar to dpkg-reconfigure ...

xrandr may help, but the problem with others is it may be that system fonts and fonts in applications are not resized, so you get left with very large buttons / fonts in applications.

Manually editing xorg.conf may help, but it may break X as well in that some sections of xorg do not work the same. It is easy to fix with sudo dpkg-reconfigure xserver-xorg
Use caution with advising a new user to manually edit xorg.conf and be prepaired for the possibility of breaking X.


All these methods are "work arounds" and IMO it is more difficult then ever to customize xorg. I think this is an issue with xorg and for example Fedora preview 9 there is no xorg.conf. This is great if it is working, but manually reconfiguring X is now much more difficult, IMO at least. At least with the old way it was *possible*. I think this will improve over time in that there will be less need to do so and if there is a need gui toola will emerge, such as nvidia-settings or the tools in Fedora.

---

### Post by Faud on 2008-05-16
bodhi.zazen I wanted to say thank you for continued support on this matter. I hope that the devs can come up with a solid work-around/solution. 
Thank you for your time spent on this thus far as we try and get ALL of our computers up to 8.04 :)

---

