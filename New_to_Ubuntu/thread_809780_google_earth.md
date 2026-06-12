---
title: "google earth"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by ozarkerbob on 2008-05-27
I have version 8.04

I installed a bin file, previously downloaded, using the proceedurefrom:

[https://help.ubuntu.com/community/Go...earth)|(google](https://help.ubuntu.com/community/Go...earth)|(google))

I did the terminal commands and installed, EXCEPT--- I hit the start button which apparently is a no-no. "Do not press Start as this will run it as root which is never a good idea"

so I have a program which shows up as an internet application. It begins to load, stalls, and then crashes.

I then ran the uninstall terminal commands, but because I didn't install correctly, it won't uninstall- "no such file or directory"


So I tried to install properly thinking it might overwrite, but it didn't help.  It still shows up in the application>internet.  but won't run at all ("could not launch-file not found")

call me stupid, but can anyone help?




ozarkerbob is online now Report Post   	Edit/Delete Message

---

### Post by mick8985 on 2008-05-27
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

The medibuntu repository provides googleearth along with non free codes dvd support etc. just follow this howto

---

### Post by ozarkerbob on 2008-05-27
> **mick8985 said:**
> [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

The medibuntu repository provides googleearth along with non free codes dvd support etc. just follow this howto


that is where I got the proceedure which I screwed up by hitting the start button at the end of the install.  What I need to know is how to get rid of the improper installation

---

### Post by mick8985 on 2008-05-27
```
sudo apt-get remove googleearth && sudo apt-get autoremove
```

but to be honest I find it hard to believe  that "the start button" had any influence on you installing googleearth from the medibuntu repo

---

### Post by kyphi on 2008-05-27
Google Earth installs all necessary files to your home directory only.

Got into your home directory, press Ctrl+h to show the hidden files and you will see a file called .googleearth.

Once you delete that file you can start again.

---

### Post by ozarkerbob on 2008-05-27
> **mick8985 said:**
> ```
sudo apt-get remove googleearth && sudo apt-get autoremove
```

but to be honest I find it hard to believe  that "the start button" had any influence on you installing googleearth from the medibuntu repo


bob@bob-laptop:~$ sudo apt-get remove googleearth && sudo apt-get autoremove
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package googleearth
bob@bob-laptop:~$ 


it is still there and still won't run?

---

### Post by mick8985 on 2008-05-27
Can you find from you bash history the command you did to install googleearth, press the "up" to look through your bash history

---

### Post by ozarkerbob on 2008-05-27
no, I don't know what a bash history is- I am very new to linux

---

### Post by Maestro23 on 2008-05-27
> **ozarkerbob said:**
> no, I don't know what a bash history is- I am very new to linux

You installed the .bin file from the website.  In what directory did you install it on your system?

---

### Post by ubuntu27 on 2008-05-27
The link the OP provided is invalid. Here is the correct one:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by Maestro23 on 2008-05-27
> **ubuntu27 said:**
> The link the OP provided is invalid. Here is the correct one:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

To the OP.  There is "Uninstallation" instructions at the bottom page of the link provided above.

---

### Post by mick8985 on 2008-05-27
After you uninstall using the link provided above, install it again using the link I provided

---

### Post by ozarkerbob on 2008-05-27
> **Maestro23 said:**
> To the OP.  There is "Uninstallation" instructions at the bottom page of the link provided above.

I did the uninstall stuff.  nothing seems to detect where it really is.  The instructions said not to do what I did- hit the start button at the end of the install.  From the instructions 

"When installation is complete, press Quit.
/!\ Do not press Start as this will run it as root which is never a good idea."


this is from:

  [https://help.ubuntu.com/community/GoogleEarth?highlight=(google)|(earth](https://help.ubuntu.com/community/GoogleEarth?highlight=(google)|(earth))

---

### Post by mick8985 on 2008-05-27
Basically everything is uninstalled except the menu entries, check for files like /usr/share/menu/googleearth or similar

---

### Post by ozarkerbob on 2008-05-27
well I'm not sure what worked, but after several uninstalls and proper install, I have a working copy.  thanks folks

---

