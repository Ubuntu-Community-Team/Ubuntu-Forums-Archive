---
title: "Super beginner"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by brentv911 on 2012-02-12
I've been a windows man all my life.  recently I decided to try a different operating system.  So after some searching i came apon Ubunutu.  So far I love it, but i'm looking for an absolute beginner resource.

Like how to install programs that aren't in the software center.  I don't have a clue as to what commands do what in the terminal.  

I currently have a dual boot laptop with windows 7 and ubuntu.   I used the instructions on the Ubuntu website to install it right next to win 7,  no partitioning involved.

But now i'm just a little lost.   Any help would be appreciated.

Thanks

---

### Post by wolfen69 on 2012-02-12
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric](http://ubuntuguide.org/wiki/Ubuntu_Oneiric)

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by jerrrys on 2012-02-12
Give us an example of what third party app's you want to install.

---

### Post by Learning Linux 2011 on 2012-02-12
When you download a file straight from the internet, it usually comes in one of three formats:
.BIN for Binary
.DEB for Debian
.RPM for Red Hat Package Manager

Ubuntu is based on another version of Linux called Debian.  Whenever possible, look for .DEB since you can usually just double click it inside Ubuntu and it will begin the install, like an .EXE in Windows.

.RPM isn't really for Ubuntu, so don't download that type.

.BIN is a more generic Linux format.  Here is a generic link for a Java installation, but you can use it for almost anything:
[http://www.java.com/en/download/help/linux_install.xml#selfextracting](http://www.java.com/en/download/help/linux_install.xml#selfextracting)

Normally you should try to use the Software center or the Terminal using the command:
sudo apt-get install <whatever package>

The Software Center has almost anything you need.

There are also files that end in .TAR or .TAR.BZ or various versions of .TAR.(whatever)
These are basically compressed files like .ZIP files in Windows.

I don't know how you learn best, but I recommend getting a printed book on Linux to learn it, as I find that trying to learn bits and pieces online is more difficult, but that depends on you.

People take years to learn Windows, but then expect to learn Linux in a few days and that just isn't realistic.  It takes time to learn Linux, just as it took time to learn Windows, but you should be able to use your knowledge to learn Linux faster than someone who never used computers before.  Still, though give it some time, I think it is worth it.

---

### Post by kc1di on 2012-02-12
Here are a couple web pages that will help you learn Linux

As far as installing third party software , Linux is not like windows most software can be found in the Ubuntu's repository if by chance you need one from another source you should be careful there and it depends what format it's packaged in as to how it is to be installed 

Here's the web pages I mentioned:

[http://linuxreviews.org/beginner/]("http://linuxreviews.org/beginner/")

And 
[http://www.justlinux.com/nhf/Installation/Familiarizing_Yourself_With_Linux.html]("http://www.justlinux.com/nhf/Installation/Familiarizing_Yourself_With_Linux.html")

Of course a google search will reveal much much more for both Ubuntu and linux in general.
Good luck , let us know what programs in particular you looking to install and there will be those here that can help.
Welcome To Linux and Ubuntu

---

### Post by grahammechanical on 2012-02-12
You have this already on your machine

[https://help.ubuntu.com/11.10/ubuntu-help/index.html]("https://help.ubuntu.com/11.10/ubuntu-help/index.html")

Open the Dash (click the ubuntu icon) and type "help" in the search panel.

Regards and welcome to the forums

---

### Post by brentv911 on 2012-02-12
> **jerrrys said:**
> Give us an example of what third party app's you want to install.


I downloaded the Full Circle Magazine from the Software center.  In it there was a link to download a notifier but it wasn't through the software center.   i downloaded the file " mrmonday-full-circle-notifier-19f6ddb13ab6.tar.gz"   and now i'm trying to figure out how to install this thing.

---

### Post by jerrrys on 2012-02-12
> **brentv911 said:**
> I downloaded the Full Circle Magazine from the Software center.  In it there was a link to download a notifier but it wasn't through the software center.   i downloaded the file " mrmonday-full-circle-notifier-19f6ddb13ab6.tar.gz"   and now i'm trying to figure out how to install this thing.

Easy, just double click on it and extract.  then read the read me file(s) for futher instruction.

---

### Post by brentv911 on 2012-02-12
> **jerrrys said:**
> Easy, just double click on it and extract.  then read the read me file(s) for futher instruction.


Ok here is possibly another dumb question..  I don't see a readme file.  but i do have a file called 
installer.nsi

In linux is there a certain file type that would be the installer like there is in windows?

---

### Post by jasonrisenburg on 2012-02-12
It is just as easy to run Ubuntu as it is windows. I do just about everything on linux that I can do on windows. I am nowhere near a power user either. now a days there is a ton of options for everyone to do anything. Ide start in the software center. look for something that interests you. or look for a option that you like to do in window pick it up in Ubuntu.

---

### Post by jerrrys on 2012-02-12
If you will give me a link to this file, I will install it and see what the deal is.

---

### Post by kc1di on 2012-02-12
> **brentv911 said:**
> I downloaded the Full Circle Magazine from the Software center.  In it there was a link to download a notifier but it wasn't through the software center.   i downloaded the file " mrmonday-full-circle-notifier-19f6ddb13ab6.tar.gz"   and now i'm trying to figure out how to install this thing.

Hi what you downloaded was not a program the program is actually located in their repository you would have to go to the following page and follow the instructions for adding their ppa to your repository list. 
here the web address you need:
[http://notifier.fullcirclemagazine.org/download.html]("http://notifier.fullcirclemagazine.org/download.html")

on that page you will see instruction like this :
```
sudo add-apt-repository ppa:laurent-parenteau/full-circle-notifier
 sudo apt-get update
 sudo apt-get install full-circle-notifier
```

Open a terminal and copy one line at a time and hit enter after each line
When it's complete you should have the notifier on your machine.
Good Luck,
dave

---

### Post by jorpoveda on 2012-02-12
In Ubuntu the easiest way to install something outside the Software Center is to download .deb files. When you have it just double click an it will automatically start installing.

---

