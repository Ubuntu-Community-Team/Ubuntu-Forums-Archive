---
title: "flash help"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by cman2227 on 2008-04-23
I just downloaded the newest version of flash and all the videos are slow and jumpy. I tried restarting,and reinstalling Firefox. I download it through the tar.gz file from flash. All help is appreciated.

---

### Post by spiderbatdad on 2008-04-23
give seamonkey a try...in synaptic. Install iceape packages and seamonkey packages, then remove iceape packages. No flash problems here.

---

### Post by amazingtaters on 2008-04-23
The choppyness is a known issue with the newest version of flash for linux. Just be glad, the release before it crashed FF3b5 all the time in Hardy.

---

### Post by cman2227 on 2008-04-23
I can't find seamonkey in synaptic how would I do this? I searched it and nothing was found. Also is there a way just to download the old version of flash?

---

### Post by spiderbatdad on 2008-04-23
Hmm. I'm running Hardy. IDK if its in the Gutsy repos...I would have assumed it was...anyway: [http://www.seamonkey-project.org/releases/](http://www.seamonkey-project.org/releases/)

---

### Post by proalan on 2008-04-23
Might be worth installing the latest win32codecs possibly. Flash videos are usually standard mpeg/wmv encoded videos inside a flash container.

---

### Post by cman2227 on 2008-04-23
How do I download the codecs?

---

### Post by cman2227 on 2008-05-16
anybody?

---

### Post by Bubba64 on 2008-05-16
> **proalan said:**
> Might be worth installing the latest win32codecs possibly. Flash videos are usually standard mpeg/wmv encoded videos inside a flash container.

If you have the right repositories open it should be in synaptic, I searched with win32 and found it. You may need medibuntu added to your etc list.
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)
I would go to add remove and install Ubuntu restricted extras and the gstreamer stuff this will save you a lot of extra work.

---

### Post by cman2227 on 2008-05-18
I'm sorry but I have no idea what you are talking about. Could you put it a little more simple/ in more clear English. again sorry.

---

### Post by gandaran on 2008-05-18
cman2227
you do need to install codecs, but the codecs are for playing media files not flash, why didn't you install the flash from the repositories, the flashplugin-nonfree (adobe flash) package, you'll find it in synaptic, you only have to check mark for install and click apply, if you don't find it there, make sure all the repositories are enabled and click the reload/refresh button. now about the flash you installed, are you sure it's the latest version 9.0.124? type **about: plugins** (without spaces) in firefox navigator bar, it will show the flash version installed,and post the results back here.

---

### Post by cman2227 on 2008-06-07
shockwave flash is 8.0 r99(I think this one is gnash) and another shockwave says 9.0 r124 can't find anything else.

---

### Post by cman2227 on 2008-06-24
anybody know what to do?

---

### Post by avtolle on 2008-06-24
Remove gnash and its plugins. Go to System>>Administration>>Synaptic Package Manager, and after logging in with your password, search for gnash in the search function. If gnash and its plugin show as being installed, click on each and select Mark for Complete Removal. Then, after that, click on Apply. This should remove gnash and its plugin, removing the conflict between it and the other flash application that is installed.

---

### Post by cman2227 on 2008-06-24
So I did what you said and removed every thing installed but their is still a problem.

---

### Post by zieglerj on 2008-06-25
you don't want to try seamonkey for a solution. I have and I love it but the flash is messed up in it too. 
I'll be back soon... hopefully with a solution

---

### Post by cman2227 on 2008-07-16
alright then.

---

### Post by cman2227 on 2008-07-21
any body have any help?

---

