---
title: "Flash Video, Google Analytics and Street View"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by wtjmiller on 2008-08-04
Hi 

I recently used wabi to install a test version of Ubuntu. There are a few things I really like about it but there are a lot of things that are a real barriers to my adopting it as my only desktop OS. Maybe there is a reason why things don't seem to be working for me. One of the most frustrating problems is viewing Google Analytics and street view. While I can view youtube video they always display (as does any flash content) with a big gray start icon. I really don't like that and I'm not sure why it's happening. When I click the icon for the Google Analytics charts or the street map view, nothing happens. The charts will just sit there with the moving wait icon revolving forever. 

I've looked through the forum and followed most of the instructions for getting flash to work. Here is what I've done 

1. I trying to view Flash in FireFox 3.01 
2. Tools>Add-ons>plugins shows I have Shockwave Flash 9.0 r100 plugin
3. I uninstalled this plugin and reinstalled it using Synaptic.
4. I disabled and unistalled the Gnash flash player using Synaptic 
5. I disable the Totem web browser plugin that includes a flash video player  
6. I have an Intel Pentium 4 CPU running at 2.26 GHz 
7. the only extension I using are ScribeFire, Print Preview and Dom Inspector. I disable the Ubuntu FireFox Extension. 
8. Java, Javascript and auto image download are enabled.
9. In the applications preferences Shockwave Flash is the application for shockwave flash files.  
10. cookies are accepted. 

Thanks in advance for any help or explanation.

I just installed Opera. Flash videos, Google Analytics and street view now work flawlessly.

---

### Post by AdamWood on 2008-08-04
Have you tried removing and reinstalling the flashplugin-nonfree AFTER you removed Gnash?

Gnash causes a few problems and even removing it doesn't fix all of them until you try to force the nonfree version of flash to install again.

I'm still having some problems with FireFox 3.01 and the flash plugin but Google analytics works perfectly and youtube only fails rarely and a quick restart of the browser fixes that.

---

