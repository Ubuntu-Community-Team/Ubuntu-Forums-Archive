---
title: "Just Started, Brand New!"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Taadaa on 2008-09-02
Hi everyone

I'm sure these questions have been answered many times already, so if someone would just point me to the correct threads . . . 

Don't know how to connect Ubuntu to my home Windows Network so I can share files, access Ubuntu file storage and use Ubuntu to access Windows file storage.

Know nothing about installing apps, would like to install Adobe Reader, found the file, but it won't "unzip".  Obviously missing the Ubuntu "unzip" program as well as how to install it.

I have been able to find my network printer, but i don't have the driver for it.  Found the Linux driver online and have downloaded both deb & rpm drivers.  Have no idea!  Now what do I do?

Thanks very much

Taadaa

---

### Post by pytheas22 on 2008-09-02
> Don't know how to connect Ubuntu to my home Windows Network so I can share files, access Ubuntu file storage and use Ubuntu to access Windows file storage.

You should be able to connect to Windows shares simply by clicking Places>Network and finding the computers you want to connect to.  Sometimes the GUI can be flaky, however, and you might need to mount network shares manually. [this tutorial]("http://industriousone.com/mounting-windows-shares-ubuntu") is good in that case.  You may also need to install samba first (not sure if it's installed by default or not), which you can do with this command (or by using the GUI applications described below):

```
sudo apt-get install samba
```

> 
Know nothing about installing apps, would like to install Adobe Reader, found the file, but it won't "unzip". Obviously missing the Ubuntu "unzip" program as well as how to install it.

Ubuntu already comes with a program for opening .pdf files.  Just click them and they should open with no problem.  Adobe Reader is not necessary (if it's even available for Linux?).

Beyond that, you should understand that in Linux, most software gets installed from centralized repositories--it's not like Windows were you troll around the web, downloading stuff from random sites.  Click Applications>Add/Remove Programs or System>Administration>Synaptic Package Manager (both do the same thing; Synaptic is a little more powerful) and you'll be able to search for tens of thousands of applications by name or type, and download and install them automatically.

You should also enable the software repositories for by going to System>Administration>Software Sources and checking all the boxes under the "Ubuntu Software" tab.
> 
I have been able to find my network printer, but i don't have the driver for it. Found the Linux driver online and have downloaded both deb & rpm drivers. Have no idea! Now what do I do?

Most printers should "just work" on Ubuntu, although depending on the manufacturer's support for Linux, some are more difficult than others to get working.  Please let us know the exact name and model of your printer, and the link to the drivers that you're trying to install, and we should be able to tell you what to do.

---

### Post by WRDN on 2008-09-02
> **Taadaa said:**
> Hi everyone

I'm sure these questions have been answered many times already, so if someone would just point me to the correct threads . . . 

Don't know how to connect Ubuntu to my home Windows Network so I can share files, access Ubuntu file storage and use Ubuntu to access Windows file storage.
**[Samba]("https://help.ubuntu.com/community/SettingUpSamba") may be what you are looking for. This allows you to share files on a network. You can also use [SSH]("https://help.ubuntu.com/community/SSHHowto") for transferring files. Regarding the Windows network, you can see if it is recognized by clicking Places > Network**

Know nothing about installing apps, would like to install Adobe Reader, found the file, but it won't "unzip".  Obviously missing the Ubuntu "unzip" program as well as how to install it.
**Adobe Reader is available in the repositories, so you should install it through them. Go to Applications > Add/ Remove or System > Administration > Synaptic Package Manager and look for the applications you want. Ubuntu has a PDF reader installed, so you don't have to install Adobe Reader. As for unzipping archives, just right click on the archive, and select "Extract Here". Alternatively, double click the archive and it will open with the Archive Manager, so you can extract files etc.**

I have been able to find my network printer, but i don't have the driver for it.  Found the Linux driver online and have downloaded both deb & rpm drivers.  Have no idea!  Now what do I do?
[B]As mentioned above, look for the driver in Synaptic first. If you have downloaded the debian package though, double click it and it will open with the GDebi Package Installer. Also, the RPM package cannot be used in Ubuntu without conversion (and luck). Install the package, "alien" to convert an rpm to debian package, though this should only be done if there isnt a debian package available. Then, once alien is installed, you can convert the RPM using the command:

```
sudo alien -d [name].rpm
```[/B]

Thanks very much


See my answers in bold.

It is best to install all software (if possible) through the repositories, because, when the software is updated, the update will appear in the Update Manager. If you install it from a package or from source, the updates will not appear (as far as I know).

---

### Post by Taadaa on 2008-09-02
> **pytheas22 said:**
> You should be able to connect to Windows shares simply by clicking Places>Network and finding the computers you want to connect to.  Sometimes the GUI can be flaky, however, and you might need to mount network shares manually. [this tutorial]("http://industriousone.com/mounting-windows-shares-ubuntu") is good in that case.  You may also need to install samba first (not sure if it's installed by default or not), which you can do with this command (or by using the GUI applications described below):

```
sudo apt-get install samba
```

[COLOR="Blue"]Thank you thank you!  That works.  It will be so much easier to learn once I get some of the basics set up.[/COLOR]



Ubuntu already comes with a program for opening .pdf files.  Just click them and they should open with no problem.  Adobe Reader is not necessary (if it's even available for Linux?).

Beyond that, you should understand that in Linux, most software gets installed from centralized repositories--it's not like Windows were you troll around the web, downloading stuff from random sites.  Click Applications>Add/Remove Programs or System>Administration>Synaptic Package Manager (both do the same thing; Synaptic is a little more powerful) and you'll be able to search for tens of thousands of applications by name or type, and download and install them automatically.

You should also enable the software repositories for by going to System>Administration>Software Sources and checking all the boxes under the "Ubuntu Software" tab.


Most printers should "just work" on Ubuntu, although depending on the manufacturer's support for Linux, some are more difficult than others to get working.  Please let us know the exact name and model of your printer, and the link to the drivers that you're trying to install, and we should be able to tell you what to do.


the website address is [http://solutions.brother.com/linux/en_us/download_prn.html#MFC-5460CN]("http://solutions.brother.com/linux/en_us/download_prn.html#MFC-5460CN")

Thank you for your clear explanation!

---

### Post by eggdeng on 2008-09-02
To install Adobe Reader, you will need to enable the mediubuntu repositories. (Repos are places from which you can download and install software you need.) This is a good idea as you will need software from these to enable playback of restricted formats like mp3, flash and DVD.
Open a Terminal (Applications -> Accessories -> Terminal) and copy and paste this command
```
sudo gedit /etc/apt/sources.list
```
& press Intro. Copy and paste the following two lines to the end of the file which opens in the text editor
```

deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free
```
Now run 
```
sudo apt-get update
```
You can now install acrobat reader with the command
```
sudo apt-get install acroread
```
In my opinion, Adobe have done an excellent job in producing an application which has nothing to envy in the W*nd*ws version.

---

### Post by Taadaa on 2008-09-02
> **WRDN said:**
> See my answers in bold.

It is best to install all software (if possible) through the repositories, because, when the software is updated, the update will appear in the Update Manager. If you install it from a package or from source, the updates will not appear (as far as I know).

Your explanations were perfect!  I can now see my Windows Network and my files.  Havent' tried copying them yet, but as long as I can access them, the rest will come.  Will be checking out the repositories (now that I know they are there).

Is there a good "For Dummies" type manual I can start with that you would recommend?

Thanks again

Taadaa

---

### Post by Taadaa on 2008-09-02
> ```

deb http://packages.medibuntu.org/ hardy free non-free
deb-src http://packages.medibuntu.org/ hardy free non-free
```
Now run 

 nothing to envy in the W*nd*ws version.

Got it and it ran pretty good, but got a public key error message on one of the medibuntu.org lines.

BUT, I now have a working Adobe Reader on my system!  Thanks!

You guys are so great in here!

---

### Post by WRDN on 2008-09-02
> **Taadaa said:**
> Your explanations were perfect!  I can now see my Windows Network and my files.  Havent' tried copying them yet, but as long as I can access them, the rest will come.  Will be checking out the repositories (now that I know they are there).

Is there a good "For Dummies" type manual I can start with that you would recommend?

Thanks again

Taadaa

Happy to help :)

As far as manuals go, you could start by reading the [Ubuntu Help]("https://help.ubuntu.com/") pages, and [Psychocats documentation]("http://www.psychocats.net/ubuntu/").

---

### Post by kansasnoob on 2008-09-02
> Know nothing about installing apps, would like to install Adobe Reader, found the file, but it won't "unzip". Obviously missing the Ubuntu "unzip" program as well as how to install it.

For Adobe reader I'd recommend downloading the Medibuntu repository, I'm assuming this is Ubuntu 8.04, aka Hardy Heron, so go to Accessories > Terminal and copy-n-paste the following into the terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

You'll be asked for your password so enter it, hit enter and then:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Hit enter again. You can then close the terminal.

And finally open synaptic by going to System > Administration > Synaptic Package Manager. It'll ask for your password again (maybe), so enter your password and you'll see synaptic:

[ATTACH]83799[/ATTACH]

Point and click - Settings > Repositories and you'll see this:

[ATTACH]83800[/ATTACH]

[ATTACH]83801[/ATTACH]

[ATTACH]83802[/ATTACH]

NOTE: You won't have the Launchpad entries under Third Party Software, but everything else should be just like mine.

Now click on Reload and when it's done running click on Mark All Upgrades. Then click on search and type in acroread, you'll see this:

[ATTACH]83809[/ATTACH]

Select to install all four of those packages and when synaptic is done you'll have Adobe Reader!

Now there are faster ways to do this, but you need to learn how to use synaptic. And you'll almost undoubtedly want to install more stuff from the Medibuntu repo. Like Adobe flash or dvd support.

It's all a matter of learning. You'll love it when you get used to it.

Oh credit where credit is due: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by kansasnoob on 2008-09-02
> Got it and it ran pretty good, but got a public key error message on one of the medibuntu.org lines.


I think you're missing the gpg key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

If that doesn't help give a shout!

---

### Post by kansasnoob on 2008-09-02
I see that most of my screenshots didn't work (probably too many) but to get a general idea this is great:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)

Just ask lots of questions!

---

### Post by pytheas22 on 2008-09-02
> the website address is [http://solutions.brother.com/linux/e...tml#MFC-5460CN](http://solutions.brother.com/linux/e...tml#MFC-5460CN)

I took a look at the printer page.  I would first try download the .deb and installing.  You can follow the installation instructions (probably best, but you'll need to use the command line), or you could just double-click on the .deb file and it will probably work.

If you still can't get the printer going, please tell us the exact make and model, and whether you're using 32 or 64-bit Linux.

---

