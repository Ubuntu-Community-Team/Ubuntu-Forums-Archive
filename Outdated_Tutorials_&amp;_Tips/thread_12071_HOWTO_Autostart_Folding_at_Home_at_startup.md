---
title: "HOWTO: Autostart Folding at Home at startup"
date: 2005-01-21
forum: Outdated Tutorials &amp; Tips
---

### Post by ions on 2005-01-21
I run mine from a dir I created called .FAH in the home directory:

```

mkdir ~/.FAH

```

Change into that directory:

```

cd ~/.FAH/

```

I know the ~ isn't necessary but in case you're not in home when you start doing this you're still gonna be ok.

Then dowload the FAH console found here: [http://folding.stanford.edu/download.html](http://folding.stanford.edu/download.html)

For the lazy: 

```

wget http://www.stanford.edu/group/pandegroup/release/FAH502-Linux.exe

```

Don't get mad at me if the version changes and that link breaks.

Run and configure it to your username, team and machine ID as they tell you here: 

[http://folding.stanford.edu/linux.html](http://folding.stanford.edu/linux.html)

Feel free to join the #justlinux irc regulars and choose team #36480.  We're doing well. 

Now let's make it start at startup!
First create the script that will run FAH:

```

sudo nano -w /etc/init.d/foldingathome

```

It will look like this:

```
#!/bin/bash

pushd /home/user/.FAH/
su user -c "screen -d -m ./FAH502-Linux.exe"
popd

```

C-o to save it in nano.

Now let's make it executable:

```
sudo chmod +x /etc/init.d/foldingathome
```

Now let's link it to the runlevel:

```

sudo ln -s /etc/init.d/foldingathome /etc/rc2.d/S99foldingathome

```

*Thanks to Retsaw & maccorin for the help.

---

### Post by Rancoras on 2005-01-21
This needs a HOWTO: tag on the title.

---

### Post by ions on 2005-01-21
[QUOTE=Rancoras]This needs a HOWTO: tag on the title.[/QUOTE]
 You'll have to do that, I can edit the topic line that appears in the thread but not the title that appears in the HOWTO area.

---

### Post by ions on 2005-01-23
[QUOTE=ions]You'll have to do that, I can edit the topic line that appears in the thread but not the title that appears in the HOWTO area.[/QUOTE]
 A problem has occured.  When FAH is started via this method it freezes once reaching 100% on a WU.  Started normally it does not freeze at 100%.

---

### Post by Saibei on 2005-02-05
For those that have trouble, this is how I did it:

Make a directory to install F@H in. Location doesn't particularly matter... I chose /home/fah so I'll be using that throughout the post. Download the F@H client to the newly created folder and run it as root:```
sudo mkdir /home/fah
cd /home/fah
sudo wget http://www.stanford.edu/group/pandegroup/release/FAH502-Linux.exe
sudo chmod +x FAH502-Linux.exe
sudo ./FAH502-Linux.exe

```

Enter the required info, and when F@H starts working on a work unit, close the client. Now to set up the startup scripts.

Make a file called fah in the /etc/init.d directory:```
sudo gedit /etc/init.d/fah

```Paste this into /etc/init.d/fah:```
#!/bin/sh
# /etc/init.d/fah for Ubuntu
# Start/stop/restart the F@H service.

fah_start() {
 if [ -x /home/fah/startfah.sh ]; then
   echo "Starting F@H:  /home/fah/startfah.sh"
   /home/fah/startfah.sh
 fi
}

fah_stop() {
 sudo killall FAH502-Linux.exe
}

fah_restart() {
 fah_stop
 sleep 2
 fah_start
}

case "$1" in
'start')
 fah_start
 ;;
'stop')
 fah_stop
 ;;
'restart')
 fah_restart
 ;;
*)
 fah_start
esac

```Save the file and close gedit, and finally make the file executable:```
sudo chmod +x /etc/init.d/fah

```

Now the startfah.sh script:```
sudo gedit /home/fah/startfah.sh
```and paste  this into it:```
#!/bin/sh
cd /home/fah
/home/fah/FAH502-Linux.exe -forceasm -advmethods >/dev/null 2>&1 &
exit 0

```And don't forget to make it executable!```
sudo chmod +x /home/fah/startfah.sh
```Feel free to remove the -forceasm and -advmethods flags, or add others of your own. I find those flags increase my weekly output a bit. For more info on what they do, see [here](http://www.liquidninjas.com/bbs/showthread.php?t=3270).

last and final step! Make a symlink into the /etc/rc2.d directory!```
ln -s /etc/init.d/fah /etc/rc2.d/S99fah
```

You can either test the script by rebooting or by typing the command:```
sudo /etc/init.d/fah start
```
Open the System Monitor and watch your CPU usage skyrocket :)

Many thanks to [XtremeSystems](http://www.xtremesystems.org/forums/showthread.php?t=44888) for the startfah.sh script and a good friend of mine for the /etc/init.d/fah script  :wink:

---

### Post by ions on 2005-04-03
I've tried both my method and Saibei's since moving to Hoary and can't get F@H to autostart.  Any idea why that would be or am I likely doing something wrong?

---

### Post by beatyou on 2005-07-09
> **Saibei]For those that have trouble, this is how I did it:

Make a directory to install F@H in. Location doesn't particularly matter... I chose /home/fah so I'll be using that throughout the post. Download the F@H client to the newly created folder and run it as root:```
sudo mkdir /home/fah
cd /home/fah
sudo wget http://www.stanford.edu/group/pandegroup/release/FAH502-Linux.exe
sudo chmod +x FAH502-Linux.exe
sudo ./FAH502-Linux.exe

```

Enter the required info, and when F@H starts working on a work unit, close the client. Now to set up the startup scripts.

Make a file called fah in the /etc/init.d directory:```
sudo gedit /etc/init.d/fah

```Paste this into /etc/init.d/fah:```
#!/bin/sh
# /etc/init.d/fah for Ubuntu
# Start/stop/restart the F@H service.

fah_start() {
 if [ -x /home/fah/startfah.sh ] said:**
> here[/url].

last and final step! Make a symlink into the /etc/rc2.d directory!```
ln -s /etc/init.d/fah /etc/rc2.d/S99fah
```

You can either test the script by rebooting or by typing the command:```
sudo /etc/init.d/fah start
```
Open the System Monitor and watch your CPU usage skyrocket :)

Many thanks to [XtremeSystems](http://www.xtremesystems.org/forums/showthread.php?t=44888) for the startfah.sh script and a good friend of mine for the /etc/init.d/fah script  :wink:
 Thanks saibei ;]

---

### Post by XDevHald on 2005-07-09
Worked like a charm!

Also note that I have created an UbuntuForums Team. If one of the Admins would like to take over this team please PM me and I will give you the password.

The Team ID Number Is: [b]45399
[/b]The Team WebPage Is: [http://vspx27.stanford.edu/cgi-bin/main.py?qtype=teampage&teamnum=45399]("http://vspx27.stanford.edu/cgi-bin/main.py?qtype=teampage&teamnum=45399")
[b]
EDIT: [/b]Yes the start up script works perfectly :D

---

### Post by mongolito404 on 2005-09-21
You can also use [finstall](http://www.vendomar.ee/~ivo/finstall) to your Folding@Home client and then use the provided *folding* script.
Simply execute finstall, follow the instructions and then```
sudo cp <install path>/foldingathome/folding /etc/init.d/folding
sudo update-rc.d folding defaults
```

---

### Post by simonp on 2005-10-05
ive just got ubutnu installed im a toal noob to Linux by the way. I followed the above text and thought i was going well got the FAh running and dowloaded a wu 
and carried on with the rest of the tutorial I think i may have gone wrong at the startFAh bit in the folder startfah.sh i can see the text that I copied and pasted 
and then it goes on to say make it execuatable so i saved the startfah and opened the terminal window and pasted  the next bit I think i cocked up here 
How do i go about starting again ? Ive gone into the process monitor and disabled the FAH process it wasnt running anyway my cpu was only showing 2% 
thanks for looking

---

### Post by jpkotta on 2005-10-09
I have written an install script for Folding@Home.  Please get it in the [Wiki]("https://wiki.ubuntu.com/FoldingAtHome").  It is based off of the Gentoo FAH install.  It installs the executable to /opt/foldingathome, and creates a client for every CPU.  It installs a startup script to /etc/init.d, and adds it to runlevel 2.

---

### Post by SLOSue on 2006-10-24
I must have gotten lost.  After creating this  "I sudo gedit /home/fah/startfah.sh"  and pasting the first bit of code into it, I tried to save and it wouldn't.  was I supposed to save then?  where do you put the rest of the code that comes after?  In that window, or the terminal window?   I think I need more detailed directions.

I've had Ubuntu on my puter for less than 24 hours, and have FAH loaded and running, but cant get it to run if I close the terminal window, and want it to run as a service.   Ive been reading till my eyes are falling out, but can't find a simple step by step for a total Linux newbie. The one above looks simple enough, but I guess I need more help?  heh

---

### Post by jpkotta on 2006-11-16
Step by step:
[http://www.ubuntuforums.org/showthread.php?t=101817](http://www.ubuntuforums.org/showthread.php?t=101817)

Up to date:
[https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

In a terminal, you can see what files are in the current directory with ```
ls
```

---

### Post by htor on 2007-11-06
ions, I like this way of autostarting F@H.=D>

How can I see the text that F@H outputs ?
I think becase of the screen command usage ** it's possbile**.

---

### Post by jpkotta on 2007-11-12
No need to muck with screen to get the output.  The client always copies stdout to the FahLog.txt file.

---

### Post by rogerhc on 2008-02-04
**/etc/rc.local** auto start method

I auto start Folding, after initial installation and first startup (that is only time FAH needs user input) by adding a line to /etc/rc.local so it looks like this

```


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Roger starts Folding 
# See http://fahwiki.net/index.php/Running_the_FAH_client_on_Linux
su - roger -c "cd ~/Folding; ./FAH504-Linux.exe >/dev/null &"
# /Roger

exit 0


```

I keep my Folding stuff in ~/Folding and my Linux username is roger. Adjust both in the "su - username ..." line above per your own setup.

I learned this rc.local auto start method at 
[http://fahwiki.net/index.php/Running_the_FAH_client_on_Linux](http://fahwiki.net/index.php/Running_the_FAH_client_on_Linux)

:popcorn:

---

### Post by pfwd.tech on 2008-03-13
Thanks for writing this post.  It works great.  I've been try to do this for ages.

---

### Post by sites on 2009-06-14
I'm using the newer client, fah6, & none of these autostart attempts are working.  I'm assuming that the only change would be executing ./fah6 instead of ./FAH504-Linux.exe.

Could someone help confirm or correct this?

---

### Post by jpkotta on 2009-06-15
> **sites said:**
> I'm using the newer client, fah6, & none of these autostart attempts are working.  I'm assuming that the only change would be executing ./fah6 instead of ./FAH504-Linux.exe.

Could someone help confirm or correct this?

Did you try the methods in the wiki ([https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome))?  Those are mostly kept up to date.

---

### Post by sites on 2009-06-15
Strangely enough, I managed to get it working.  But thank you for the link. :D

---

