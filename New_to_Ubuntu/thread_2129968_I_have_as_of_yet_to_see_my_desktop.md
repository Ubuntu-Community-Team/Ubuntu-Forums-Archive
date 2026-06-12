---
title: "I have as of yet to see my desktop"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by Mecharius on 2013-03-27
Working with a Toshiba satelite. Has AMD Turion(tm) II Dual-Core Mobile M500 for its CPU.

Recently acquired the book Ubuntu Unleashed and it came with an install disk for Ubuntu 12.10, I wanted to try this on one of the machines I have laying around. Went through the process, and it installed Ubuntu on the Toshiba, eliminating windows in the process, unfortunately now when I start it up it goes to the GNU GRUB menu. This gives me the options Ubuntu, Advanced options for Ubuntu, as well as two memory tests. So, being the new user that I am, the obvious choice is Ubuntu. Select that and I get a black screen with a flashing _ symbol. if I let this sit for awhile i will eventualy receive 
[       7.808320] sp5100_tco: mmio address 0xfec000f0 already in use

My question here is how would I go about correcting this issue?

---

### Post by r.stiltskin on 2013-03-27
There are bug reports involving the sp5100 module (for example [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1055096]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1055096")), and some people reported that blacklisting that module solved their problems.

Get to a terminal window: try ctrl+alt+F2 from your black screen & see if that gets you to a command line prompt.  If so, login there. If that doesn't work reboot and select recovery mode from the grub menu and then choose "drop to root shell".

Run this command:
```
printf "blacklist sp5100_tco" | sudo tee /etc/modprobe.d/blacklist-sp5100.conf
```
(In a root shell you can omit the word sudo.)

That will create a file /etc/modprobe.d/blacklist-sp5100.conf containing the line **blacklist sp5100_tco** which should prevent the sp5100 module from loading.  Reboot & see if that helps.  If not, you can easily delete that file.

---

### Post by Mecharius on 2013-03-28
> **r.stiltskin said:**
> There are bug reports involving the sp5100 module (for example [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1055096](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1055096)), and some people reported that blacklisting that module solved their problems.

Get to a terminal window: try ctrl+alt+F2 from your black screen & see if that gets you to a command line prompt.  If so, login there. If that doesn't work reboot and select recovery mode from the grub menu and then choose "drop to root shell".

Run this command:
```
printf "blacklist sp5100_tco" | sudo tee /etc/modprobe.d/blacklist-sp5100.conf
```
(In a root shell you can omit the word sudo.)

That will create a file /etc/modprobe.d/blacklist-sp5100.conf containing the line **blacklist sp5100_tco** which should prevent the sp5100 module from loading.  Reboot & see if that helps.  If not, you can easily delete that file.

ctrl alt f2 did nothing from the black screen. 

The only way i see to access the command line is to have one of the options, such as recovery mode highlighted and then hit c. Typed in what you posted and received:
error: can't find command 'printf'

I have at no point seen anything which allows me to select an option 'drop to root shell'

There has to be something that I am missing. 

When I select the recovery mode I am given a black screen with a decent quantity of information scrolling on it that ends at 

[       5.099871] toshiba_acpi : Toshiba Laptop Acpi Extras version 0.19

On this black screen Amidst the provided information I do see 

[      5.011652] microcode ; failed to load file amd-ucode/microcode_amd.bin

Could this have something to do with my problem? Or is it something that will be a problem later on?

---

### Post by oldfred on 2013-03-28
You probably do not have nVidia, but nomodeset sometimes works for other video issues. But it sounds like you may need other boot options.

 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


 [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by Mecharius on 2013-03-28
in fact, the only command that currently seems to work is date.

I do appreciate any patience and attention that is thrown my way. persistance is one of my qualities, but I can only go so far without help.

---

### Post by r.stiltskin on 2013-03-28
> **Mecharius said:**
> ctrl alt f2 did nothing from the black screen. 

The only way i see to access the command line is to have one of the options, such as recovery mode highlighted and then hit c. Typed in what you posted and received:
error: can't find command 'printf'

I have at no point seen anything which allows me to select an option 'drop to root shell'

There has to be something that I am missing. 

When I select the recovery mode I am given a black screen with a decent quantity of information scrolling on it that ends at 

[       5.099871] toshiba_acpi : Toshiba Laptop Acpi Extras version 0.19

On this black screen Amidst the provided information I do see 

[      5.011652] microcode ; failed to load file amd-ucode/microcode_amd.bin

Could this have something to do with my problem? Or is it something that will be a problem later on?
Yes there is something you're missing.

When you highlighted recovery mode and then hit 'c', you were opening a grub command line, not a complete linux shell, so you didn't have all of the normal bash commands available.  What I wanted you to do is highlight recovery mode and hit enter -- in other words boot into recovery mode, and at the end of that process, after all the scrolling lines, you should be presented with a menu and among the selections is "drop to root shell".

Do you not see that menu?  If not, what is the last thing you see when you boot in recovery mode?

Also, please eliminate one mystery: exactly which model of Toshiba Satellite is this?

One more thing: can you boot Ubuntu directly from the CD using the "try Ubuntu" selection from the initial screen?

---

### Post by Mecharius on 2013-03-28
> **r.stiltskin said:**
> Yes there is something you're missing.

When you highlighted recovery mode and then hit 'c', you were opening a grub command line, not a complete linux shell, so you didn't have all of the normal bash commands available.  What I wanted you to do is highlight recovery mode and hit enter -- in other words boot into recovery mode, and at the end of that process, after all the scrolling lines, you should be presented with a menu and among the selections is "drop to root shell".

Do you not see that menu?  If not, what is the last thing you see when you boot in recovery mode?

Also, please eliminate one mystery: exactly which model of Toshiba Satellite is this?

One more thing: can you boot Ubuntu directly from the CD using the "try Ubuntu" selection from the initial screen?

The machine does not have which model it is written on it, so I would not know how to check beyond that. I acquired this one off of one of my coworkers when he upgraded. It started off with windows seven on it, if that is in any way helpful. I did understand that there was supposed to be a menu at the end of recovery mode, but no such thing appeared. The last line presented in this was:

[       5.099871] toshiba_acpi : Toshiba Laptop Acpi Extras version 0.19

try ubuntu is not an available option when I start up the machine with the disk in. As far as I can tell, the only way to access said disk is by hitting f12 and getting into the boot options. From there selecting boot from disk. When I go by this boot option, it begins to load and then freezes at the purple screen with two or three of the circles illuminated below the word UBUNTU.

---

### Post by Mecharius on 2013-03-28
I feel like an idiot, and I have yet again found myself with an example of why I need to do further searching before I come begging fo help. I have to give thanks to oldfred for pointing this out to me. Some how, the push any button when I begin boot had managed to escape me. It was a link posted that managed to show this to me. Yes, I have the option to try ubuntu.

---

### Post by Mecharius on 2013-03-28
And as for the helpfulness of this Try ubuntu option, it leads back to the purple screen which freezes with a few of the circles illuminated. The numerous times I have had to resort to the power button to shutdown the machine so I may get to a different screen cannot be healthy for my machine. But what can be done at this point? moving on...

At the suggestion of a friend who has slightly more experience with computers then I, I tried to install ubuntu again from the disk. unfortunately this had the same effect as everything else which leads to the purple screen. I am going to let this sit for an hour or so while I try to dig up more information that may be helpful, waiting to see if there is any other change to the screen. Maybe it is not frozen, just slowed to a crawl. That is my new hope at least.

---

### Post by oldfred on 2013-03-28
That dammed "any" key. I still am looking for it on my keyboard. :)

Do you get the accessibility icons at bottom of screen? Tiny keyboard & person?

f6 lets you then choose boot options. If not nomodeset there are others. But what options may be required is trial and error unless you have seen a thread where someone says what works. Since last entry on boot screen has to do with acpi I might try some of those settings. See post #4.

---

### Post by Bashing-om on 2013-03-28
Mecharius; Hi!

Regretfull that you are experiencing such difficulties installing. Try with baby steps:
1. Boot the install cd - bios is set to boot the cd as 1st boot priority;
2. At the purple screen, if you hit the enter key what results ? We hope at this point you load to a language selection screen. Do you ?
[INDENT=2]one step at a time


just try'n to help

[/INDENT]

---

### Post by Mecharius on 2013-03-28
After letting it sit for some time I had to eventualy hard shutdown then bring it back up. Went to boot options then back into the cd. From the menu which among other things allows me to select thr try ubuntu option, I hit f6 to bring up other options. Here I see that acpi is set to off (presented as (acpi=off). Now, I may not currently be the most computer literate individual but I am fairly certain that acpi is something which in most cases is needed. Could changing this have a positive result for my machine?

In the other options I tried nomodeset then hit try ubuntu without install. From there back to the purple screen. Only instead of Ubuntu, it says ubuntu 12.10 in much more plain lettering. this screen stops and presents with two things I have seen before.

[      53.816300]  sp5100_tco: mmio address 0xfec000f0 already in use_amd.bin

and

[      52.733627] microcode: failed to load file amd-ucode/microcode_amd.bin

At least this time I am given something when it stops. I feel at least some progress has been made. enter key does nothing. Pressing any key does nothing. One small step and all that...

---

### Post by Mecharius on 2013-03-28
@Bashing-om:
As soon as the purple screen pops up, i can hit any key (enter included) and get the language selection options. 

I am willing to sit through having this broken down for me Barney style if that is what it takes to have my machine up and running. Everything I do is exposing me to more of this machine, which is helping me have a more complete knowledge of my machine as an entire system as well as the specific operating system that I am trying to use. Much appreciation is given to all those who are willing to help me through this drawn out process.

---

### Post by Mecharius on 2013-03-28
So I selected the nomodset as well as the no acpi setting from the boot options and then hit try ubuntu without install. This was my why not(?) option, and, suddenly i find myself with a proper desktop up and running. Ubuntu would appear to be functional with those two settings. Now the only problem is, this is the try version. How shall I go about installing it like this?

---

### Post by Mecharius on 2013-03-28
Sa (situational awareness) is something I hear frequently in my job. It is drilled into us again and again and again. Yet, apparently I lack the ability to apply this when I am off duty. I look at the desktop and I see an icon labelled 'Istall ubuntu'. probably should have tried that before posting up my previous comment.

---

### Post by Mecharius on 2013-03-28
unfortunately in the install screen from the try ubuntu option it froze up on the select wireless internet option. I guess saying it is frozen is not quite correct, as the cursor is able to be moved, it is just perpetually in the loading icon. But I still feel as if I have achieved some form of victory here, finally I have gotten to the desktop, even if it is only a temporary thing. At least now I have a better idea of what must be done.

---

### Post by oldfred on 2013-03-28
Do you have an Ethernet connection? Hardwired not wireless? There seem to be a lot more wireless drivers and not all are included with the installer. But almost all wired drivers are, so you can get on-line with the wired Ethernet driver.

---

### Post by Mecharius on 2013-03-28
Unfortuantely I do not have the option to connect to the internet via ethernet cable. Since my internet is available via this building and not some elected option (this si the cheapest option available) then i must rely on the wireless which they have flowing through the walls of my room. I do believe that it would not ne smile upon if I broke into the comms room and hardwired myself into the internet.

---

### Post by Mecharius on 2013-03-28
I have received the same result from selecting the 'do not want to connect' option.

---

### Post by oldfred on 2013-03-28
I do not know all the issues with wireless, mine just works. Those that know can help but it may be best to start another thread.
lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Now post a new thread and attach (via the paperclip in advanced reply) the abs-network.txt file which will be in your home folder.

Some also have had this issue.
 There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/996568)
From liveCD before install. 
sudo apt-get remove ubiquity-slideshow-ubuntu
or (ubiquity-slideshow-lubuntu) (and ubiquity-slideshow-xubuntu)
The Alternate iso is another option as it is text based and also does not use the slideshow.
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

### Post by squakie on 2013-03-28
> **Mecharius said:**
> So I selected the nomodset as well as the no acpi setting from the boot options and then hit try ubuntu without install. This was my why not(?) option, and, suddenly i find myself with a proper desktop up and running. Ubuntu would appear to be functional with those two settings. Now the only problem is, this is the try version. How shall I go about installing it like this?

You should be able to try booting your installed ubuntu but you want to edit the boot line when you go to it on the grub menu.  From there, add those 2 options and it should boot to the gui.  If it does, post back and we'll tell you how to make simple edit to make it permanent.

---

### Post by Mecharius on 2013-03-28
I highlighted in the grub ubuntu and hit 'e' to take me to the edit option. Now I am looking at this, and am uncertain as to where I would add these? Or even if I am in the proper location.

---

### Post by oldfred on 2013-03-29
On the linux line where it has splash quiet replace the splash quiet with nomodeset  and the acpi setting you used before. No commas, just entries like the quiet splash are. 
Without quiet splash you will see the boot process scroll by instead of the splash screen.

---

### Post by Mecharius on 2013-03-29
I added nomodeset and no acpi after quiet splash and now I am back to just receiving the sp5100_tco.

---

### Post by Mecharius on 2013-03-29
@oldfred
I did not see your most recent post until after I had added what I just posted, I shall correct the issue time now.

---

### Post by Mecharius on 2013-03-29
I did as you said, let it sit for about ten min. Back to the black screen with scrolling information. This ended with:

[      4.949820] Adding 2877436k swap on /dev/sda5.  Priority:-1 extents:1 across:2877436k

tried pressing various keys, but this was what stayed on the screen.

---

### Post by r.stiltskin on 2013-03-29
Try editing the grub line for recovery mode with the same no apic and nomodeset parameters & see if that lets you get to a root shell.  Then maybe you can manually install the amd64 microcode (if this package is included on the install cd)

```
apt-get update && apt-get install amd64-microcode
```

---

### Post by oldfred on 2013-03-29
Were you ever able to do r.stiltskin's suggestion in Post #2?

---

### Post by r.stiltskin on 2013-03-29
> **r.stiltskin said:**
> Try editing the grub line for recovery mode with the same no apic and nomodeset parameters & see if that lets you get to a root shell.  Then maybe you can manually install the amd64 microcode (if this package is included on the install cd)

```
apt-get update && apt-get install amd64-microcode
```

I just realized that apt-get update is pointless as long as you can't get online, but the other part, apt-get install amd64-microcode, may still be worth trying if you can get to a root command line.

---

### Post by Mecharius on 2013-03-31
> **oldfred said:**
> Were you ever able to do r.stiltskin's suggestion in Post #2?
I was not able to get into command line except for the grub version(does this have a name to differentiate from normal command line?) which would not allow me to do as was suggested.

---

### Post by Bashing-om on 2013-03-31
Mecharius;
Try this to get to a command line terminal:
Boot up to the grub boot menu; ensure the top line is highlighted and depress the "e" key for edit mode;
Arrow down to the line containing "quiet splash" delete these terms and all after; insert the term "text" -with out the quotes -
ctl+x keys to continue the boot process -> text terminal login;
Enter your user name and then password ( will get no response to the screen).

Hopefully now you are logged into the system and can now execute commands.
[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by Mecharius on 2013-03-31
> **Bashing-om said:**
> Mecharius;
Try this to get to a command line terminal:
Boot up to the grub boot menu; ensure the top line is highlighted and depress the "e" key for edit mode;
Arrow down to the line containing "quiet splash" delete these terms and all after; insert the term "text" -with out the quotes -
ctl+x keys to continue the boot process -> text terminal login;
Enter your user name and then password ( will get no response to the screen).

Hopefully now you are logged into the system and can now execute commands.[INDENT=3]
just try'n to help

[/INDENT]


The desired result was not achieved. Back to the black screen with the scrolling information. Ending line of:

[      8.471373] sp5100_tco: mmio address 0xfec000f0 already in use. 

After reading over what you said, I typed in my username and password, did not work. So i tried it with a space between. Did what i could but had no result. I am assuming that by no response from the screen you mean I will not see what I am typing. Because that is exactly what I have. Hit enter after typing in the information both times.

---

### Post by Mecharius on 2013-03-31
Is there anyway to make it install from the command line when I am in the try ubuntu option on the disk? Change the settings from there?

---

### Post by Bashing-om on 2013-03-31
Mecharius;
Yes, the present install may be mounted and accessed from the liveCD. However, it is late my time and I am tired. Let me look over again where you stand and I will get back at you in my Am. I am GMT -6 time.
[INDENT=3]
I'll be Baackk

[/INDENT]

---

### Post by Mecharius on 2013-04-01
The amount of assistance that has been given to me here has far exceeded my expectations. Everyone who has offered me suggestions has my gratitude. Persistance is one of my qualities, I shall not be beaten by a Toshiba

---

### Post by r.stiltskin on 2013-04-01
I'm a little uncertain about one of the F6 "other options" that you selected when you successfully booted from the CD.  It's clear that **nomodeset** was one of them, but was the other one **acpi=off** or **noapic**? Obviously these are two very different parameters.  Are you sure that when you attempted booting by editing the grub command line you typed those parameters _exactly_ as they appeared in the LiveCD options?  e.g., a blank space separating each option from the others, but no blank spaces within either command?

---

### Post by Mecharius on 2013-04-01
it was acpi=off, for what ever reason when i typed it up here i was thinking no acpi. I shall double check and retry to be certain, but I am sure that I had typed them properly into my linux machine.

---

### Post by Mecharius on 2013-04-01
Yes, I had typed in acpi=off. But, I found at least part of my issue, I caught myself doing it, and corrected the matter as it came up. I was doing two things wrong, and I feel like an idiot for it. I was putting a space between the no and the m, and I was typing modset, not modeset. Much thanks for setting me up to notice this. Now I must learn how to make these settings stay.

---

### Post by Bashing-om on 2013-04-01
Mecharius;
Wonderful attitude, you will go far.

Ok; procedure to edit the system files to exclude the module "sp5100_tco".
1. Boot up the liveCD to the desk top (use your boot parameters);
2. At the desk top activate a terminal -> combo keys ctl+alt+t
2a. In this terminal you will establish a mount point; terminal commands:
```
sudo mkdir /mnt/test
```
now one wants to make sure of what one is working with;
2b, ```
 sudo fdisk -l
```
in that output IF there is only one hard drive will be a line "sda1" with an "*", the "*" denotes the boot flag set here.
now we are going to attach that hard drive to the file systems' mount point as established above;
3. ```
 sudo mount /dev/sda1 /mnt/test
```
3a. Make sure we are smart and working with the correct file system;
```
 mount
ls -la /mnt/test/etc/default/grub ##(known reference)
```you see the mount point is made (last line from the mount command ?) and the "ls" command shows that the grub file exist. Looking good !
4. Now it gets dicy, you are going to enter super user mode, where you have supreme authority, ubuntu is going to do exactly what you tell it to do -even if it is wrong- pay careful attention to what you and I are doing. We are going to make that edit to a system file.
5. First make a backup - for whatever might happen reason-;
```
 sudo cp /mnt/test/etc/modprobe.d/blacklist.conf /mnt/test/etc/modprobe.d/blacklist.conf-bak 
```
6.```
gksudo gedit /mnt/test/etc/modprobe.d/blacklist.conf
``` ##note the use of "gksudo" we are using a graphical application and we want the elevated privileges as opposed to the term "sudo".
6b. The file editor opens with the blacklist.conf file loaded ("*Untitled Document 1") is a non-invasive bug you can safely kill it.- black bold X and "close without saving -
6c. gedit is ubuntu's default file editor, in this instance it is a what you see is what you get editor. So, arrow down to the last line in that file and to the end of that line do a "return" to start a new line. Documentation is a really good thing to do - the 5 "w"'s.
add: this line: -> > #XXX01Apr13 edit made to exclude module sp5100_tco as it conflicts with other modules upon booting.where XXX is your initials. Reason: makes a search easy when looking at some later time for any edits to any files. the "#" says to ignore this line as only a comment and not to be processed.
enter to make a new line
insert >  blacklist sp5100_tco ## do another retun
and insert a "#" on this line. That indicates to anyone/thing reading this file that there is a newline character in that last line.
add only "sp5100_tco
#"[last line]
double check that I and/or you have made no mistakes.
7. SAVE and exit from your work -> back to the terminal.

8. MOST IMPORTANT if you have to - tie a string on you finger - (un)mount the hard drive from the file system, failing to do so will result in file system corruption on some level. I say again UNMOUNT that hard drive.
```
 sudo umount /mnt/test
```
9. Close everything out and back on the desktop -> reboot
10. Try now to boot into your installed system without any boot parameters and see if you can. No, try with only the "nomodeset" option. No ? Add the next option .... No ? I have a boot options we can try.
-------------
This is lengthy and looks daunting, once you have done this a couple of times you can do it in a matter of seconds.
------------
I have proof read this twice, looks good. But please look it over carefully, make sure you fully understand what we are doing and how we are doing it. Please if you have any questions, now is the time to ask before proceeding.

I welcome anyone else to proof read my directions.[INDENT=3]
how now brown cow 
[/INDENT]

---

### Post by Bashing-om on 2013-04-01
et all ;

Hold my last post in our back pocket, I was preparing my post while the ups were taking place. By all means try the correct boot parameters before the file edit procedure.
[INDENT=2]
watching and waiting

[/INDENT]

---

### Post by Mecharius on 2013-04-01
So I can regularly get into the desktop now. Goes to the login screen then directly to the desktop once i type in my password. But the issue is that I had to go into edit in the grub and remove quiet splash and replace it with nomodeset and acpi=off. I still need to figure out how to makes these changes lasting. I can get to the actual command line. 

@Bashing-om

I am going to hold onto you previous post, but as long as I am understanding everything correctly I am currently at a point where I have moved beyond needing that.

---

### Post by Mecharius on 2013-04-01
```
printf "blacklist sp5100_tco" | sudo tee /etc/modprobe.d/blacklist-sp5100.conf
```

From the first reply I had received. Is this what I need to do?

---

### Post by Bashing-om on 2013-04-01
Mecharius;
Yeah, you are now beyond that need to edit from the liveCD.. good !

But, let's not get to hasty with making those boot parameters permanent as they have adverse affects.
Try this, before proceeding further.
See if any other drivers are offered in the 'Additional Drivers" utility ( all software repositories are enabled ?) and install one of them. See then if you are able to boot.

else we look at the display/card info and consult the knowledge bases for guidance. 
[INDENT=3]
that just my opinion

[/INDENT]

---

### Post by r.stiltskin on 2013-04-01
I'm glad you're making progress.  I think the first thing you should address next is the amd64 microcode matter.  First of all run (in a terminal window)
```
lscpu
```so we can find out what kind of cpu you have.  Then run
```
lsmod | grep amd
```to see if the amd64-ucode module has been installed.  If not, we need to try & find out if it is actually appropriate for your specific CPU.

Maybe resolving that will also take care of the sp5100 problem.  If not, you can create that blacklist file.

And after that, you can experiment with the boot parameters.  Maybe these fixes will eliminate the need to turn of acpi and modeset.

---

### Post by Mecharius on 2013-04-01
Bashing-om
You post about editing the cd, it has now been printed and posted on my wall. I feel as if something that well typed out should be kept. One day, I may need it as my collection of machines increases.

I don't want to be the spoiled kid who is handed everything he wants but, this "additional drivers" utility you speak of is unknown to me.

---

### Post by Mecharius on 2013-04-01
@r.stiltskin
The first symbol in the code you posted here is unknown to me. How do I produce that?

---

### Post by Mecharius on 2013-04-01
Typed in scpu and was given a "did you mean this, this or this" collection of options. Used the mouse to copy and paste the one that was requested. entered that. What of this information is needed? why not, i'll post it all.

Architecture: i868
CPU op-mode: 32-bit, 64-bit
Byte Order: Little Endian
CPU(s):1
On-Line CPU(s) list: 0
Thread(s) per core: 1
Core(s) per socket: 1
Socket(s): 1
CPU Family: AuthenticAMD
Model: 16
Stepping: 6
CPU MHz: 2
BogoMIPS: 2194.552
Virtualization: AMD-v
Lid Cache: 64k
L2 cache: 512k

---

### Post by Bashing-om on 2013-04-01
Mecharius;
Let us do one thing at a time,and try not to scatter this thread too much. I agree with r.stiltskin's approach and maybe fix the module conflict that way. It is always good to know what one is working with. 
We are making progress. Will return to "Additional Drivers" when it is time.[INDENT=3]
just try'n to help


[/INDENT]

---

### Post by Mecharius on 2013-04-01
So is the information I provided sufficient? Currently I am at the mercy of those who know more then I, so I shall go along and gain as much knowledge of this system as I can. I still would like to know how to properly produce the symbol that r.stiltskin had shown at the beginning of the scpu line

---

### Post by Bashing-om on 2013-04-01
Mecharius;
Are you in reference to post #44 ?? if so the first character in lscpu is a lower case "L"// else specifics for location.
[INDENT=3]
I be watching

[/INDENT]

---

### Post by Mecharius on 2013-04-01
Yes, that was it! It looked odd, so I wanted to be certain. Much appreciation.

---

### Post by r.stiltskin on 2013-04-01
> **Mecharius said:**
> @r.stiltskin
The first symbol in the code you posted here is unknown to me. How do I produce that?

Yes, lowercase L.

So, I tried to figure out exactly which cpu you have from the "lscpu" output but I haven't found anything that corresponds to "model 16, stepping 6" etc.  But judging by  the error messages you were getting yesterday you probably should have that amd64-microcode package.

If it doesn't show up among the output of "lsmod | grep amd", I think you should try to install it by
```
sudo apt-get install amd64-microcode
```

---

### Post by Mecharius on 2013-04-01
this gave me:

E:  Unable to locate package amd64-microcode

I was running under the assumption that this is something which has to be pulled from the internet, but felt i should try anyway. Unfortunately I can only have one machine connected to the internet at a time, and it takes a half hour or so to register that the machine has logged off. so it may be a bit before I can test this next part.

---

### Post by Mecharius on 2013-04-01
Still having the same result. Currently posting from my phone so I can allow my Linux machine internet access. I will dig around the internet see if I can find a download link somewhere.

---

### Post by Mecharius on 2013-04-01
[https://launchpad.net/ubuntu/+source/amd64-microcode/1.20120910-1](https://launchpad.net/ubuntu/+source/amd64-microcode/1.20120910-1)

Is this what I should be looking for?

---

### Post by r.stiltskin on 2013-04-01
Yes.  I believe it's in the multiverse section of the repository.   In the Ubuntu Software Center's edit menu select software sources and then check  "software restricted by copyright or legal issues".  Then click reload.  After that you should be able to install the amd64-microcode package if it's included on the installation CD.  If not, you'll have to get your internet connection working so you'll be able to get it online.

---

### Post by Mecharius on 2013-04-01
I have the internet up on my toshiba currently. i can get online with linux. The CD did nothing for me. On the page that I posted a link for there are multiple download possibilities. Which one do I want? What am i looking for exactly here? Hopefully in the future, after I learn this, I will need less assistance.

---

### Post by oldfred on 2013-04-01
Years ago before I had router, I also had the 20 to 30 minute wait between computers being recognized. I was frustrated as I knew I was an authorized user and it took me a while but I found I could spoof my HWaddr. I believe my current router is still using the hw setting from a computer long since retired.
But now you can get an inexpensive router and easily share multiple computers and one Interent. It also makes it a lot easier to move data from one to another.

---

### Post by Mecharius on 2013-04-02
The wifi is distributed throughout the building. It is not specific to me. Unfortunately I have no access to hardwired internet or to the machines which provide the wireless. So I am limited to one account which means one machine at a time.

---

### Post by r.stiltskin on 2013-04-02
????????

Oh, I get it.  Somehow it seems like oldfred's comment in #58 is the answer to your #59.  His point is that  you can get a wireless router for a few bucks, have the router sign into your wifi account thus creating your own little subnet, and then you can connect your several computers to the router's subnet (either wirelessly or wired).  But that's a project for another day.

I don't want you to download anything directly from the link you posted.  Instead, I want you to stop using the installation CD altogether and start updating your machine directly from the internet using the Ubuntu Software Center, or Synaptic (which I personally prefer), or just using apt directly on the command line.  Over the next few hours or days you should try all 3 & see which you like.  (Just so you'll know, Software Center and Synaptic are both just graphic front-ends to apt, and apt is a command line front-end to the Debian dpkg package management system.)

For the moment ...
since your machine wasn't connected to the internet when you installed, the installer probably didn't configure them to use an online repository.  Here's a [tutorial]("https://help.ubuntu.com/community/Repositories/Ubuntu") that should help you get that set up. At this point you should designate a download server, select the various repositories you want to use, deselect the installation CD, and then "Update", which will download an up to date listing of all programs that are available for your Linux distribution.  After that, you will be able to install the amd64-microcode package just by selecting from the Software Center's menu, or by running the apt command described earlier.

You will also find that your Update Manager (another apt front-end) will notify you that updates are available for many (probably 100s) of the packages you have installed.  You should install those updates at this point.  It might even turn out that some of your installation problems were automatically fixed by these updates.

---

### Post by Bashing-om on 2013-04-02
et all: In regards to the sp5100_tco conflict:

As advised from the original launchpad bug link, the bug appears to be fixed in later kernels. The latest kernel will be installed (automagically) when you get on-line and do the updates and will resolve many of the present problems.
As a reminder, always use the repositories/package manager first for any situation in regards to any package, Then if problems still exist look for alternatives,[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by Mecharius on 2013-04-02
I used the software updater. Unfortunately I still need to add in nomodeset and acpi=off to get into my desktop. Machine does seem to be running faster now. So, at least some improvement. I was hoping that would fix the issue for me.
One small step and all that.

---

### Post by Bashing-om on 2013-04-02
Mecharius;

looking better alla the time !
Let me offer this for your careful consideration while we wait for r.stiltskin's continued input:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If at all possible we need better alternatives to the current boot parameters.[INDENT=2]
look'n for ways to help

[/INDENT]

---

### Post by Mecharius on 2013-04-02
> **Bashing-om said:**
> Mecharius;

looking better alla the time !
Let me offer this for your careful consideration while we wait for r.stiltskin's continued input:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If at all possible we need better alternatives to the current boot parameters.[INDENT=2]
look'n for ways to help

[/INDENT]


The link you posted inspired me to try switching in the grub edit acpi=off with acpi_osi. But unfortunately It took me back to receiving the sp5100_tco.

---

### Post by r.stiltskin on 2013-04-03
Do you now have the amd64-microcode package installed and loaded?  I think you can check this by examining the output of
```
dmesg | grep microcode
```

Have you tried blacklisting sp5100_tco (post #2)?

---

### Post by r.stiltskin on 2013-04-03
By the way, what output do you get from
```
dmesg | grep AMD
```

---

### Post by Mecharius on 2013-04-03
I had become so concerned with waiting for the next reply I had forgotten to go back over what had already been given to me. I will post up the results after work.

---

### Post by Mecharius on 2013-04-03
So I put in the blacklist and restarted my machine. started up ubuntu without making edits in the grub, and I still got the sp5100. I am going to try again just in cased I some how messed something up, but i am certain I put it is as it was supposed to be.

---

### Post by Mecharius on 2013-04-03
Is this something which should be done as a superuser? I still have the $ and not the # in terminal.

---

### Post by Bashing-om on 2013-04-03
Mecharius;

Surprised that the conflict still exist....Think it is now time to look at the system logs and see what errors are reported.
```
 dmesg | less
```
dmesg is a huge file so we run it through the utility "less" in order to page through it - q to guit-.
```
 man dmesg
man less
``` Like I say dmesg is a huge file, look through it and post any portions of it that is questionable, for us to look at.[INDENT=3]
now we be look'n !
[/INDENT]

---

### Post by Bashing-om on 2013-04-03
Mecharius;
> Is this something which should be done as a superuser? I still have the $ and not the # in terminal.
 Any system file edited that is not in your home directory requires elevated privileges,
In the file manager take a look at the file and see if the changes stuck.
(this is a case where from your normal user login, the term "sudo" elevates you to temporary administrative authority).
Please exercise with care, caution, knowledge and awareness !
for starters) yeah lot's of reading - you are getting the crash course!))
```
man sudo 
```[INDENT=2]
I do hope this helps

[/INDENT]

---

### Post by r.stiltskin on 2013-04-03
You should have a file /etc/modprobe.d/blacklist-sp5100.conf containing a single line:
blacklist sp5100_tco

Do you?
Be sure that the filename contains a hyphen - and the module name (sp5100_tco) in the file has an underscore_

The cat command prints the contents of a file (if it exists), so an easy way to check is to run:
```
cat /etc/modprobe.d/blacklist-sp5100.conf
```

The grep command looks for a specific pattern in a block of text, and lsmod lists all the kernel modules that have been loaded, and the pipe character | directs the output of one command to the input of another, so you can check for any module containing sp5100 in its name by running
```
lsmod | grep sp5100
```

Similarly, the command
```
dmesg | grep AMD
```should tell us the name of your CPU (from which I hope we can determine whether the amd64-microcode is applicable), and ```
lsmod | grep amd64
```will tell us if amd64-microcode has been loaded.

---

### Post by Mecharius on 2013-04-03
Before I continue on, I want to check for user error. The vertical line, as seen here:

lsmod | grep amd64

what is its meaning? I would like to be able to blame at least some of this on the user. Production method and all that for it?

---

### Post by oldfred on 2013-04-03
A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources - cortman
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

then if you go to this 
More Linux commands:
[http://doors.stanford.edu/~sr/computing/more-unix.html](http://doors.stanford.edu/~sr/computing/more-unix.html)

>  **|** (**piping**) --- Lets you execute any number of commands in a sequence.  
 The second command will be executed once the first is done, and so forth, using the previous command's output as input. You can achieve the same effect by putting the output in a file and giving the filename as an argument to the second command, but that would be much more complicated, and you'd have to remember to remove all the junkfiles afterwards. Some examples that show the usefulness of this: 
**ls | more** --- will show you one screenful at a time, which is useful with any command that will produce a lot of output, e.g. also **ps -aux** 


---

### Post by Mecharius on 2013-04-04
I had misunderstood the purpose for piping, and now I know the name I can expand upon my knowledge base. much appreciation.

---

### Post by Mecharius on 2013-04-04
> **r.stiltskin said:**
> By the way, what output do you get from
```
dmesg | grep AMD
```

[      0.000000]   AMD AuthenticAMD
[      0.000000] RAMDISK: [mem0x3631c000-0x37185fff]
[      0.001008] using AMD E400 aware idle routine
[      0.234226] Performance Events: AMD PMU driver.
[      0.241196] System has AMD C1E enabled
[      0.266519] perf: AMD IBS detected (0x0000001f)
[      1.028341] powernow-k8: Found 1 AMD Turion(tm) II Dual-Core Mobile M500 (1 cpu cores) (version 2.20.00)

---

### Post by Mecharius on 2013-04-04
> **r.stiltskin said:**
> You should have a file /etc/modprobe.d/blacklist-sp5100.conf containing a single line:
blacklist sp5100_tco

Do you?
Be sure that the filename contains a hyphen - and the module name (sp5100_tco) in the file has an underscore_

The cat command prints the contents of a file (if it exists), so an easy way to check is to run:
```
cat /etc/modprobe.d/blacklist-sp5100.conf
```

The grep command looks for a specific pattern in a block of text, and lsmod lists all the kernel modules that have been loaded, and the pipe character | directs the output of one command to the input of another, so you can check for any module containing sp5100 in its name by running
```
lsmod | grep sp5100
```

Similarly, the command
```
dmesg | grep AMD
```should tell us the name of your CPU (from which I hope we can determine whether the amd64-microcode is applicable), and ```
lsmod | grep amd64
```will tell us if amd64-microcode has been loaded.

The cat command gave me:

blacklist sp5100_tcogeist@geist-Satellite-L505D:~$

geist is my username. The lsmod gave me:

sp5100_tco                           13418   0

---

### Post by Mecharius on 2013-04-04
@r.stiltskin:

> **Mecharius said:**
> Before I continue on, I want to check for user error. The vertical line, as seen here:

lsmod | grep amd64

what is its meaning? I would like to be able to blame at least some of this on the user. Production method and all that for it?

I Do not know why I posted this up almost immediately after you told me what it is. Not sure of my own logic behind that one. I hope that in no way this caused offense.

---

### Post by Mecharius on 2013-04-04
```
lsmod | grep amd
```
A few pages back I was asked to type this in and post the results. This is what it gave me.

kvm_amd                    54395    0
kvm                           357807   1 kvm_amd

---

### Post by Mecharius on 2013-04-04
> **r.stiltskin said:**
> There are bug reports involving the sp5100 module (for example [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1055096](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1055096)), and some people reported that blacklisting that module solved their problems.

Get to a terminal window: try ctrl+alt+F2 from your black screen & see if that gets you to a command line prompt.  If so, login there. If that doesn't work reboot and select recovery mode from the grub menu and then choose "drop to root shell".

Run this command:
```
printf "blacklist sp5100_tco" | sudo tee /etc/modprobe.d/blacklist-sp5100.conf
```
(In a root shell you can omit the word sudo.)

That will create a file /etc/modprobe.d/blacklist-sp5100.conf containing the line **blacklist sp5100_tco** which should prevent the sp5100 module from loading.  Reboot & see if that helps.  If not, you can easily delete that file.

Since, apparently, blacklisting is not working, then should I just delete it?

---

### Post by Bashing-om on 2013-04-05
Mecharius;
Still hang'n with you.
Double check this:> cat /etc/modprobe.d/blacklist-sp5100.conf does indeed result in this:
> The cat command gave me:

blacklist sp5100_tcogeist@geist-Satellite-L505D:~$

as the config line should only be "blacklist sp5100_tco".[INDENT=3]
just check'n on where things stand

[/INDENT]

---

### Post by Mecharius on 2013-04-06
```
bash: cat/etc/modprobe.d/blacklist-sp5100.conf: No such file or directory
```
This is what I received.

---

### Post by Bashing-om on 2013-04-06
Mecharius;
Apparently the file creation did not happen to blacklist that module.
- This is ubuntu - for every user there is a different way of doing things. In this instance what I would do:
As a mechanism already exist for the purpose of not loading a particular module; I would use it -> /etc/modprobe.d/blacklist.conf ::
```
sudo cp /etc/modprobe.d/blacklist.conf  /etc/modprobe.d/blacklist.conf-old #just to be safe
sudo gksudo gedit /etc/modprobe.d/blacklist.conf
```
((all prior admonishments in respect to elevated privileges apply !!)
In the file editor, arrow down the existing last line and arrow across to the end ->do a return to begin on the next as a new line;
type # (each line) -> who, what when where and why making this change in the file -> new line;
insert the text "blacklist sp5100_tco" - with out the quotes -> return
enter a final # and return to indicate that final line in the config does indeed contain a new line character.
save the file and exit back to the desktop. Close all out.
Reboot. and see what results, see what might have to be done now to get a operable stable operating system.[INDENT=2]
just my opinion

[/INDENT]

---

### Post by Zill on 2013-04-06
> **Mecharius said:**
> ```
bash: cat/etc/modprobe.d/blacklist-sp5100.conf: No such file or directory
```
This is what I received.
You have been requested to show the output of "cat /etc/modprobe.d/blacklist-sp5100.conf" where "cat" is the command and "/etc/modprobe.d/blacklist-sp5100.conf" is the file path.

You seem to have entered "cat/etc/modprobe.d/blacklist-sp5100.conf" which is not the same thing - a space *must* exist between a command and a path.

To avoid errors I suggest you copy and paste code into the terminal, rather than trying to type it out. ;-)

Please try "cat /etc/modprobe.d/blacklist-sp5100.conf" again and post the output so that we can see the contents of this file.  Hopefully this will be the single line "blacklist sp5100_tco".

---

### Post by Mecharius on 2013-04-09
> **Zill said:**
> You have been requested to show the output of "cat /etc/modprobe.d/blacklist-sp5100.conf" where "cat" is the command and "/etc/modprobe.d/blacklist-sp5100.conf" is the file path.

You seem to have entered "cat/etc/modprobe.d/blacklist-sp5100.conf" which is not the same thing - a space *must* exist between a command and a path.

To avoid errors I suggest you copy and paste code into the terminal, rather than trying to type it out. ;-)

Please try "cat /etc/modprobe.d/blacklist-sp5100.conf" again and post the output so that we can see the contents of this file.  Hopefully this will be the single line "blacklist sp5100_tco".

Unfortunately copy&paste is not always an option for me. The wireless reception is less for my linux machine then it is for my windows machine. 

You are correct, I missed the space there. 

```
blacklist [EMAIL="sp5100_tcogeist@geist-Satellite-L505D:~$"]sp5100_tcogeist@geist-Satellite-L505D:~$[/EMAIL]
```
This is the response I continue to be given when I enter this.

---

### Post by Bashing-om on 2013-04-09
Mecharius;
IF that output > blacklist sp5100_tcogeist@geist-Satellite-L505D:~$
is what is contained in that file .......... it is a incorrect entry in that file.
That entry should read blacklist sp5100_tco

By the way, I thought we had lost you; Pleased to hear from you.[INDENT=2]
just ry'n to help

[/INDENT]

---

### Post by Mecharius on 2013-04-09
My employer keeps me away from my machines for what can sometimes extend up to a month. I will never be lost to this. The seeds of obsession have already gone to root and all that. SO would this have been an issue with the attempt to blacklist or with the cat command? And in post #83 you said file editor or you meaning in the edit function of the grub? Or again, is there something here I am missing?

I feel the need to express my gratitude towards any patience and time given to me. This is easily the most involved use of one of my machines I have had and I do believe that it is apparent that my skills as a computer user are only now, through this project, beginning to grow beyond a basic level user.

---

### Post by Mecharius on 2013-04-09
> **Bashing-om said:**
> Mecharius;
IF that output 
is what is contained in that file .......... it is a incorrect entry in that file.
That entry should read blacklist sp5100_tco

By the way, I thought we had lost you; Pleased to hear from you.[INDENT=2]
just ry'n to help

[/INDENT]


That is also what I get from putting in:

```
printf "blacklist sp5100_tco" | sudo tee /etc/modprobe.d/blacklist-sp5100.conf
```

as suggested in post #2

---

### Post by r.stiltskin on 2013-04-10
Sorry, it seems I somehow missed the activity in this thread for the past few days.

So, we have learned that your cpu is an AMD Turion(tm) II Dual-Core Mobile M500 which is in the K10 family of AMD processors.  (I don't understand why your dmesg output says it has "1 cpu cores" immediately after naming it as a Dual-Core processor.)  Anyhow, being a K10 means that the amd64-microcode package should be installed and loaded, so you should try to install that.

Have you configured your machine to update itself over the internet?  If not, here's that [tutorial]("https://help.ubuntu.com/community/Repositories/Ubuntu") link again.  Once that's done you should apply ALL available updates -- the Ubuntu update manager should do that for you painlessly.

Then, check in your Software Center to see if amd64-microcode has been installed, and if not, install it.

So much for that.

Now back to the sp5100_tco module.  This output
```
blacklist sp5100_tcogeist@geist-Satellite-L505D:~$ 
```
is fine.  It just indicates that there is no newline character at the end of the blacklist-sp5100.conf file.  So the output of the cat command is followed immediately by your shell prompt, on the same line.  That should not prevent the blacklisting from working.  I've tried using single blacklist entries like that, with no blank line at the end of the file, and they work.  So I don't know why the sp5100_tco module is still being loaded.  Apparently something else in your system is overriding the blacklist.  I think there is another way to deal with that, but before worrying about it any further I'd like to be sure we still need to.  So yes, you can delete that file:
```
sudo rm /etc/modprobe.d/blacklist-sp5100.conf
```
And then post back to confirm that you have updated EVERYTHING and (hopefully) resolved the amd64-microcode matter, and let us know whether you are still getting errors regarding the sp5100_tco when you reboot.  Hopefully, updating may magically get rid of that problem too.

You will be able to check that by running
```
dmesg | grep "sp5100_tco"
```

---

### Post by Bashing-om on 2013-04-10
Mecharius;

Uhhh... If the code given by r.stiltskin was successful, then there is no need to do the file edit as per my post #83. Both do the same thing; to add a module to the blacklist file. And Yeah we were going to use the tett editor after copying the file as a backup (the command, cp)

At the present time we need to know if that module is blacklisted. So let's look. In order to just look at a file we will use the command "cat" for contatenate (sp??)  and give it a path to that file (blacklist.conf) who's path (location) is "/" for root, in the top directory "etc" in a subdirectory "modprobe.d"... So that becomes this command:
```
cat /etc/modprobe.d/blacklist.conf
``` a space between the command "cat" and what "cat" is going to act on.
the last line in that file should be --   blacklist sp5100_tco .

Is that so, or do we still have to make that happen ?

[INDENT]it is all a learning experience[/INDENT]

woops  r.stiltskin was faster with his post than I was// We will follow that guidance and if needed return to editing that file .
Bt the way, his explanation on the output is nice to realize //

---

### Post by Bashing-om on 2013-04-10
Guys, it is late here (GMT-6) and I am tired and not thinking to clearly.
I will pick this back up at a later time.
[INDENT=3]
take care

[/INDENT]

---

### Post by Bashing-om on 2013-04-10
Guys;
In regards to the number of processors, let's keep "dmidecode" in our back pocket and look at it when some of these other snakes are stomped out.[INDENT=3]one stepper ;till journey's end

[/INDENT]

---

### Post by Mecharius on 2013-04-11
It is currently looking as if my employer is going to keep me completley occupied until the weekend. Please do not think that I am for whatever reason trying to avoid this or loosing my interest or patience in it. The employment is demanding more of my time, and considering it is what provides food, electricity and internet for me, I must give into its demands.

---

### Post by Mecharius on 2013-04-14
> **r.stiltskin said:**
> Sorry, it seems I somehow missed the activity in this thread for the past few days.

So, we have learned that your cpu is an AMD Turion(tm) II Dual-Core Mobile M500 which is in the K10 family of AMD processors.  (I don't understand why your dmesg output says it has "1 cpu cores" immediately after naming it as a Dual-Core processor.)  Anyhow, being a K10 means that the amd64-microcode package should be installed and loaded, so you should try to install that.

Have you configured your machine to update itself over the internet?  If not, here's that [tutorial]("https://help.ubuntu.com/community/Repositories/Ubuntu") link again.  Once that's done you should apply ALL available updates -- the Ubuntu update manager should do that for you painlessly.

Then, check in your Software Center to see if amd64-microcode has been installed, and if not, install it.

So much for that.

Now back to the sp5100_tco module.  This output
```
blacklist sp5100_tcogeist@geist-Satellite-L505D:~$ 
```
is fine.  It just indicates that there is no newline character at the end of the blacklist-sp5100.conf file.  So the output of the cat command is followed immediately by your shell prompt, on the same line.  That should not prevent the blacklisting from working.  I've tried using single blacklist entries like that, with no blank line at the end of the file, and they work.  So I don't know why the sp5100_tco module is still being loaded.  Apparently something else in your system is overriding the blacklist.  I think there is another way to deal with that, but before worrying about it any further I'd like to be sure we still need to.  So yes, you can delete that file:
```
sudo rm /etc/modprobe.d/blacklist-sp5100.conf
```
And then post back to confirm that you have updated EVERYTHING and (hopefully) resolved the amd64-microcode matter, and let us know whether you are still getting errors regarding the sp5100_tco when you reboot.  Hopefully, updating may magically get rid of that problem too.

You will be able to check that by running
```
dmesg | grep "sp5100_tco"
```

```
sudo rm /etc/modprobe.d/blacklist-sp5100.conf
```
Just gave me my prompt.so I checked the dmesg you gave.
```

[   13.853133] sp5100_tco: SP5100 TCO WatchDog Timer Driver v0.01
[   13.853286] sp5100_tco: Watchdog reboot not detected
[   13.853348] sp5100_tco: initialized (0xf84100f0). heartbeat=60 sec (nowayout=0)

```

---

### Post by r.stiltskin on 2013-04-14
The command *sudo rm /etc/modprobe.d/blacklist-sp5100.conf* just deleted the blacklist-sp5100.conf file, so it shouldn't give any output as long as no error occurred.  We already suspected that the blacklist wasn't working anyway, and the output you got from  *dmesg | grep "sp5100_tco"* confirms that.

But before worrying about what else can be done to prevent that module from loading, you still seem to be avoiding answering my questions about whether you have yet gotten apt, or Software Center, or Synaptic, connecting online to the Ubuntu repositories, and updated all of your packages.  Until you've done that, everything else may be a waste of time.

When you install from a cd or usb image, and especially a cd that came with a book, you are getting many packages that have been updated between the time the image was created and the time you installed it.  Probably hundreds of fixes have been applied to various packages that you have installed, so whenever you install any Linux distribution the first thing you should do is update everything.

---

### Post by Mecharius on 2013-04-14
And I checked the software, up to date. Set up for automatic updates.

---

### Post by Mecharius on 2013-04-14
Did not mean to post that already. about to check up on the AMD to makesure that information is complete and accurate.

---

### Post by Mecharius on 2013-04-14
For whatever reason my machine seems to be slowing down. After This sp5100 and AMD issue is resolved that shall become my major concern.

---

### Post by r.stiltskin on 2013-04-14
Please remind us: exactly what is your status now?  Are you still unable to boot normally (without editing the boot menu)?

Or, if you still need to edit the boot menu, what modifications are you making?

Are you still getting error messages during bootup?  (Check in the output of dmesg.)

---

### Post by Mecharius on 2013-04-14
update:
sp5100 error is no longer showing up. I now do not need to edit and add nomodeset to boot up. But I do still need acpi=off. I tried the:
```
apt-get update && apt-get install amd64-microcode
```
 as seen on page 3, but my machie ends up asking me if I am logged in as root. So I believe that I need to find how to log in as root to update that. I do not know if it was the new updates or if it is the lack of nomodeset but my machine is running at a much faster rate. It is up to the level I believe that it should be, except when dealing with the internet. And that issue I believe can be blamed on the wireless services of my building, and not the machine.

---

### Post by oldfred on 2013-04-14
sudo

I still type commands in and it gives the raspberries. So I hit up arrow, home and add sudo to the front of the command.

       [http://xkcd.com/149/](http://xkcd.com/149/)


But sudo still does not ever get me a sandwich. Its always make it yourself. :)

---

### Post by Mecharius on 2013-04-14
I used sudo -i to get in as root and then ran 
```
apt-get update && apt-get install amd64-microcode
```
It looked like it was all running properly but then it froze up after hitting 100% leaving me with
```
Using per-core interface to update on online processors
```
apparently this was the wrong thing to do. Let it sit like that for 10 or 15 min but the cursor was not even blinking. Just frozen. So resorted to the power button to shut off the machine. Now when I start up Ubuntu in the GRUB, even using both nomodeset and acpi=off it freezes up on the black screen with the scrolling information (does this screen have a proper name?). Using both nomodeset and acpi=off the last piece of information it brings up is:

[      14.952590] Adding 2877436k swap on /dev/sda5.  Priority:-1 extents:1 across:2877436k

---

### Post by Mecharius on 2013-04-14
> **oldfred said:**
> sudo

I still type commands in and it gives the raspberries. So I hit up arrow, home and add sudo to the front of the command.

       [http://xkcd.com/149/](http://xkcd.com/149/)


But sudo still does not ever get me a sandwich. Its always make it yourself. :)

Now that is awesome

---

### Post by Bashing-om on 2013-04-14
Mecharius;

I see this, but, I know nothing !

Hopefully others can advise.[INDENT]
what an experience

[/INDENT]

---

### Post by Mecharius on 2013-04-14
With what I have learned upto this point my google-fu has greatly increased. Hopefully between Google, my books, and the extremly helpful users on this forum, it won't take too much longer for a solution to be found. I shall search as I hope and wait for more help.

---

### Post by r.stiltskin on 2013-04-15
Awesome.  I suppose that shouldn't be too much of a surprise when dealing with an AMD Turion(tm) II "Dual-Core Mobile M500" with "1 cpu cores".  :p

Can you boot into (advanced options) recovery mode and get to a root shell?  If so, you can uninstall the amd-microcode package.

In a root shell there's no need for sudo:
```

apt-get remove amd64-microcode
```

---

### Post by r.stiltskin on 2013-04-15
I found some other threads relating to various Toshiba notebooks including Satellite L-505-D in which people reported success booting with the grub option **acpi=copy_dsdt** instead of acpi=off.  If you can get over the microcode hurdle (sorry about that), this acpi option is probably worth trying.  Better not to turn power management completely off if you can avoid it.

---

### Post by Mecharius on 2013-04-15
Under advanced options there are now three recovery modes and three Ubuntus to go with them. 
Ubuntu, with Linux 3.5.0-27-generic
3.5.0-26-generic
3.5.0-17-generic

---

### Post by Mecharius on 2013-04-15
Trying with the 3.5.0-27-generic (recovery mode):
freezes up on:
[       7.176949] toshiba_acpi:  Toshiba Laptop ACPI Extras version 0.19

Freezes is ot the proper word. At least the cursor icon (does this have another name?) is still flashing. Try ctrl+alt+f1, but that did nothing for me. samething with ctrl+alt+f2 through f6

---

### Post by r.stiltskin on 2013-04-15
> **Mecharius said:**
> Trying with the 3.5.0-27-generic (recovery mode):
freezes up on:
[       7.176949] toshiba_acpi:  Toshiba Laptop ACPI Extras version 0.19

Freezes is ot the proper word. At least the cursor icon (does this have another name?) is still flashing. Try ctrl+alt+f1, but that did nothing for me. samething with ctrl+alt+f2 through f6

Was that while attempting to boot with **acpi=off** or **acpi=copy_dsdt** or neither?

---

### Post by Mecharius on 2013-04-15
That was with neither, about to try with acpi=copy_dsdt and see if that works. Then i shall try with acpi=off if it did not. Will post back up with how this turns out.

---

### Post by goldshirt9 on 2013-04-15
> **oldfred said:**
> You probably do not have nVidia, but nomodeset sometimes works for other video issues. But it sounds like you may need other boot options.

 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
Try the post from oldfed, I had tried to install on a old Toshiba and had similar troubles.
The above solved my problem

---

### Post by Mecharius on 2013-04-15
acpi=copy_dsdt changed nothing. So I tried with acpi=off. This is what the last line was when it stopped:
[      7.231703] microcode: Microcode Update Driver: v2.00 [EMAIL="tigran@aivazian.fsnet.co.uk"]tigran@aivazian.fsnet.co.uk[/EMAIL], Peter Oruba

---

### Post by Mecharius on 2013-04-15
> **goldshirt9 said:**
> Try the post from oldfed, I had tried to install on a old Toshiba and had similar troubles.
The above solved my problem

I was past the need for nomodeset, but then i managed to mess something up when I was in as root. Already tried going back to using that but it did nothing for me now.

---

### Post by r.stiltskin on 2013-04-15
> **Mecharius said:**
> acpi=copy_dsdt changed nothing. So I tried with acpi=off. This is what the last line was when it stopped:
[      7.231703] microcode: Microcode Update Driver: v2.00 [EMAIL="tigran@aivazian.fsnet.co.uk"]tigran@aivazian.fsnet.co.uk[/EMAIL], Peter Oruba

This is while trying to boot recovery mode?

Have you tried either of the older recovery mode options (3.5.0-26-generic or 3.5.0-17-generic )?

---

### Post by Mecharius on 2013-04-15
Yes, recovery mode. Will try the older two next.

---

### Post by r.stiltskin on 2013-04-15
If you can boot with either of the older kernel images (possibly with acpi=off) post back with details before making any changes.

---

### Post by Mecharius on 2013-04-15
the 3.5.0-26-generic gave me the same. acpi=off did not make a difference.

---

### Post by Mecharius on 2013-04-15
And the same for the 17. I am beginning to think I may need to go back to the disk and start over. Whatever I damaged by accident must have been important.

---

### Post by Mecharius on 2013-04-16
I am back to the point where the only way I can get to a desktop is by using the "try Ubuntu" on the disk. But at least that works. I was partialy afraid that not even the disk would get me back to graphical.

---

### Post by r.stiltskin on 2013-04-16
Do you know on which hard disk partition you installed Ubuntu?  I recall that something you posted showed swap on sda5 (I'm wondering why) but I don't think you posted anything about the location of /.  You'll have to determine that before going any further.  I don't have a Ubuntu live cd handy so I don't know if you can immediately see that (in Nautllus for example).  If not, you can run fdisk.  In a terminal window:
```

sudo su
fdisk /dev/sda
```
and then in response to fdisk's prompt, just press **p** <enter> and you should be able to see which /dev your Ubuntu is installed on.  Then press **q** <enter> to quit fdisk.

Then, still in the same terminal (ASSUMING that Ubuntu is on sda1; otherwise change this accordingly)
```

TARGET=/media/sda1
mkdir -p $TARGET
mount /dev/sda1 $TARGET
mount --bind /dev     $TARGET/dev
mount --bind /proc    $TARGET/proc
mount --bind /sys     $TARGET/sys
chroot $TARGET /bin/bash

```
(I hope I got all of that right.)
Don't close the terminal.
If all went well you should now be in *your* Ubuntu.  Try to verify that by listing the files, e.g., ls /home/[your username], or ls /boot, and look at the filenames, dates, etc., to verify that you're looking at your Ubuntu and not the live cd.

Now you can try to uninstall that amd64-microcode:
```

apt-get remove amd64-microcode

```
Then exit the chroot:
```

exit
umount  $TARGET/dev
umount  $TARGET/proc
umount  $TARGET/sys
umount $TARGET
reboot

```
Remove the cd and hopefully you'll be able to reboot without it.

---

### Post by Mecharius on 2013-04-20
The fdisk listed it as being in /dev/sda1

Now the second set of code you gave me I ran, and it gave me:
```
chroot: cannot change root directory to /media/sda1: No such file or directory
```
I am going to go back over it to be sure but I am certain that I had put everything in proper.

---

### Post by Mecharius on 2013-04-20
I am not seeing any issues in what I put into terminal in comparison to what you gave me. So maybe I am doing something wrong? 

```
TARGET=/media/sda1
mkdir -p $TARGET
mount /dev/sda1 $TARGET
mount --bind /dev     $TARGET/dev
mount --bind /proc    $TARGET/proc
mount --bind /sys     $TARGET/sys
chroot $TARGET /bin/bash
```
I typed that all out in text editor then copy pasted it into terminal and hit enter. Should I be doing each line individualy?

---

### Post by sudodus on 2013-04-20
> **Mecharius said:**
> I am not seeing any issues in what I put into terminal in comparison to what you gave me. So maybe I am doing something wrong? 

```
TARGET=/media/sda1
mkdir -p $TARGET
mount /dev/sda1 $TARGET
mount --bind /dev     $TARGET/dev
mount --bind /proc    $TARGET/proc
mount --bind /sys     $TARGET/sys
chroot $TARGET /bin/bash
```
I typed that all out in text editor then copy pasted it into terminal and hit enter. Should I be doing each line individualy?

It is possible to do like you did, but I suggest that you create a file with that content (write it to a file with a suitable name **[FONT=courier new]filename[/FONT]**) and those commands will be saved in a shell-script file.

Then run the file with the following command ```
bash filename
```

---

### Post by Mecharius on 2013-04-20
I shall try that now.

---

### Post by r.stiltskin on 2013-04-21
I did expect you to run each command (line) individually.  That way you would be sure to see any error messages that might appear.  But if you copied everything correctly I see no reason why copy/pasting all the lines shouldn't work.  sudodus' method should work as well.

I suspect that you overlooked the part of post #121 that says "Then, [COLOR="#FF0000"]still in the same terminal[/COLOR] ..."  If you are not the superuser, you will fail at mkdir -p $TARGET because an ordinary user lacks write permission to /media, and you probably didn't see that error message because of running all the commands together.

You must run
```
sudo su
```
at the beginning of the terminal session in which you want to chroot.  Then you can copy/paste each line individually or all together or in a file and it should work.  But if you're retyping be sure you get the spaces right.  No spaces at all in the first line.
TARGET=/media/sda1
Then:
mkdir[space] -p[space] $TARGET
mount[space] /dev/sda1[space] $TARGET
mount[space] --bind[space] /dev[space]     $TARGET/dev
mount[space] --bind[space] /proc[space]    $TARGET/proc
mount[space] --bind /sys[space]     $TARGET/sys
chroot[space] $TARGET[space] /bin/bash

Obviously, don't type "[space]".

On the three lines where I used multiple spaces to align $TARGET, that was just for esthetics.  A single space for each of them would be fine.

---

### Post by Mecharius on 2013-04-21
Yes, you are correct, some how the "still in the same terminal" managed to escape me as I moved through this. I apologize.
I decided to put them in individualy:
```
 sudo su TARGET=/media/sda1
```
this gave me:
```
Unknown id: TARGET=/media/sda1
```

---

### Post by r.stiltskin on 2013-04-21
No, that's two separate commands.  First do
sudo su

That will give you a root prompt.

Then do the other commands, one at a time.

---

### Post by Mecharius on 2013-04-21
```
sudo su
root@ubuntu:/home/ubuntu# TARGET=/media/sda1
root@ubuntu:/home/ubuntu# mkdir -p $TARGET
root@ubuntu:/home/ubuntu# mount /dev/sda1 $TARGET
root@ubuntu:/home/ubuntu# mount -bind /dev $TARGET/dev
mount: invalid option -- 'b'
Usage: mount -V                              : print version
           mount -h                              : print this help
           mount                                  : list mounted filesystems
           mount -l                               : idem, including volume labels
So far the informational part. Next the mounting.
The command is 'mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
          mount -a [-t|-o] ...                 : mount all stuff from /etc/fstab
          mount device                         : mount devices at the known place
          mount directory                      : mount known device here
          mount  -t type dev dir             : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
          mount  --bind alddir newdir
or move a subtree:
          mount  --move olddir newdir
One can change the type of mount containing the directory dir:
          mount  --make-rshared dir
          mount  --make-rslave dir
          mount  --make-rprivate dir
          mount  --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw]  [-o options]  [-p password].
For many more details, say  man 8 mount .
root@ubuntu:/home/ubuntu# mount -bind /proc $Target/proc
mount: invalid option  --  'b'
Usage:  mount -V                             : print version
           mount -h                              : print this help
           mount                                  : list mounted filesystems
           mount -l                               : idem, including volume labels
So far the informational part. Next the mounting.
The command is 'mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
          mount -a [-t|-o] ...                : mount all stuff from /etc/fstab
          mount device                        : mount device at the known place
          mount directory                     : mount known device here
          mount -t type dev dir             : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
Once can also mount an already visible directory tree elsewhere:
         mount  --bind oldirr newdir
or move a subtree:
         mount  --move olddirr newdir
One can change the type of mount containing the directory dir:
         mount  --make-rshared dir
         mount  --make-rslave dir
         mount  --make-rprivate dir
         mount  --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@ubuntu:/home/ubuntu# mount -bind/sys $TARGET/sys
mount: invalid option  --  'b'
Usage:  mount -V                              : print version
            mount -h                              : print this help
            mount                                  : list mounted filesystems
            mount -l                               : idem, including volume labels
So far the informational part. Next the mounting.
The command is 'mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
          mount -a [-t|-o] ...                 : mount all stuff from /etc/fstab
          mount device                          : mount device at the known place
          mount directory                      : mount known device here
          mount  -t type dev dir             : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
         mount  -bind olddir newdir
or move a subtree:
         mount --move oldirr newdir
One can change the type of mount containing the directory dir:
         mount  --make-shared dir
         mount  --make-slave dir
         mount  --make-private dir
         mount  --make-runbindable dir
A device can be given by name, say /dev/hda1  or  /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw]  [-o options]  [-p passwdfd].For more details, say  man 8 mount .
root@ubuntu:/home/ubuntu# chroot $TARGET  /bin/bash
root@ubuntu:/#
```

---

### Post by Mecharius on 2013-04-21
I posted that up as much to get suggestions on how to dig through as to have a copy in a place other than the terminal so I can read through it.

---

### Post by Mecharius on 2013-04-21
For some reason, some of the spacing is off in that, not sure why. But I think in this case the spacing is not important. its the wording I am concerned with.

---

### Post by r.stiltskin on 2013-04-21
Look:

> **Mecharius said:**
> ```
sudo su
TARGET=/media/sda1
mkdir -p $TARGET
mount /dev/sda1 $TARGET
mount [COLOR="#FF0000"]-bind[/COLOR] /dev $TARGET/dev

```

versus: 

> **r.stiltskin said:**
> 
```

sudo su
TARGET=/media/sda1
mkdir  -p  $TARGET
mount  /dev/sda1  $TARGET
mount  [COLOR="#FF0000"]--bind[/COLOR]  /dev  $TARGET/dev
mount  --bind /proc  $TARGET/proc
mount  --bind /sys  $TARGET/sys
chroot  $TARGET  /bin/bash

```


You would probably do better by highlighting & copying each line to the clipboard and then pasting it into the terminal.

Do you know how to do that?  Highlight (either with your mouse or by arrowing the cursor to the beginning of the subject text and then shift-rightarrow to highlight what you want.  Then ctrl-c copies it to the clipboard.  Then click where you want to place it (on the command line) and ctrl-v pastes it there.  Then press enter.  Voila!  No typos.

---

### Post by Mecharius on 2013-04-21
I am trying to force myself beyond the point of typos. My typing has made major improvements just through these past 14 pages. That, and again, i can only have one machine logged in at a time and my windows machine is far faster on the internet. So, currently no ubuntu forums on the ubuntu machine.

---

### Post by Mecharius on 2013-04-21
corrected the issue with the typo and put it back in terminal, checked it over three times to be certain. No issues. Hit enter, and it gave me the prompt again:
```
root@ubuntu:/#
```
So no change, so long as I am understanding everything correctly. Should be my name in place of ubuntu, yes?

---

### Post by Mecharius on 2013-04-21
Going to go back over your post, check to see if i missed something again. Just to be certain. And then try again.

---

### Post by r.stiltskin on 2013-04-21
Then you can highlight & copy the entire series of commands, paste them to a file, save it to a usb flash drive, then plug that into the ubuntu machine, etc.

---

### Post by Mecharius on 2013-04-21
So I tried going back from the beginning with:
```
fdisk /dev/sda
```
this gave me 
```
Command (m for help)
```
So I hit m to see what it gave me:
[code]Command action
     a   toggle a bootable flag
     b   edit bsd disklabel
     c   toggle the dos compatibility flag
     d   delete a partition
     l    list known partition types
     m  print this menu
     n   add a new partition
     o   create a new epty DOS partition table
     p   print the partition table
     q   quit without saving changes
     s   create a new empty sun disklabel
     t    change a partition's system id
     u   change display/entry units
     v   verify the partition table
     w   write table to disk and exit
     x   extra functionality (experts only)

---

### Post by r.stiltskin on 2013-04-21
> **Mecharius said:**
> corrected the issue with the typo and put it back in terminal, checked it over three times to be certain. No issues. Hit enter, and it gave me the prompt again:
```
root@ubuntu:/#
```
So no change, so long as I am understanding everything correctly. Should be my name in place of ubuntu, yes?

So that's what you see after running **chroot  $TARGET  /bin/bash** correct?
If so, good.  But that's not the solution yet.  That just get's you in position to attempt the solution.  Now you are "superuser" in _your own_ ubuntu system, not the one on the CD.  So, if the amd64-microcode is what's preventing you from booting normally, you can uninstall it.

So, in that same root terminal session [_it must be the same terminal session in which you just ran that series of commands ending with "chroot $TARGET /bin/bash"_] run these two commands (one at a time):

```

apt-get remove amd64-microcode
apt-get autoremove
```

Then to exit the chroot environment, simply:
```
exit
```

Then try to reboot without the cd.  You may still need to edit the grub boot parameters with acpi=copy_dsdt or acpi=off.

---

### Post by oldfred on 2013-04-21
Press q to exit.
You are in advance mode to create new partition table which I do not think you want.

---

### Post by r.stiltskin on 2013-04-21
> **Mecharius said:**
> So I tried going back from the beginning with:
```
fdisk /dev/sda
```
this gave me 
```
Command (m for help)
```
So I hit m to see what it gave me:
```
Command action
     a   toggle a bootable flag
     b   edit bsd disklabel
     c   toggle the dos compatibility flag
     d   delete a partition
     l    list known partition types
     m  print this menu
     n   add a new partition
     o   create a new epty DOS partition table
     p   print the partition table
     q   quit without saving changes
     s   create a new empty sun disklabel
     t    change a partition's system id
     u   change display/entry units
     v   verify the partition table
     w   write table to disk and exit
     x   extra functionality (experts only)

OK so you jumped the gun & now I don't know what status your system is in.  So your best bet now is to close that terminal completely, open a new terminal, and start over again with this series of commands:

[code]sudo su
TARGET=/media/sda1
mkdir  -p  $TARGET
mount  /dev/sda1  $TARGET
mount  --bind  /dev  $TARGET/dev
mount  --bind /proc  $TARGET/proc
mount  --bind /sys  $TARGET/sys
chroot  $TARGET  /bin/bash
```
and then, without closing that terminal, continue with

```
apt-get remove amd64-microcode
apt-get autoremove
```

and then
```
exit
```
and reboot.

---

### Post by Mecharius on 2013-04-21
I hit q to quit and am now back at 
```
root@ubuntu:/#
```

---

### Post by r.stiltskin on 2013-04-21
So you will better understand what we're trying to do:  **chroot** in and of itself doesn't solve anything.  All chroot does is change what the system views as its root file system.

You can't boot to your Ubuntu partition, so you're booting with a CD.  Therefore, your system regards the files on the CD as its root file system.  If you try to install or uninstall anything, you're trying to modify the files on the CD, which is pointless.  You need to modify the files on your hard disk.  Therefore, you "chroot" into the file system which you installed on /dev/sda1 -- the first partition on your hard disk.  Now the system regards that partition as its root file system, and any changes you make will be reflected in the files on your hard disk.

Then when you "exit" from the chroot environment, you're back in the CD's file system.

Hope that helps.

---

### Post by Mecharius on 2013-04-21
x out the terminal and started back over. sudo su took me back to being:
```
root@ubuntu:/#
```
put everything in again, checked twice for mistakes, none. Hit enter:
```
root@ubuntu;/#
```
put in

```
apt-get remove amd64-microcode
apt-get autoremove
```

This gave me:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

---

### Post by r.stiltskin on 2013-04-21
> **Mecharius said:**
> x out the terminal and started back over. sudo su took me back to being:
```
root@ubuntu:/#
```
put everything in again, checked twice for mistakes, none. Hit enter:
```
root@ubuntu;/#
```
put in

```
apt-get remove amd64-microcode
apt-get autoremove
```

This gave me:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

Exactly when  did you get that message?  After "apt-get remove amd64-microcode" or after "apt-get autoremove"?   Were there any other messages (and when?)

---

### Post by Mecharius on 2013-04-21
came up after both.

---

### Post by r.stiltskin on 2013-04-21
And there were no other messages before that one?  (Immediately after "apt-get remove amd64-microcode"?)

---

### Post by Mecharius on 2013-04-21
```
root@ubuntu:/# apt-get remove amd64-microcode
E: dpkg was interrupted, you must manually run 'sudo-dpkg --configure -a' to correct the problem.
[EMAIL="root@ubuntu:/"]root@ubuntu:/[/EMAIL]# apt-get autoremove
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
[EMAIL="root@ubuntu:/#"]root@ubuntu:/#[/EMAIL]
```

---

### Post by r.stiltskin on 2013-04-21
As things stand, I can't tell whether you actually have uninstalled the amd64-microcode package or not.  (I think not.)  It appears that dpkg is simply refusing to do anything, including that removal, until "configure" is completed.  It sounds like something went wrong when you installed something (who knows what) in a previous session.  I just don't have enough information.

If you have nothing else to report, you should simply run that one single command, and then post back with as much information as you can glean from the output it gives you.  It's probably going to be too much to post here in full, so you'll have to make your best effort to try and distinguish which parts are important.  So just run this single command:

```

dpkg --configure -a
```

By the way, dpkg is the "back-end" program that apt-get calls to install, uninstall, and update packages.  That error message is just telling you that there is a package (or packages) that was not successfully configured some previous time that dpkg ran.  Running this command will (hopefully) complete that process.

Then tell us what the output was & we can try to figure out what to do next.

---

### Post by Mecharius on 2013-04-21
ran the dpkg, this is what I was given.

```
Setting up amd64-microcode (1.20120910-1) ...
Using per-core interface to update microcode on online processors...
update-inttramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-27-generic
[EMAIL="root@ubuntu:/#"]root@ubuntu:/#[/EMAIL]
```

So my next guess would be to go on with the apt-get remove, but due to recent events, i wish to wait and see what suggestions are made?

---

### Post by r.stiltskin on 2013-04-21
And in fact, it may not even be necessary or appropriate to remove amd64-microcode because the actual problem may be related to whatever was not properly configured in that previous session a week ago.  Furthermore, for all we know, you may not even have installed amd64-microcode yet.

---

### Post by r.stiltskin on 2013-04-21
Ignore post #150.  I'll post again soon.

---

### Post by r.stiltskin on 2013-04-21
OK, so it seems there is no reason to remove that package (at least not yet), since you have only just finished installing it.

I think you should **exit** and try to reboot without the CD.

---

### Post by Mecharius on 2013-04-21
I shall do that, and then post the results.

---

### Post by r.stiltskin on 2013-04-21
Even if you can't boot without the CD, the amd64-microcode may not be the problem.

But still, if you can't boot, you should repeat the process of booting with the CD, chrooting into /dev/sda1, and then remove that package.  Refer to post #140 for the entire sequence.

Then try booting again without the CD.

If that still fails, we could try to figure out what you did PRIOR to installing amd64-microcode, but it might be easier to start the entire installation over again from the beginning.  Your choice.

---

### Post by Mecharius on 2013-04-21
I tried booting ubuntu without edits, i was given the sp5100_tco again. Replaced quiet splash and was given this after the scrolling information:
```
 [       1.174720] microcode: Microcode Update Driver: v2.00 [EMAIL="tigran@aivazian.fsnet.co.uk"]tigran@aivazian.fsnet.co.uk[/EMAIL], Peter Oruba
```
same thing from both nomodeset and acpi=off

---

### Post by r.stiltskin on 2013-04-21
Well I'm not sure but it certainly seems that it's crashing when it tries to apply the microcode driver, so try uninstalling it.  
Follow the steps that I summarized in post #140 and then try to boot.

---

### Post by Mecharius on 2013-04-22
Unfortunately I am at a temporary stopping point. My employer requires me to go off for two weeks to a place where I can not take any of my machines with me. I must leave early morning, so I must halt my Ubuntu progress And offer my most sincere appreciation to r.stiltskin, Bashing-om, as well as the others who have offered me their help. I will return to this in two weeks with the hope that I have not been forgotten. If during that time period anyone can think of any suggestions then it is my request that they be posted here so that I can immediately dive back into this upon my return. Again, you have my appreciation and my thanks.

---

### Post by Mecharius on 2013-05-28
What was supposed to be two weeks became five. I hope I am not completley forgotten, because as soon as is possible I would like to continue on with this where I left off. I am going to take the time to go back over everything that has been posted up here, retry a few things and see where that puts me. Maybe now I can find a soulution to my Toshiba's issue with not wanting to use Ubuntu.

---

