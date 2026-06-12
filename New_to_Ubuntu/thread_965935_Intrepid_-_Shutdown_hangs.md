---
title: "Intrepid - Shutdown hangs"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by davidsrsb on 2008-10-31
8.10 release - Shutdown problem. The graphical shutdown blanks to a blinking cursor at the top left. This stays for several minutes, but can be unstuck by removing the network cable.

This was happening all the time to many people during the beta phase, but suddenly started working properly a few days ago. The latest update (base-files 4.0.4ubuntu2.2?) has broken it again

---

### Post by BenAshton24 on 2008-10-31
That's odd but without any errors or any logs its a bit difficult to get a solution. my advice would be to wait and hope for the best :D

--Ben

---

### Post by lovinglinux on 2008-11-02
Same here. Turning off the wireless also help, but that isn't a solution.

---

### Post by unutbu on 2008-11-02
What happens if you type
```

sudo ifdown wlan0
```
and then try to shutdown? (Change wlan0 to the name of your wireless interface).

If you can avoid the hanging problem by typing the above command first, then we can probably eliminate the problem by shutting down networking earlier in the shutdown sequence. But first test if my suggestion works.

---

### Post by lovinglinux on 2008-11-03
> **unutbu said:**
> What happens if you type
```

sudo ifdown wlan0
```
and then try to shutdown? (Change wlan0 to the name of your wireless interface).

If you can avoid the hanging problem by typing the above command first, then we can probably eliminate the problem by shutting down networking earlier in the shutdown sequence. But first test if my suggestion works.

It works.  What is strange is that my wireless card is listed as eth1. Anyway, how do I change the shutdown sequence?

---

### Post by unutbu on 2008-11-03
Run this command
```

sudo ln -sf /etc/init.d/networking /etc/rc0.d/K40networking

```
Doing so will cause the computer to run 
```

sudo ifdown eth1

```
as part of the shutdown sequence.

---

### Post by lovinglinux on 2008-11-03
> **unutbu said:**
> Run this command
```

sudo ln -sf /etc/init.d/networking /etc/rc0.d/K40networking

```
Doing so will cause the computer to run 
```

sudo ifdown eth1

```
as part of the shutdown sequence.

Thank you again.

I have followed [[COLOR="Red"]**this suggestion **[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6069946&postcount=6") and it works. I guess is the same solution, with different method.

---

### Post by unutbu on 2008-11-03
I'm very glad to hear you've found a method to solve the problem! Thanks also for reporting back here to share the solution with others.

I guess it should be pointed out, however, that /etc/init.d/alsa-utils is a script for restoring ALSA (sound) driver settings. It really is not a good place for shutting down network interfaces. The reason why it works is merely because the alsa-utils script gets called during the shutdown sequence. 

My suggestion adds /etc/init.d/networking to the shutdown sequence. If anyone out there chooses to try my suggestion and it works, I would recommend it over the alsa-utils solution on the basis of being more logical place to put network shutdown commands.

---

### Post by lovinglinux on 2008-11-03
> **unutbu said:**
> I'm very glad to hear you've found a method to solve the problem! Thanks also for reporting back here to share the solution with others.

I guess it should be pointed out, however, that /etc/init.d/alsa-utils is a script for restoring ALSA (sound) driver settings. It really is not a good place for shutting down network interfaces. The reason why it works is merely because the alsa-utils script gets called during the shutdown sequence. 

My suggestion adds /etc/init.d/networking to the shutdown sequence. If anyone out there chooses to try my suggestion and it works, I would recommend it over the alsa-utils solution on the basis of being more logical place to put network shutdown commands.

Thank you again. Your solution works like a charm.

---

### Post by ubnewbie2 on 2008-11-04
> **unutbu said:**
> Run this command
```

sudo ln -sf /etc/init.d/networking /etc/rc0.d/K40networking

```
Doing so will cause the computer to run 
```

sudo ifdown eth1

```
as part of the shutdown sequence.

That didn't work for me.  Is that because my network is on eth0?

---

### Post by unutbu on 2008-11-04
ubnewbie2, there are at least 2 different reasons why a machine may not shutdown properly: Besides a hanging network device, the problem is also sometimes caused by ACPI not working properly. There could very well be other reasons that I don't know about.

Given that 
```

sudo ln -sf /etc/init.d/networking /etc/rc0.d/K40networking

``` did not work for you, it seems likely your problem lies elsewhere.

You could try this
[http://ubuntuforums.org/showpost.php?p=5586513&postcount=3](http://ubuntuforums.org/showpost.php?p=5586513&postcount=3)
or this
[http://ubuntuforums.org/showpost.php?p=5879657&postcount=10](http://ubuntuforums.org/showpost.php?p=5879657&postcount=10)

---

### Post by ubnewbie2 on 2008-11-04
> **unutbu said:**
> ubnewbie2, there are at least 2 different reasons why a machine may not shutdown properly: Besides a hanging network device, the problem is also sometimes caused by ACPI not working properly. There could very well be other reasons that I don't know about.

Given that 
```

sudo ln -sf /etc/init.d/networking /etc/rc0.d/K40networking

``` did not work for you, it seems likely your problem lies elsewhere.

You could try this
[http://ubuntuforums.org/showpost.php?p=5586513&postcount=3](http://ubuntuforums.org/showpost.php?p=5586513&postcount=3)
or this
[http://ubuntuforums.org/showpost.php?p=5879657&postcount=10](http://ubuntuforums.org/showpost.php?p=5879657&postcount=10)


It is indeed the networking causing the problem, because turning it off in alsa-utils works.  I wondered why the above didn't however, as it is supposed to address the same problem.

---

### Post by unutbu on 2008-11-04
Hm. That's very interesting, ubnewbie2.
I don't know the answer to that.

If you would like to get to the bottom of this, try the following:
```

gksu gedit /etc/init.d/alsa-utils
```
Put a # sign in front of the line you added:
```
# ifconfig eth0 down
```
The # sign tells the script interpreter that that line should be ignored. (This is also known as 'commenting out'). At any time that you wish to restore the alsa-utils solution, you simply remove the # sign.

Type 
```

sudo /etc/init.d/networking stop

```
Then try to shutdown. Does it work?

---

### Post by ubnewbie2 on 2008-11-05
I tried it and

```
 sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                        
Ignoring unknown interface eth0=eth0.
                                                                       [ OK]

```

that looked odd.  I tried shutting down anyway, and sure enough it stopped waiting for ALSA again.

I have uncommented the line in alsa-utils again for now

---

### Post by lovinglinux on 2008-11-05
While I was installed additional software and configuring stuff, the problem appeared and went away a few times. Now that I have finished most of the work the fix seems to be holding up.

---

### Post by unutbu on 2008-11-05
>  sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                        
Ignoring unknown interface eth0=eth0.

Wow, this is very exciting, ubnewbie2. Somewhere on your system there is a configuration file that says
"eth0=eth0" when it should say "eth0". It might be 
/etc/udev/rules.d/70-persistent-net.rules
or perhaps some file in /etc/modprobe.d/
or maybe /etc/network/interfaces... or maybe some file I don't know about.

To see if the string "eth0" shows up in any file in 
/etc/modprobe.d/, type```

grep -r eth0 /etc/modprobe.d/
```
You can check /etc/udev/rules.d/70-persistent-net.rules and /etc/network/interfaces in a text editor.

Tell me what you find.
Also, please post the output of 

```
ifconfig
```

PS. I think the offending file is /etc/network/interfaces. Check for "eth0=eth0" there first.

---

### Post by ubnewbie2 on 2008-11-06
> **unutbu said:**
> Wow, this is very exciting, ubnewbie2. Somewhere on your system there is a configuration file that says
"eth0=eth0" when it should say "eth0". It might be 
/etc/udev/rules.d/70-persistent-net.rules
or perhaps some file in /etc/modprobe.d/
or maybe /etc/network/interfaces... or maybe some file I don't know about.

To see if the string "eth0" shows up in any file in 
/etc/modprobe.d/, type```

grep -r eth0 /etc/modprobe.d/
```
You can check /etc/udev/rules.d/70-persistent-net.rules and /etc/network/interfaces in a text editor.

Tell me what you find.
Also, please post the output of 

```
ifconfig
```

PS. I think the offending file is /etc/network/interfaces. Check for "eth0=eth0" there first.

Well, ifconfig gives me

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:d4:d0:7a  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fed4:d07a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:750282 (750.2 KB)  TX bytes:126283 (126.2 KB)
          Interrupt:216 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

```

and

```
~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

```

and 

grep -r eth0 /etc/modprobe.d/    returns nothing

and 

```
$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:15:d4:d0:7a", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```


so where does that leave us?

---

### Post by unutbu on 2008-11-06
Hm, ubnewbie2. I would only give myself a 10% chance of figuring out this problem. However, what I'm suggesting won't hurt anything and if you are willing to pursue this a little further, please post your 

/etc/init.d/alsa-utils
/etc/init.d/networking
/var/run/network/ifstate

and the output of ```

ls -l /etc/rc0.d/
```

---

### Post by karhulitos on 2008-11-06
Hi,

I believe I'm suffering from the same. I tried
```
~$ sudo ifdown ath0
Ignoring unknown interface ath0=ath0.
```

then tried it again:
```
~$ ~$ sudo ifdown ath0
ifdown: interface ath0 not configured
```

and I'm writing this via above ath0 so it's definetively up.
I won't bother testing the ALSA way as I guess it'll fail too.

---

### Post by rrashkin on 2008-11-06
I don't know if this is the same thing but I noticed that **shutdown** takes about 2 minutes.  I get the blinking cursor for what seemed an alarming amount of time but eventually it does shut down.

---

### Post by karhulitos on 2008-11-07
> **rrashkin said:**
> I don't know if this is the same thing but I noticed that **shutdown** takes about 2 minutes.  I get the blinking cursor for what seemed an alarming amount of time but eventually it does shut down.

Hups, I thought of this too but not anymore sure if I waited really 2 or more minutes.. Need to test when I get back home! Good point!

[edit] darn computer stayed powered up for 2h, so I don't have same case as you. Also I wonder do I have same case as the thread starter at all. My PC (Acer Aspire 7520G) just stays powered up the empty "Ubuntu shutdown bar" on the screen. No blinking cursors anywhere.
Also I noticed that by pressing any button triggers the PC to power itself down immediately. Even touching the touchpad shuts the system down when in above state.

---

### Post by davidsrsb on 2008-11-07
The common bug with the blinking cursor does eventually timeout. I have just upgraded a second pc and this does it too. My suspicion now is on my newish Aztech router not handling an ipv6 AAAA dns request. Ibex should not be sending ip6 during shutdown anyway.

---

### Post by Gilanel on 2008-11-17
After reading 3 pages I'm cofused what is the Problem.
On my PC it looks like it:
1)During shutting down, progress bar is stopping 
2)I'm pressing ALT+F7 to change to my terminal 
3)And there is "Stopping ALSA" and that's it, some time it take 2 minutes sometime 40 minutes to shutdown 

And sometimes this problem is not occurring 

Can someone explain me how to fix this bug PLEASE


No importat 
Problem Fixed..

---

### Post by albesan on 2008-11-21
hey Gilanel,

Great that your problem is solved. Do you mind telling how it happened? if you remember.

thanks

a

---

### Post by samthurston on 2008-11-22
My problem appears to be distinct from the eth/alsa problem.  I've upgraded all the way from gutsy, and installed a lot of weird stuff (RT kernel,etc) so this may be hard to track.

symptoms: shutdown hangs.  Complete freeze, can't even get a virtual term.  my gnome desktop background is still up, mouse cursor is frozen on screen, no other elements on the screen at this time.

I tried the alsa fix, as well as manually stopping eth0 before shutdown.  No luck with either.

Two interesting things of note:

this bit of dmesg output looks interesting: 

```
[    0.394443] TCP: Hash tables configured (established 131072 bind 65536)
[    0.394447] TCP reno registered
[  507.669737] NET: Registered protocol family 1
[  507.669851] checking if image is initramfs... it is

```

two days ago was the day i did my upgrade and on that day, right before a startup, /var/log/messages has a big block of ^@^@^@^@'s, don't know if that means anything.  the last entries before that block is a long string of these:
```

Nov 20 17:22:56 kestrel -- MARK --
```

Where am I forgetting to look?

---

### Post by babloo75 on 2008-11-22
sorry, i m wrong

---

### Post by ciscosurfer on 2008-11-22
> **samthurston said:**
> ...two days ago was the day i did my upgrade and on that day, right before a startup, /var/log/messages has a big block of ^@^@^@^@'s, don't know if that means anything.  the last entries before that block is a long string of these:
```

Nov 20 17:22:56 kestrel -- MARK --
```Where am I forgetting to look?These lines are nothing to worry about; they are not causing your box to hang. 
 They are normal and set to 20 minute intervals by default via sysklogd (syslogd, et al.)

```
man sysklogd
``````
-m interval
              The syslogd logs a mark timestamp regularly.  The default interval between two -- MARK -- lines
              is  20  minutes.   This can be changed with this option.  Setting the interval to zero turns it
              off entirely.  Depending on other log messages generated these lines may not be written consec&#8208;
              utively.
```There are numerous suppositions on the Net as to the reasoning behind the -- MARK --.  Here are a few: That the daemon is working properly, consecutive marks may indicate no trouble during this time-frame, to serve as an easy visual queue, and the list goes on.

---

### Post by samthurston on 2008-11-22
> **ciscosurfer said:**
> These lines are nothing to worry about; they are not causing your box to hang. 


I wasn't worried about them, just pointing out there was nothing in the log indicating what the hang was about.  However I was able to log into my machine via a second machine and SSH, and I am no longer convinced that this isn't related to the alsa bug.

sure enough, trying the solution [http://ubuntuforums.org/showpost.php?p=6069946&postcount=6](http://ubuntuforums.org/showpost.php?p=6069946&postcount=6) seems to have fixed it.  This worries me though because I use my box for serving files and stuff, and I don't want eth0 killed every time I log out.  WHY does this work and is there a better solution that doesn't involve uselessly killing my ethernet connection?

---

### Post by Gilanel on 2008-11-23
> **albesan said:**
> hey Gilanel,

Great that your problem is solved. Do you mind telling how it happened? if you remember.

thanks

a

Please try solution from 
[http://ubuntuforums.org/showthread.php?p=6069946#post6069946]("http://ubuntuforums.org/showthread.php?p=6069946#post6069946") 
post no 6 by > m0ridin

---

### Post by samthurston on 2008-11-23
Well I spoke too soon.  

[http://ubuntuforums.org/showpost.php?p=6069946&postcount=6](http://ubuntuforums.org/showpost.php?p=6069946&postcount=6)

did not solve my problem, and has actually made it worse, in that now I can't log in via ssh to try to fix things once it crashes.  

the freeze happens if i try to logout, shutdown, or fast-user-switch. ctrl-alt-backspace won't kill the xserver, ctrl-alt-f# won't switch terms. I look at the processes after the freeze, and I don't see anything that's obviously running out of control. attempts to manually kill the xserver fo not work.

This is a really serious problem as I installed originally with EXT2 instead of EXT3 and now I basically have to wait 20 minutes every time I reboot for fsck to run because it doesn't shutdown cleanly.

---

### Post by ciscosurfer on 2008-11-23
First, you can modify fsck parameters to prevent it from running based on an unclean shutdown in either /etc/fstab other system files.  But beware that if you turn it off or change the timing, you should periodically run it anyhow to be sure that your system doesn't indeed get borked.

Second, you should add your story/account/details to the long list of people who have complained about this issue on Launchpad.  This is a serious issue that the devs have yet to address properly and all other solutions are simply kludges that may or may not for your current situation.

---

### Post by unutbu on 2008-11-23
samthurston, there is a way to convert ext2 filesystems into ext3:

```
sudo tune2fs -j /dev/sda1
```
(substitute the correct device name for sda1).
The only difference between ext3 and ext2 is the presence of a journal, which this command adds.

---

### Post by samthurston on 2008-11-23
can I do this on a mounted filesystem?

---

### Post by ciscosurfer on 2008-11-23
> **samthurston said:**
> can I do this on a mounted filesystem?```
man tune2fs
``````
 -j     Add an ext3 journal to the filesystem.  If the -J option is not specified, the default journal parameters will be used to create an appropriately  sized  journal
              (given  the  size  of the filesystem) stored within the filesystem.  Note that you must be using a kernel which has ext3 support in order to actually make use of
              the journal.

              If this option is used to create a journal on a mounted filesystem, an immutable file, .journal, will be created in the top-level directory of the filesystem, as
              it  is  the only safe way to create the journal inode while the filesystem is mounted.  While the ext3 journal is visible, it is not safe to delete it, or modify
              it while the filesystem is mounted; for this reason the file is marked immutable.  While checking unmounted filesystems, e2fsck(8) will automatically move .jour&#8208;
              nal  files  to the invisible, reserved journal inode.  For all filesystems except for the root filesystem,  this should happen automatically and naturally during
              the next reboot cycle.  Since the root filesystem is mounted read-only, e2fsck(8) must be run from a rescue floppy in order to effect this transition.

              On some distributions, such as Debian, if an initial ramdisk is used, the initrd scripts will automatically convert an  ext2  root  filesystem  to  ext3  if  the
              /etc/fstab  file  specifies the ext3 filesystem for the root filesystem in order to avoid requiring the use of a rescue floppy to add an ext3 journal to the root
              filesystem.

```

---

### Post by unutbu on 2008-11-23
Ah. Good point. The tune2fs command can be run on a mounted filesystem, but after re-reading the man page (man tune2fs), it appears there is an easier way to convert a root filesystem from ext2 to ext3:

Instead of running the tune2fs command, edit your /etc/fstab:```


gksu gedit /etc/fstab

```
Find the line that looks something like this:
```

UUID=03a507ee-cdac-4bd9-b438-eccd616b66ed [COLOR="Red"]/[/COLOR] ext2 defaults,errors=remount-ro 0 1
```

(in particular, look for  '/' in the second column -- this is the mount point).

Simply change ext2 to ext3 here. Save and exit.
Next time you reboot, the filesystem will become ext3.

From the man page:

```
              On some distributions, such as Debian, if an initial ramdisk is used, the
              initrd scripts will automatically convert an ext2 root filesystem to ext3
              if the /etc/fstab  file  specifies  the  ext3  filesystem  for  the  root
              filesystem  in order to avoid requiring the use of a rescue floppy to add
              an ext3 journal to the root filesystem.

``` Since Ubuntu is based on Debian, this  paragraph should apply.

Edit: Rescue floppy? Those were good times... Good times... :)

---

### Post by majiciannz on 2008-11-24
> **unutbu said:**
> I'm very glad to hear you've found a method to solve the problem! Thanks also for reporting back here to share the solution with others.

I guess it should be pointed out, however, that /etc/init.d/alsa-utils is a script for restoring ALSA (sound) driver settings. It really is not a good place for shutting down network interfaces. The reason why it works is merely because the alsa-utils script gets called during the shutdown sequence. 

My suggestion adds /etc/init.d/networking to the shutdown sequence. If anyone out there chooses to try my suggestion and it works, I would recommend it over the alsa-utils solution on the basis of being more logical place to put network shutdown commands.

I to have had the same problem without realising it was the network that caused it to hang. However, after trying your advise it now works perfectly. So many thanks from a newby. 
Now on to solving the next problem.........

---

