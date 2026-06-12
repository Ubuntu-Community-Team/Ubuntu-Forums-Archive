---
title: "Offline Software Installation in Ubuntu"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by cortman on 2011-12-26
**[SIZE="3"]Offline Software Installation in Ubuntu[/SIZE]**

There's been a number of requests for help regarding installing programs in Ubuntu without an internet connection. It was one of my first questions when I started using Ubuntu, so I thought I'd make this thread to explain how.
This tutorial assumes you have access to another Ubuntu machine that is online, and Synaptic Package Manager is installed on both machines.


[SIZE="2"]**1.**[/SIZE] Open a terminal with Control+Alt+t and type

```
synaptic
```

This will open the Synaptic Package Manager. You can browse available software in the column on the far left, or if you know specifically what you're looking for, type it into the search box.
When you find the software you want to install, right click it and select "Mark for Installation". If a dialog comes up "Mark Additional Required Changes" select Mark. This will ensure that all the packages required for the selected software get installed as well.

[SIZE="2"]**2.**[/SIZE] Once you've picked your software, go to File>Generate Package Download Script. Save the script to a USB flash drive or some other portable media. You can name the script whatever you want, but for clarity we'll assume you named it "download".
The Package Download Script is just a little text file (with a .sh extension) that will tell your online computer which packages to download, so you can transfer them to the offline computer.

**[SIZE="2"]3.[/SIZE]** Take the flash drive to your online computer. Create a new folder called "packages" in the home folder to hold the downloaded packages, and copy the script to that folder.

[SIZE="2"]**4.**[/SIZE] Open up a terminal on the online computer using Control+Alt+t, and type

```
cd package
```

Now type

```
chmod +x download.sh
```

And finally

```
./download.sh
```

This will download the packages to the folder containing the script. If you open the package in a file manager you'll see one or more files with the extension .deb. These are the software package files. 

[SIZE="2"]**5.**[/SIZE] Copy the "packages" folder containing the .deb files to the flash drive and onto the /home folder of the offline computer.

[SIZE="2"]**6.**[/SIZE] Open up a terminal on the offline computer and type

```
sudo dpkg -iR packages
```

You'll be prompted for your administrator password, which will be the same as your user login password. Enter it and Ubuntu will install your software!

---

### Post by Frogs Hair on 2011-12-26
Thank You
 
I will bookmark this and add a link for an offline software center .

[http://www.webupd8.org/2011/12/portable-software-center-create-custom.html#more](http://www.webupd8.org/2011/12/portable-software-center-create-custom.html#more) (Offline Software Center)

---

### Post by jerrrys on 2011-12-26
this is all good if you have synaptic installed

also

[http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/](http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/)

---

### Post by cortman on 2011-12-26
> **jerrrys said:**
> this is all good if you have synaptic installed

also

[http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/](http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/)

Good point.

I've added a way to get Synaptic installed at the bottom.

---

### Post by jerrrys on 2011-12-26
> **cortman said:**
> Good point.

I've added a way to get Synaptic installed at the bottom.

I like that, but wont a fresh install of synaptic also require an update?

---

### Post by cortman on 2011-12-27
I tested the Synaptic installation out on a fresh installation of 11.10 in VBox, and I can confirm that you're right, Jerry. Apparently aptitude doesn't come bundled with any repo information, or else Synaptic simply isn't grabbing it.
I'm curious, though. Would there be some way to update Synaptic offline?

---

### Post by jerrrys on 2011-12-27
Update Synaptic offline?

Never done this, but looks like you can:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=update+synaptic+offline&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=update+synaptic+offline&sa=Search&cof=FORID:9)

---

### Post by cortman on 2011-12-27
Very good- looks possible. I'm working on this right now.

---

### Post by elliotn on 2011-12-27
> **jerrrys said:**
> Update Synaptic offline?

Never done this, but looks like you can:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=update+synaptic+offline&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=update+synaptic+offline&sa=Search&cof=FORID:9)

is there a way to  update repository list offline? I am yet to find a working way 

you can install downloaded packages using synaptic by going to file add downloaded packages. synaptic will load them and ignore those that don't meet dependency satisfaction

---

### Post by jerrrys on 2011-12-27
> **elliotn said:**
> is there a way to  update repository list offline? I am yet to find a working way 

you can install downloaded packages using synaptic by going to file add downloaded packages. synaptic will load them and ignore those that don't meet dependency satisfaction

Cortman wants to update, but you could also:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=offline+repositories&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=offline+repositories&sa=Search&cof=FORID:9)

---

### Post by grahammechanical on 2011-12-27
This is also useful for those who are on-line but using a dial-up modem. 

When I was using a dial-up modem I would install the latest Ubuntu from a DVD given away by a computer magazine. Then I would have to download those extra programs that I wanted to use. I always wanted to know how to do this in the off-line way.

Thank you.

Regards.

---

### Post by cortman on 2011-12-27
Glad some of y'all find it useful.

Updating Synaptic offline seems to be rather involved but possible. I'm doing the research now. What I think I'll do is leave this thread as it is, and start a new one on installing and updating Synaptic offline. Maybe I'll put a link or something then at the bottom of this one.

---

### Post by cortman on 2011-12-27
OK! Got the offline update thing figured out. I'm working on the second tutorial right now.

---

### Post by cortman on 2011-12-28
Alright! [Tutorial completed]("http://ubuntuforums.org/showthread.php?t=1901441"). I'm going to get it posted in Tutorials & Tips as well, but for now it's in Absolute Beginner.

---

### Post by jerrrys on 2011-12-29
Congratulations :)

---

### Post by cortman on 2011-12-29
> **jerrrys said:**
> Congratulations :)

Thanks!!

---

