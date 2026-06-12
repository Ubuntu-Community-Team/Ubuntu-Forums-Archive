---
title: "Installing an application from an online source..how do I do this?"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by DBUKOFFS on 2012-01-29
I am a very new user to Linux and have been using Ubuntu 11.10 for a few months now. I have been trying to install Absinthe for Linux version from this site [http://www.iphonehacks.com/2012/01/absinthe-jailbreak-iphone-4s-ipad-2-updated-supports-linux.html](http://www.iphonehacks.com/2012/01/absinthe-jailbreak-iphone-4s-ipad-2-updated-supports-linux.html). I tried to figure it out..but I don't know what I am doing wrong..any ideas?

---

### Post by chughes27 on 2012-01-29
Well download the file from the site, then find it and double click it. It should open up in a program called archive manager. Then hit the button that says "Extract" and then choose a location to extract it to. When its done extracting, find the folder where you extracted it and run the program absinthe.x86 or absinthe.x86_64 depending on if your computer runs 64 or 32 bit.

Hope this helps! :D

---

### Post by sanscents on 2012-01-29
> **chughes27 said:**
> It should open up in a program called archive manager.

Your file is a tar.gz, so you have to figure out how to install tar.gz files, called tarballs.   Ubuntu's Archive Manager only handles .deb files, I think.  I've never  installed a tar.gz.

---

### Post by DBUKOFFS on 2012-01-29
See I tried this many times with no luck. I extract everything and once I click the x86 file to run...it doesn't do anything. I researched tar.gz files but I have no idea what anyone is talking about..nobody really explains how to do it step by step

---

### Post by grahammechanical on 2012-01-29
Try a right click and select Open with Ubuntu Software Centre. The Software Centre should load giving you an option to install and the Software Centre will install the deb package for you. I think that a double click on the deb file will also do this.

Then look for an icon in the Dash to run the program. You can use the software Centre to remove the application as well as install it.

Regards.

---

### Post by Elfy on 2012-01-29
> **sanscents said:**
> Your file is a tar.gz, so you have to figure out how to install tar.gz files, called tarballs.   Ubuntu's Archive Manager only handles .deb files, I think.  I've never  installed a tar.gz.
You might be thinking of gdebi - archive manager is just that ;)
> **DBUKOFFS said:**
> See I tried this many times with no luck. I extract everything and once I click the x86 file to run...it doesn't do anything. I researched tar.gz files but I have no idea what anyone is talking about..nobody really explains how to do it step by stepAssuming you extracted it to the desktop open a terminal and do

```
cd ~/Desktop/absinthe-linux-0.3/
```

then

./abs<tab>

tab to autocomplete the name - either the 32 or 64 bit

You might find that you need other packages as you go. 

Some general compiling pages 

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

There is a 'ubuntu' specific search engine in my sig - use that to look for things - most have already been addressed at some point :)

---

### Post by VraiChevalier on 2012-01-29
I am not one to suggest a person Read The Fine Manual but in this instance I think you would be best served by reading up on installing software under Linux.

A quick search of the internet reveals a wealth of how-to's, tutorials, and videos on the subject.

Here are a few possible search terms: "how do i install programs on linux",
"how to install anything in linux", "install software in linux".

And here is a page on compiling from source: [http://howto.wired.com/wiki/Compile_Software_from_Source_Code](http://howto.wired.com/wiki/Compile_Software_from_Source_Code)

---

### Post by Elfy on 2012-01-29
> **grahammechanical said:**
> Try a right click and select Open with Ubuntu Software Centre. The Software Centre should load giving you an option to install and the Software Centre will install the deb package for you. I think that a double click on the deb file will also do this.

Then look for an icon in the Dash to run the program. You can use the software Centre to remove the application as well as install it.

Regards.

It's a tarball :)

---

### Post by mcduck on 2012-01-29
> **DBUKOFFS said:**
> See I tried this many times with no luck. I extract everything and once I click the x86 file to run...it doesn't do anything. I researched tar.gz files but I have no idea what anyone is talking about..nobody really explains how to do it step by step

The reason is because a .tar.gz is justa  compressed archive which can contain any types of files, just like a ZIP archive. So there is no generic rule how it's contents should be installed. Perhaps it's something that you just need to extract somewhere and run, perhaps it's source code that needs to be compiled into executable program, perhaps there's a script or installer program included, or maybe something completely different. You might also need to install other things or make some additional configurations to make the program work.

However, pretty much every time you will either find instruction included in the archive, or on the web site where you downloaded it.

Anyway, in this case it seems the archive contained a pre-compiled program, ready to run as it is. So all you need to do is right-click it, select Properties, and on the Permissions-tab make sure the "Allow executing file as program"-checkbox is marked. After that double-clicking the program should work.

---

### Post by sanscents on 2012-01-29
> **forestpiskie said:**
> You might be thinking of gdebi - archive manager is just that 

That's exactly what I meant :cool:

> Originally Posted by **DBUKOFFS** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11648984#post11648984") 				
 				*See I tried this many times with no  luck. I extract everything and once I click the x86 file to run...it  doesn't do anything. I researched tar.gz files but I have no idea what  anyone is talking about..nobody really explains how to do it step by  step*


I've used psychocats as a resource before - [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

