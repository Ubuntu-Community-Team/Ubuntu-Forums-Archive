---
title: "[SOLVED] Need help installing Ubuntu"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by 843 on 2008-06-08
I got a Linux DVD from a local magazine, but I haven't been able to fully install it properly. The DVD contains Ubuntu, Kubuntu and Xubuntu. My laptop already has Windows XP installed, but I'm willing to reformat everything since it's still relatively new. When I boot from DVD, it gives me the option to run CDLinux or boot from hard drive. If I boot from hard drive, XP loads. If I run CDLinux, the DVD runs Xubuntu as a live CD.

I've successfully installed Ubuntu through Wubi, but it only allows installation of up to 30GB. As I said, I want a clean install. Downloading the ISO is not an option since internet connection here is horrible. Therefore I'm asking which files are necessary to burn into an ISO so that I can properly install Ubuntu, or if there is a way to do so without burning a new ISO. Any help is appreciated. Thanks in advance.

Here is the content of the DVD. I'm not going to list everything since it's otherwise a very long list.

_boot_
-**CDLinux**
--*autoboot*
---.config
---bzImage
---CDLinux
--*extra*
---firmwares
--*lang*
-**grub**
--memdisk
--menu.lst
--splash.xpm
stage2_eltorito
-**boot.catalog**

_DVD1-IL062008_
-browser, database, plugin, utility, etc...
-distro
--ubuntu
--kubuntu
--xubuntu

_MD5SUM-DVD1-IL062008_

---

### Post by shifty_powers on 2008-06-08
do you mind waiting a week or two? if so, try shipit and canonical will ship you a copy of your choice for free on cd,...

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by hovzio on 2008-06-08
I would download Ubuntu from the ubuntu website. Use the desktop cd.
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

### Post by The Cog on 2008-06-08
Are there any .ISO files in the distro folders? I wonder if you might find a CD image you could burn. I would expect that there is a way to do it, since they claim the DVD contains Ubuntu and Kubuntu.

---

### Post by The Cosmic Hobo on 2008-06-08
Isn't it normal for Ubuntu live CDs/DVDs to have an "install" option on the desktop when booted? I know the CDs I've used do, but I can't comment on your DVD.

Been out of the loop a couple of years so I'm not familiar with Wubi, but it sounds like an Ubuntu installer that runs under Windows. Of course it won't let you totally wipe Windows while it's running - it's nigh-on impossible to do that while Windows is up. I don't think you can even format your HD from within Windows. So that's a normal restriction.

---

### Post by ugm6hr on 2008-06-08
> If I run CDLinux, the DVD runs Xubuntu as a live CD.

Why not just install Xubuntu then?

Once installed, you should be able to install Gnome (ubuntu-desktop) from the DVD, assuming the files are on there somewhere.

That will give you both Ubuntu and Xubuntu (and you could remove Xubuntu if you wanted).

Out of interest - does it boot directly to the Xubuntu desktop, or does it go to a "login" screen.  It might be worth "logging out" of the Xubuntu LiveCD, and seeing what options you get.  I have never used an install DVD, but I suspect that you should be able to select "Gnome" from the login options (after logging out).

PS: Which magazine / country did you get the DVD from?

---

### Post by stalkingwolf on 2008-06-08
sounds like your best bet would be to order one from shipit,
or check to see if you have a LoCo team [http://ubuntuforums.org/forumdisplay.php?f=183]("http://ubuntuforums.org/forumdisplay.php?f=183") in your area. I think they usually have them available.

---

### Post by drs305 on 2008-06-08
The current 32-bit ubuntu iso image that you download from the site is called **ubuntu-8.04-desktop-i386.iso** and is 699 MB. The 64-bit AMD version is called **ubuntu-8.04-desktop-amd64.iso** and is 697 MB. Since you have a DVD it's possible the entire image is on your disk. If so, you could burn that iso to a CD and try to install it.

As the Cosmic Hobo stated, if you can start with the LiveCD instead of booting into windows, there is normally an "Install" icon in the upper left. Of course, I would expect you would have to boot from the LiveCD instead of into windows to run this.

---

### Post by bikinguy77388 on 2008-06-08
Hi 843,

Best of luck to you. Newbie here and have been using HH for  about 2 weeks now.

I would urge you to NOT delete your winXP install but set up a dedicated partition in which to run HH in.

HH really behaves like a beta install.

After using HH for awhile then delete XP if you so choose.

bikinguy

---

### Post by 843 on 2008-06-08
I've been using HH for awhile from the Wubi installation and it's pretty easy to use. It's still pretty troublesome navigating folders since I don't know where things are supposed to be, but I think it should be second nature in time.

So is this the file I'm supposed to be burning? Somehow I missed this file since it appears to be a RAR archive without file extension enabled.

[http://img134.imageshack.us/my.php?image=48483553dz3.jpg](http://img134.imageshack.us/my.php?image=48483553dz3.jpg)

---

### Post by drs305 on 2008-06-08
> **843 said:**
> So is this the file I'm supposed to be burning? Somehow I missed this file since it appears to be a RAR archive without file extension enabled.

[http://img134.imageshack.us/my.php?image=48483553dz3.jpg](http://img134.imageshack.us/my.php?image=48483553dz3.jpg)

The image link you provided looks exactly like the latest ubuntu LiveCD of 32-bit hardy. If you can make a cd with that image, you should be good to go. I'd use a slow speed.

---

### Post by 843 on 2008-06-08
I guess that's the one, thanks for the help, guys! :)

Now the problem is installing the rest of the programs from the DVD, I hope that's not too difficult...

---

### Post by ugm6hr on 2008-06-08
> **drs305 said:**
> The image link you provided looks exactly like the latest ubuntu LiveCD of 32-bit hardy. If you can make a cd with that image, you should be good to go. I'd use a slow speed.

You are looking for a file called *ubuntu-8.04-desktop-i386.iso*, which is presumably within that RAR.

---

### Post by drs305 on 2008-06-08
Just to clarify the last couple of posts (and especially mine). If you look at the image you posted, it shows that the contents you are looking at are contained in *ubuntu-8.04-desktop-i386.iso* So you would move one directory/folder up and you should see the iso listed. The iso is what you want to burn to disk.

For a good guide and techniques for burning the iso, look at the following:
[http://www.psychocats.net/ubuntu/iso]("http://www.psychocats.net/ubuntu/iso")

**Added:** You mentioned a RAR archive. It is possible the iso is contained within the RAR. If that is the case, you may first have to extract it from the RAR and then burn the extracted iso. I noticed on the image you posted that there is an "Extract to" button which should make this easy.

---

### Post by balachandarlinks on 2008-06-08
:KS
 Hey that is the iso file...since u doesnt install any iso software winrar opens the iso....So u first install iso burning tool like power iso and then burn the iso to a cd or dvd...then boot with it....

  then it is simple to follow the steps and install the ubuntu....If u want Xp then install ubuntu in a partition...else just click the Guided Installation....
  
  Dont go with WUBI if u dont want windows...it might need windows...
  
  Thats all...I think it ll solve ur problem...:popcorn:

---

### Post by Sealbhach on 2008-06-08
Once you get the ISO disk burned to a CD, you can install a dual-boot, which I would recommend if you're new to Linux.

There's a good walkthrough guide here:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)


.

---

### Post by 843 on 2008-06-08
Everything up and running now. Thanks for the help! :)

---

