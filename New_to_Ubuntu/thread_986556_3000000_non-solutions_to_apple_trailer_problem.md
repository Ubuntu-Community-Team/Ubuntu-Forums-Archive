---
title: "3000000 non-solutions to apple trailer problem"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Knacker on 2008-11-18
Hi, 
I'm trying to get quick time movies at apple trailer to play with fire fox in hardy. I have been installing, uninstalling packages for hours, days, months and every time I get to the stage I'm at now (where I'm screaming and hitting things), I end up giving up.
How is it that there are hundreds of different guides to how to make apple trailers work and none of them work? 
I mean, isn't there just a problem for which there is a solution?

I've tried: VLC plugin, Mplayer plugin, totem plugin gecko plugin, quick time 7 plug-in...ah! 
I've tried: editing the pluginreg.dat file (6.0 / 7.0 fix...)
I've tried gecko, i've tried different combination of these 
I've tried installing qt through wine (installation errors) 
I've tried erasing every codec on my computer and starting from scratch
..Nothing works. 
I've read about 15 guides on this and i've tried it all. 
Please can someone just tell me the thing that fixes this actually. 

The problem: when i try to play quick time videos, i get a "get the latest quicktime" or "no video" or FF crashes...depending on which combination of the above "solutions" I use. If I even knew which one of the above errors was better than the others! 

How can this seriously be this messed up? Is it just me?
Grateful for any help. :)

---

### Post by andrew.46 on 2008-11-19
Hi,

I am not on my Ubuntu partition at the moment but I attach a screenshot of one of the small apple trailers playing happily with firefox 2 and the MPlayer plugin. So it can be done :-)

  Andrew

---

### Post by billgoldberg on 2008-11-19
> **Knacker said:**
> Hi, 
I'm trying to get quick time movies at apple trailer to play with fire fox in hardy. I have been installing, uninstalling packages for hours, days, months and every time I get to the stage I'm at now (where I'm screaming and hitting things), I end up giving up.
How is it that there are hundreds of different guides to how to make apple trailers work and none of them work? 
I mean, isn't there just a problem for which there is a solution?

I've tried: VLC plugin, Mplayer plugin, totem plugin gecko plugin, quick time 7 plug-in...ah! 
I've tried: editing the pluginreg.dat file (6.0 / 7.0 fix...)
I've tried gecko, i've tried different combination of these 
I've tried installing qt through wine (installation errors) 
I've tried erasing every codec on my computer and starting from scratch
..Nothing works. 
I've read about 15 guides on this and i've tried it all. 
Please can someone just tell me the thing that fixes this actually. 

The problem: when i try to play quick time videos, i get a "get the latest quicktime" or "no video" or FF crashes...depending on which combination of the above "solutions" I use. If I even knew which one of the above errors was better than the others! 

How can this seriously be this messed up? Is it just me?
Grateful for any help. :)

I'll start by saying that nobody like quicktime movies.

There are hundreds of other sites that offer as much or more trailers in decent formats.

I can play quicktime videos, don't know about the apple website, I'm not on Ubuntu atm.

Follow the guide in my sig called "codecs in ubuntu" and see if it works.

---

### Post by lakersforce on 2008-11-19
Again, I advice to install the restricted Gstreamer* plugins (all of them).

---

### Post by philinux on 2008-11-19
> **Knacker said:**
> Hi, 
I'm trying to get quick time movies at apple trailer to play with fire fox in hardy. I have been installing, uninstalling packages for hours, days, months and every time I get to the stage I'm at now (where I'm screaming and hitting things), I end up giving up.
How is it that there are hundreds of different guides to how to make apple trailers work and none of them work? 
I mean, isn't there just a problem for which there is a solution?

I've tried: VLC plugin, Mplayer plugin, totem plugin gecko plugin, quick time 7 plug-in...ah! 
I've tried: editing the pluginreg.dat file (6.0 / 7.0 fix...)
I've tried gecko, i've tried different combination of these 
I've tried installing qt through wine (installation errors) 
I've tried erasing every codec on my computer and starting from scratch
..Nothing works. 
I've read about 15 guides on this and i've tried it all. 
Please can someone just tell me the thing that fixes this actually. 

The problem: when i try to play quick time videos, i get a "get the latest quicktime" or "no video" or FF crashes...depending on which combination of the above "solutions" I use. If I even knew which one of the above errors was better than the others! 

How can this seriously be this messed up? Is it just me?
Grateful for any help. :)

Ok plays here on default install, thats totem's plugin, but, with ubuntu-restricted-extras installed.
Post what you got in ```
about:plugins
``` That goes in FF address bar.

---

