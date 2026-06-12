---
title: "can't enter ubuntu /welcome screen/"
date: 2016-01-04
forum: New to Ubuntu
---

### Post by 1ns1d3r on 2016-01-04
I'm trying to enter the password on welcome screen but there is no effect. If I enter wrong password - nothing happens and 'invalid password' on the screen. If I enter right password there is a black screen on a second and then welcome screen with password field again. The only one thing that I did before is installation of NVidia drivers (NVidia-352).

---

### Post by grahammechanical on 2016-01-04
Does the Nvidia 352 driver support your Nvidia graphic adapter? It does not support my Nvidia GT220. So, I cannot install Nvidia 352 driver. How did you install this driver. Through Additional Drivers? Or did you download from the Nvidia web site?

At the Grub boot menu if we select Advanced options for Ubuntu we open a sub-menu that will offer to load different Linux kernels. Included in the list will be kernel we can boot that will load recovery mode. In fact each kernel will have a recovery mode option.

At the recovery menu select Resume. That may load to a working desktop where we can experiment with a different video driver.

Regards.

---

### Post by 1ns1d3r on 2016-01-04
I found my videocard GTX 850M here [http://www.geforce.com/drivers](http://www.geforce.com/drivers)

I added a repo (ppa), then just install drivers in command line (sudo apt-get install nvidia-352).
So I guess that something wrong in my actions, could you explain how to install video drivers on ubuntu?

---

### Post by Bashing-om on 2016-01-04
1ns1d3r; Welll ....

While there is nothing inherently wrong in installing the proprietary nvidia graphic's driver from a PPA, there is no demonstrated need in your case to do so.
The 352 version driver is available in our software repository.
Presently, let's try and find out why the install of the driver has failed; clean up residue, and install the driver from the repo.

At the login screen activate a console interface with key combo ctl+alt+F1 and now we can look .

So what have we ?
As you are not able to activate the GUI - we resort to another means to gather information. We have a pastebin site for our use in cases such as this.
Install the tool:
```

sudo apt install pastebinit

```
Please post back - Between Code Tags - the outputs of terminal commands :
```

dpkg -l | grep -i nvidia | pastebinit
sudo ubuntu-drivers devices | pastebinit
sudo ubuntu-drivers list | pastebinit
cat /var/log/Xorg.0.log | pastebinit

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

The result of piping (|) the commands to our pastebinit site is a URL back in your terminal. pass these links back to this thread. We can access the files on the site to see what the situation may be.

[INDENT][INDENT]so a tale gets told
[/INDENT][/INDENT]

---

### Post by 1ns1d3r on 2016-01-07
unfortunately, I reinstall ubuntu (but I could just remove the driver...) and right now don't know which nvidia driver I need to install, how to detect right version of driver?

---

### Post by Bashing-om on 2016-01-07
1ns1d3r'; Hey, hey ..

> 
how to detect right version of driver?

1) Identify the hardware:
```

lspci -vnn | grep -i VGA

```
2) See what driver Nvidia recommends:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
3) See what ubuntu recommends:
```

sudo ubuntu-drivers devices | pastebinit
sudo ubuntu-drivers list | pastebinit

```
4) auto-install the driver IF all looks compatible:
```

sudo ubuntu-drivers autoinstall

```

Mind you, it is rare indeed that ubuntu makes a mistake in advising on a driver.

[INDENT][INDENT]all in knowing how
[/INDENT][/INDENT]

---

### Post by 1ns1d3r on 2016-01-08
I install nvidia-352 (recommendation from nvidia) and bumblebee (recommendation for systems with two videocards) and it looks fine - previous problem disappear. 
I can't detect second monitor - image duplicate on second one but I can't control it: extending image, e.g. /I remember that it was at settings->displays/  

response from first command (lspci -vnn | grep -i VGA)  - I see my integrated videocard. For similar command with "3D" - I see my discrete videocard.

response from the rest commands:
[http://paste.ubuntu.com/14440562/](http://paste.ubuntu.com/14440562/)
[http://paste.ubuntu.com/14440564/](http://paste.ubuntu.com/14440564/)

---

### Post by Bashing-om on 2016-01-08
1ns1d3r; Welp ....

As we now have :
> 
I install nvidia-352 (recommendation from nvidia) and bumblebee (recommendation for systems with two videocards)

I must wonder if there is now a conflict between BumbleBee and nvidia-prime .
What is presently installed ?
Post back - Between code tags - the output of :
```

dpkg -l | grep -i nvidia

```

With Nvidia picking up the slack, BumbleBee is now depreciated in favor of nvidia-prime IF this graphics situation is optimus .
nvidia-settings should permit setting up for 2 monitors .

[INDENT][INDENT]I would think
[/INDENT][/INDENT]

---

### Post by 1ns1d3r on 2016-01-10
> dpkg -l | grep -i nvidia
[http://paste.ubuntu.com/14457176/](http://paste.ubuntu.com/14457176/)

There are no options for tuning monitors and video performance is bad like no drivers is working in right way.

---

### Post by Bashing-om on 2016-01-10
1ns1d3r; Yeah ....

We do have a conflict on 2 fronts:
> 
ii  bumblebee 
ii  nvidia-prime

ii  nvidia-346
ii  nvidia-352

Where 'ii' is desired=(i)nstalled; 2nd 'i' is state=(i)nstalled.

Decide which graphic's' controller you want to utilize .. BumbleBee or nvidia-prime .. there can be but one in control .
Decide which graphic's driver you want to use ... 346 or 352 there can be but one making that interface between the card and the kernel . 



[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by 1ns1d3r on 2016-01-11
I've removed all and install only nvidia-prime and nvidia-352, but there is no effect - we have come to the origin: I can't to enter Ubuntu. Also I tried to install older versions of driver (e.g. 346, 340). I'm confused...

and one new thing! Sometimes my notebook shuts down because of overheat (as I think), probably drivers not properly control cooler on videocard.

---

### Post by Bashing-om on 2016-01-11
1ns1d3r; K

So ... what have we now to work from, now  ?
```

ls -ld ../1ns1d3r /home
ls -al .Xauthority .ICEauthority
sudo lshw -C display
dpkg -l | grep nvidia

```

and yes:
> 
Sometimes my notebook shuts down because of overheat (as I think), probably drivers not properly control cooler on videocard.

A real possibility as the display driver also interacts with the fan control system(s) (ACPI) .

[INDENT][INDENT]seek to find out
[/INDENT][/INDENT]

---

### Post by 1ns1d3r on 2016-01-11
We have following:

[http://paste.ubuntu.com/14472695/](http://paste.ubuntu.com/14472695/)

[http://paste.ubuntu.com/14472705/](http://paste.ubuntu.com/14472705/)

---

### Post by Bashing-om on 2016-01-11
1ns1d3r; OK;;;

So now presently you have no driver installed and of course no driver loaded . You want to discuss this, as to how why and a "proper" method to install a driver ?

We still do not know if "you" - 1ns1d3r ??? - have authorization to access your desktop ( ls -ld ../1ns1d3r /home ; ls -al .Xauthority .ICEauthority ).

-----------------
We have been going around and around - for a week- getting a driver loaded for you ... are you learning from this experience ?
If you do not understand, or have any question; please please ask .. We also exist as an institution of teaching and higher learning. We do want that you know .

[INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by 1ns1d3r on 2016-01-12
Sorry, Bashing-om, I didn't catch why this information important:
[http://paste.ubuntu.com/14479339/](http://paste.ubuntu.com/14479339/)
[http://paste.ubuntu.com/14479370/](http://paste.ubuntu.com/14479370/)

thank you, I'm learning, but I can't understand current problem fully. So let's continue)

---

### Post by Bashing-om on 2016-01-12
1ns1d3r; Hey ! Hey ...

We can do this

> **1ns1d3r said:**
> Sorry, Bashing-om, I didn't catch why this information important:
[http://paste.ubuntu.com/14479339/](http://paste.ubuntu.com/14479339/)
[http://paste.ubuntu.com/14479370/](http://paste.ubuntu.com/14479370/)

thank you, I'm learning, but I can't understand current problem fully. So let's continue)

So long as you are willing to learn I will hang with you.

Presently I am ware of 3 problems with your install.
1) You do not own your /home ... root now does instead of "you" . Until we make that right there is not much we can do .
Please re-confirm by posting back the result:
```

ls -al /home

```
where "you" - insider- should be the owner and the group .. for reference, my result:
```

sysop@1404mini:~$ ls -al /home
total 28
drwxr-xr-x  4 root  root   4096 May 19  2013 .
drwxr-xr-x 25 root  root   4096 Jan  7 17:23 ..
drwx------  2 root  root  16384 May 19  2013 lost+found
drwxr-xr-x 29 sysop sysop  4096 Jan 12 10:49 sysop
sysop@1404mini:~$ 

``` where my username is sysop.

2) There is no driver installed .. There can be only 1 ! When installing/re-installing a driver one must insure that all vestiges of the old driver have been removed . Then install the proper driver for the graphics card.

3) There is no graphic's driver loaded - because there is no driver installed.

--------------------
OK ? Do we need to pause and discuss permissions and ownership rights ?
See: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) ; [http://mywiki.wooledge.org/Permissions](http://mywiki.wooledge.org/Permissions)
------------

So we fix the authorization to your /home and then purge graphic's drivers and then install a graphic's driver. We know we can do this as we have done it before.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by 1ns1d3r on 2016-01-12
1) [http://paste.ubuntu.com/14480310/](http://paste.ubuntu.com/14480310/) - all permissions like on your machine

2) nvidia-352 is a proper driver (for GeForce 850M), but after its installation I can't enter system. If I install elder driver then the newest appears too.

---

### Post by Bashing-om on 2016-01-12
1ns1d3r; Hummm .....

odd ???
1st result
> 
drwxr-xr-x  3 root    root    4096 &#1103;&#1085;&#1074;.   4 17:21 /home

2nd result:
> 
drwxr-xr-x 30 insider insider 4096 &#1103;&#1085;&#1074;.  12 19:58 insider

we go with that 2nd, and say that access is alright .

So, we are back to purging and re-installing:
In that last output I do not see any entry for " ii bumblebee  " ; did you remove it ? As nvidia does prefer nvidia-prime, and nvidia-prime will be reinstalled when the 352 version driver is installed. We must avoid the conflict between BumbleBee and nvidia-prime  -> only one to control the GPUs .
```

sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-352

```
Reboot to see the effect.
Now show after coming back up:
```

sudo lshw -C display
dpkg -l | grep -i nvidia

```
Too see that the Nvidia module ( in linux a driver is a module ) is loaded ...
and that the 352 version of the Nvidia driver is installed ... in that process of installation are also installed the supporting packages .

Now at this point :
> 
If I install elder driver then the newest appears too.

on that dpkg output there will only be those for 352, as all others were purged (???) .

How to use prime:
After your computer has restarted, open the dash and type "nvidia". Open "Nvidia x-server settings".
Here you can choose between the intel and nvidia graphics driver. Choose the intel one for maximum power saving, choose the nvidia one for maximum performance.

After changing graphics card, you'll have to logout and log back in to apply the changes.

[INDENT][INDENT]all good now ?
[/INDENT][/INDENT]

---

### Post by 1ns1d3r on 2016-01-13
I've done
> 

sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-352



but after reboot I can't enter Ubuntu again. And it returns us to origin.

Responses for
> 

sudo lshw -C display
dpkg -l | grep -i nvidia


[http://paste.ubuntu.com/14490286/](http://paste.ubuntu.com/14490286/)
[http://paste.ubuntu.com/14490294/](http://paste.ubuntu.com/14490294/)

There were "rc bumblebee" and "ii bbswitch" - so as I understand it's config file for bumblebee and installed module from nvidia-prime - I've removed these too and tried to reinstall nvidia-352 -> fail at the end.

---

### Post by Bashing-om on 2016-01-13
1ns1d3r; Yuk . 

Do not know ... the search continues

Insure in bios that both the Intel on-die chip AND the PCi (Nvidia) GPU are enabled . IF disabled in bios the operating system will never see the devices !

One more time clean up the system:
```

sudo apt-get purge bumble*
sudo apt-get remove --purge nvidia*
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Now, What is the world is preventing the build of the Nvidia driver ?
what returns:
```

sudo find / -name "NVIDIA-Linux-*"
ls -al /usr/bin/nvidia*
ls -la /etc/modprobe.d/
cat /etc/modprobe.d/blacklist.conf
cat-n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

When we KNOW there is nothing preventing the build, we try again. Then look at the log file and see what took place.

[INDENT][INDENT]when I know better
[INDENT][INDENT][INDENT]I will do better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

