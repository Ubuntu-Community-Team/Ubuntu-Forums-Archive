---
title: "Latest gEDA"
date: 2006-09-21
forum: Outdated Tutorials &amp; Tips
---

### Post by calvinthomas on 2006-09-21
This is my first ever how-to and i'm not sure if its useful to people but its taken me forever to get this working so I thought i'd try and save everybody else the effort.

**Note: This is only useful for Dapper for Edgy the latest version is available in the repositories.**

**Note: Scripts are provided by Adrian Nania which are a lot easier and probably better than my method, they didn't work for me the first time I tried but I think that is me giving up to soon or my computer rather than the script. When I tried again on a fresh dapper install they worked perfectly, If you have problems, the method described below should work. **

**Note: My method installs the very latest version of this software and have been told in a following post that there are some bugs in it. For a stable release use the cvs script provided by Adrian, for a script for the unstable try the CD version (I THINK this is correct, awaiting verification as I have not tried the CD script)**

**Note: If you have tried my method and had problems with dependencies, thanks to Adrian Nanias' script I have updated the list of dependencies at the start which hopefully will solve problems.**

Note: While I have tried my best I may have missed out a required sudo command in some places, if it doesn't work without try adding sudo, also if you need to please let me know so I can update accordingly.

**Warning: This method takes a long time (about 50mins on my Turion 3000+, 512Mb RAM) and requires a fairly large download (129Mb)**

Thanks to UofLSpeed and Klitz who gave me advice while I was working through it.

If your not worried about the latest version then gEDA is available in the repos, however its over a year old.

Now we need to get a bunch of dependencies, paste this into a terminal:

```
sudo apt-get remove -y automake1.4
sudo apt-get install -y autoconf libtool guile-1.6 guile-1.6-dev libgtk2.0-dev latex2html groff \
tetex-base tetex-extra libgdk-pixbuf2 libgdk-pixbuf-dev libglib2.0-dev build-essential \
automake1.9 libreadline5-dev tcl8.4-dev libwxgtk2.6-0 libwxgtk2.6-dev texinfo flex cvs \
libgd2 libgd2-dev tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev bison gawk libxaw7-dev libedit-dev \
ssh libguilegtk-1.2-0 libguilegtk-1.2-dev libxml2-dev libglade2-dev libgtkextra-dev \
xaw3dg xaw3dg-dev guile-gnome0-gtk libgtk+2.0-directfb0 libgtk+2.0-directfb-dev \
libgnome2-0 libgnome2-dev gettext gettext-base readline-common libreadline5 pkg-config \
gdk-imlib11 gdk-imlib11-dev libgdk-pixbuf-gnome2 libgdk-pixbuf-gnome-dev make gcc \
colorgcc
sudo apt-get remove -y automake1.4
# for pcb:
sudo apt-get install -y ssh libgd2 libgd2-dev tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev bison gawk
# for ngspice
sudo apt-get install -y libxaw7-dev libedit-dev
# for gwave
sudo apt-get install -y libguilegtk-1.2-0 libguilegtk-1.2-dev
# for gtkwave
sudo apt-get install -y libxml2-dev
# libxaw7-dbg libxaw-headers xaw3dg xaw3dg-dev ?
```

First things first from the repositories install gEDA and gwave. This is necessary as I haven't found another way to get the gEDA package manager or gwave. **Note: I have not tried just installing these, I installed every package as its small and I wasn't worried about harddisk space, I don't however think its necessary, if you have problems try installing all of the packages first.**

```
sudo apt-get install geda gwave
```

Note: this will also install gschem, unfortunately we are going to have to let it do this.

Now go here: [http://www.geda.seul.org/download.html](http://www.geda.seul.org/download.html) and download the gEDA Suite ISO (Note this is a fairly large download 129Mb)

Either mount or burn this ISO file, I find it easier to mount like this:

```
sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop
```

where file.iso is changed for the ISO file of gEDA

Now navigate to the mounted ISO and type:

```
installer --verbose --log
```

If you have any problems you can leave out the log part (I had to do this but UofLSpeed did not)

You should get a GUI installer which is very simple, follow the instructions of this.

**Note: If you have missing dependencies (i.e. it fails to install things let me know what the error was and i'll see if I can find what you need to install, alternatively search on google for the missing part and you'll find it (I did anyway!)**

I installed it to this directory: /home/user/ but you can install it wherever you want.

Now you must edit /etc/environment:

```
sudo gedit /etc/environment
```

and add these lines, editing the directory where necessary (as per where you installed it)

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/home/username/gEDA/bin"
LD_LIBRARY_PATH="/home/username/gEDA/lib"
```

Finally we need to install Easy Spice, to do this we are going to compile it from source directly.

Paste this into a terminal to retrieve the file:

```
wget -c [http://superb-west.dl.sourceforge.net/sourceforge/easy-spice/easy_spice-0.6.7.tar.gz](http://superb-west.dl.sourceforge.net/sourceforge/easy-spice/easy_spice-0.6.7.tar.gz)
```

Now extract the file (I do this by right clicking on the file and clicking extract here)

Navigate to the directory in the terminal and type:

```
./configure
```

```
make
```

```
sudo make install
```

You now have everything installed and configured.

Now go to the geda-install directory (where you installed from the ISO) and in there is a bin folder. For me this is:

```
sudo nautilus /home/calvin/geda-install/bin
```
copy all of the files from there. 

Now in the terminal type: 

```
sudo nautilus /usr/bin 
```

and paste all copied files there, overwriting if necessary.

Now you can start the geda project manager by typing geda into a terminal or from the run application dialog.

To check this has worked, try opening all the applications that are in the Tool menu.

If it does, enjoy!

Any problems or easier ways to do any of this please let me know!

---

### Post by calvinthomas on 2006-09-22
I have added the link for the ISO file that I missed out and also, added a not that root access is required so commands should be entered with sudo.

Calv

---

### Post by Adrian Nania on 2006-09-23
An updated version of gEDA-CVS-ubuntu can be found attached as tar.gz archive at:
[http://www.ubuntuforums.org/showthread.php?t=282040&highlight=geda](http://www.ubuntuforums.org/showthread.php?t=282040&highlight=geda)

Some errors were corrected. the script is up to date as of today, 20061222

---

### Post by Adrian Nania on 2006-09-23
for gEDA-CD-ubuntu:

This is really sad, the CD version of gEDA is useless for quite a while.
Too many packages are missing and not installed because of many errors.
I recommend installing gEDA from CVS and/or the latest available package.
Here are the same bugs but is a lot easier to fix them.
See the gEDA-CVS-ubuntu.txt.tar.gz file.

---

### Post by Adrian Nania on 2006-09-23
Soon I will extend the gEDA-CVS-ubuntu.txt.tar.gz file to include some extra packages

---

### Post by nrayever on 2006-09-23
thanks for this howto calvinthomas!! and let's see how much time it's going to take on my centrino duo + 1gb of ram. i believe that there's a lack of programs for electric/electronics in linux. maybe we should need to work in some more programs. hope someday this change.

sincerly nrayever

---

### Post by calvinthomas on 2006-09-23
> **Adrian Nania said:**
> oops! looks like a few special characters are replaced by "smelly" faces.
attached are the real scrips I am using.

The script isn't working for me but its probably just my machine, it gets to the installing Geda, this takes 6mins on AMD 64 and then doesn't do anything! Nevermind the version i've got seems ok to me (i'll never use it, its for my Dad, he's an electronics engineer, i'm a Maths student!)

I've put a bold note about your script at the top of the first post so other people can use it if it works for them, which hopefully it will because then its easier for them.

Also I have updated my post with the dependencies from the start of your script as it is more complete than mine. Hope that is OK.

Calv

---

### Post by calvinthomas on 2006-09-23
> **nrayever said:**
> thanks for this howto calvinthomas!! and let's see how much time it's going to take on my centrino duo + 1gb of ram. i believe that there's a lack of programs for electric/electronics in linux. maybe we should need to work in some more programs. hope someday this change.

sincerly nrayever

No problem, it does seem a shame there are so few. Its not my type of software (I did it for my Dad) but its a shame this type of software is so lacking, there is the proprietry Eagle which is apparently quirky but excellent but Geda seems to be the best of the open source and my Dad said it seems good! He prefers ares & isis in windows as its so easy to use. Its very expensive though.

Let me know how long it takes and whether it works!

Note: If you had trouble with dependencies, I have updated the dependencies at the start thanks to Adrian Nanias' script.

Calv

---

### Post by Adrian Nania on 2006-09-23
> **calvinthomas said:**
> Note: Scripts are provided by Adrian Nania which are a lot easier and probably better than my method, they didn't work for me but I think that is me and my computer rather than the script. If you have problems, the method described below should work. 
I am not sure how fast is that computer. For example, the original gEDA installer is calling for something like one hour to install gEDA. On my computer each package needs around 6 min. Even if the shell is asking you to wait and seems like is doing nothing, for the CVS version, check the real time log files:
$HOME/gEDA.log
$HOME/pcb.log
$HOME/gerbv.log
$HOME/ngspice.log
$HOME/easy_spice.log
$HOME/gwave.log
$HOME/gtkwave.log
You will be able to see here what is happening, just refresh from time to time. I choose to work with log files not direct messages to keep the result. My computer is am AMD64 with kernel K7, I installed gnome and KDE.

---

### Post by estratos on 2006-10-11
I'm trying to install the last version of gEDA with Adrian's script. Meanwhile, Calvin, your father maybe could try KiCad ([http://iut-tice.ujf-grenoble.fr/kicad/)](http://iut-tice.ujf-grenoble.fr/kicad/)). It's a very good GNU Schematic/PCB editor for Windows and Linux (based on wxWidgets) that works really well and is very easy to install.

I'll let you know if I have any problem with the instal of gEDA.

Regards,

Daniel.

---

### Post by calvinthomas on 2006-10-11
Note: On a fresh dapper install I had no problem with the scripts and may have just not left it long enough before, sorry for the lack of response I kept forgetting, I will update the original post accordingly, thanks for the software tip i'll get him to check it out.

Note 2: In edgy which i'm now using the version I give instructions for here is installable through the repos and works perfectly.

Question: Adrian am I right in thinking that your first script cvs installs Jan 06 (i.e. Stable) and the second cd script installs Sep 06 (i.e. Unstable)?

Calv

---

### Post by calvinthomas on 2006-10-11
> **estratos said:**
> I'm trying to install the last version of gEDA with Adrian's script. Meanwhile, Calvin, your father maybe could try KiCad ([http://iut-tice.ujf-grenoble.fr/kicad/)](http://iut-tice.ujf-grenoble.fr/kicad/)). It's a very good GNU Schematic/PCB editor for Windows and Linux (based on wxWidgets) that works really well and is very easy to install.

I'll let you know if I have any problem with the instal of gEDA.

Regards,

Daniel.

Daniel, I just had a look at KiCad and think my Dad might prefer it to Geda, it seems a little bit neater and tidier to me (I don't know much though, since I can't design even an easy circuit)

Was just wondering though, when in the schematic editor, if you click on netlist, then spice it gives the option to run simulator, have you managed to get this working with any simulator? If so which? Also does this simply open the simulator application or actually do the simulation through the simulator program for you. If it was the latter I would be very interested to know.

Calv

---

### Post by calvinthomas on 2006-10-12
I have noticed a problem that i'm hoping someone can fix, it seems the used link in both my post and Adrians scripts for Easy Spice no longer works and I haven't been able to find any other way of getting it, if you know of a link or have the file, please can you provide it.

Calv

---

### Post by Adrian Nania on 2006-10-21
Sorry for the delay.
I created two install scripts because of some problems with the CD version. Right now I suspect the latest CD image offered for download (Sat 21 Oct, 2006, version 20060907) is simply bad. The reason I am saying this is because I tried to install this one under Ubuntu, SUSE and Fedora, and is not working properly. All the times the actual gEDA project manager is missing, although the script itself is doing the supposed job. I suspect as soon as a new CD version will be released, it will start working again.
So, I am relaying on the CVS version, here you know at least you have the very latest versions with the minimum amount of bugs.
Very important, regardless of what version is used, is to understand the PATH and the System Variables. Do not relay on the default mechanism to deal with this, Linux is way too messed up. To work around this incredible mess, the technique used is how to start gEDA components: part of the launching shortcut is first to redefine the variables and the PATH specific for the gEDA package inside of the shell used by the launcher. Seems like the  PATH and the System Variables are known inside of the current shell only and unknown to the rest of the operating system. The story with the /etc/environment is just a story.
I tried the latest gEDA package from Edgy, looks like this time is working. Unfortunately, a whole bunch of weird things are happening. For example, I tried to tune-up the gEDA package to use my standard settings, libraries, colors and the default window size. I am not saying “it is not working” but it is not working the same way like the latest version from the CVS. As an example, the libraries are sorted in a very strange way, with a bug.
I do have a “work in progress” file with my personal tricks I am discovering when I am trying to tune gEDA to my need: [http://www.ubuntuforums.org/showthread.php?t=282040&highlight=geda](http://www.ubuntuforums.org/showthread.php?t=282040&highlight=geda)
Right now I am using the default package from Edgy, I hope the Ubuntu team will keep this version up to date (close to the CVS version). This way all Ubuntu users could talk the same language (finally).
Calv, could you help me here? I will appreciate if we can team-up to start some sort of step by step  tutorial to make easier the actual use of gEDA, with all the quirks we can identify. If anyone else is interested in such experience exchange please let us hear from you, Ubuntu users.
I will check why Easy Spice is not working? I suspect something minor, just give me a little bit more time.

Adrian

---

### Post by Adrian Nania on 2006-10-21
> **calvinthomas said:**
> I have noticed a problem that i'm hoping someone can fix, it seems the used link in both my post and Adrians scripts for Easy Spice no longer works and I haven't been able to find any other way of getting it, if you know of a link or have the file, please can you provide it.

Calv

Calv, looks like the old mirror used is down. I have checked again [http://easy-spice.sourceforge.net/](http://easy-spice.sourceforge.net/) and the single mirror still listed here:
[http://prdownloads.sourceforge.net/easy-spice/easy_spice-0.6.7.tar.gz?download](http://prdownloads.sourceforge.net/easy-spice/easy_spice-0.6.7.tar.gz?download)
is actually working but after a few attempts and with a huge delay (a few minutes). So I replaced on my script:

clear
echo install easy_spice
echo
mkdir $HOME/tmp
cd $HOME/tmp
# from [http://easy-spice.sourceforge.net/](http://easy-spice.sourceforge.net/)
# wget -c [http://superb-west.dl.sourceforge.net/sourceforge/easy-spice/easy_spice-0.6.7.tar.gz](http://superb-west.dl.sourceforge.net/sourceforge/easy-spice/easy_spice-0.6.7.tar.gz)
wget -c [http://kent.dl.sourceforge.net/sourceforge/easy-spice/easy_spice-0.6.7.tar.gz](http://kent.dl.sourceforge.net/sourceforge/easy-spice/easy_spice-0.6.7.tar.gz)
...

I hope this it will work for you too. If you wish, I stilll have a copy of the file easy_spice-0.6.7.tar.gz on my computes, let me know and I will send it to you.

Adrian

---

