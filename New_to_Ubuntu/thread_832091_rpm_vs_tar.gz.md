---
title: "rpm vs tar.gz"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-06-17
Ok, this is a hypothetical question.If I want some application, but I can't find a .deb file only a .rpm and a tar.gz, what would be best to do:try to translate the .rpm into a .deb, or start from scratch and compile the source file?
I;m new to linux, but I'm eager to learn. :)

---

### Post by stchman on 2008-06-17
> **Troll_the_Great said:**
> Ok, this is a hypothetical question.If I want some application, but I can't find a .deb file only a .rpm and a tar.gz, what would be best to do:try to translate the .rpm into a .deb, or start from scratch and compile the source file?
I;m new to linux, but I'm eager to learn. :)

You can use alien to convert an rpm to a deb.  A .tar.gz is an archive that usually contains source code.

From everything I have read building from source is better than package conversion but more of a PITA.

It will be pretty rare that you cannot find a .deb package to do what you want.  I also look aw [www.getdeb.net](www.getdeb.net) for Ubuntu packages.

---

### Post by Tomatz on 2008-06-17
If you compile from source the app will be more compatible to your system so compiling is always the best route other than official deb packages.

Only convert an rpm if you cant get the source. E.g you need to install a lexmark printer driver as they only release them in rpm not deb or source ;)

---

### Post by bufsabre666 on 2008-06-17
id always compile if at all possible, it matches the file to your system so much better than even debs

---

### Post by feisty john on 2008-06-17
I have only recently passed out of the n00b stage, and I had trouble for the longest time compiling from source. Basically, I didn't know where to put things or what to do if something was slightly different from textbook. I found the following resources immensely useful, so I hope they're useful to you or someone else reading this thread:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[http://www.firewall.cx/linux-introduction-installing-software.php](http://www.firewall.cx/linux-introduction-installing-software.php)
[http://articles.techrepublic.com.com/5100-10878_11-1060693.html](http://articles.techrepublic.com.com/5100-10878_11-1060693.html)

---

### Post by JohnPta on 2008-06-22
> **stchman said:**
> You can use alien to convert an rpm to a deb.  A .tar.gz is an archive that usually contains source code.

From everything I have read building from source is better than package conversion but more of a PITA.

It will be pretty rare that you cannot find a .deb package to do what you want.  I also look aw [www.getdeb.net](www.getdeb.net) for Ubuntu packages.

Ok I will sound very stupid now, but I manage to install "Alien" convert package. But now I can not find the "Alien" program in Applications not in System/Preferences and not in System/Administration nor the sub categories. Please advice me where to look for that Package/Application.

---

### Post by meindian523 on 2008-06-22
In terminal,simply run

```
alien <target name.rpm>
```

The default option is to convert to deb,though you can convert a deb to an rpm too,if you want to.

---

### Post by Paqman on 2008-06-22
> **bufsabre666 said:**
> id always compile if at all possible, it matches the file to your system so much better than even debs

I disagree strongly. Compiling from source breaks the dependency system of the package manager, which introduces instability to your system. Compiled software is also much more difficult to uninstall cleanly.

If you're using a compile-only distro, then compiling is good. On a distro that uses a package-manager it's a bad idea. Proper .debs are always the best option.

---

### Post by Paqman on 2008-06-22
> **JohnPta said:**
> But now I can not find the "Alien" program in Applications

It's a command-line tool. Use:
```

sudo alien -i <package name>

```

To build and install the package. It'll create a .deb, meaning you'll see the package listed in Synaptic and can uninstall it from there if you want.

---

### Post by meindian523 on 2008-06-22
> **Paqman said:**
> I disagree strongly. Compiling from source breaks the dependency system of the package manager, which introduces instability to your system. Compiled software is also much more difficult to uninstall cleanly.

If you're using a compile-only distro, then compiling is good. On a distro that uses a package-manager it's a bad idea. Proper .debs are always the best option.
I agree.Compiling provides only a small and insignificant increase in the speed of response,which is not even worth the time the box spends on compiling the package.

---

### Post by gfg on 2008-06-22
> **Paqman said:**
> I disagree strongly. Compiling from source breaks the dependency system of the package manager, which introduces instability to your system. Compiled software is also much more difficult to uninstall cleanly.

If you're using a compile-only distro, then compiling is good. On a distro that uses a package-manager it's a bad idea. Proper .debs are always the best option.

While I always prefer to install debs, if you use "checkinstal"l to install compiled software, it will show up in the package-manager, so it's easy to remove it.

---

### Post by Paqman on 2008-06-22
> **gfg said:**
> While I always prefer to install debs, if you use "checkinstal"l to install compiled software, it will show up in the package-manager, so it's easy to remove it.

Ah i'd forgotten about checkinstall, very handy little app. Good tip!

---

### Post by doug1212 on 2008-06-22
Sometimes you have no choice but to install from source, I had to for wlan driver on my laptop and my dlan ethernet over powerline config app.

Some folks even go to trouble of building amorok and the like from source to get support for some obscure DAP.

As long as I remember not to do a dist upgrade and only do a fresh install :)

---

### Post by JohnPta on 2008-06-23
> **Paqman said:**
> It's a command-line tool. Use:
```

sudo alien -i <package name>

```

To build and install the package. It'll create a .deb, meaning you'll see the package listed in Synaptic and can uninstall it from there if you want.

I tried, to my opinion, all possibilities but I keep on getting this error message.  

[COLOR="Red"]jan@jan-desktop:~$ sudo alien -i avast4workstation-1.0.8-1.i586.rpm
File "avast4workstation-1.0.8-1.i586.rpm" not found.
[/COLOR]

I even tried to copy the file to the desktop, because to my opinion, I am in the Desktop directory. But that also not works. 

My original down loaded file is in the [COLOR="Blue"]/home/jan/Downloads/Avast[/COLOR] directory. How do I change directory?

---

### Post by Barrucadu on 2008-06-23
You are in your home folder (/home/jan). You can change directory with the 'cd' command, but remember that it is case sensetive.

---

### Post by meindian523 on 2008-06-23
1:Your opinion is wrong.You are in your home directory ie /home/jan
2:Assuming that the downloaded file is now on your desktop,you need

sudo alien -i ~/Desktop/avast.....rpm

---

### Post by Tomatz on 2008-06-23
To make it easier for you open a terminal and type:

```
sudo apt-get install nautilus-open-terminal
```

Once that has installed **logout and login**.

Then just r-click (on the desktop or the filemanager nautilus) and you will see an option **"open terminal here"**.

Self explanatory from there though i do suggest you buy an ebook explaining the bash shell ;)

---

### Post by balagosa on 2008-06-23
I go with tar.gz as noted by my "VMware installation" experience.

I had two Installers, both of the same versions. I first tried the .rpm (reading that it is convertible to .deb via alien); this did not work. I tried Installing it via rpm, also did not work. Maybe i just suck at configuring rpm, because i never got it to work. tar.gz on the other hand was flawless. just followed the basic commands of: 1)configure 2)cd <directory> 3)make 4)make isntall.

Note: I was still an Ubuntu noob when i first tried this (2 day old Ubuntu user)

---

