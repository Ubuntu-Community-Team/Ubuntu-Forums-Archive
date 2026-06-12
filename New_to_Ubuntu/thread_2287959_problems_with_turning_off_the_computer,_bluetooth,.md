---
title: "problems with turning off the computer, bluetooth, skype"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by marta3 on 2015-07-23
Hi,
i'm quite new in Ubuntu (i've always used Windows before). I have the latest version 15.4. 
Lot of friends told me that Ubuntu in better better better a lot, but i still (after 5 mounths) can't see that "better".
Since i change into Ubuntu the computer doesn't turn off properly, well, doesn't turn off at all, but restart it every time, and it turns off only if i press the top button shortly after it has starting to restart.

And in addition to that, the bluetooth doesn't work and i can't install skype. (And i can't use Itunes, as i did)

I don't have many necessities with the computer, i just need it to write documents for uni, download music, surfing the net...
I don't know much about computers, but at this point of the thing i think: with windows before the computer turned off properly, i could skype, i could use the bluetooth...and i had no problems at all!
My friends told me that Ubuntu could give me only advantages, because i don't need the computer much but...where are the advantages? 

Thanks,
Marta

---

### Post by sgian on 2015-07-24
Several suggestions...
1.  Sometimes the LTS versions, like 14.04 and 12.04, are more stable than the regular releases and are supported for a longer time.
2.  Use amazon or google for your music.  Apple is very proprietary about it's digital rights and doesn't get along with linux as well.  If you have a lot of music already downloaded through itunes, you can save the music by making audio discs with itunes on Windows and then ripping them them back into mp3's in Ubuntu so they are digital again without DRM.  That's how I made the switch away from iTunes.
3.  There is a linux version of skype for Ubuntu 12.04 and 10.04.  Skype is now owned by Microsoft, so don't expect Microsoft to release Skype for newer versions of Ubuntu, because Microsoft does not like linux.  
4.  You can always dual boot computers so that they can run both in case you want both.

The main advantage of linux for me is that there are no significant viruses at large that will infect your computer.  Security is much better with linux and you are not likely to get hacked on linux unless you open yourself up to it somehow.  For almost everything there is a linux alternative, you just have to look for it.  For documents on linux, libreoffice will save files as word documents if you tell it to do so.  Surfing the net is much safer on linux than windows, even if you use Chrome like me.

---

### Post by Vladlenin5000 on 2015-07-24
Hi and welcome.

If you need (or think you need and can't see alternatives) Windows apps then use Windows.
I agree with your friends, Ubuntu (Linux) is better. But they forgot to tell you it ISN'T a "free clone" of Windows. It's an entirely different OS, with a history and *pedigree* completely different and independent of those of Windows (or MacOS).
Software made for one OS won't run in a different one.
That said, Skype can be installed and run in Ubuntu. There's a Linux version and, unlike the "negative felling" one gets from point 3 of the previous post, it preceded Microsoft's acquisition of Skype, but against all odds it got updated ONLY after Microsoft took over. The app was in a lousy state at the time and Microsoft actually improved it and kept releasing updates up to this day.
Installing Skype is as easy as going to System Settings > Software & Updates and activate the Partners repository. Then just do, in a terminal:
```
sudo apt-get update
sudo apt-get install skype
```
-or-
You can download and double-click the .deb file from Skype's website, thus installing it exactly the same way you would do in Windows. You do know how to install apps in Windows, don't you? And I suppose you know how the use Google search, don't you? Everything I said above takes less than 2 seconds to search...

Regarding iTunes, do you really need it? If you own iDevices then certainly you do; if not then you DEFINITELY don't. There are hundreds of players that run natively in Ubuntu.


Regarding other issues, we need a complete description of the hardware to understand where to start. Conflating everything in one thread is a very bad idea. I suggest you post your hardware specs in another thread and describe exactly what happening (unable to shutdown) and what hardware isn't recognized/don't work.

---

