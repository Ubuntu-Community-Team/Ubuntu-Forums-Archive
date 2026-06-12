---
title: "Dolphin problems"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by bbboB on 2008-05-12
I recently converted my aging laptop over to Xubuntu 8.04, since I can't run Ubuntu 8.04 on it.
One disappointment I received was that Thunar did not have the ability to browse network folders in the same way that Nautilus does.  
After searching the boards for sometime, I found Dolphin was recommended as having network connectivity and also being light on the system resrouces.  I installed it into my XFCE environment using Synaptic.
Unfortunately, Dolphin won't find the network and, in fact, most all the bookmarks in Dolphin return a "malformed URL" error message when I click them.
I have thus far tried installing Konqueror...this did not solve the problem, even though some have had success with it.
Through threads on the boards, I've gotten ownership of the XML files for the bookmarks and can now save, but the problem still exists.
So, 
1)is this a known bug with Dolphin (meaning it doesn't work like Nautilus;
2)the program won't work in my environment;
3)do I need to install something else
4)Or can someone point me to where I can find the commands necessary to make the bookmarks find my network.


Thanks!

---

### Post by ugm6hr on 2008-05-12
2 possibly better (or easier) options:
[http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131)

I don't browse networks often, so used pyneiborhood.  See the link in my signature - Easy Windows file sharing.

---

### Post by utUtu on 2008-05-12
> **bbboB said:**
> I recently converted my aging laptop over to Xubuntu 8.04, since I can't run Ubuntu 8.04 on it.
One disappointment I received was that Thunar did not have the ability to browse network folders in the same way that Nautilus does.  
After searching the boards for sometime, I found Dolphin was recommended as having network connectivity and also being light on the system resrouces.  I installed it into my XFCE environment using Synaptic.
Unfortunately, Dolphin won't find the network and, in fact, most all the bookmarks in Dolphin return a "malformed URL" error message when I click them.
I have thus far tried installing Konqueror...this did not solve the problem, even though some have had success with it.
Through threads on the boards, I've gotten ownership of the XML files for the bookmarks and can now save, but the problem still exists.
So, 
1)is this a known bug with Dolphin (meaning it doesn't work like Nautilus;
2)the program won't work in my environment;
3)do I need to install something else
4)Or can someone point me to where I can find the commands necessary to make the bookmarks find my network.


Thanks!

Dolphin and Konqueror are KDE apps so they would not work as good in your XFCE as in KDE.

---

### Post by kuja on 2008-05-12
> **bbboB said:**
> I recently converted my aging laptop over to Xubuntu 8.04, since I can't run Ubuntu 8.04 on it.
One disappointment I received was that Thunar did not have the ability to browse network folders in the same way that Nautilus does.  
After searching the boards for sometime, I found Dolphin was recommended as having network connectivity and also being light on the system resrouces.  I installed it into my XFCE environment using Synaptic.
Unfortunately, Dolphin won't find the network and, in fact, most all the bookmarks in Dolphin return a "malformed URL" error message when I click them.
I have thus far tried installing Konqueror...this did not solve the problem, even though some have had success with it.
Through threads on the boards, I've gotten ownership of the XML files for the bookmarks and can now save, but the problem still exists.
So, 
1)is this a known bug with Dolphin (meaning it doesn't work like Nautilus;
2)the program won't work in my environment;
3)do I need to install something else
4)Or can someone point me to where I can find the commands necessary to make the bookmarks find my network.


Thanks!

Try installing dolphin-kde4. resource-wise it's similar, but it has more functionality. If it JustWorks then it should be a suitable alternative to the KDE3 one.

---

### Post by bbboB on 2008-05-14
Thanks for all the replies and I wish I could say that any single solution worked, but that is not the case.

Tried the dolphin kde-4 first and, while pretty, can't find a network with a flashlight and a map.

Looked into the pyneighborhood, but I've never been able to get my head around how to configure Samba and can't seem to find a reference as to how to configure it on the boards, so that didn't work out.

What I've ended up with, for the moment, is a hybrid configuration using Nautilus as a second file manager, but allowing Xfce to manage the desktop.  This gives me the needed network connection with the least amount of fuss.

Far as I'm concerned, Dolphin doesn't work in an Xubuntu install and, if anyone stumbles across this thread, it won't solve the problems caused by the lack of network support in Thunar.

---

