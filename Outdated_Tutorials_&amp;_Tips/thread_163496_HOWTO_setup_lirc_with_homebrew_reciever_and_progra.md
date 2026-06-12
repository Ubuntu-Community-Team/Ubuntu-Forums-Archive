---
title: "HOWTO setup lirc with homebrew reciever and program your keybindings..."
date: 2006-04-21
forum: Outdated Tutorials &amp; Tips
---

### Post by encompass on 2006-04-21
These instructions are no longer valid for the latest ubuntu.  Might I recommend closing this and going here... 
[http://ubuntuforums.org/showthread.php?p=8741679#post8741679](http://ubuntuforums.org/showthread.php?p=8741679#post8741679)
It is based on these instructions.
BR...
I would like to say that it looks like a fix for this every annoying problem has been released. [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/65174](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/65174) As soon as I get the guts to try gutsy, I hope to try it out and see how well it works with the serial setups.  Post if you find any good news. :D
HOW-TO:	Home-brew receiver setup, common uses, and ideas for IR receiver
I would like to say thank you for everyone who helped me do this.  I learned a great deal from those that have helped me.  In so much that I feel others should know what I know.  So I am producing a how-to to help others who felt like me.
Cheer y'all.
I started be going to the lirc website and looking for recommended receivers.  I always wanted to make my own receiver but never had the time so I ended up purchasing one from here for very cheap.. [http://www.zapway.de/index1.htm](http://www.zapway.de/index1.htm).  The device came very quickly.  Got it from Germany and I live in Finland.  I was impressed with the device.  But how to start.

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 

1.Downloads and Installs...
NOTE: With the next command that I used the 2.6.12 kernel, which at the time was the newest I could use with Ubuntu defaults, so if you wish to use a different one enter it.  If you want to use one the matches you computer... look at...

> 
uname -r


It should tell you something like 2.6.12 so just take that num.num.num and replace it with the one I used...
OK got it? (hope so)...

> 
sudo apt-get remove lirc
sudo apt-get install linux-source-2.6.12 build-essential
cd /usr/src/
sudo tar xvf linux-source-2.6.10.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
cd /usr/src/linux
sudo make oldconfig
sudo make menuconfig
sudo make include/linux/version.h
sudo make modules
sudo touch /usr/src/linux/Rules.make


Download the source code for the lirc tool... [http://www.lirc.org/](http://www.lirc.org/)
Go to where you downloaded the file and type: (remember the name of the file... mine with lirc-0.8.0.tar.bz2)
It would be important to also note that this file needs to be in the /usr/src/linux/directory when it is extracted.  So move it there when you do finaly get it downloaded... then run.

> tar -xvf lirc-0.8.0.tar.bz2

A new directory will be created with a pile of files in it:
Change to that directory and type:

> 
sudo ./setup.sh


ALL righty... now select the first option then select the home-brew receiver.
All good?  Lets get compiling and installing....
[[IMG]http://img162.imageshack.us/img162/6246/lircsetup1hq.th.png[/IMG]](http://img162.imageshack.us/my.php?image=lircsetup1hq.png)
[[IMG]http://img161.imageshack.us/img161/3912/choice8oq.th.png[/IMG]](http://img161.imageshack.us/my.php?image=choice8oq.png)

> 
make
sudo make install


If everything went good, no errors that is, lets start-up that lirc receiver!
<--/dev/ttyS0 is com port 1 so if you need com 2 use ttyS1...-->

> 
setserial /dev/ttyS0 uart none
sudo update-modules
sudo depmod -ae
sudo modprobe lirc_serial
sudo modprobe lirc_dev


You should get a /dev/lirc0.  That is your lirc device!
Now lets poke the animal to see if it moves:
You should get something like this...
[[IMG]http://img162.imageshack.us/img162/8500/mode26xu.th.png[/IMG]](http://img162.imageshack.us/my.php?image=mode26xu.png)
> 
sudo mode2


Point your remote control or other IR device to the receiver and press some buttons.
"OH MY GOSH!!"
(At least that's what I said as I hugged my confused wife hold the remote I told her to press buttons from.)


- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


2. Setup and use...

The next step is to make these changes permanent so that when you reboot, your device will be up and running every time you boot.
We need to create a file so let's use an editor...

> nano lircd

Type the following in the editor and save and close with the file name:
'homebrew'

> 
#! /bin/sh
# /etc/init.d/homebrew: Loading the Homebrew IR receiver (IT'S ALIVE!).
setserial /dev/ttyS0 uart none
modprobe lirc_serial
modprobe lirc_dev
sleep 1
ln /dev/lirc0 /dev/lirc
lircd


Close and save the file with 'ctrl-x'
A few more things...

> 
chmod +x homebrew
sudo mv homebrew /etc/init.d/
sudo ln -s /etc/init.d/homebrew /etc/rcS.d/S99homebrew


Once that is done... everything hardware wise should be working just fine.  You can test it by rebooting... and typing:

> 
mode2


and pressing buttons again. (Don't forget to hug your wife.)
If it works, let's move on to setting up your remote control.
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

3.  Setup your transmitter with your reciever...

First find out your remote control. I hand a 'KONIG IR9836', how did I know?  It is on the remote itself.
Then I checked out the list of preconfigured remotes found here... [http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/)
My remote was not on the support list, so I had to make my own which wasn't too hard.
If your remote is on the support list... skip this next section...

A. Use irrecord to program a driver for your remote...
As scary as it sounded to me, I found irrecord a very simple program to use.
Knowing that your system is ready, type:

> sudo irrecord remote_name

this will start the irrecord program and record your buttons to the file remote_name.  This file is what will be used as your lircd.conf file located in the /etc/ directory.
Follow the intructions carefully.  If you make a mistake just start up the program again... and use a different name like remote_name2 and 3 and so forth.  It took a while for me... I kept messing up what name to what button... so I had remote_name 13 when I was done. :P

B. Time to insert the lircd.conf file...
Next, once you have your config file for your remote the way that you want it:

> 
sudo cp remote_name13 /etc/lircd.conf
sudo killall lircd
sudo lircd


Lets see if you can make your beast take your language!

> irw
now press some remote keys...
you should get something like this...
[[IMG]http://img49.imageshack.us/img49/5753/irw5ew.th.png[/IMG]](http://img49.imageshack.us/my.php?image=irw5ew.png)
It will have the names of the buttons that you have entered into irrecord diplayed everytime you press a button.
If so your over all the hard parts.
We can now set your remote buttons to do different things with different programs.
Attached to this post is a file called 'lircrc.txt' this file will have a basic setup of what I used for my remote with my lirc program.
Go ahead a get that file... open it with nano and setup a nother terminal window with irw running.
Like this:
[[IMG]http://img225.imageshack.us/img225/6611/lircrc7ji.th.png[/IMG]](http://img225.imageshack.us/my.php?image=lircrc7ji.png)
now... when you are typing in your settings just go to the command you want to change...
prog = totem  <--- this is the program that uses lirc that lircd should look for...
button = GREEN <--- This is the button signal that is given when you press the button you want... you will see it on the left with the irw command running.  in my case 'GREEN'
repeat = 1 <--- This is if you want the computer to sence the signal over and over, or just once and ignore the repeated signals from the remote.  This is good to have on with things like volume and channnel change.
config = play <--- this is the command sent to the program that lirc is set to look at.  In this case, play is sent to the program totem to well, play the information in totem.
The begin and end is just to devide the file up into sections of commands... they are needed and I wouldn't change them.
OK so you have made your changes, now press ctrl-x and save the file as .lircrc in your home directory.
That should be it... try your program, like totem, and start a file and press pause or adjust the volume.  IT should work, if you want, I will do my best to help you out.

Additions notes:
Keyboard events:
I wanted to use my reciever while using OOImpress and found this little guy...
> irxevent
I set the fallowing in my lircrc file...
> 
begin
	prog = irxevent
	button = BLUE
	config = Key Right CurrentWindow
end

begin
	prog = irxevent
	button = RED
	config = Key Left CurrentWindow
end
That makes it so that when I have my presentation running I can go forward and back in my presentation.

If you have more ideas or things you have done... feel free to email me and I will place it here and give you credit.
NOTE: you can record signals from many different things... forinstance, now I can shutdown my computer at night with my cellphone.  Cool huh?  if you have any ideas.. please submit and I can add it to this howto.

---

### Post by Greeface on 2006-04-23
You said > sudo apt-get remove lirc
sudo apt-get install linux-source-2.6.12 build-essential
sudo tar xvf linux-source-2.6.10.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
cd /usr/linux
sudo make oldconfig
sudo make menuconfig
sudo make include/linux/version.h
sudo make modules
sudo touch /usr/src/linux/Rules.make but "sudo tar xvf linux-source-2.6.10.tar.bz2" doesn't work because I never downloaded the file

how do i correct this?

---

### Post by encompass on 2006-04-23
[QUOTE=Greeface]You said  but "sudo tar xvf linux-source-2.6.10.tar.bz2" doesn't work because I never downloaded the file

how do i correct this?[/QUOTE]
You quoted me... my second line...
sudo apt-get install linux-source-2.6.12 build-essential
contains the download.  it is located in
> /usr/src/
NOTE:  I see your problem... if you fallow everything you may not have been in the /usr/src/ dir... added the change thanks.

---

### Post by TmP on 2006-04-27
Hi!

I'm trying to set up my remote. It works through a tv tuner (winfast2000xp).

I'd like to follow your suggestions, but since I'm fairly fresh to Linux, I would like to know what I'm doing... 

I assume I can copy these steps of yours:
> 
sudo apt-get remove lirc
sudo apt-get install linux-source-2.6.12 build-essential
sudo tar xvf linux-source-2.6.10.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
cd /usr/linux
sudo make oldconfig
sudo make menuconfig
sudo make include/linux/version.h
sudo make modules
sudo touch /usr/src/linux/Rules.make 


So after this step, we have a Linux kernel ready to be compiled. Where exactly did you add the lirc? Where did you learn it? I'm lacking some basic knowledge...  

Next step depends on using your homebrew receiver:

> If everything went good, no errors that is, lets start-up that lirc receiver!
<--/dev/ttyS0 is com port 1 so if you need com 2 use ttyS1...-->

Quote:
setserial /dev/ttyS0 uart none
sudo update-modules
sudo depmod -ae
sudo modprobe lirc_serial
sudo modprobe lirc_dev

Mine works a bit differently. It's connected directly to the tuner, through a jack socket. According to my dmesg my ir receiver is detected as bttv0's subdevice: remote0.
> 
/sys/bus/bttv-sub/devices/remote0
/sys/devices/pci0000:00/0000:00:09.0/remote0


Can I use it to connect to LIRC? There is a configuration file for my receiver, so i guess it's supported.

And here's my dmesg

> [4294727.018000] Linux video capture interface: v1.00
[4294727.130000] bttv: driver version 0.9.15 loaded
[4294727.130000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294727.141000] bttv: Bt8xx card found (0).
[4294727.143000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[4294727.143000] PCI: setting IRQ 5 as level-triggered
[4294727.143000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294727.143000] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 5, latency: 32, mmio: 0xde000000
[4294727.143000] bttv0: detected: Leadtek TV 2000 XP [card=34], PCI subsystem ID is 107d:6609
[4294727.143000] bttv0: using: Leadtek WinFast 2000/ WinFast 2000 XP [card=34,insmod option]
[4294727.143000] bttv0: gpio: en=00000000, out=00000000 in=003ff502 [init]
[4294727.182000] bttv0: using tuner=38
[4294727.182000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[4294727.184000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[4294727.186000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[4294727.189000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[4294727.293000] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[4294727.293000] tuner 1-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[4294727.343000] bttv0: registered device video0
[4294727.348000] bttv0: registered device vbi0
[4294727.353000] bttv0: registered device radio0
[4294727.353000] bttv0: PLL: 28636363 => 35468950 .. ok
[4294727.561000] bttv0: add subdevice "remote0"
[4294727.957000] bt878: AUDIO driver version 0.0.0 loaded
[4294727.968000] bt878: Bt878 AUDIO function found (0).


I've been struggling with this tuner of mine for 3 months, and it turned out it's recognised wrong. I've corrected it and posted the solution in the forums, but I need to add a way to make the remote controll working as well.

Thanx for Your help!

---

### Post by encompass on 2006-04-27
If , according to lirc's website, your reciever work with linux then we are doing good so far.  I can't describe the full reason why we need to recompile the kernel, but I think it is to grabe certain parts that are needed when compiling our lirc download that we do later.
When you get to the choice of what kind of reciever you have... don't choose the homebrew but what ever reciever your suppose to have.  Not sure what.  But it will probably be on that list somewhere.  from there... you do't have to free the com port.  But you should run mode2... if you get a signal that great you can make it work.  Otherwise... well, I can try to help, but havn't the fogiest clue how your reciever works.

---

### Post by [Yatta] on 2006-05-21
Wondering if any can help me here... when i do
```
mode2
```
i see gibberish when i press keys on my remote, btw which is a One-for-All URC-8910. When i use 
```
irw
```
Nada ](*,) .... I know that is sorta good :cool:. If i remember correctly i jsut need to find lircd.conf file for my 8910.
Any help would be greatly appreciated.

---

### Post by encompass on 2006-05-21
[QUOTE='[Yatta]']Wondering if any can help me here... when i do
```
mode2
```
i see gibberish when i press keys on my remote, btw which is a One-for-All URC-8910. When i use 
```
irw
```
Nada ](*,) .... I know that is sorta good :cool:. If i remember correctly i jsut need to find lircd.conf file for my 8910.
Any help would be greatly appreciated.[/QUOTE]
Did you happen to do step three in my instructions?  It gives you the site to see if your remote is already setup.  It also sounds like you have a programmable remote... Those are great because you get to set the remote you want to use.
Probalby the easiest thing to do is to pick a remote setting in your remote control that uses all buttons.  Then setup the remote manually so that you can assign each button to a different event.  Need more help keep dropping lines here on the forum.

---

### Post by toganet on 2006-05-21
Greate how-to, but for some reason this is not working for me.  

I'm working off of a fresh install of Breezy, kernel version 2.6.12-9-686, and all is well until I get to the 'make' step in compiling lirc.  At this point, I get a string of errors:
```
make[5]: *** [/usr/src/lirc-0.7.2/drivers/lirc_gpio/lirc_gpio.o] Error 1
make[4]: *** [_module_/usr/src/lirc-0.7.2/drivers/lirc_gpio] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.12-9-686'
make[3]: *** [lirc_gpio.o] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.7.2/drivers/lirc_gpio'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lirc-0.7.2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.7.2'
make: *** [all] Error 2

```

This happens with lirc versions 0.7.2 and 0.8.0.  

I'm hoping I made a stupid mistake that will stand out.  I have successfully done this in the past, on this exact machine, with the same hardware and software configuration, though the kernel version may have been different.

---

### Post by [Yatta] on 2006-05-27
:arrow:  **encompass** Sorry i never noticed there was a reply. I have my URC-8910 working now. I found the lircd files needed :D 

NOW my problem is that every time i boot up i lose my lirc ](*,)  When i check the dev dir i get:
$ ls -l /dev/li*
crw-rw----  1 root root 61, 0 2006-05-27 05:17 /dev/lirc0

Where previuoulsy i had 
/dev/lircd= and /dev/lircm| 

On boot i also get:
```
[4294689.432000] lirc_serial: port 03f8 already in use
[4294689.432000] lirc_serial: use 'setserial /dev/ttySX uart none'
[4294689.432000] lirc_serial: or compile the serial port driver as module and
[4294689.432000] lirc_serial: make sure this module is loaded first

```
Right now i'm trying to script to see if this will still allow lircd to work

===EDIT===

I tried the script.. nothing.. quick question dont i have to be root to setserial? .. i'm redoing the script but doing it as **sudo -s -H** not sure if that'll make a difference but nothign tried nothing gained :D

=== Edit #2===

NOW it works .. no applause please, no applause.. :mrgreen: 
I typed in **irw** at the command prompt pressed keys on my remote and i recievved a output. BRAP!!! BRAP!!! Thanks for the script.
Granted i know there should be an easier way.. but i'll save that for when i get more verse in linux.
 When i do **ls -l /dev/li*** :
```
$ ls -l /dev/li*
crw-rw----  2 root root 61, 0 2006-05-27 06:34 /dev/lirc
crw-rw----  2 root root 61, 0 2006-05-27 06:34 /dev/lirc0
srw-rw-rw-  1 root root     0 2006-05-27 06:34 /dev/lircd
```
So i guess it generates the files upon load???

---

### Post by [Yatta] on 2006-05-27
One thign i noticed.... the homebrew script doens't work all the time. Soemtime when i reboot...
irw works no problem other times
```
~$ irw
connect: Connection refused
```
So i have to run 
 /etc/init.d/homebrew 
Then i'm back working again

Starting to get to me now... i want to know how to properly 
setserial /dev/ttyS0 uart none
from the beginning so lircd_serial can take it over.. instead of it hearing that t is in use

---

### Post by [Yatta] on 2006-05-29
I had enuff..... i ended up recompiling my kernel setting the serial as a module and just made sure that lirc_serial was loaded first... VOILA!!!!!!!! On reboot lirc up an running no problem.
2 weeks of work on lirc just aout complete.
Thanks for the help though

---

### Post by _Petya_ on 2006-06-05
Hi!

I' ve tried to follow this howto, and got this:

[http://pastebin.com/760853](http://pastebin.com/760853)

What's the problem?

Petya

---

### Post by [Yatta] on 2006-06-05
do u have all proper packages to build lirc??
```
sudo apt-get install build-essential bin86 kernel-package

sudo apt-get install libqt3-headers libqt3-mt-dev
```
 it seems like u mae also be missing the headers for ur kernel...... check synaptic for the following:

linux-headers-2.6.15-23

PLUS it makes no sense u
```
make install
```
when u have errors errors when u do make.
BTW when u compiled did u also get errors?

---

### Post by Greeface on 2006-06-06
Bah, Dapper!  I had it working on breeezy but it stopped when I upgraded.  Now when I follow the instructions and i try to "modprobe lirc_streamzap" (i am not using a serial receiver, hence the streamzap part) it gives me this error: ```
WARNING: Error inserting lirc_dev (/lib/modules/2.6.15-23-386/misc/lirc_dev.ko): Invalid module format
FATAL: Error inserting lirc_streamzap (/lib/modules/2.6.15-23-386/misc/lirc_streamzap.ko): Invalid module format

``` What am i doing wrong?  I just want it to work again!

thanks a bunch

---

### Post by encompass on 2006-06-07
could be that lirc doesn't work with the new kernel.
I have yet to make it work in dapper... I am still doing all that stuff with dapper latter.  I have otherthings I am doing right now.
If youwant to try to get it working in dapper go for it... then just make your own howto.
Sorry that I can't help you right now.

---

### Post by Greeface on 2006-06-08
Ah, I figured it out, I had the old linux-source and linux-headers packages installed and they never got upgraded with the new kernel.  I just updated 'em and remade that symbolic link, and then tried again and it worked.

Thanks for the howto, by the way, it saved me hours.

---

### Post by encompass on 2006-06-22
It works in Dapper just the same way... I tried getting it to work with the built in stuff but it was too confusing... funn a package would make things worse.  Anyway, you can fallow the same instructions until I get the new howto up.

---

### Post by amr2205 on 2006-06-30
After a little effort and some changes to the circuit, it works! Thankyou for this Howto, it was very useful for me. Keep the good work.=D>

---

### Post by Jhongy on 2006-07-26
This is a great howto.... it should really help me get my report (MCE remote) installed.... Am I right in thinking that this creates a kernel module, which must be recompiled every time I update the kernel?

---

### Post by encompass on 2006-07-26
Thanks for the compliment... and yes.. new kernel... new compile... sorry, that is why I wish they made a better package for it.

---

### Post by zarej on 2006-09-28
When I restart my computer remote does not work unless I do the following commands:

```
$sudo killall lircd
$sudo lircd
```

What shall I do to skip this process? 
PS. I follow all the instructions and use the given /etc/init.d/homebrew script.

---

### Post by encompass on 2006-10-01
I am currently working on it... it has to do with the init script that it runs... I think you have to manually change that setting so that it finds the right port.  I have found that I have to do that same thing.  Thanks for the question.

---

### Post by Jimmy The Clown on 2006-10-27
This how-to worked great in helping me set up my mythbox using dapper and a homebrew serial receiver with LIRC.

Unfortunately, after I rebooted everything went poof. I had irw working and keys mapped to mythtv. My remote was changing channels and scrolling around and all that good stuff. On reboot nothing works. I have dev/lirc but no dev/lirc0 which I think is the issue.

doing killall lircd and then restarting lircd doesn't help. Running mode2 does nothing, irw gives me a "no connection".

Even running thru the howto I can't seem get everything working again manually. Anyone got some clues?

-JTC

---

### Post by mirshafie on 2006-10-30
Everything works well until i get to the part to test my remote (All In One URC-8203) with irw. irw starts, but when i press buttons, absolutely nothing happens.

I've used the ready made config for my remote, and I've made my own with irrecord, but it's the same result with both.
I've also tried to use my remote with IRKick, but again, nothing happens when i press buttons, though IRKick seems to recognize LIRC (which it did not with the precompiled package from the repos).

I'm on Edgy and have a zapway homebrew reciever. Anyone know how to solve this?

Edit: looks like irw works with other remote controls, with their respective configs. So how come my URC-8203 doesn't work with irw when it works with irrecord?

---

### Post by fdmarco3 on 2006-11-07
i followed this howto and finally my remote works but i have problems trying to use it in programs such as mplayer...i have to be root to use lirc and if i run irw as normal user it gives me a "connect: Permission denied" and the file .lircrc must be located in /root because lirc looks for it there...i think the problem is in:

> Download the source code for the lirc tool... [http://www.lirc.org/](http://www.lirc.org/)
Go to where you downloaded the file and type: (remember the name of the file... mine with lirc-0.8.0.tar.bz2)
It would be important to also note that this file needs to be in the /usr/src/linux/directory when it is extracted. So move it there when you do finaly get it downloaded... then run.

Quote:
tar -xvf lirc-0.8.0.tar.bz2 

when i compile lirc i am root...
how can i do to solve my problem?
thanks in advance

---

### Post by zarej on 2006-11-08
@fdmarco3
I has the same problem. Check permission on /etc/lircd.conf is readable for all and reboot your comp. After reboot everything was fine in my case.

---

### Post by fdmarco3 on 2006-11-08
thank you zarej your suggestion works for me ;) Now all ok, great!!!:D

---

### Post by energiya on 2006-12-28
> /usr/src/linux/lirc-0.8.0$ sudo ./setup.sh
dialog not found!

no errors until this point ](*,)
a little confused... help please...

*** EDIT ***
False alarm!!! After a "aptitude dialog setserial" it works! :mrgreen:

---

### Post by zarej on 2007-01-06
The solution is:
```
sudo apt-get install dialog
```

---

### Post by encompass on 2007-01-06
Thank you for posting your results....

---

### Post by joshidax on 2007-02-09
First of all : THX for this great HowTo !
I have been truggeling with lirc since switching from Suse to Kubuntu Edgy last November.
I first tried to get the IR from my Nexus-s to work using eventx and then found this is nowhere native supported and used  av7110_loadkeys.
As I wanted much more using a remote, i finally bought a homebrew serial ir receiver and this is the most frustrating experinece I ever had .
I reinsatlled Kubuntu now 3 times , tried Ubuntu as no howto really worked , I even installed a seriel mouse to test my com port wich worked fine and this evening followed this howto.
Actually it still does not work but , huray I have a mode2 output the first time in 3 weeks !!!!
Unfortunately no wife to hug :-)
So my problem :
I have Kernel 2.6.17-10-generic and used the latest lic 0.8.1.
First I thought it is not working ,just as the other howtos's i followed but now I have this:
Starting mode2 and pressing keys on the remote nothing happens
Disconnecting the IR module and reconnecting, it receives a signal once.
Typing again , nothing , disconneting , resonnecting , once it gets an output.
I hope anybody here beeing so happy to get lirc to work has a suggestion what went wrong and were  I can start looking at .
Thx in advance !
Maybe there are more people having the same problem , so when mode2 is not responsive try at least once disconnecting and reconnecting! 

greetings Dax

---

### Post by encompass on 2007-02-10
Sounds like your batter may be going dead.
Sounds crazy but it happened to me once.
Most people using these recievers end up using some really old remote that has a bettery that works very maybe a second.  Happened to me.
Try finding another remote device and trying again.
If you got mode to... odds are it is working.

---

### Post by encompass on 2007-02-10
So you _did_ get mode2 signals when you press your remote buttons?

---

### Post by joshidax on 2007-02-10
Thanks for getting back on this.
Yes I received signals via mode2.
Unfortunately no battery issue , tried a 8in1 remote and just to doublecheck a nexus-s remote.
Same behavior on both , once i get a signal after reconnecting the ir , but just once.
Last night i tried the reciever on a win machine , worked without problems using winlirc..
Any suggestion is welcome !

---

### Post by encompass on 2007-02-10
That is very interesting... if the reciever works then we know it has got to be something with the driver or the os.
So lets think about it...
have you provided the set seriel part of the setup.  did you reserver the port for the device.  Redo those steps or, make sure they were done.

---

### Post by joshidax on 2007-02-12
So I have done this a few times already
please have a look at the code , looks fine by me:
> 
test@kubuntu:~$  lsmod |grep lirc_
lirc_serial            14592  0
lirc_dev               16484  1 lirc_serial

test@kubuntu:~$ ls -al /dev/lirc*
crw-rw---- 2 root root 61, 0 2007-02-12 18:59 /dev/lirc
crw-rw---- 2 root root 61, 0 2007-02-12 18:59 /dev/lirc0

only weak point in my configuration startup i saw
> 
[17179636.336000] lirc_dev: IR Remote Control driver registered, at major 61
[17179636.344000] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179637.344000] lirc_serial: auto-detected active high receiver
[17179637.344000] lirc_dev: lirc_register_plugin: sample_rate: 0


Found an article where it was stated it should appear as low receiver
but according lirc.org active high receiver should be ok , too.....
Anybody has it run and working with this dmesg ?

greetings
> 


---

### Post by encompass on 2007-02-12
Sorry but I don't know that much... :)
But I do know that you should set serial.  It is the number one thing that happens to people doing this kinda stuff....   You need to do it at every boot.
What did you type for the mode2 command?

---

### Post by joshidax on 2007-02-12
Hi again !
I used the startup script just as you discribed in the HowTo
using :
> setserial /dev/ttyS0 uart none
This seems to work as , when I change this i get an error on startup
about the bussy device.
The mode2 I used see here ,Strange enough I get the same result using
> 
mode2
or
mode2 /dev/lirc
or
mode2dev//lirc0

Always the same ,connecting IR ,once i get an output
I will once agin startall over and post when i finally suceeded.

---

### Post by encompass on 2007-02-13
did you use -d
mode2 -d /dev/lirc0

---

### Post by joshidax on 2007-02-13
Hi !
so feeling like Odysseus!
ok, all from scratch , used kubuntu eggy 6,10 live cd
Sytem:
Asus P2B-DS,Dual PIII 800, 1 GB Ram,ATA-100 controller,3x160 GB HDD Samsung,Nexus-s DVB card 2.1 Fullfeatured
Software
-Did all upgrades>- used 2.6.17-11-generic and lirc-0.8.1
- Following the howto i just once when trying to use : ./setup 
had to install 'dialog' package using apt
-all went well . no error 
( there were warnings but the compile went through without stopping)
Used exactly these commands:
> 
setserial /dev/ttyS0 uart none
sudo update-modules
sudo depmod -ae
sudo modprobe lirc_serial
sudo modprobe lirc_dev

AND ?
> 
sudo mode2 #same behavior as in first posting
sudo mode2 -d /dev/lirc0 #same behavior as in first posting
sudo mode2 -d /dev/lircd
mode2: error opening /dev/lircd
mode2: No such file or directory
 
Just to make sure  , i then tried the 'homebrew' script
and exactly followed the chart
On restart all looks well again, lirc and lircd device seen but same behaviour.
As it does not matter which lirc device i use , the connect /disconnect  thing seem to be normal when the hardware is not properly configured. I give up !
Thanks for all your help , but I will try again using the device method as I still have the interface from my nexus-s .
regards

JoshiDax

---

### Post by encompass on 2007-02-14
Don't know then...
I still can't quite perfect the system working on boot.
I will try the instructions I made on my system again. and then see if I missed something.  But this wouldn't be the first time I have used these instructions.  Are you using the serial reciever?  Is that what you one and the driver that you chose?

---

### Post by starfry on 2007-06-21
So when downloading the kernel sources which version should I use for Feisty? I am running 2.6.20.16 but there is no "linux-source-2.6.20.16" package. There is "linux-source-2.6.20" which I have downloaded. Is this right?

Are any settings / selections to be made while in "make menuconfig" ? There is no explanation of this so I just exited to accept defaults. Also, I had to do "sudo apt-get install libncurses" otherwise "make menuconfig" does not work.

When I do "make modules" it takes a lifetime. Surely only the modules required need to be built? Perhaps this is because I did nothing when in menuconfig?


Also, on a second machine (to be my mythtv client) I have Xubuntu Feisty and that is running 2.6.20.15. when I do "make modules" on that it bombs out with an error:

make[1]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'. Stop.
make: *** [arch/i386/kernel] Error 2

Any ideas?  thanks :p

---

### Post by TheEremite on 2007-07-14
I'm at a loss.

I made it through the whole tutorial. I had to change some permissions to make mode2 work as a normal user,  but it all works... but when I go to try it out in mythtv, I get nothing.

I linked a lircrc file from /home/mythtv/.mythtv/lircrc to /home/mythtv/.lircrc but I get nothing. Is mythtv lircrc aware by default?

thanks for any help

---

### Post by encompass on 2007-07-14
Did the irw command report back that your buttons were setup correctly?  Have you tested it with a simpler program like totem, or rhythmbox?
Glad to here this tutorial is still working.  Let's hope we don't have to do this with the future version of mythbuntu.

---

### Post by TheEremite on 2007-07-14
yeah, it works with irw

everything in the tutorial worked as described until getting to mythtv recognizing the signals.

I don't have any other programs installed... I have mythtv running without metacity/desktop setup. I guess I could install all that, but I'd rather not just to test the remote.

---

### Post by encompass on 2007-07-15
if that is the issue... then I think my work is done here and now you should make a new post on how to get the unit working with mythbox.  I don't use mythbox, but I think your issue involves them not lirc.  Sorry dude.

---

### Post by drytear on 2007-07-21
any idea to why irexec doesn't work ? 

i have :
```

begin
         button = SOUND
         prog = irexec
         config = totem
end

```
But it wouldn't start totem. The button is fine cause irw knows it.

---

### Post by encompass on 2007-07-21
> **drytear said:**
> any idea to why irexec doesn't work ? 

i have :
```

begin
         button = SOUND
         prog = irexec
         config = totem
end

```
But it wouldn't start totem. The button is fine cause irw knows it.

Did you make sure you have the irexec program running?
That was my mistake.  I just had it load when I started my gnome session as not all uses used irexec.
Hope that help.

---

### Post by Elv13 on 2007-07-21
it is what i get when i do irrecord (my receiver work (100% sure, confirmed)): .

Now start pressing buttons on your remote control.

It is very important that you press many different buttons and hold them
down for approximately one second. Each button should generate at least one
dot but in no case more than ten dots of output.
Don't stop pressing buttons until two lines of dots (2x80) have been
generated.

Press RETURN now to start recording.

irrecord: could not find gap.
irrecord: gap not found, can't continue


and when i do mode2, like 1000 thing aprear each second even if i dont touch the remote

---

### Post by encompass on 2007-07-21
I can see 2 things happening.  But I could be wrong on both. :P
IF the device is in the sun is will put up enough IR waves to make a signal.  Not good.  Try Covering the remote with your hand.  Does it still give signals?  What about the device, what kind is it?
Do you have more than one serial device and your picking up those signals?

---

### Post by Elv13 on 2007-07-22
no chance for sun, it is in my basement, their is any light exept the computer screen. But i dont know, my sound is noisy, it is possible that there is a lot of EMI (interferences) around, but i got it to work (almost) on gentoo, irrecord was working 1/2.

i got 1 serial port in the back of my computer case, but i thik their is one inside too, i dont know witch one is com1.

---

### Post by drytear on 2007-07-22
happy to say the irexec problem is solved. i had to start it just like lircd and it works.

---

### Post by segalion on 2007-09-13
For people having a AV Onkyo receiver, they can connect the IR out directly on the mic-in to have lirc working with the Onkyo remote.

[B]It doenst require no hardware, and no compiling tasks...!!!
[/B]
See instructions for feisty in this post...
[http://ubuntuforums.org/showthread.php?p=3255315#post3255315](http://ubuntuforums.org/showthread.php?p=3255315#post3255315)

---

### Post by visionviper on 2007-12-18
I am stuck at point where you type the "make" command. I get the following error:
```
make: *** No targets specified and no makefile found.  Stop.
```

I even tried using the -C option and directing it to the directory with the source code, but it gives me the same error.

EDIT: Just kidding, I figured out that I didn't have the g++ package installed.

---

### Post by visionviper on 2007-12-18
Where does the lircrc file go?

My MythTV install was not compiled (as far as I know) to have native lirc supprt.

---

### Post by encompass on 2007-12-18
> **visionviper said:**
> Where does the lircrc file go?

My MythTV install was not compiled (as far as I know) to have native lirc supprt.

Well mythTV may have a different setting... but it should go into your home... and I can remember but it may need to be hidden... like this...
.lircrc

---

### Post by Timon&amp;Pumba on 2008-01-17
I can properly configure my remote with irrecord: works fine!
Also I can see xmode2 respond to my remote control. You would say that it works nicely, BUT:
irw cannot connect to lirc: connection refused.

Also when I start for example Rhythmbox, I tells me:
Rhythmbox: could not connect to socket
Rhythmbox: Connection refused

The lircd socket in /dev/lircd has permission 666, so that should not be a problem, and again: xmode2 works fine.

Any pointers anyone?

---

### Post by encompass on 2008-01-17
ok... irw is what connects your lirc mode2 information to a command that lirc compatable devices can use.
run "man irw" to learn the command to point it to the proper device.  I don't use lirc anymore as my remote works automatically now.  it irw -d /dev/lirc0 or something similar I am sure. your vary close to complete this.

---

### Post by Timon&amp;Pumba on 2008-01-17
Well, I already did what you propose before I posted my problem.
To be, again, more precise; I am experiencing the same (part of) problem
a user describes here: [http://ubuntuforums.org/showthread.php?t=656859&highlight=lirc](http://ubuntuforums.org/showthread.php?t=656859&highlight=lirc)

> 
If I attempt to test the IR receiver with the irw command this is what I get
Quote:
$ irw
connect: Connection refused
However if I start the lircd daemon it doesn't give me the error when I run 'irw' immediatley afterwards, it just drops to a new line. However the second time I run 'irw' I get the connection refused error again. 'irw' seems to kill the lircd daemon for some reason
Quote:
$ sudo /etc/init.d/lirc start
Starting lirc daemon: lircd.
$ irw
$
$irw
connect: Connection refused 


Only the difference is though that at my setup "/dev/lirc0" en "/dev/lircd" do exist, en mode2 (xmode2) work correctly. Only irw does not work, en (I guess) therefor my lirc support is broken and not usable in for example rhythmbox.

---

### Post by encompass on 2008-01-17
double check that mode2 is working then try starting lirc and then irw.  is it still giving you the error?

---

### Post by BXCracer on 2008-12-23
everything seems to be working fine in 8.10 the only problem is that lircd does'nt starts up autamticaly using this script 
```
#! /bin/sh
# /etc/init.d/homebrew: Loading the Homebrew IR receiver (IT'S ALIVE!).
setserial /dev/ttyS0 uart none
modprobe lirc_serial
modprobe lirc_dev
sleep 1
ln /dev/lirc0 /dev/lirc
lircd 
```

Is there any other way to do it ?

---

### Post by justplay on 2009-01-04
Also having 8.10 and had the same problem with lircd. Everything worked fine only after manual start of lircd. Like this:
```
sudo lircd
```
Solved it with this "homebrew" in /etc/init.d/
```

#! /bin/sh
# /etc/init.d/homebrew: Loading the Homebrew IR receiver (IT'S ALIVE!).
setserial /dev/ttyS0 uart none
modprobe lirc_serial
modprobe lirc_dev
sleep 1
ln /dev/lirc0 /dev/lirc
start-stop-daemon --start --quiet --exec /usr/local/sbin/lircd

```
Works for me.

---

### Post by BXCracer on 2009-01-06
Thanks that worked for me too

---

### Post by swingboy3 on 2010-01-24
For me all is well up until the command

> $sudo killall lircd 

At which it replied

> lircd: no process found 

I assumed this might be normal and proceeded to 

> $lircd

and it returned

> Can't start lirc: "lircd: can't open or create /var/run/lirc/lircd.pid"

Also beyond that the command of 
> irw
is not found as well

Everything up to this point was very clear to me though.

I checked the directory and there is no folder lirc in /var/run/ which is disturbing to me.

Any help would be appreciated.

---

### Post by encompass on 2010-01-25
First I would like to say, I use my bluetooth and cell phone for my remote control now, so I haven't done this in a long while.
It is also 3 years old now and I am sure they have improved the process.
Could you tell a little more about your setup?  Especially your version of ubuntu that your running? The type of IR reciever your using and the intent of your use.
---
Best Regards,
Jason Brower

---

### Post by swingboy3 on 2010-01-25
Mythbuntu 9.10 with mythtv 0.22.  I haven't gotten to the Mythtv connectivity yet, but I will.
I am using my homebrew receiver which works according to the first section of your post.  It receives my signals just fine and I can use irrecord to create custom remote code.  I was able to transfer that into my lirc.conf file in /etc/.  But when I try to stop LIRCD or start it I can't find the file lircd.pid.   I don't know if this is a change to Ubunut 9.10 (lots of problems so far with some updates) or if LIRC is completely different.

Also the command IRW is not found.  I believe this should have been installed with LIRC.

As I said I followed your initial post all the way until I was supposed to restart LIRCD with my new lirc.conf file and it was missing the PID.

If this is not enough information please let me know.  Your post up until that point was really good.

---

### Post by encompass on 2010-01-25
Doesn't mythbuntu have a section specifically on how to setup your remote controll?
[http://www.mythpvr.com/mythtv/distribution/mythbuntu/mcc.html](http://www.mythpvr.com/mythtv/distribution/mythbuntu/mcc.html)

---

### Post by swingboy3 on 2010-01-26
Thanks for your help so far.  I have made some progress with your link and others, but here is what I have found.

Everything works if I do
> sudo make
sudo make install
sudo /etc/init.d/homebrew


in the /usr/src/linux/lirc.0xxx/ 
I don't want to have to recompile this every time I reboot and I shouldn't have to to run lircd

Otherwise there is no /var/run/lirc/ folder and thus no lircd.pid

What program creates the lirc/lircd.pid?

In addition I have made my lircrc file.  Where do I put it and how do I tie it to my existing configuration.

---

### Post by swingboy3 on 2010-01-26
So, as per normal, I have solved my own problem.  As it turns out for some reason at reboot the folder /var/run/lirc is completely removed. If I add one line in the homebrew file...> mkdir /var/run/lirc
After that all of my lircrc stuff fell into place and I am doing very well.
Excellent post my friend encompass.

---

### Post by encompass on 2010-01-27
Good problem solving.  They need a more up to date post.  Perhaps you could make a details set of instructions that could work with the most modern ubuntu.  I would reference to that.

---

### Post by swingboy3 on 2010-01-29
Hey Encompass,  Thanks for your suggestion.

I have made a new post

[http://ubuntuforums.org/showthread.php?p=8741679#post8741679]("http://ubuntuforums.org/showthread.php?p=8741679#post8741679")

I plagiarized much of yours but added quite a bit of stuff that was needed and changed the stuff that was wrong.

---

### Post by fitos on 2010-11-21
Hi guys!

I`m new user of linux (mythbuntu) and it seems to me too difficult ... I`m trying to slove issues with my remote.  I`m using homebrew receiver as shown on:

[http://www.lirc.org/images/schematics.gif](http://www.lirc.org/images/schematics.gif)

Remote from avermedia98 tuner

I run commands:

setserial /dev/ttyS0 uart none
sudo modprobe lirc_serial
sudo modprobe lirc_dev 			 		
ln /dev/lirc0 /dev/lirc
xmode -d /dev/lirc

and on the scree I can see frames which I sen by my remote - seems to be fine

but then I run:

lircd
irw 

and program is running, cursor in still position, when I press buttons on remote nothing happens.

Part of my etc/lirc/hardware.conf
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_DRIVER=""
REMOTE_LIRCD_CONF="/etc/lirc.conf"



driver file I was able to create by command :
irrecord -d /dev/lirc0 /etc/lirc.conf

during that remote was working perfecty

I try to run mythTV but it seems very hard thing I spent on that almost five days already. Does anyone knows what could be the reason of my troubles?

---

### Post by swingboy3 on 2010-11-21
Fitos,

First of all check out the newer version of this post:
[http://ubuntuforums.org/showthread.php?t=1393154](http://ubuntuforums.org/showthread.php?t=1393154)
It may help you.

Secondly have you gotten mode2 to work?

try running

>sudo mode2

You can point any remote you want at your receiver and it should just spit out garbage numbers.  This will test whether you have a properly built homebrew receiver or not and if you have things set up previously to this correctly.

Also I don't understand this line from your post 
"driver file I was able to create by command :
irrecord -d /dev/lirc0 /etc/lirc.conf"  

In order for IRW to work you need to have two working config files  The first is the lircd.conf file located at /etc/lirc/lircd.conf
This file is created using the irrecord command and following the instructions.  If you do not have things working to make the mode2 command work, then this will certainly not work.  Also instead of making your own custom lircd.conf file see if your current remote has an existing file.  You can check at:
[http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/)
Mine is a universal remote that I used a multifunction pre-programmed setup for and recorded my own custom codes using irrecord
Getting this file alone into working order should get irw to work.  Remember that once you make an lird.conf file you must restart both lircd and lirc. You can do this by:

>sudo killall lircd
>sudo /etc/init.d/lirc restart
>sudo lircd

You should get now warnings or errors when you do this.1

The second is .lircrc file located at /home/{uname}/.lircrc.  This file transfers the code that you get when you display the irw command to a command to run in a program.  I use mine primarily for mythtv, but it I also use it to run command line arguements using irexec.

---

### Post by fitos on 2010-11-22
Thank You for replying!!!

In my post earlier i wrote that I have run mode command - it shall be xmode2 - of course. Yes,mode2 works,seems to be fine. I put correct lirc.conf file for avermedia remote to /etc/lirc/lirc.conf.

In /home/rafal/ I found one file -  "xx.lircrc" - is it the one which shall work with irw?

I try to run as You said, see below, but still on irw command I didn`t get any response so I had to cancel it by ^Z

rafal@mythtv:~$ sudo setserial /dev/ttyS0 uart none
[sudo] password for rafal: 
rafal@mythtv:~$ sudo modprobe lirc_serial
rafal@mythtv:~$ sudo modprobe lirc_dev   
rafal@mythtv:~$ sudo ln /dev/lirc0 /dev/lirc
rafal@mythtv:~$ sudo mode2 -d /dev/lirc
space 3993675
pulse 9063
space 4428
pulse 627
space 499
pulse 626
space 1617
pulse 632
space 496
pulse 628
space 493
pulse 632
space 496
pulse 632
space 490
pulse 627
space 495
pulse 634
space 492
pulse 628
space 1621
pulse 628
space 495
pulse 636
space 1614
pulse 626
space 1627
pulse 622
space 1625
pulse 623
space 1620
pulse 631
space 1616
pulse 630
space 1623
pulse 629
space 1617
pulse 629
space 1622
pulse 626
space 1624
pulse 626
space 1621
pulse 623
space 1620
pulse 627
space 498
pulse 625
space 493
pulse 632
space 496
pulse 626
space 495
pulse 632
space 497
pulse 625
space 496
pulse 633
space 493
pulse 629
space 493
pulse 628
space 1626
pulse 622
space 1629
pulse 625
space 1612
pulse 632
space 39836
pulse 9055
space 2180
pulse 632
space 96031
pulse 9058
space 2179
pulse 631
^Z
[1]+  Stopped                 sudo mode2 -d /dev/lirc
rafal@mythtv:~$ sudo killall lircd
rafal@mythtv:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC
   ...fail!
 * Loading LIRC modules
   ...done.
 * Starting remote control daemon(s) : LIRC 
   ...done.
rafal@mythtv:~$ sudo lircd
lircd: there seems to already be a lircd process with pid 1704
lircd: otherwise delete stale lockfile /var/run/lirc/lircd.pid
rafal@mythtv:~$ irw
^Z
[2]+  Stopped                 irw
rafal@mythtv:~$

---

### Post by swingboy3 on 2010-11-22
It looks like the lirc daemon is getting clogged a little for some reason. So delete the process by:
sudo rm /var/run/lirc/lircd.pid
to stop it.  Or you can reboot.  Your choice.
Also you are putting your lirc.conf file in the wrong spot and it is likely overwriting something important you are also calling it the wrong name.

lircd.conf belongs in /etc/lirc/lircd.conf  
and it has a "d" in it.  It should look like [this]("http://lirc.sourceforge.net/remotes/adaptec/lircd.conf.AVC-2410")

The different codes are recorded from your remote or from an example config file.  If these are not correct irw will do nothing.  The lircd.conf file can decipher noise on the receiver from a specific pattern from the correct remote, so the lircd.conf file is specific to the remote you would like to use.

the .lircrc file is a hidden file  the "." before the file means that it is hidden.  It may already exist and is also specific to your remote.  To see if it is there go to /home/uname/ and type:  ls -a
The "-a" command will display even hidden files.
The .lircrc file can be automatically generated by installing ["mythbuntu-lirc-generator"]("http://packages.ubuntu.com/hardy/mythbuntu-lirc-generator")

This program can be installed by:
sudo apt-get install mythbuntu-lirc-generator
and then running it.  It will create an .lircrc file based on the lircd.conf file you should have already made.

When you reply post what is in your lircd.conf file and what is in your .lircrc file.

Also make sure that when you run mode2 that the terminal output changes as you press buttons on a remote.

---

### Post by fitos on 2010-11-24
Swingboy! 

It works now, thank You so much for Yor help!

The issue was probably with .lircrc file which not sure why was missing. I have run generator, created the file and I saw commands on irw.:lolflag:

---

### Post by justplay on 2011-05-12
> **encompass said:**
> First I would like to say, I use my bluetooth and cell phone for my remote control now, so I haven't done this in a long while.
It is also 3 years old now and I am sure they have improved the process.
Could you tell a little more about your setup?  Especially your version of ubuntu that your running? The type of IR reciever your using and the intent of your use.
---
Best Regards,
Jason Brower

Your HOW-TO helped me once again with IgorPlugUSB. Ubuntu 9.10, kernel 2.6.31-22-generic, lirc 0.9.0. Thanks!!
P.S. What do use for Bluetooth control?

---

