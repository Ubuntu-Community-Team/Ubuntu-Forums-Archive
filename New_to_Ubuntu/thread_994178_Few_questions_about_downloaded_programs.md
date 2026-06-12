---
title: "Few questions about downloaded programs"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Keatoru on 2008-11-26
First off, the programs I have downloaded couldn't be found in the Add/Remove Programs.

What I would like to know is how I install these programs to where i can got to applications and then click it to run instead of opening the folder and running the script each time.

Also, when I compile source, where is it the product...

I'm asking because I had downloaded TuxBoy and the program wouldn't run so i tried compiling the source by cd to the source directory and then running the make command in terminal. It ran through and completed but i can't find what it made...

---

### Post by Titan8990 on 2008-11-26
You typically have to run the make install command as well. You should see the readme and install instructions that come packaged with the source code.

To find a program you can use the which command.

An example:

jordan@bourne:~$ which tomboy
/usr/bin/tomboy

---

### Post by taurus on 2008-11-26
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by bobnutfield on 2008-11-26
Just a note to tell you that you can right click on the desktop, choose "Create Launcher", and enter the run command you use on the command line to start your app,  You can also assign a custom icon for it, if you wish.

---

### Post by cariboo on 2008-11-26
You usually have to install the program too. Type:

```
sudo make install
```

If the author has followed the guidelines it will be installed in either /usr/bin, /usr/local/bin or /usr/games

Jim

---

### Post by Titan8990 on 2008-11-26
> If the author has followed the guidelines it will be installed in either /usr/bin, /usr/local/bin or /usr/games


I have also found /opt to be common.

---

### Post by Keatoru on 2008-11-26
I don't get it...

@Titan idk what you mena by which. and I have already checked the txt files that came with it and they don't say anything but to compile source go to the source folder and execute command make in the terminal(i know i'm in the right place for the make command cuz it goes through the compile process) with the make install command it says "*** No rule to make target 'install', Stop."

@taurus i read those guides but they don't help me any. they tell me about synaptic and add/remove but i don't know how do get to the steps of haveing the package in there. and the compile guide didn't help either cuz the checkinstall did same as make install.

@bobnutfield thanks could help but right now no use for it when the program won't work

-----------

I think the source is compiling to Desktop/tuxboy_lin_100rc3/system/i686 but the autorun script 'tuxboy' won't work when i click it. and i triend install commands from there and nothing.

---

### Post by Titan8990 on 2008-11-26
When doing make install on Debian based distros (Ubuntu) you have to sudo the make install command. Example:


sudo make install


Also, if you want to send me a link the specific program you are trying to compile, I will have a look.

---

### Post by Keatoru on 2008-11-26
the adding sudo does the same thing.

[http://www.tuxemu.se.nu/](http://www.tuxemu.se.nu/)

trying to use that on Ubuntu 8.04

---

### Post by Titan8990 on 2008-11-26
Did you install the sdl and sdl_image dev libraries? 


sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev

Make install is not needed for this program which typically means it runs out of the directory you compiled it in.

---

### Post by Keatoru on 2008-11-26
yes i have all the right libraries. it compiles completely no errors. but the file it creates won't run

---

### Post by Titan8990 on 2008-11-26
Did you try running the linux.sh script in the top level directory?

---

### Post by Keatoru on 2008-11-26
terminal only flashed but i think it said could not open slave then i didn't get to read the second line. and then another window open adn tehn closed. when i jsut ran it a window opened and closed

---

### Post by Titan8990 on 2008-11-26
Don't double click it. Run it from the terminal:

From the directory that it is in:

sudo ./linux.sh

---

### Post by Keatoru on 2008-11-26
"ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Sound Error: Couldn't open system/gfx/icon.png"

---

### Post by Titan8990 on 2008-11-26
It looks like that error is a documented bug: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202089](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202089)


Did you set up pulseaudio?

---

### Post by Keatoru on 2008-11-26
yes pulseaudio is installed

---

### Post by SunnyRabbiera on 2008-11-26
> **Keatoru said:**
> the adding sudo does the same thing.

[http://www.tuxemu.se.nu/](http://www.tuxemu.se.nu/)

trying to use that on Ubuntu 8.04

well tuxboy is a game boy emulator, you could just install VBAexpress via the repositories, no compiling needed :D

---

### Post by Titan8990 on 2008-11-26
This took a while but before running the script, try this:


sudo /etc/init.d/pulseaudio stop

---

