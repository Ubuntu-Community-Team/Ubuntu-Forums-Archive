---
title: "cannot connect to x server ubuntu 12.04 with GNS3"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by AndyCole on 2012-10-18
I am studying for a network exam, and use a router simulator called GNS3. In order to get better performance I've installed it on Ubuntu 12.04, and it worked well. I just follwed a step by setp guide as I'm new to Ubuntu and 'nix in general.

Now when I try to start the application from the command line with the command "sudo python gns3" I'me getting an error message:

gns3: cannot connect to X server

I've tried searching for a solution to this on this site and also the gns3.net site, both search engines report that the search contains too many common words, so ignores them!

Earlier versions of Ubuntu allowed me to put the gns3 application in a folder, I am unable to locate the folder in this version, desktop is very different. However, if I can get this to work from the command line that will do for me.

How do I go about fixing this?

Andy

---

### Post by steeldriver on 2012-10-18
In general you shouldn't run graphical applications using sudo - the root environment is wrong - in particular root will likely not have Xauthority i.e. since you (the ordinary logged in user) 'owns' the display, no one else (not even root) can write to it (without jumping through some hoops)

Why are you trying to run it like that anyway? I just installed the version via Synaptic and the command to run it is just

```
gns3
```

---

### Post by AndyCole on 2012-10-18
I used sudo to run the program as that was what the installation instructions indicated I needed to do, and it has worked without any problem until yesterday. 

Looking over the original video that I used to install gns3 it states to run using sudo so that the application could access ethernet interfaces on the host PC.

Trouble is I'm well out of my comfort zone when it comes to Ubuntu, and this shows when a problem crops up.

Earlier versions of Ubuntu had a different desktop, I ran the gns3 application from the education folder, but I cannot find this folder in 12.04. I have read that its possible to set up the earlier desktop on 12.04 but cannot get that to work either.

---

### Post by steeldriver on 2012-10-18
well if you absolutely must run it with elevated permissions I would try

```
gksudo gns3
```

 (the gns3 executable appears to be a python script, but since it has a   #! you shouldn't need to specify the python interpreter explicitly)

---

### Post by audiomick on 2012-10-18
> **AndyCole said:**
>  I ran the gns3 application from the education folder, but I cannot find this folder in 12.04. 


That would indicate that the application is in a folder somewhere. You could try finding this folder using the document search. One of the options that the dash offers is that. I am not to sure, as I don't have a 12.04 install, but I was just looking at one in the live environment. If you press the super key (will likely have a windows logo on it...), or click on the ubuntu logo at the top of the bar on the left of screen, the dash will open. There are, I believe, four symbols at the bottom of the screen. Click on the one that looks like it might represent a sheet of paper, and type gns3 in the search box.

---

### Post by AndyCole on 2012-10-18
Steeldriver, I tried the gksudo command, that returns an error of unable to open display. 

However, I followed up audiomick's suggestion and found my way around the folders, when I click on the gns3 file I can get it to run.

You are correct, it is a python script, I took a look at this, I'm still puzzled as why it worked a couple of weeks back, but now no longer runs from the command prompt.

Anyway, at least I can get it to work so can continue with my studies. Just got to get Ubuntu to connect to my webdav drive now, but I'll ask that one in a seperate thread, thanks to both of you for your help.

Andy

---

### Post by AndyCole on 2012-10-19
Hmm, spoke to soon, have fallen foul of the Ubuntu permissions! I can run the application in the GUI, but when I come to save any projects, get permission denied, so cannot save my work. Have had a read up on permissions last night and think this is due to the way I installed the gns3 appication originally.

Also, I now understand why it had to be run with sudo. 

Getting there!

But still dont understand what the message regarding the x server means.

---

### Post by AndyCole on 2012-10-19
Sorted the permissions!

set my project folder to rwx for everyone.

---

