---
title: "[SOLVED] Problems installing Songbird"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by mjmark223 on 2008-10-18
Hi

I am having some problems installing Songbird for Ubuntu 8.04

I download it from the site but when I try to run it the following warning pops up

[I]/tmp/Songbird_0.7.0_linux-x86_64.tar.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences
[/I]

I tried both x86_64 and the i686.

I don't know what any of that means though.

Thanks for any help

Mark

---

### Post by phidia on 2008-10-18
You have to unpack that compressed archieve before trying to install it.
You can right click the package and select "extract here..." from the menu that appears. There should be a README file there that gives instructions for install.

There might be a better way to install than the way you're doing though but I'm not that familar with songbird. If there is a deb package you are much better off installing that.

> I tried both x86_64 and the i686. You need to use the correct package for the version you have installed.
If you didn't install the 64 bit version of Ubuntu you need to use the i686 package.

---

### Post by SunnyRabbiera on 2008-10-18
Well lets start with the type of linux kernel you have.
Go up to system, then to administration and then hit the control center.
in the first tab you can get information on what kind of linux kernel you have.
second for songbird you can try this site and search out songbird:
[http://www.getdeb.net/](http://www.getdeb.net/)

But first to find out what type of system you have here.

---

### Post by cozmicharlie on 2008-10-18
First - welcome to using Ubuntu.  I will make an assumption from your post that you are coming from the Windows world and trying to install as you would in Windows.  Ubuntu (or any Linux distro) is different and installing programs is different than what you are accustomed to in Windows.  What you have downloaded is a compressed file (like a zip file in Windows).  I suggest you may want to do some reading to give you a better understanding of how to install programs in Linux - this should help ([https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)).

For Songbird it will be easier for you to install using what are called deb files.  The instructions are here ([https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)).  To start with you need to know if you have a 32 bit system or a 64 bit system.  If you installed the normal Ubuntu desktop it is probably the 32 bit so you want to install programs for 32 bit systems not 64.  

Also, be aware that for multimedia you will need to install a number of packages with codecs etc.  This imho is the best tutorial for multimedia ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683))

The instructions on the link I provided should work for you but if you have problems please post back and we can help.

Enjoy

---

### Post by mjmark223 on 2008-10-18
This is what I found.

Ubuntu Release 8.04 (hardy)
Kernel Linux 2.6.24-21-generic
GNOME 2.22.3

Thanks for those links. I ran into .deb files when I tried to install OpenOffice, which has also been unsuccessful.

Yes I have just started using Linux coming from Windows and I was expecting the usual click OK...OK...OK.

I have however managed to connect to a wireless network and make my desktop look like a cube.

Thanks again for the help and do you guys know of any good books to help my transition.

---

### Post by cozmicharlie on 2008-10-21
> **mjmark223 said:**
> This is what I found.

Ubuntu Release 8.04 (hardy)
Kernel Linux 2.6.24-21-generic
GNOME 2.22.3

Thanks for those links. I ran into .deb files when I tried to install OpenOffice, which has also been unsuccessful.

Yes I have just started using Linux coming from Windows and I was expecting the usual click OK...OK...OK.

I have however managed to connect to a wireless network and make my desktop look like a cube.

Thanks again for the help and do you guys know of any good books to help my transition.

Open Office should have come already installed in Ubuntu.  Are you trying to upgrade to Open Office 3?  If so this may help [http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/).

As per books.  There are a number of good books.  A Practical Guide to Ubuntu Linux is good.  The Official Ubuntu Book is a good one also.  There are others - if you go to your local Borders or Barnes & Noble - they usually have a good selection.  I really like Linux Format magazine personally (a bit expensive though).  

Enjoy

---

### Post by mjmark223 on 2008-10-22
Thanks for the book suggestions. All I had to do was go to add/remove programs and check the box to get office to work. I still haven't got Songbird to run yet though

---

### Post by cozmicharlie on 2008-10-22
> **mjmark223 said:**
> Thanks for the book suggestions. All I had to do was go to add/remove programs and check the box to get office to work. I still haven't got Songbird to run yet though

What is the problem you are having with Songbird?  Were you able to install it?

---

