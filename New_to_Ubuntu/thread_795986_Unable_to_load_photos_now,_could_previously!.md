---
title: "Unable to load photos now, could previously!"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Redptc on 2008-05-16
I can't download photos from my camera anymore! I have photos on file that were previously loaded using this camera but it is not now possible to download my recent pictures.

A camera is detected and when I click on ***Import Photos*** my camera is specifically detected, Kodak cx4310, but I am told.. 'An error occured in the io-library('bad parametrs'): could not find USB device (vendor 0x40d, product 0x560). Make sure this device is connected to the computer.

The 'device' works on the Windows side so it is connected. 

I thought it may need a driver but I am allowed to select from the 'catalog' and this doesn't change things. I get the same error message.

Does anybody know a solution or work-around?

---

### Post by Falcorian on 2008-05-16
What's the command in your:

System > Preferences > Removable Drives and Media > Cameras 

They switched the default program from gthumb to F-Spot with Hardy, so maybe that's causing problems. You might give gthumb a try:

```

gnome-volume-manager-gthumb %h

```

You'll have to install gthumb though.

```

sudo apt-get install gthumb

```

Hope that helps... Otherwise I'm stumpted.

---

### Post by Redptc on 2008-05-16
Many thanks for your help! That is the 'command' loaded in removable drives etc.."gnome-volume-manager-gthumb %h"

I have both gThumb and F-spot loaded. I have also loaded gtkam to no effect.

You may be right in that the 'upgrade' or change may be to blame. I will explore that possibility except I have no idea where to start!:confused:

---

### Post by Superkoop on 2008-05-16
Are you using a differant Kernal, other than the default Hardy one? 
Because I had the same problem in Gutsy when I installed a new Kernal, and the only way I could upload photos was to boot into an older Kernal. 

So your problem is probably linked to that problem, somehow.

---

### Post by Falcorian on 2008-05-16
> **Redptc said:**
> Many thanks for your help! That is the 'command' loaded in removable drives etc.."gnome-volume-manager-gthumb %h"

I have both gThumb and F-spot loaded. I have also loaded gtkam to no effect.

You may be right in that the 'upgrade' or change may be to blame. I will explore that possibility except I have no idea where to start!:confused:
Hmm, the only thing I would think to do in your case would be to try fspot instead... But I don't know the command for that. You can probably load up fspot and try manually. I had a problem with uploads, but mine was an gthumb was not installed, but was still trying to import issue. ;)

Best of luck though! Sorry I couldn't be of more help!

---

### Post by Redptc on 2008-05-16
That seems to be it Supercoop, I had to use an early Hardy kernel to offset a 'bug' and haven't installed the latest. When I used the previous kernel I found I was able to download photos OK.

Have you solved your problem by switching to the default?

I guess I had better do the upgrade!

---

