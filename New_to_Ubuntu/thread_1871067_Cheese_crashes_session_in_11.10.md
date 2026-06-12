---
title: "Cheese crashes session in 11.10"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by oregonbob on 2011-10-28
Since installing 11.10 the Cheese program will not run and rapidly uses all computer resources bringing the system to a standstill. Within seconds of starting the Cheese program my CPU usage goes up to 100% and memory usage builds until it uses all available memory. The problem is not my webcam (logitech 9000) because it works perfectly in Google video chat.

Any ideas?

---

### Post by dargaud on 2011-10-28
I just tried cheese on the same camera. It worked fine, although the CPU increased quite a bit (but not to 100%). Don't know what to say here. Test it with some other webcam apps. Also try to figure out which driver the camera uses, maybe the kernel picked the wrong one...

---

### Post by khelben1979 on 2011-10-28
If it's a software problem and you want to experiment a little, you got different versions for download on their official webpage: [http://projects.gnome.org/cheese/](http://projects.gnome.org/cheese/)

Maybe it could be worth a try? Also, make a note that the Cheese software relies on system libraries which also needs to be up to date, so you can have a look at the [GStreamer]("http://en.wikipedia.org/wiki/Gstreamer") in Ubuntu Software Center to check which version you got.

I've had some problems with the Cheese software myself using older versions, and the freeze problem can go away by itself after just killing the application and restart it, that is if the bug behaves the same way...

---

### Post by oregonbob on 2011-10-29
Just another experience with Ubuntu: I was running cheese 3.2 so I d/l and compiled 3.3. Before I did a 'make install' I wanted to remove the old cheese. When I used Ubuntu Software Center to remove cheese it told me it would also remove gnome-shell and gave me no other choice. LOL, so the whole Gnome system is tied to...cheese.

I am seriously considering downgrading all the way to 10.04 for LTS and something not so outrageously buggy as is 11.10. I can't believe this release of Ubuntu.

---

### Post by khelben1979 on 2011-10-29
> **oregonbob said:**
> Just another experience with Ubuntu: I was running cheese 3.2 so I d/l and compiled 3.3. Before I did a 'make install' I wanted to remove the old cheese. When I used Ubuntu Software Center to remove cheese it told me it would also remove gnome-shell and gave me no other choice. LOL, so the whole Gnome system is tied to...cheese.

Hmm.. but it should not be a problem if you choose to rename the binary of the old cheese application in let say /usr/bin/cheese to /usr/bin/cheese.old letting the new one taking it's place by the make install procedure, right?

Any way, the reason why the system wants to remove the whole Gnome system if you remove Cheese would be because of dependencies, but it shouldn't stop you from doing it..

---

### Post by oregonbob on 2011-10-29
I renamed the original Cheese and installed the new compiled version. It produced the same problem. After that I went looking for other webcam apps. I installed Camorama and amazingly it worked fine. So it is definitely a cheesy problem with Cheese.

BTW: Yes it would allow me to remove cheese in Ubuntu Software manager, but who would want to if it also removes Gnome shell? That is ridiculous and wrong to assert an entire window system like Gnome is dependent on one little app. It's just one more broken things on 11.10 along with a very long list.

---

### Post by khelben1979 on 2011-10-29
> **oregonbob said:**
> I renamed the original Cheese and installed the new compiled version. It produced the same problem. After that I went looking for other webcam apps. I installed Camorama and amazingly it worked fine. So it is definitely a cheesy problem with Cheese.

Sounds positive.

> **oregonbob said:**
> BTW: Yes it would allow me to remove cheese in Ubuntu Software manager, but who would want to if it also removes Gnome shell? That is ridiculous and wrong to assert an entire window system like Gnome is dependent on one little app. It's just one more broken things on 11.10 along with a very long list.

Since it's built with Debian testing as a base, yes it got bugs. To actually remove the cheese application, you can actually do a force uninstall without other software packages affected.. but you haveto do it manually and not just let the Ubuntu Software Center itself handle it. That means you need to _mark all packages which it selects for uninstall as hold_ so they will not get affected. I tried it myself, and it works.

Also simply removing the binary for cheese in /usr/bin/ works too, nothing from the Ubuntu system will be able to use it once it's done.

I think for the regular Ubuntu user, he or she should not haveto do these things and everything is just supposed to work, but since it's based on Debian testing, that feels a bit too optimistic. Going for an Ubuntu LTS release would be a better idea, I think, if you feel really annoyed about the bugs which plagues Ubuntu 11.10.

---

