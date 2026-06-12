---
title: "New to Lubuntu 14.04"
date: 2014-08-24
forum: New to Ubuntu
---

### Post by Richard_Sejour on 2014-08-24
Hey guys, before I begin, heed my cavet: I am very new to Linux, as my ignorance will undoubtedly reveal. I am switching over from Windows XP (7 years), so its not like I was on the pulse of technology anyways. However, I did notice the learning curve to be ridiculous; It took me an hour to hook up my computer, because I was used to downloading/installing a file just by clicking the icon, whereas I had to open up a terminal (for the first time) and manually install it. After completing that task, I was filled with such a sense of accomplishment... that is until I tried to install Apache openoffice. :confused:

Needless to say, the tutorials were way above my comprehension, so I (somehow) managed to install Libreoffice, but I think its outdated. LOL, the thing doesn't even have Times New Roman!!!

[B]1) Can someone explain to me how to download and install programs without using the terminal everytime?

2) Can someone show me how to download the latest version of Apache openoffice; if I cannot, please explain to me how to update Libreoffice to the latest version.

3) The clock is in 24 hours. How can I change it to the 12 hour clock?[/B][B]

4) Is there anyway I can...spice up Lubuntu? EVERYTHING is in small font, square edges, and have bland colors. This is a petty request, but I need some stimulation.[/B]

Please be patient with me, because as I mentioned above, I am a babe here at Linux; I welcome any advice on making my transition smoother. Thanks in advance!!!;)

---

### Post by deadflowr on 2014-08-24
The only one I can truly answer is number one.
Lubuntu comes with it's own software center, through which you can install applications.

As far as installing apache openoffice, you can go to [apache's openoffice]("https://www.openoffice.org/download/") site and get it from there, as well as read their [documentation]("http://www.openoffice.org/download/common/instructions.html#linux-preinstall") about how to install it.
(Be aware, you will need to use the terminal to install it)
But from the feel I get, you might not have times roman installed on the system.
Libreoffice should have access to whatever fonts are on the system at the time it is installed.
Maybe more on that here
[http://ask.libreoffice.org/en/question/17479/how-do-i-install-new-fonts-to-libreoffice-writer/](http://ask.libreoffice.org/en/question/17479/how-do-i-install-new-fonts-to-libreoffice-writer/)

That stated, I don't normally use lubuntu so I don't know how to change the clock, nor what tweaks will increase productivity.

---

### Post by ibjsb4 on 2014-08-24
Have you see this?

[https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)

---

### Post by vasa1 on 2014-08-25
And because you've just migrated from Windows, [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm") maybe worth a read.

---

### Post by mozalmy on 2014-08-25
Hi Richard.

First things first. These are things you need to do right after installing Ubuntu, Xubuntu, Lubuntu or Kubuntu.

Run following command in terminal (Ctrl+Alt+T) and tick all check boxes under Software and Updates tabs.

```
sudo software-properties-gtk

```
#2 Download all updates. Open up the terminal from your menu or press Ctrl+Alt+T. Then type following command each at a time:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Reboot

#3 Get the source of your kernel. Open up the terminal from your menu or press Ctrl+Alt+T. Then type following command:

```
sudo apt-get install linux-source
```

#3 Find out the version of your kernel. Type:

```
uname -r
```

#4 Assuming your kernel version is 3.13.0-34-generic. You may need to download extra packages. Some of them may already been installed in your system but it's okay to 'reinstall'. Your system will recognize the installed packages and skip the process. Type following command each at a time:

```
sudo apt-get install linux-generic-lts-trusty
sudo apt-get install linux-headers-3.13.0-34 (**[COLOR=#ff0000]Important![/COLOR]** remember to replace with your actual kernel version)
sudo apt-get install linux-headers-3.13.0-34-generic (**[COLOR=#ff0000]Important![/COLOR]** remember to replace with your actual kernel version)
sudo apt-get install linux-headers-generic-lts-trusty
sudo apt-get install linux-image-3.13.0-34-generic (**[COLOR=#ff0000]Important![/COLOR]** remember to replace with your actual kernel version)
sudo apt-get install linux-image-generic-lts-trusty
```

Reboot

#5 Ensure you have all the drivers installed. Again, open up the terminal from your menu or press Ctrl+Alt+T. Then type following command:

```
sudo apt-get install --install-recommends xserver-xorg-lts-trusy
```

Reboot

Your system is now up-to-date.

To install LibreOffice you can follow the instructions here (item 2.3): [https://sites.google.com/site/easylinuxtipsproject/first-xubuntu](https://sites.google.com/site/easylinuxtipsproject/first-xubuntu)

To tweak Lubuntu, check out this site: [https://sites.google.com/site/easylinuxtipsproject/lubuntu](https://sites.google.com/site/easylinuxtipsproject/lubuntu)

Good luck!

---

### Post by Ksiencha on 2014-08-25
*** I have to say if you want to upgrade to LibreOffice 4.3 you'd have to use terminal (just a little bit), don't be intimidated by it, though it's ok to be after Windows (I was).
In terminal do the following commands:
```

sudo add-apt-repository ppa:libreoffice/libreoffice-4-3
sudo apt-get update
sudo apt-get upgrade

```
I hope this will help, cause I did this and it worked for me.

*** As for the CLOCK settings, I don't remember exactly, I guess you have to right-click it and you'll find Edit clock settings (or something like that), then instead of **%R** type in **%r**. This should help.
Also you may find helpful [**this advanced article**]("https://help.ubuntu.com/community/Lubuntu/Documentation/CustomizingTheClock") on how to change your clock settings.

*** For FONTS look at [**this answer**]("http://askubuntu.com/a/218486/277426").

*** For overall customization read (I really hope those tricks will help to do what you want do):
**1.** [http://www.everydaylinuxuser.com/2013/11/how-to-customise-lxde-desktop-using.html](http://www.everydaylinuxuser.com/2013/11/how-to-customise-lxde-desktop-using.html)
**2.** [http://www.theotherinformation.com/2014/04/change-lubuntu-theme-feel-ubuntu.html](http://www.theotherinformation.com/2014/04/change-lubuntu-theme-feel-ubuntu.html)

Good luck ;)

---

### Post by Impavidus on 2014-08-25
> **Richard_Sejour said:**
> 1) Can someone explain to me how to download and install programs without using the terminal everytime?Use the software centre or synaptic, another great graphical tool for installing software. You can install software from random websites, but this is not recommended unless there is no other way and you know what you're doing, and there is no standard recipe.
> 2) Can someone show me how to download the latest version of Apache openoffice; if I cannot, please explain to me how to update Libreoffice to the latest version.The version of LibreOffice you can get from the software centre is version 4.2.4. It's not the most recent version, but still only half a year old, so not terribly outdated. If you really want the latest release, use Ksiencha's post. If you want OpenOffice, use deadflowr's post.
> **mozalmy said:**
> Hi Richard.

First things first. These are things you need to do right after installing Ubuntu, Xubuntu, Lubuntu or Kubuntu.

(...)
I think most of these are not really necessary. But you have to keep you system up-to-date. You should get a pop-up automatically when updates are available, unless you disable this. If your graphics card or any other piece of hardware needs proprietary drivers, you can install them via a graphical tool labeled additional drivers or additional hardware or something like that. It should tell you whether anything is available.

---

### Post by ibjsb4 on 2014-08-25
> **mozalmy said:**
> First things first. These are things you need to do right after installing Ubuntu, Xubuntu, Lubuntu or Kubuntu.
> **Impavidus said:**
> I think most of these are not really necessary.
Your update method does not seem to be supported by any other thread that I can find.
> **Richard_Sejour said:**
> **Can someone explain to me how to download and install programs without using the terminal everytime?**
> **Impavidus said:**
> Use the software center or synaptic
+1
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by deadflowr on 2014-08-25
If you want a more robust package manager than what comes with lubuntu, then install synaptic from the software center.

The program called software-properties-gtk is usually called software sources in the menu.
I know it is integrated with synaptic and ubuntu's own software center, so I would assume it is also integrated with the lubuntu software center as well.
It might even have it's own menu entry in lubuntu main menu system. It usually does.

In software sources you can add the ppa's such as the one for libreoffice, by going into the "other software" tab, and click "add".
Simply paste the ppa entry like the one above in post#6 ([COLOR=#000000][FONT=Ubuntu Mono]ppa:libreoffice/libreoffice-4-3).
[/FONT][/COLOR]After you add the ppa entry, you need to update you package archives listings you have, so that the new ppa gets added to it. Basically, run the update manager.

Hopes this helps in your quest to avoid the terminal...

---

### Post by Richard_Sejour on 2014-08-25
Thank you guys so much for the literature. My bookmarks page is getting a lot more hefty.

I updated everything as mozalmy instructed, and so far everything works great; I also updated Libreoffice to the most recent version as Ksiencha instructed. I customized Ubuntu a little more to spice it up, so that is a huge plus.
I am sure that I will have more questions, so don't stray off too much. ;)

---

### Post by Ksiencha on 2014-08-25
I'm really glad that you got it all to work ;) Since you solved your current questions, please mark this thread as SOLVED ([**read here on how to do this**]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"))

---

### Post by Richard_Sejour on 2014-08-25
Definitely, and I would like to mention that Libreoffice now has Times New Romans and a slew of other fonts that were not present before, so I guess updating Libreoffice corrected that issue. Again, thank you guys.):P

---

