---
title: "Ubuntu vs Kubuntu ??"
date: 2010-05-04
forum: Recurring Discussions
---

### Post by bigseb on 2010-05-04
I have both the Ubuntu and Kubuntu 10.04 discs and was browsing them extensively today. I was a bit disappointed with Ubuntu, it seemed very sparce program-wise(must admit I'm spoilt as I have been using the 9.10 Ultimate Edition which packed with lovely goodies). 

Kubuntu, which I see for the first time ever today, seems visually very different... surely there's more to it though. 

What is the difference between the two? Is Kubuntu made for a specific purpose?

---

### Post by Untitled_No4 on 2010-05-04
Both KDE and Gnome aimed mainly at the desktop user. Some people prefer Gnome, some people prefer KDE, some even like both. In essence, under the hood both are the same and you can install kubuntu-desktop on Ubuntu or ubuntu-desktop on Kubuntu.

Beyond the aesthetics, each has their own collection of programmes to work with the desktop. To view files on your system you would use Nautilus in Gnome but Dolphin in KDE. To edit text files you use Kate on KDE and Gedit on Gnome. There are countless more examples, but in essence, no one is stopping you from installing and using Dolphin in Gnome or Gedit in KDE.

Despite what some people may say, neither is better than the other in absolute terms. In subjective terms some people find one better than the other. You can ask for people's opinions, why do you prefer this over that, but you'll never know what you prefer unless you try both.

As for being sparse, Ubuntu and Kubuntu CDs feature less packages after installation because they aim to fit on one CD. You can install whatever you had in Ultimate Edition from the repositories, or just download the DVD instead of the CD.

---

### Post by kellemes on 2010-05-04
Great answer!

---

### Post by shebaw on 2010-05-04
I don't want to create a thread for this, so I will ask here. Can the same application work for both Gnome and KDE? I'm confused because they tend to have different default applications so what's the point of having them if the same application works on both of them?

---

### Post by kellemes on 2010-05-05
> **shebaw said:**
> I don't want to create a thread for this, so I will ask here. Can the same application work for both Gnome and KDE? I'm confused because they tend to have different default applications so what's the point of having them if the same application works on both of them?

Applications for KDE are build on a different development platform than applications build for Gnome, basically the only difference is the way application-windows are handled, mostly cosmetic.
In other words.. running a KDE application doesn't integrate very well (visually) within the Gnome environment and vica versa. Also you'll loose some KDE specific features because they're not supported by Gnome.

---

### Post by shebaw on 2010-05-05
> **kellemes said:**
> Applications for KDE are build on a different development platform than applications build for Gnome, basically the only difference is the way application-windows are handled, mostly cosmetic.
In other words.. running a KDE application doesn't integrate very well (visually) within the Gnome environment and vica versa. Also you'll loose some KDE specific features because they're not supported by Gnome.

Thanks for the clarification.

---

### Post by bigseb on 2010-05-06
Thanks, that's clarified things nicely.

---

### Post by kokoshmusun on 2010-05-17
I have Ubuntu 10.04 (dual-boot with Win Vi$ta) and don't want to install another distro.  But I do want to try KDE.  What's the easiest way.  Can I do virtualization and try a KDE distro like Kubuntu or I guess PCLinuxOS?  Should I do Live CD.  Or should I just install KDE on top of Ubuntu (I'd rather not at first).

---

### Post by Untitled_No4 on 2010-05-17
In my opinion the easiest way is to open a terminal window and type
```
sudo aptitude install kubuntu-desktop
```

which will install the KDE desktop besides your Gnome desktop. You can switch between desktops from login, just choose which session you want to start.

If you later regret it, all you need to do is run
```
sudo aptitude purge kubuntu-desktop
```
which will remove all packages installed for KDE. It's important you use aptitude for that and not apt-get if you want to be able to remove without having to remove each package manually.
Enjoy.

---

### Post by kokoshmusun on 2010-05-17
That's slick, thanks a lot for the answer...

---

### Post by kokoshmusun on 2010-05-17
Couldn't find a thread related to this so I'll ask here: Is there a way to show only Gnome apps in Gnome and only KDE apps in KDE?  Both of them show and it's clutter... 
cheers.

---

### Post by Elfy on 2010-05-17
> **Untitled_No4 said:**
> ...If you later regret it, all you need to do is run
```
sudo aptitude purge kubuntu-desktop
```

If that fails - and I think it will now 

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by XubuRoxMySox on 2010-05-17
GTK applications (Gnome, Xfce, etc) run just fine in a QT (KDE) environment and vice-versa on most computers with at least 512 MB of RAM. Most of the dependencies you get when you install K3B or K-Mail for example, in _U_buntu (Gnome) or _X_ubuntu (Xfce) are just *libraries*. It's more a matter of storage space on your HDD than it is of CPU and RAM usage.

Hope this helps a little more,
Robin

---

### Post by tommytomtom on 2010-05-31
I have always been a kubuntu user from the beginning.  I am addicted to the eye-candy in kubuntu.  Ubuntu simply has nothing to compare with the "mac like" windows system available to a 3d accelerated kubuntu.  Actually it is even more eye candy then a "mac".  If you don't understand what I mean when I say "eye candy" then I can just say "imagine a fantastic 3d opengl computer game with screens to your programs flying around in 3d space." Yes it is fun.

BUT

I am seriously considering going back to Ubuntu.  Why would an eye-candy sugar addict like myself do such a thing? After a while you get tired of the bugs.  Yes, Ubuntu has bugs as well but my impression of ubuntu is that there is a MUCH larger team behind that development then kubuntu so the releases are of MUCH higher quality.  I am not just talking about bugs in the KDE window system.  That works actually pretty well. I am talking about integration bugs in almost everything else.  My impression is that there are more bugs in Kubuntu then Ubuntu and at the end of the day I need to get work done and in that case eye-candy may just have to go out.  But I am already experienceing sugar withdrawl symptoms with the idea of leaving kubuntu...I got the shakes!!!

Anybody else out there with a similar experience??

---

### Post by Untitled_No4 on 2010-05-31
> **tommytomtom said:**
> Anybody else out there with a similar experience??

Not really.
First, I like KDE because I find it much more user-friendly (and I'm talking about me as the user). The eye candy and aesthetics are a nice bonus, but it's not the main reason I use it.

As for Kubuntu, I use it on a daily basis and I use it to get work done. While I guess I do encounter sometimes, it's not often and not usually something that I can pinpoint down to the fact that Kubuntu has a small developer team. If I couldn't get my work done on then it would be useless for me.

I always thought I like KDE more than I like Kubuntu and so I think I've tried almost every KDE distro out there and I've always ended up coming back to Kubuntu because I prefer it, but if I was facing the same issues as you are I'd rather use a different distro than go back to Gnome.

---

### Post by n_s_simpson on 2010-06-01
Just out of interest why have two totally separate installs?

Why not have just one install and have an option to either install Ubuntu, Kubuntu or both?

Just a thought.

Thanks

Nick

---

