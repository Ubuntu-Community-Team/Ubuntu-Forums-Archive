---
title: "Executing commands"
date: 2014-12-24
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2014-12-24
all these programs tell me i need to type in sudo "blah, blah, blah" and i don't even know where to begin to look to open the command prompts.  i still have to put the factory linux drivers in and a few other things that require me to delete old programs first so i need to be able to type in the command coding.  ty for your help in advance.

---

### Post by sammiev on 2014-12-24
You need to run the sudo commands within the Terminal.

I would install "Synaptic Package Manager" it's great for installing/un-installing packages.

If you tell us the name of the packages you want to add or remove, we can help.

---

### Post by yancek on 2014-12-24
You can open a terminal by clicking the Dash (Ubuntu logo in upper left of Desktop) and in the Search box type:  terminal.  Also simultaneously holding down the Ctrl+Alt+t keys should do it.

---

### Post by cryofreeze666 on 2014-12-24
i am sorry i don't actually know the jargin for what i'm calling a command line, so i will type out an example given to me by hp for my wireless printer.
user@host:~$ cd Desktop
user@host:~/Desktop$ sh hplip-3.14.10run

those are the type of commands i'm trying to figure out what app to open, and where it is, so i can finish the "work portion" and begin the "play portion" by installing tera online with PlayOnLinux.

i downloaded the drivers for amd catalyst and other amd drivers directly from amd's linux sections, and i wanted to try load bastille to harden ubuntu 14.10. the program is currently telling me i ave to delete programs before i can install amd drivers.  the research i did shows me how to delete the programs, but not how to open the application that allows me to type in the programming lines.  currently i am using a toshiba satellite L75D- A7283, if that helps at all. 

thats the best i can do in my current state of cluelessness.

---

### Post by schragge on 2014-12-24
How to use terminal is fully explained in [uhelp]community/UsingTheTerminal[/uhelp]

Please note that you shouldn't type the parts I've marked [COLOR=green]green[/COLOR] in your example.
```

[COLOR=green]user@host:~$ [/COLOR]cd Desktop
[COLOR=green]user@host:~/Desktop$ [/COLOR]sh hplip-3.14.10run

```
They are what computer responds.

---

### Post by grahammechanical on 2014-12-24
If you used a web browser to download hplip-3.14.10.run then chances are that it has not downloaded to the Desktop but into the Downloads folder. The command cd = change directory. If hplip-3.14.10.run is in the Downloads directory/folder then the first command would be

```
cd downloads
```

To see what files and folders are in each directory use

```
ls
```

after you have used cd to get into that directory. Or use the File Manager first.

Regards

---

### Post by schragge on 2014-12-24
Another thought. Are you sure, you absolutely need the latest and greatest dirvers for you hardware to work? The HP driver you're trying to install is at version 3.14.10, while Ubuntu 14.10 has 3.14.6 it its repository. It's not so far behind. Maybe your wireless printer would work just fine with the driver from Ubuntu.

---

### Post by whitesmith on 2014-12-24
+1 to schragge for comments on the driver issue. You may want to read the second reference on my signature line for a better handle on using the terminal and learning command line details. Regards.

---

### Post by james_king2 on 2014-12-27
I know little to knothing working with Ubuntu at the moment as I have only started fooling around with it. I have Ubuntu 14.04.1 LTS installed on an old Asus desktop that was given to me. I have several HP printers, HP Deskjet 6988, connected to an SMC WiFi Router. All I can tell you at the moment is that Unbuntu found both the router as well as was able to locate the printer without any real problems and it works as it should with whatever driver might be in the Unbuntu package.  I had read some place about having to install a driver but as most folks, I had no idea about or where to look for "Terminal" to try to type in a command I don't understand. What I did do was to let the installer search for the printer and it found it on my WiFi and installed it through clicking on Add a Printer. I can't be of more help as I found this out through just goofing around. (A lot!) I also have a Brother DCP 7020 Laser printer connected through USB and Add a Printer was able to find and install that printer as well which operates as it sould with whatever drivers are present in Unbuntu. Someone else might be able to steer you a lot better than myself as I just kept fooling around and happened across a few things that worked out. I also had gone to HP's site as well as Brother's but I simply didn't understand what I was looking at concerning their drivers. I had found a lot of things playing around in the Unbuntu icon and the File icon and going from there. All I can say is that as per one answer, you will likely get your printer up and running without having to jump through a lot of hoops.
Jim

---

### Post by pfeiffep on 2014-12-27
> i am sorry i don't actually know the jargin for what i'm calling a  command line, so i will type out an example given to me by hp for my  wireless printer.
user@host:~$ cd Desktop
user@host:~/Desktop$ sh hplip-3.14.10run [**[COLOR=#000000]cryofreeze666[/COLOR]**]("http://ubuntuforums.org/member.php?u=1167910") The gui interface is sometimes preferable to command line for users just starting the Linux journey.

I used Synaptic to install the working drivers for my HP printer. HP printer C6200 series connects directly to my router and accessed via wifi from Dell Laptop running Ubuntu 14.04.1 and Macbook Pro[INDENT]HPLIP-3.14.3 version was installed
hp-lip gui 
[/INDENT]
 
These programs found the network printer and configured it correctly without me running any terminal commands. I believe that they are updated when software updater runs.

---

