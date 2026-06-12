---
title: "remove ubuntu"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by bretagne on 2012-05-19
hello, recently bought hp compaq nx-9010 sold as running xp pro[though no xp installation /recovery disk just coa sticker]. Only had ubuntu 9.04 installed,no partition, assume windows overwritten[nothing in boot menu]. Seemingly couldn't do much with it as obsolete,downloaded 12.04[now snail slow], but really want to use what I know ie windows. Question is can xp be recovered/reinstalled, which type of xp disk, and how do I remove Ubuntu.Thanks

---

### Post by Linux_junkie on 2012-05-19
> **bretagne said:**
> hello, recently bought hp compaq nx-9010 sold as running xp pro[though no xp installation /recovery disk just coa sticker]. Only had ubuntu 9.04 installed,no partition, assume windows overwritten[nothing in boot menu]. Seemingly couldn't do much with it as obsolete,downloaded 12.04[now snail slow], but really want to use what I know ie windows. Question is can xp be recovered/reinstalled, which type of xp disk, and how do I remove Ubuntu.Thanks

As you have said there are no partitions then I am affraid that when you installed 9.04 it had over written Windows XP.  The only way of returning to Windows XP is by buying a copy of XP on a disk and installing it which will over right 9.04.

Alternatively, as you claim 12.04 is running s l o w (I am assuming your using Unity) you can alway try Xubuntu or Lubuntu on your machine.  Both are lighter than Ubuntu.  You do not need to install Xubuntu/Lubuntu just download XFCE or LXDE desktops from repos.

If you type the following command
```
sudo apt-get install xubuntu-desktop
```
It will install the XFCE desktop environment
```
sudo apt-get purge ubuntu-desktop
```
will remove unity
(if you want LXDE simply replace xubuntu with lubuntu above) Hope this helps.

---

### Post by LeGasp on 2012-05-19
Seconding the above post. Definitely consider Lubuntu or Xubuntu! Lubuntu has a similar layout to Windows XP, so it'd be easy to get used to. Last time I had it running, it used about 100 mb of RAM after booting. Compare that to my Ubuntu 12.04, which uses about 350mb. In other words, very fast. 
Xubuntu is also very good, just slightly heavier on resources. If you turn off compositing though, you'll find it running around 120 mb of RAM after boot. Slightly slower than Lubuntu. 
The main difference between these two is Lubuntu uses LXDE and Xubuntu uses XFCE. LXDE is much lighter than XFCE, but is a less complete desktop environment.
Not all Linux distros are heavy on resources. It's very easy to get a fully functional, modern operating system that's lighter than anything you'll get from Microsoft or Apple.

---

### Post by wyliecoyoteuk on 2012-05-19
sorry you have been sold a pup.
If you can get the correct XP disk (not easy as it is no longer available from stores) you can install using the COA key.
However, XP will cease to be supported soon.
Your choices: if you want to stick to windows is windows 7 or nothing, around £100.
Or try the distros suggested.

---

### Post by HunterDX77M on 2012-05-19
I'd like to try the Xfce interface, but I don't wan't to get rid of Unity. If I type the code in the first box above (and only that first box), will I be able to switch to Unity from the login screen later?

---

### Post by Lisiano on 2012-05-19
> **HunterDX77M said:**
> I'd like to try the Xfce interface, but I don't wan't to get rid of Unity. If I type the code in the first box above (and only that first box), will I be able to switch to Unity from the login screen later?

Yes, it only adds the Xubuntu stuff. After running purge it will still be there, look here if you later wish to switch to Pure Xubuntu [http://psychocats.net/ubuntu/purexubuntu](http://psychocats.net/ubuntu/purexubuntu) or here if you wish to switch to Pure Ubuntu [http://psychocats.net/ubuntu/pureubuntu](http://psychocats.net/ubuntu/pureubuntu)

Note, it might delete something you want, so review the command.

---

### Post by HunterDX77M on 2012-05-19
Sorry for any redundancy, Lisiano, but just to clarify: I can switch back and forth from Unity to XFCE without any problem, after I install XFCE?

---

### Post by LeGasp on 2012-05-19
You should be able to select an XFCE session from the login screen, and go back to Unity in the same way.

---

### Post by Linux_junkie on 2012-05-19
> **HunterDX77M said:**
> Sorry for any redundancy, Lisiano, but just to clarify: I can switch back and forth from Unity to XFCE without any problem, after I install XFCE?

If you only type in the first command I quoted it will install the Xubuntu features alongside Unity.  When you login you can then select which desktop to use (Ubuntu/Unity or Xubuntu/XFCE).

---

### Post by Lisiano on 2012-05-19
> **HunterDX77M said:**
> Sorry for any redundancy, Lisiano, but just to clarify: I can switch back and forth from Unity to XFCE without any problem, after I install XFCE?

Before you login, look at the little gear near your username, if you click it, you can then select what session you want. For Xubuntu just click Xubuntu (Or XFCE).

---

### Post by HunterDX77M on 2012-05-19
Thank you very much for clearing that up! (Everyone)

---

