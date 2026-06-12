---
title: "If I install KDE apps will it harm my Ubuntu Hardy Installation...?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by jaydoc on 2008-05-12
Hi all....

If I install some KDE apps that seem to be better than GNOME equivalents accdg to a lot of people (K3b, and Amarok for example) then it seems to pull down the whole KDE library along with the apps..

Does this mean I have the KDE envt alongside the GNOME one...?

Will this harm my installation of Hardy in any way...? 

I'm very very new to Linux, hence this paranoia...! don't want to do something silly and have to do a whole reinstall from scratch...!

Help.

---

### Post by rockerphil on 2008-05-12
not that i know of, i'm personally running Fluxbuntu which uses Fluxbox as my WM and ROX as my filer, and iv'e got a Hienz 57 collection of apps that work best for my purposes from the KDE, Gnome and Xfce DE's and Hardy works great for me

---

### Post by volkswagner on 2008-05-12
I love K3b, which is why it is installed on my ubuntu and mythbuntu machines.  It seems very happy under Gnome.

---

### Post by PeterJS on 2008-05-12
The only problems you'll have are that the KDE apps won't fit your theme, you'll have some duplicate libraries in RAM and on disk, and your menus will might end up cluttered if you install both full desktops. So all in all not much more than cosmetic problems, and a little resource usage.

---

### Post by django0909 on 2008-05-12
You'll know whether you have KDE/GNOME or both when you are at the login prompt. It's under 'session type', I think.

---

### Post by penguinbreath on 2008-05-12
I have Amarok on Ubuntu, and Amarok has not given my Ubuntu setup any trouble.

---

### Post by jaydoc on 2008-05-12
PeterJS....

Is there anyway I can avoid installing a full KDE desktop when using such KDE apps...?

Personally I love the lean clear looks of GNOME, than the kiddish-looking KDE....!

My laptop runs PCLinuxOS 2008 GNOME, and now my desktop has Ubuntu Hardy.... Its the nice uncluttered looks that made me go GNOME on both my computers...!

I surely don't want an awry looking menu...



@Volkswagner,

have you noticed any problems with the menu after K3b was installed...?

---

### Post by SunnyRabbiera on 2008-05-12
No issues here either, they just use different libraries thats all, no harm will come to your computer if you install KDE apps.

and no you dont have to install the full KDE to use its apps.

---

### Post by PeterJS on 2008-05-12
I didn't mean to imply you needed to install of KDE, just that if you did it could cause additional cosmetic issue.

---

### Post by volkswagner on 2008-05-12
> **jaydoc said:**
> PeterJS....

I surely don't want an awry looking menu...

@Volkswagner,

have you noticed any problems with the menu after K3b was installed...?

I do not have any menu problems. I do notice one issue.  I am not sure if it is normal/would happen if I had KDE.  When I have a burn session running, or complete (k3b is minimized)I have the small progress bar always shown.  It is small and movable so not an issue.  As soon as I close the burn session it goes away.

I have had no coasters, and the program is user friendly.

When you select any application for install withing synaptic you will be shown the list of dependency.  You can then decide if you still want to proceed.

---

### Post by bgast1 on 2008-05-12
I also use a mixture of KDE programs on my Ubuntu Gnome install as well.

---

### Post by jaydoc on 2008-05-13
thanks all..... I haven't tried it yet

Will try and let the fellow beginners know.....

---

### Post by jaydoc on 2008-05-17
Hi all.....

Well i did it.....

Always this happens with me....!

Whenever I'm in a quandary/conundrum as to do something or not, I invariably end up doing, MUCH more than I intended to....!

So It happened to me this time.... After being in so much doubt as to whether a single KDE app install would contaminate my GNOME install, I went ahead and downloaded and installed the ENTIRE KDE esktop to the existing GNOME Hardy install....

When i went back to GNOME dektop, which IS my Default I found that its menus are FULL of all the KDE apps as well.... And I hate that...! Makes them soooo long....

the QUESTION: How can I make KDE apps show up only on KDE, and GNOME apps only on GNOME....?

P.S: there was a similar question on the forums, but it was in 2005...!

---

### Post by Average Joe on 2008-05-17
You could remove the entire KDE environment and all its applications first. To do so follow the [Psychocats]("http://www.psychocats.net/ubuntu/puregnome") instructions.

When you are back to pure Gnome, you could then install just the KDE application(s) you would like, the same way you would install a new Gnome application. By far most of the KDE applications work just file with Gnome. You don't need the entire KDE environment for that. Just a bunch of KDE libraries, but those will be installed automatically along with the (first) KDE application you install.

---

### Post by jaydoc on 2008-05-17
After I have uninstalled KDE....

Will the KDE files I downloaded be on my computer...?

i'm on a limited bandwidth network and don't want to pay my ISP for downloading the same thing twice....

---

### Post by Average Joe on 2008-05-17
If you use```
sudo apt-get remove ...
```
to remove stuff, the downloaded files will remain on your computer (in /var/cache/apt/archives)

If you use ```
sudo apt-get purge ...
```
to remove stuff, the downloaded files will be deleted.

If you follow the Psychocats instructions, the files will thus remain on your computer, and you won't be needing to download them again if you want to reinstall (some of) them later.

---

### Post by tacutu on 2008-05-17
search the forums & the web. basically, in /usr/share/applications you have a lot of .desktop files. edit them and add to them a ShowOnlyIn=KDE or ShowOnlyIn=Gnome entry, depending on what DE you want them to be visible. Of course, editing them by hand is a pain, so you want to automate the process. Search for that and you'll find plenty of info.

---

### Post by jaydoc on 2008-05-18
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
jegen@jegen-desktop:~$ 



I got this error message at the fag end of using psychocats instructions to remove KDE....

actually i tried installing Kubuntu with aptget at first, but gave up after the downloads were done... then i read Psychocats instructions.... and used aptitude to get the remaining packages... 

Now during the uninstallation when i tried it the aptitude way, it removed only the kubuntu desktop, but the KDE libs and the rest of the apps were still there.... so I once again used psychocats code to remove the apps....

DID something go wrong.for me to get the error message...?

---

### Post by jaydoc on 2008-05-18
E: kio-umountwrapper: subprocess post-removal script returned error exit status 2


PANIC.....

No new install can be made with synaptic....

the mesage above is what I get....

what can I do to get back to normalcy...?

---

### Post by tacutu on 2008-05-18
[http://ubuntuforums.org/showpost.php?p=4786808&postcount=3](http://ubuntuforums.org/showpost.php?p=4786808&postcount=3)

---

### Post by jaydoc on 2008-05-18
@tacutu....

Saw your post by searching, did it, got rid of the issue....

And thanked you too....!

BTW, what caused the problem and has it gone away forever...?

Paranoid bcoz, this is my main workstation and I don't wnat anything strange happening especially when i can't connect to the forums when my ISP goes in for its random periods of "maintanance".

---

