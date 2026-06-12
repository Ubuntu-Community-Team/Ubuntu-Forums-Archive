---
title: "how to install .tar.gz file"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by shreyanshjain8 on 2008-11-14
can any1 tell me the commands in terminal to install a .tar.gz extension files....


i want to install G3Dviewer

---

### Post by underground on 2008-11-14
> **shreyanshjain8 said:**
> can any1 tell me the commands in terminal to install a .tar.gz extension files....


i want to install G3Dviewer

Right click on the file and select extract here.Now you can go to the folder without terminal and there should be a read me file...it has the installation commands...if there is no read me file but there is a file named configure do the following
Open terminal..navigate to the extracted folder..and enter the commands
./configure
sudo make
sudo make install

If there are no errors during configure the next commands should work..

---

### Post by dmizer on 2008-11-14
Three questions:

1) Why are you trying to install G3Dviewer?
2) Why are you trying to install G3Dviewer from source?
3) Is there a specific reason why you would need G3Dviewer?

Ubuntu already has 3D graphics capability installed by default, all you have to do is click to enable it under the desktop settings.

Also, please give people time to find and respond to your threads. Your trouble is no more or less important than anyone else. If you need immediate help, you're better off using the IRC channel: [http://www.ubuntu.com/support/community/chatirc](http://www.ubuntu.com/support/community/chatirc)

Thank you.

---

### Post by 3rdalbum on 2008-11-14
g3dviewer looks like old software... last updated in 2006?

When you want to install software on Linux, first you should check if there's an equivilant program available in Synaptic Package Manager. A quick search didn't yield any leads, but maybe my search terms were wrong.

Next, you should look for an Ubuntu or Debian repository that holds the packages. In this case, I found one on the offical g3dviewer website: [http://automagically.de/g3dviewer/](http://automagically.de/g3dviewer/)

Add the line that begins "deb " to your Third Party Software tab in the Software Sources control panel. Reload the package list and you will find g3dviewer ready to install from Synaptic Package Manager.

If you couldn't find a repository, you would look online for a DEB or RPM package.

Compiling from source code isn't difficult once you know how, but even though I *can* compile I'd rather make life easier for myself and get a prebuilt package.

---

### Post by iaskedalice09 on 2008-11-14
Also if you are compiling from source please don't forget to install build-essential!

It's a shame the How to Install ANYTHING in Ubuntu guide is down. It is very clear.

Basics in Terminal:

```

cd /home/bob/Desktop/test/

```

**c**hanges the **d**irectory to /home/bob/Desktop/test/
you can also write it as ~/Desktop/test/

Installing/Uninstalling/Searching for Software in Terminal

```

sudo apt-get install **package-name**
sudo apt-get remove **package-name**
sudo apt-cache search **package-name** or **description of package or its functions**

```

I hope this helps! Though, you should take it easy for awhile and use Synaptic. It is in System > Administration > Synaptic Package Manager

When you enter a password in Terminal it shows up blank *this is normal*.
When you enter a password in Synaptic it shows up as dots.

Terminal is in Applications > Accessories > Terminal
...though I *highly* recommend using Synaptic, in System > Administration > Synaptic Package Manager until you get more comfortable with this fabulous OS!

Good luck and post if you have problems - that's what we're here for! :-)

---

### Post by shreyanshjain8 on 2008-11-14
thanx every body for there valuable time....


i tried using the commands but a error came " glib >= 1.2.0 not found
"

..so nowwhat to do...

---

### Post by dmizer on 2008-11-14
> **shreyanshjain8 said:**
> ..so nowwhat to do...

You are trying to do a difficult procedure which is almost certainly not necessary.

Why do you need this software? Or to be more precise ... does compiz not work on your computer?

---

### Post by philinux on 2008-11-14
It's not compiz it's a 3d modeling cad like tool.

---

### Post by dmizer on 2008-11-14
> **philinux said:**
> It's not compiz it's a 3d modeling cad like tool.

Interesting, that's not what I gathered when I looked it up. Looked more like a 3d desktop effect.

---

### Post by gangsta.mostwanted on 2008-11-19
Dear Friends, I have a similar issue.. I am unable to install a software on Ubuntu. This is an expensive software and I was using it on windows machine from last some time. the strange thing is there is no config. file in that folder... 


I was able to ger one similar thread but it was closed, please check the link below
[http://ubuntuforums.org/showthread.php?t=324712&page=2](http://ubuntuforums.org/showthread.php?t=324712&page=2)



I have extracted the file on the desktop and I have to similar file structure... the only difference between this thread and my post is I have a  registered version of this software...


Please help me to install this package on ubuntu..

Thanks,
Mukesh

---

### Post by dmizer on 2008-11-19
> **gangsta.mostwanted said:**
> Dear Friends, I have a similar issue.. I am unable to install a software on Ubuntu. This is an expensive software and I was using it on windows machine from last some time. the strange thing is there is no config. file in that folder... 


I was able to ger one similar thread but it was closed, please check the link below
[http://ubuntuforums.org/showthread.php?t=324712&page=2](http://ubuntuforums.org/showthread.php?t=324712&page=2)



I have extracted the file on the desktop and I have to similar file structure... the only difference between this thread and my post is I have a  registered version of this software...


Please help me to install this package on ubuntu..

Thanks,
Mukesh

Is the software made for Linux (not Windows only)? If it is linux software, and it's registered, your best bet will be to consult the makers of the software for installation directions. If it's paid for and registered, you will have better support from them than you will get here.

---

### Post by oldos2er on 2008-11-19
> **shreyanshjain8 said:**
> can any1 tell me the commands in terminal to install a .tar.gz extension files....


i want to install G3Dviewer

 A tar.gz extension on a file tells you nothing of what it contains; it could be source code, or it could be precompiled binaries, or something else entirely. Once you extract it, there should be some documentation that explains what to do.

---

### Post by gangsta.mostwanted on 2008-11-19
Thanks for help guys.. I am using Windows from last 10 years and not I am trying to move to Ubuntu (Linux based OS) that's the reason I am trying to understand whats going on here with this software. 

Yes, this is a fully register software and I have consulted with the Silvaco Tech Support and still waiting for there reply. I am just trying to get the things done ASAP that's the reason I have started this thread. 

Yes, the package I am talking about is for 32 bit Linux OS. the strange thing is there there is no Configuration file or folder on the extracted Tar.gz folder.  i have extracted that Tar folder and there are only few folder that I am listing below..

bin
doc
etc
examples
lib
updates
var

Thanks,
Mukesh

---

### Post by Keen101 on 2008-11-19
@gangsta.mostwanted

In your case it's probably not source code at all, it's probably pre-compiled software and there is probably an executable file that you can run if you can figure out what file.

browse to the folder in terminal, and try this in terminal but replace with correct name:

./silvacosoftwareprogram

@shreyanshjain8

it depends on what kind of software.
usually doing the 
./configure
sudo make
sudo make install

(after doing "sudo apt-get install build-essential" that is)

usually works fine,
but, sometimes it's a different install file...

something like:

./install-py

or

./install-flashpalyer-10

---

### Post by oldos2er on 2008-11-19
> **gangsta.mostwanted said:**
> 
Yes, the package I am talking about is for 32 bit Linux OS. the strange thing is there there is no Configuration file or folder on the extracted Tar.gz folder.  i have extracted that Tar folder and there are only few folder that I am listing below..

bin
doc
etc
examples
lib
updates
var


 "doc" is short for documentation, so you might want to have a look inside it for information.

---

### Post by dmizer on 2008-11-20
> **oldos2er said:**
> "doc" is short for documentation, so you might want to have a look inside it for information.

A "README" file may also be in the home directory. It would have information on how to install it.

---

