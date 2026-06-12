---
title: "[SOLVED] What happens if..."
date: 2008-08-22
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-08-22
I installed the "home" directory on a different partition as recommended in several forum posts. Everything is working fine, but being a Windows power user and Linux newbie I'm installing and testing a lot of applications. Some work well for me, some doesn't. So I'm starting to use the Synaptic Manager to completely wipe out those applications that I don't want anymore.

I have a few concerns:

1 - Could Linux lose performance because of removed applications left-overs like Windows?

2 - What happens if after some weeks testing I decide to format the system drive and re-install a clean Ubuntu, without formatting the "home" partition? Does all my installed programs, personal files and configurations will be preserved inside the "home" partition? Do I still need to install all applications again?

3 - How do I clean up the system without re-installing Ubuntu? I don't want any left-overs making a party inside my system.

---

### Post by mevets on 2008-08-22
1/3 - Generally this is not a problem. When you uninstall packages some do get left behind though. There are a couple things you can do. One that comes to mind is running
```
sudo apt-get autoremove
```
Understand that if you uninstall apps in synaptic that their configuration files are often left behind. This is done because you might decide to reinstall the app. Select "completely" remove in Synaptic to get rid of configurations files as well when you uninstall an app.

2 - If you format / (root) you will not harm the configuration for most your apps. But, yeah you will have to reinstall the apps again. Up side is that once you install the apps, it will seem like you never reinstalled, cause the apps will be configured just as they were before you reinstalled.

---

### Post by xeth_delta on 2008-08-22
As a side note to 1. If you want to completely remove a program together with its configuration files, you can select the package for complete removal in synaptic or from the command line:
```
apt-get purge package_name
```
or
```
aptitude purge package_name
```
As usual, when removing something read carefully what is being done before approving a change, so that nothing vital to the system is taken out.

---

### Post by lovinglinux on 2008-08-23
Thanks for the quick replies. Very helpful, specially now that I installed something that is messing with compiz.

> **mevets said:**
> Up side is that once you install the apps, it will seem like you never reinstalled, cause the apps will be configured just as they were before you reinstalled.

AWESOME! I'm starting to hate Windows and regret not using Linux before.

> **xeth_delta said:**
> As usual, when removing something read carefully what is being done before approving a change, so that nothing vital to the system is taken out.

That is the tricky part :)

---

### Post by lovinglinux on 2008-08-23
Freaking awesome! I already have a clean install with almost all apps installed and configurations still intact.

Now I see how handy the "sudo apt-get" command is. I can download all my apps with a simple copy & paste action \\:D/

---

### Post by nothingspecial on 2008-08-23
If you use aptitude to install and remove apps 

```
sudo aptitude install
```

```
sudo aptitude remove
```

it will find and automatically remove any unneeded dependencies that were installed with the package you are removing.

This wont work if you installed the package with apt-get

---

### Post by lovinglinux on 2008-08-23
> **nothingspecial said:**
> If you use aptitude to install and remove apps 

```
sudo aptitude install
```

```
sudo aptitude remove
```

it will find and automatically remove any unneeded dependencies that were installed with the package you are removing.

This wont work if you installed the package with apt-get

I would like understand this. Please correct me if I'm wrong.

 When you want to install or remove a new applet you can use the GUI or CLI. In the first case you can use the "Add/Remove" manager or the "Synaptic Manager". The first will not remove dependencies, but will install necessary ones. That's why some apps ask you to use the Synaptic for removal, because it can install and remove all dependencies.

So, I guess using the CLI, "apt-get" is the command for accessing the "Add/Remove Mananger" backend and "aptitude install" or "aptitude remove" are commands to use the "Synaptic Manager" backend, right?

Which one is use when you download and install a "*.deb" file or when you click an apt URI?

---

### Post by nothingspecial on 2008-08-23
I believe that both add/remove and synaptic use apt-get -  someone please correct me if I`m wrong.
Also I beleive it is possible to get in a mess if you chop and change between apt-get and aptitude. If you have used synaptic, add/remove and apt-get alot in the past it is probably better to stick with them - there is apt-get autoremove. 
If you can remember what you installed every program with then it doesn`t matter but problems arise because you should remove something  with the same command you installed it with.
Hope that makes sense.

---

### Post by lovinglinux on 2008-08-23
> **nothingspecial said:**
> I believe that both add/remove and synaptic use apt-get -  someone please correct me if I`m wrong.
Also I beleive it is possible to get in a mess if you chop and change between apt-get and aptitude. If you have used synaptic, add/remove and apt-get alot in the past it is probably better to stick with them - there is apt-get autoremove. 
If you can remember what you installed every program with then it doesn`t matter but problems arise because you should remove something  with the same command you installed it with.
Hope that makes sense.

It makes sense that could cause problems, because it is almost impossible to remember how I installed every app. This could lead to big mess, specially because a newbie like me tend to follow instructions from the forum posts by the book, usually without knowing the difference between "apt-get" and "aptitude". 

Usually when I want to simply remove an app I go to "Add/Remove" manager. When I want to wipe out personal configurations I go to Synaptic and select "completely remove" option, which I guess is the interface for "aptitude remove". I'm using CLI only when suggested by tutorials from this forum.

---

### Post by ibuclaw on 2008-08-23
If you accidentally remove, just reinstall.

Ubuntu won't let you do the really hazardous things, like remove perl-base, for instance.

You will get a message like so:
> 
You are about to do something potentially harmful
To continue type in the phrase &#8216;Yes, do as I say!&#8217;


But equally, it is better to use a package manager, rather than apt-get (aptitude and synaptic) simply because you can **see** what you are doing.
That way, you can decide for yourself whether it be a good or bad thing...

[EDIT]
Alternatively, you could dry-run the install/removal process before actually doing so.
```
sudo apt-get --simulate
```
and you'll be able to see what apt-get will do to your system had the command been ran.

Regards
Iain

---

### Post by youthforlinux on 2008-08-23
If you  use Synaptic most of the time and mix in with aptitude you should be ok if you run ```
sudo apt-get autoremove
``` as stated above to make sure you don't have useless package dependencies floating around!

---

### Post by Cheesehead on 2008-08-23
> **lovinglinux said:**
> ...it is almost impossible to remember how I installed every app.

While I love the command line, and use 'apt-get', I do a lot of experimenting using Synaptic because it has a HISTORY feature, showing what you installed/removed and when.  File-->History. 

Very handy for undoing a mess later without trying to *remember* what I did. It takes more screen space at times, and it's slower than just typing it, but it *saves* time in the end.

---

### Post by lovinglinux on 2008-08-26
> **Cheesehead said:**
> While I love the command line, and use 'apt-get', I do a lot of experimenting using Synaptic because it has a HISTORY feature, showing what you installed/removed and when.  File-->History. 

Very handy for undoing a mess later without trying to *remember* what I did. It takes more screen space at times, and it's slower than just typing it, but it *saves* time in the end.

Very nice tip. I was wandering if Ubuntu has this feature, mainly because I would like to create an install command for all software I have installed after the OS, in case I need to re-format my system drive. 

Can I install all apps again with a single command? I yes, which command would be better to use? Does the history display installed dependencies?

---

### Post by silverglade00 on 2008-08-26
Open up Synaptic and click on the File menu. Choose the one called Save Markings As... Give it a name and make sure it is in your home folder (after you reinstall, it will still be there!). Check the Save full state box and it will save a list of what is installed and what isn't. This is used for installing the same packages on multiple machines, but it will server your purpose as well. I have used this in the past when reinstalling and it works great.

---

### Post by lovinglinux on 2008-08-26
> **silverglade00 said:**
> Open up Synaptic and click on the File menu. Choose the one called Save Markings As... Give it a name and make sure it is in your home folder (after you reinstall, it will still be there!). Check the Save full state box and it will save a list of what is installed and what isn't. This is used for installing the same packages on multiple machines, but it will server your purpose as well. I have used this in the past when reinstalling and it works great.

OMG. Why I was still using Windows after so many years?

This is freaking beautiful. Thank you very much.

I will test it on a virtualbox.

---

