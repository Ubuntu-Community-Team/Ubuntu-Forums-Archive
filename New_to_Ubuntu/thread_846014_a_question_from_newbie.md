---
title: "a question from newbie"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by xieu90 on 2008-07-01
hi everyone
when I install new programs through Synaptic I can see that I need to download X MB and Y MB will be used
after my computer download X MB and installed a program what will happen with this X MB ? will my computer automatically delete it ?
and where does my computer store this X MB ? I'm just curious ^^

---

### Post by bumanie on 2008-07-01
The downloaded package has compression, that is why the installed package takes up more mb than the download. The download is how much bandwidth you use and the installed package is how much hard drive space it will use once installed.

---

### Post by benfindlay on 2008-07-01
They do get stored I think, however I don't know where. You can run a command which will purge these temporary installation files. The command is: ```
sudo apt-get clean
```

Hope this helps!

---

### Post by abhilashkumar on 2008-07-01
I think he wants to know whether the downloaded compressed package will remain on the system or not after installation?

---

### Post by sayakb on 2008-07-01
No, the computer will not automatically delete it. So actually you will lose X+Y MB diskspace.
To find the downloaded (but not installed) package, check /var/cache/apt/archives folder
To delete them all:
```
sudo apt-get clean
```
Note: the above command will not remove the installed program but just deletes the deb packages.

---

### Post by xieu90 on 2008-07-01
thank you ^^

there is nothing in archives , a bit strange 
an angel has deleted them for me ? where is my goddess ?
^^

---

### Post by Tomatz on 2008-07-01
It will be stored localy until you open a terminal and run the above command :)

---

### Post by benfindlay on 2008-07-01
Its stored until you remove them yourself, in /var/cache/apt/archives folder and you remove them by putting sudo apt-get clean into a terminal

Hope this helps

---

### Post by ChameleonDave on 2008-07-01
> **xieu90 said:**
> hi everyone
when I install new programs through Synaptic I can see that I need to download X MB and Y MB will be used
after my computer download X MB and installed a program what will happen with this X MB ? will my computer automatically delete it ?
and where does my computer store this X MB ? I'm just curious ^^

Go into the Synaptic preferences and under the "Files" tab you can see what your current preferences for the downloaded packages are.  I believe the default is to keep all files.  You can decide to keep only files which are still available in the repositories, or no files at all.  I'd say it is a good idea to keep all files unless you are running out of disk space.

---

### Post by Fingers &amp; Thumbs on 2008-07-01
Hello and welcome xieu90.

  In synaptic, go to the top right of the window, click through >Settings >Preferences, and select the "Files" tab, here you will find all the options you need to tell synaptic what to do with temporary files.

---

### Post by Paddy Landau on 2008-07-01
Is there any point in keeping them?

Wouldn't it be useful to put the command into the boot procedure?

(My archives have taken 0.5Gb already.)

---

### Post by ChameleonDave on 2008-07-01
> **Paddy Landau said:**
> Is there any point in keeping them?


Obviously.

If you decide to remove something, and reinstall it at a later date, you won't have to download it again.  You can also transfer the files to another computer in order to install them without any more downloading.

---

