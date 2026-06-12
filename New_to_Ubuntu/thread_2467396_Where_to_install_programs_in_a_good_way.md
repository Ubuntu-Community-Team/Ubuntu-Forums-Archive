---
title: "Where to install programs in a good way?"
date: 2021-09-25
forum: New to Ubuntu
---

### Post by fernand2226 on 2021-09-25
Hi I'm new to Ubuntu, I'd appreciate your help :) 

Regarding to my question, the reason I ask for is: I just installed ubuntu 20.04 LTS, I did it with 4 partitions:
- /          - 20GB
- /boot   - 1GB
- /home - 100GB
- And Swap

Well based on this distribution or partitions, where should I install programs, for instance the files ending in .sh?

Based on what I've read the right thing to do is to install them on /opt, however I think that if I do that I'd be using the partition '/' which has limited storage (20GB) and also in case I change my version or distribution of OS it could be affected. Please let me know if I'm wrong :) 

Therefore, taking in account those details, should I install programs on /home/username?

Thank you so much for your help

---

### Post by ActionParsnip on 2021-09-25
I like to make /scripts and put my scripts there. You can add the folder to your PATH variable using ~/.bashrc

---

### Post by ActionParsnip on 2021-09-25
You can install to $HOME if you want. It's a bit messy but will work.

---

### Post by vanadium on 2021-09-25
Install programs using the software center: the system automatically takes care of proper location, integrates them in your application menu, sets up associations, and ensures you can remove it easily anytime.

Install your own scripts in a directory "bin" or ".local/share/bin" in your home folder. Each of these folders will, next time you log in, automatically be included in your PATH. That means that you will be able to execute these programs and script by typing their name at the terminal.

---

### Post by Impavidus on 2021-09-25
Most applications you install will (or should) be handled by your package manager (Ubuntu Software, apt, Synaptic, whatever tool you use) and that will decide where it will be installed. Or rather, the packager has decided, and usually it will be in your root partition. The standard location for your manually installed stuff, if you have any, would be in your home directory or in /usr/local.

BTW, 20GB for your root partition is a bit small, but may work. I make it about 30GB. A /boot partition is only needed (and useful) in special cases, like when you have an encrypted system.

---

### Post by grahammechanical on 2021-09-25
I must be missing something.

I last used Microsoft's Windows almost 20 years ago. So, things might have changed. But as I understand things, in Windows the user can choose a folder to install a program in.  But in Linux we do not do that. When we use the install command or a GUI front end such as Ubuntu Software a program called dpkg does the actual work. 

The program/application files go in the / directory and related user files go in /home/username. The application's files or libraries are spread over several directories in / directory.

This is why a / partition of 20 GB will be considered close to being too small to be useful if we intend to install additional applications/programs. On my system shell scripts used by the system are in /bin/. But they can go in other directories but we would need to change to that directory if we are going to run the script.  Or put the path to the directory containing the script as part of the command.

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

I will accept that shell scripts are executable and are therefore technically a program. But this is a section of the forum for new users. And there is a another definition of the word "program" and with those type of programs/applications the user does not get a choice of where to install the "program." Lets us not confuse new users.

Regards

---

### Post by GhX6GZMB on 2021-09-25
@fernand2226
Don't worry about this. 20 GB is plenty, you'll be surprised at how little space the applications take. I have LibreOffice, KiCAD, LibreCAD, GNU Octave, VLC Player, Opera, AVIDemux, and, and, and... installed and I'm at around 13 GB total on /. I could reduce this by placing the CAD libraries under /home instead (that's really where they belong), but have been too lazy until now. Then it would probably drop to 10 GB.
Let Synaptic or muon or whatever install manager you're using do the placement. It works best that way.
Your partitioning is good BTW. Congrats. :)

---

### Post by ajgreeny on 2021-09-25
Just like ml9104, I am inclined to say that 20G should be enough for most users; in my 16 years of using Ubuntu or other DE versions (eg Xubuntu, Kubuntu) I have never had a root partition of more than 20G and have never once filled it with more than about 13G even though I also install a lot of programmes and packages, usually all from the repos.  I have however installed both Plexmediaserver and Embymediaserver, both of which use quite a lot of space in root with their large databases of the mediafiles which they serve to client devices, eg smart-TVs.

I am not a gamer, but I believe that games can use a great deal of space in the root partition if they are installed from the normal repositories, so if you are going to install lots of games you might wish to have a root partition that is larger, say 30G.

---

### Post by ActionParsnip on 2021-09-26
Let's do this another way. What applications are you thinking about installing to other locations?

---

### Post by GhX6GZMB on 2021-09-26
> **ActionParsnip said:**
> Let's do this another way. What applications are you thinking about installing to other locations?

Good question. I think this is more the phase of getting out of the M$ mindset. I went through this myself a couple of years ago, and it takes a bit of time to get things turned around.

Still, the OP has done a good job of partitioning and of identifying the issue. Applause from my side.

---

### Post by ajgreeny on 2021-09-26
> **ActionParsnip said:**
> Let's do this another way. What applications are you thinking about installing to other locations?
That is a very good question because, as you will have gathered from replies we have already given you, there is normally no choice of where to install applications; they are automatically installed by the package manager into the file system where they must be for them to work.

I have almost nothing installed manually into places chosen by me when installing them except for one or two that I run directly as appimage installations which are in my home folder/partition, such as musescore.

Where you decide to put any shell scripts will depend entirely on what they are, where they came from and what they're going to be used for; I have many personal scripts in the /bin folder in my home which means they are in the system $PATH so can be called simply by their name in terminal.

---

### Post by ActionParsnip on 2021-09-27
Yeah just sounds like a weird question probably coming from Windows where you can choose the location of the files. Linux puts things where they are needed and the folder structure is very purposeful. Libs and so on are stored where needed, once, and loaded into RAM once, and referenced as many times as needed.
You only really get applications outside of this with snaps and flatpack etc but they install where they need to go as well.
Some people like to manually install applications like OpenOffice and people do tend to put them in /opt but this is outside of the Ubuntu package system so you will need to manually update these yourself. I used to work at a place that used WingFTP where the update was part of patching but it wasn't a deb and the "upgrade" was to extract the archive over the top of the standing data to update files... Awful.

---

### Post by SeijiSensei on 2021-09-27
Use the package manager for everything.  Don't try customizing the organization of the system. It's not worth it, and it can break things.

There are few programs that aren't available from the Ubuntu repositories. If you want to install Zoom, you need to download the .deb file from zoom.us/download and install it manually. Pretty much everything else I run comes from the repositories.

---

