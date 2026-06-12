---
title: "Computer boots to terminal instead of GUI"
date: 2015-08-10
forum: New to Ubuntu
---

### Post by thomas58 on 2015-08-10
I just did a clean install of 32-bit LXLE 12.04.5 from the live DVD onto my wife's old computer.  It's an eMachines D3415 with an AMD Sempron 3400+ processor, 1.5GB RAM, an NVIDIA GeForce 6100 graphics adapter, and a 160GB HDD.

The system booted and ran well from the DVD and displayed a graphical user interface.  However, when I boot from the HDD the entire screen is a terminal window.

I need to know what I did wrong and how to fix it as she's not going to want to work from the Linux command line (nor am I). :(

Thanks in advance for any help and please ask if you need any more information about the old computer.

---

### Post by Bashing-om on 2015-08-10
thomas58; Hi ! Welcome to the forum.

A better description of what you are booting to ?
Maybe a black screen with only a cursor in the top left corner ?

Then maybe looking at a graphics driver issue.

Try booting up with the boot parameter " nomodeset ":
This tutorial:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Additional info:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Let us know how it goes;
we get ya booting

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by thomas58 on 2015-08-10
Bashing-om; Hi and thanks for the reply.

Yes, I get a black screen that asks for the user name and password and then gives me a blinking cursor on the left side of the screen.

I followed the directions in the tutorial to update the grub configuration.  I only got as far as the command "gksudo gedit /etc/default/grub" as pressing <Enter> resulted in "Gtk-WARNING **: cannot open display:"

I was trying to add "nomodeset" to the GRUB_CMDLINE_LINUX_DEFAULT line but maybe I'm not understanding how to do it.

Any further enlightenment would be greatly appreciated.

Thanks.

---

### Post by Bashing-om on 2015-08-10
thomas58; Hey;

Pardon me, but I do not have a clear idea of what is going on here .
Let's get to a real terminal and see what we can determine.
We do that from grub's boot menu.
Reboot the system, and as soon as the bios screen clears depress and hold the right -shift key -; that brings up the grub boot menu.
with the top most current kernel selected (asterisk) press the 'e' key for edit mode -> boot parameters screen.
In this screen arrow down to the line similar " inux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " and replace "  quiet splash $vt_handoff  " with the term " text " with out the quotes;
key combo ctl+x to continue the boot process to the terminal TTY1.

Log into this terminal with your credentials.
Now we venture into waters I am not accustomed to in the LXLE environment. I am not sure what the Desktop Manager is at this time to start the GUI. But I "think" it is 'lightdm' .

Try this to start the GUI from terminal and to see if any errors are generated/reported.
```

sudo service lightdm start

```


I do expect the system to scream and holler, perhaps there is no graphics driver to drive the GUI . We will see and then take a look at that situation.

Admittedly, installing 'buntu should not be at all difficult, but there are these outside cases . I will be interested to see how it relates with that old Nvidia graphics card .

[INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]to restoration
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by thomas58 on 2015-08-11
Bashing-om;  Hi again!

Well, I followed your instructions as far as the "sudo service lightdm start" command.  After re-entering the password, the whole screen filled with lines of text that involved either starting or stopping various services.  They all had an [OK] after them except for "Starting Initializes zram swaping" which failed.  There were several [OK] lines after that with the last one being "* Checking battery state...  [OK]."  That is a bit odd as this is a desktop machine and doesn't have a battery.  Anyway, that's where it stopped and where it still is.  I'm just going to leave it there until I find out what to do next.

Thanks much for your help so far.

---

### Post by Bashing-om on 2015-08-11
thomas58; Hey and yikes !

Looks as if I steered you wrong, I have been "looking" about and I did find :
Edit: wrong site .[http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)
[http://www.lxle.net/forums/](http://www.lxle.net/forums/) <- Better link.
Their WIKI . And there are instructions to start the GUI !

Try the terminal command:
```

startlxde

```

Keep in mind we have not to this time ruled out that the graphics driver is at fault here ( or no driver installed).

We should verify the graphics card:
Boot back to the TTY1 terminal and execute :
```

lspci -vnn | grep -i VGA

```

See that a grphics driver is loaded. Rather then you doing a lot of effort we just want to know what is in the configuration line.
For reference my output:
```

sysop@1404mini:~$ sudo lshw -C display
[sudo] password for sysop: 
  *-display:0             
       description: VGA compatible controller
       product: RV515 [Radeon X1300/X1550]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       [color=green]configuration: driver=radeon latency=0[/color]
       resources: irq:16 memory:e0000000-efffffff memory:fd4f0000-fd4fffff ioport:4c00(size=256) memory:fd400000-fd41ffff
  *-display:1 UNCLAIMED
<snip>

```
Where I am running an old ATI card and I have the open source graphics driver 'radeon' loaded.
Does your config line reflect 'nvidia' ?

[INDENT][INDENT]a call from out here in left field
[/INDENT][/INDENT]

---

### Post by thomas58 on 2015-08-11
Bashing-om, Hi!

Typing the "lspci -vnn | grep -i VGA" command resulted in output that reflected the nvidia GeForce 6100 adapter.  Running "startlxde" results in the message "Program 'startlxde' is currently not installed," followed by instructions for installing it.  Should I do that or might it break something?

Thanks for the help.

P.S.  Do I want lxde when I'm running lxle?

---

### Post by Bashing-om on 2015-08-11
thomas58; Yikes (again) !

I have no idea how I got a LXDE result on my LXLE search . I failed to spot my error !
NO, do not install "LXDE" . We will get LXLE to boot . I go back to making sure it is a 'lightdm' Display Manager such that the "thought" for the GUI start command is still valid.

Wires crossed
[INDENT][INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT][/INDENT]

---

### Post by thomas58 on 2015-08-11
Bashing-om, Hi!

Don't worry, I haven't installed anything and won't until I get an 'all clear."  I did for fun(?) try a 'startlxle' command only to be informed there isn't any such.

Thanks again.

---

### Post by Bashing-om on 2015-08-11
thomas58; Hey;

I do have good news. The Geforce 6100 card is still supported " The 304.xx driver supports the following set of GPUs: >> GeForce 6100	0x0242 "

So if and when we get the GUI activated, and can get to the desktop we can install a driver from the "Additional Drivers" utility .

Meanwhile, back at the ranch
[INDENT][INDENT][INDENT]see what I can learn about the LXLE GUI.
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-08-11
thomas58; Well;

As I live and learn:
[http://www.lxle.net/forums/discussion/598/need-to-know-how-to-disable-gui-for-server/p1](http://www.lxle.net/forums/discussion/598/need-to-know-how-to-disable-gui-for-server/p1)
seems to indicate we may have better success in starting the GUI as :
```

sudo service lxsession  start

```

[INDENT][INDENT]who wudda thunk it ?
[/INDENT][/INDENT]

---

### Post by thomas58 on 2015-08-11
Bashing-om,  Hi again!

Sounds like progress.  I suppose there's no way to install the driver from the Live DVD?

Just an idea.

Thanks for continuing to work on this for me.

---

### Post by thomas58 on 2015-08-11
Bashing-om, Hi!

I just got your last message.  Entering "sudo service lxsession start" gives the message "lxsession: unrecognized service."

Thought you should know.

---

### Post by Bashing-om on 2015-08-11
thomas58; Welp;

I still think my first thunk was correct. 'lightdm' to start the GUI IF we had a graphics driver for the GUI, I bet it would start.

Let's try this to get to the desktop.
Reboot back to grub's boot parameter screen. and instead of replacing the terms add an additional term nomodeset
key combo ctl+X to continue to the GUI login screen . 
If you get this far, login with your credentials -> desktop ? Degraded graphics is OK at this point.

If now you are at the desktop, look around for "Additional Drivers" ( I can not tell you where it is in the LXLE DE ) and install the recommended driver - which I do expect to be the 304 version .

[INDENT][INDENT][INDENT]fingers crossed
[/INDENT][/INDENT][/INDENT]

---

### Post by thomas58 on 2015-08-11
Bashing-om, Hi!

Did as you said by adding "nomodeset" to the line in the boot parameter screen, pressed ctrl+x, and logged in.  It came up with the command prompt just as before.

Thanks for keeping on with this.

---

### Post by mörgæs on 2015-08-12
I have used one of these graphics cards myself and the only version that worked well was 15.04.
If you have some space left you could try Lubuntu 15.04 in its own partition. Remember to select additional/closed source drivers during install.

---

### Post by thomas58 on 2015-08-12
Hello mörgaes!

I'll give Lubuntu 15.04 a try if I can't get LXLE to work.  This is a 10 year old computer and LXLE is supposed to work well with older hardware.  I'm not sure if the same is true for Lubuntu.

Thanks for the suggestion.

---

### Post by Bashing-om on 2015-08-12
thomas58; Hey ;


I do support mörgæs' suggestion. As much as I might want to know why 12.04 LXLE does not boot to a GUI, the more important thing is to get you a usable system.
I have had nothing but good results on old hardware with (L)ubuntu, Have not tried LXLE, as when I have had problems installing 'buntu I have used puppy or DSL; When there just is not the horsepower to run 'buntu. A lack of horsepower is not the issue in your case, however much maxed out ram would help .

Let's do this right from the start.
Download 15.04 LXLE .iso file
Verify the .iso integrity:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

verify the burn:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
(there is an option on the install medium's expert ,ode boot menu to "check disk for defects)
Boot the liveDCD ( that install medium) to "try ubuntu" making sure that all devices function as expected.

Then install to hard drive ... IF 'buntu is to be your sole operating system I do recommend the option " errase disk and install ubuntu" and let the wizard set all up. 

[INDENT][INDENT]your call
[INDENT][INDENT][INDENT]what ya want to do 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by thomas58 on 2015-08-12
Bashing-om, Hi!

I'd like to do as you suggest and make a clean install of Lubuntu 15.04.  Since I wiped out the Windows XP installation on the old computer that I used to burn the Live LXLE DVD, and my other computers either can't burn DVDs or are running Ubuntu from a Live DVD because the HDD needs replacing, I'll have to find another machine to make the disc.  When I get that done, I'll let you know how it went.

Until then, thanks so much for helping me with this problem.

---

### Post by Bashing-om on 2015-08-12
thomas58; Hey;

As you can work this from a Live "try ubuntu" mode ; download and burn to some install media.

In this initial stage as we are getting nowhere with getting the spin-off functional, let's work with a release we are all comfortable with. I sure do like (L)ubuntu, just as a suggestion.

It is our goal to get you up on 'buntu
[INDENT][INDENT][INDENT]we all will fall over backwards -if that helps - in trying
[/INDENT][/INDENT][/INDENT]

---

### Post by mörgæs on 2015-08-12
If burning is a problem then install CDs/DVDs can be bought cheap. Many websites sell them.

---

### Post by thomas58 on 2015-08-12
Bashing-om and mörgæs, Hi guys!

Success!  I downloaded the Lubuntu 15.04 i386 iso and discovered the file is only 696MB, which means I was able to burn it to a 700MB CD-R disc on my T43 laptop.  Calculated the MD5 check-sum for the iso and saw that it matched the value on the download site.  Booted the old computer from the Live CD and had it check the disc for errors.  None were found.  So I re-booted into the 'try Lubuntu' mode.  Everything seemed to work as expected so I set about installing Lubuntu from the Live CD GUI.  The installation was entirely straightforward with no problems encountered.  I never did see an option to select additional/closed source drivers, but it doesn't matter as the re-start after installation resulted in the GUI coming up.  So far it's working perfectly and I see no reason for it to not continue doing so.

Thank you both so very much for getting my old machine up and running and for all your time, research, and effort in helping me out.  I really appreciate it.

All the best!

---

### Post by col48 on 2015-08-12
Please ignore this if not relevant!

Occasionally (maybe once a month), my 12.04 boots up to a full-screen terminal - I guess due to the boot process sometimes getting past the point where it wants to start lightdm before lightdm is ready to start (there must be a race going on behind the scenes between threads in the boot process)

I have two remedies which each get to the GUI login screen.

1. command-line signon with the usual username/password. Then 'sudo service lightdm restart' (NB REstart) which asks again for my password
or
2. Right Alt+Sys Rq+K

---

### Post by Bashing-om on 2015-08-12
thomas58; Outstanding !

Pleased that you are now pleased.
If and only if this situation is now at an end;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThread](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThread)

Any additional questions, we are here, open as many threads as needed . - one thread to one question -

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by mörgæs on 2015-08-12
Good, please spread the word.  Only use old releases as a last resort.  15.04 is one of the most complete buntus to date with regards to hardware support.

---

