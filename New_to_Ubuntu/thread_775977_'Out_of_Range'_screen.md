---
title: "'Out of Range' screen"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by elend_heiler on 2008-04-30
halooo all.... :)

i've a problem,,
first time i installed ubuntu..there is no problem..
but..after update the system, enable the graphic card
n then i restart the computer...
appear this message box like this..

" out of range, max 1024 x 768 " 

what should i do???
is there a problem with my monitor?? :confused:

thanks before!! :KS

---

### Post by Six_Digits on 2008-04-30
Have you done any searching on this issue? I've answered a very similar question, minus the text box...
It is not your monitor, your xorg.conf needs to be set-up I'm sure. Could you possibly give us some info? Graphics card, and read-out of your xorg.conf?

---

### Post by elend_heiler on 2008-04-30
i've searching..but i don't too understand... :(

hmmm sorry..
but,,what is 'xorg.conf'?? is this some of a command..??
oyeah...my graphic card is GeForece 8500GT...

thanks before!! :KS

---

### Post by Six_Digits on 2008-04-30
Try installing [Envy]("http://albertomilone.com/nvidia_scripts1.html") first, if you haven't yet installed any drivers for your video card. After following through with that and still getting the error, try [this]("http://ubuntuforums.org/showthread.php?t=156243&highlight=edit+xorg").

---

### Post by elend_heiler on 2008-04-30
but,,how can i install it??
i even can't go to my ubuntu...when i go to Login menu...
the message box appear...with black on the background..

or,,is there i can do in the recovery mode??? :confused:

thanks before!! :KS

---

### Post by Pethegreat on 2008-04-30
Can you get into a failsafe terminal? It should be listed in your grub. For me the esc key brings up grub when I boot. It is listed as "failsafe mode"

Once you get into the terminal and enter your password type in this in.

```
sudo dpkg-reconfigure xserver-xorg
```
sudo is super user do

Once you run this it will lead you through a series of screen to get everything set up properly.

---

### Post by Six_Digits on 2008-04-30
I was avoiding that, as he seems quite new...

---

