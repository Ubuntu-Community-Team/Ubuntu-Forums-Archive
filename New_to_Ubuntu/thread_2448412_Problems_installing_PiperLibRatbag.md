---
title: "Problems installing Piper/LibRatbag"
date: 2020-08-07
forum: New to Ubuntu
---

### Post by hajnyckel on 2020-08-07
[HR][/HR]                        
 Greetings.


 
I am new to Linux and have been running Ubuntu 20.04 for a few weeks now trying to make sense of how to use it which I find somewhat difficult as I came from Windows 7 it is to be expected. I am trying to get the program Piper to run as I would like to be able to set up my mice, Logitech M705, with macros, scroll speed and more to work in games, browsing the internet as I could do in the Logitech proprietary drivers for windows (maybe not exactly the same but at least somethings). However, I now have run in to a small problem that I cannot solve. First I used the Ubuntu Software to install Piper and from Piper I had to install Ratbag from the guide at Github ([https://github.com/libratbag/libratbag](https://github.com/libratbag/libratbag)). I follow the guide:

```
git clone https://github.com/libratbag/libratbag.git
cd libratbag
meson builddir
``` 
When I get to meson builddir I get some errors, missing packages. I managed to install the needed packages using Synaptic package manager until now. I get this error &#8220;meson.build:369:1: ERROR: Dependency "check" not found, tried pkgconfig and cmake&#8221;. This dependency &#8220;check&#8221; I cannot find so I am in need of some guidance on how to fix this so I can keep working on getting Piper running.


 
A second thing, as I have instilled several packages to get libratbag to work I do wonder if there is a simpler way, a way to install all the required packages at once so I do not have to look for each and everyone?


 
Kind regards

---

### Post by CatKiller on 2020-08-07
So, last question first. Yes, if a package is included in the repositories, there is a way to install all of its build dependencies in one go. I can't remember the command off the top of my head, though.

However, for the overall point, compiling from source isn't the best way to install things if you're new to Linux. Project websites have build instructions because the only people that need to be looking at project websites are other developers that want to help. Downloading things from websites is not a good plan when you already have a package manager. For Piper, there is already a version in the (universe) repository, so you can just install that and it may well do what you want. If you need a newer version, there's [a PPA](https://launchpad.net/~libratbag-piper/+archive/ubuntu/piper-libratbag-git) which your package manager can use as a source for the newer software.

---

### Post by hajnyckel on 2020-08-07
Thank you @CatKiller.

As I thought that compiling from source is not a good idea for beginners. Also found out that my universe repository is are enabled and up to date, which really do not make any sens to me at this point. (Sorry if I am being stupid now) I do believe i managed to install the PPA from ([https://launchpad.net/~libratbag-piper/+archive/ubuntu/piper-libratbag-git](https://launchpad.net/~libratbag-piper/+archive/ubuntu/piper-libratbag-git)) using the commands:
```
sudo add-apt-repository ppa:libratbag-piper/piper-libratbag-git
sudo apt-get update

```
And next : sudo apt install ratbagd

Piper still will not run. What am I missing here?

---

### Post by CatKiller on 2020-08-07
> **hajnyckel said:**
> Piper still will not run. What am I missing here?

Do you get any error messages that might point to the issue?

As I recall, the versions of piper and libratbag are paired: for the version of Piper in the repositories you need the version of libratbag that's in the repositories, and for the PPA version of Piper you need the PPA version of libratbag. It's been a while since I played with it, though.

---

### Post by hajnyckel on 2020-08-08
Piper now says "Cannot find any device. Please make sure your device is supported and plugged in". According to the supported list my Logitech M705 is supported.
([https://github.com/libratbag/libratbag/tree/master/data/devices](https://github.com/libratbag/libratbag/tree/master/data/devices)) I found my device file installed in my libratbag folder and checked it with the document from the link and they match up. Tried to re-plugg my device and change USB port but nothing changed. Any more ideas?

Kind regards

---

### Post by CatKiller on 2020-08-08
So one thing to try is using ppa-purge to test using the versions from the standard repositories to see if there's been a regression, which does happen from time to time. That should automatically downgrade the versions, I think. It's easy enough to re-add the PPA afterwards if you do need the latest version. 

There are also ratbag commands that you can run from the command line to see how far it's getting in detecting your device.

Other than that, the wiki might have some information that might help you. The libratbag devs are quite friendly & helpful. I don't have that mouse, and it's been a while since I played with Piper at all.

---

### Post by hajnyckel on 2020-08-08
> **CatKiller said:**
> So one thing to try is using ppa-purge
Now I feel kind of stupid but I found how to do a PPA-purge I just seem to be unable to do it as I get the name wrong. Using "sudo ppa-purge ppa:name/here" tried both piper and libratbag. 

> **CatKiller said:**
> There are also ratbag commands that you can run from the command line to see how far it's getting in detecting your device.
I will see if I can find that command in the wiki, thank you :)

> **CatKiller said:**
> The libratbag devs are quite friendly & helpful. I don't have that mouse, and it's been a while since I played with Piper at all.
I will dig deeper into the wiki and see what I can find.
If I may ask, if you are not using Piper then which program, if any, are you using for you mouse?


Kind regards

---

### Post by CatKiller on 2020-08-08
> **hajnyckel said:**
> Now I feel kind of stupid but I found how to do a PPA-purge I just seem to be unable to do it as I get the name wrong. Using "sudo ppa-purge ppa:name/here" tried both piper and libratbag.  

One neat thing about the command line is Tab-completion. You can type the start of a command or filename and press Tab and the shell will fill in the rest. If there's more than one way to complete it, pressing Tab twice will show the options. For many commands, Tab-completion also works for arguments. 

> If I may ask, if you are not using Piper then which program, if any, are you using for you mouse?

My mouse stores its settings in firmware, so after I'd set the DPI and colours with Piper I didn't need to look at it again. I'd only need to fire it up if I wanted to change them to something else.

---

### Post by ajgreeny on 2020-08-08
The command needed for ppa purge to do what you want will use the same ppa name syntax as was used to add the repository, so in your case I think it should be ```
sudo ppa-purge ppa:libratbag-piper/piper-libratbag-git
```
This just replaces the ***add-apt-repository*** part of the command you used previously with ***ppa-purge***.

---

