---
title: "no drives found?"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by Kickinthedoor on 2012-08-11
A friend of mine gave me his dell inspiron 6000 to try to get a os running on it. it originally had xp home on it and when booted it comes up with error " internal hdd soft error: fixed by retries. strike f1 to continue, f2 to run setup utility. when i press f1 i get a black screen.
 
i then try to install a copy of window 7 ultimate(as requested by friend) and it loaded files and started the install. when it gets to the prompt to select drives it says that no drives are found. I rebooted to try again and it wont go past the windows logo screen.

next i wanted to try putting ubuntu on so i threw in a ubuntu 10.4 live cd and attempted an install. i get threw the 7 steps and start the installation and it gets 15% and stops with input/output error during read on /dev/sda. pressing retry does nothing and after pressing ignor about 8 times it starts over runs up 5% and pops up with Failed to create a file system The ext4 file system creation in partition #1 of sci1 (0,0,0)(sda) failed. clicking ok birngs me back to step (5 who are you?). if i try to go back or forward another pop up says ubi-migrationassistant fail. 

I am able to use the try ubuntu feature and i tried to format the hdd but gparted and the disk utility show no drives. not sure if the drive is shot or im just doing something wrong

---

### Post by NikTh on 2012-08-11
Hi , 
sorry to post that but I think you must tell your friend to prepare his pocket for a new drive.
To make this for sure.. Boot up and click "Try Ubuntu" and when you are in desktop environment open a terminal (ctrl+alt+t) and copy-pate below commands from here to terminal one at time. 
```
sudo apt-get install smartmontools --no-install-recommends
sudo smartctl -a /dev/sda
```Give the results of second command here 
Put the results inside [CODE] tags , by highlighting the text and click the [SIZE=3]**#**[/SIZE] symbol on top of message pane.
Thanks

---

### Post by Bashing-om on 2012-08-12
Kickinthedoor;
  Another option might be to zero out that disk with the VERY destructive command dd .. and see if you can then install ubuntu. It is a lengthy process but might be worth the effort.

---

### Post by Kickinthedoor on 2012-08-12
I will try that command as soon as i get back to the machine. If the drives dead its no biggie. We just wanted to have another comoputer in are shop just for social networking and ordering products. thanks for the help

---

### Post by Kickinthedoor on 2012-08-12
@NikTh- Here is the result from the second command in terminal. 

```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Smartctl open device: /dev/sda failed: No such file or directory
```

I'm guessing that the failure isn't a good sign.

@ Bashing-om can you tell me more about this destructive command or maybe a link to a walk through? I'm not worried about doing any more damage so I'm game to try anything. Or is the results of that command enough to determine the drive has gone belly up? Once again, thanks for the help. this community is the best around!

---

### Post by NikTh on 2012-08-12
Hi ,
can you give the results of 
```
sudo parted -l 
sudo fdisk -l 
``` 

are you sure the disk is well connected ? check the wire if you can.
Thanks

---

### Post by Kickinthedoor on 2012-08-12
Once again im not near the machine. Ill check the conection when i get home. Should blow it out with some dust off? I will also run those commands. Thanks for helpin me out

---

### Post by Bashing-om on 2012-08-12
Kickin:
  After ya comply with NikTh's advise/directive we can see 'bout the dd comand.
I have faith in it to restore a disk if it has no physical defects.

Motto: one thing at a time! ===>BDQ

---

### Post by Kickinthedoor on 2012-08-13
@ NikTh I took out the 2 little screws holding the drive in place, removed and checked the connection. no damage i could see and it was clean as well. replaced and secured drive and ran those commands. here are the reuslts

```
ubuntu@ubuntu:~$ sudo parted -l
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$
```

---

### Post by NikTh on 2012-08-13
> **Kickinthedoor said:**
> @ NikTh I took out the 2 little screws holding the drive in place, removed and checked the connection. no damage i could see and it was clean as well. replaced and secured drive and ran those commands. here are the reuslts

```
ubuntu@ubuntu:~$ sudo parted -l
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$
```

Hi , 
sorry but I cannot understand what happened. It seems that Ubuntu cannot even recognize that you have Hard Drive installed. (plugged) . 
Wait for someone more experienced with new idea or something. 
Thanks and sorry I cannot help.

---

### Post by mr-woof on 2012-08-13
I'd definitely check the physical connection, but it sounds like the drive is dead. You could try burning gparted to a live cd and see if it picks it up.

---

### Post by Bashing-om on 2012-08-13
kickin ;

 Looks like we are back to trying to zero out the disk with dd .... here goes
I suggest that you look at the manual " man dd " in terminal . This command is awesome but very powerful and will destroy if used in a inappropriate manner.
OK
From the live cd (so your devices are not mounted) in terminal paste/copy this:```
sudo dd if=/dev/zero of=/dev/sda bs=1M
```this command sequence is for only one drive installed (hence /dev/sda).
  There will be no echo to the terminal of any output (work-around-below) until finished.... will take a long time ... my 500G drive took 2 hours to complete.

here is the way to get a status on "dd"

open up another terminal and enter this code:
```
ps -ef | grep dd
```in this result look for the line that designates dd's process ... NOT the process of the grep for dd's process...you will need the process numbers from the first column (this is the pid).
ok ?
enter this code in the same (#2) terminal:
```
sudo kill -SIGUSR1 <the pid number>
```without the brackets in the above, just to show what/where to place pid.

the output from this terminal will be in your first terminal after a bit of number crunching... In 'bout an hour input the above again to get updated status... 

when done see if Gparted from the live cd will see the disk and then install a great operating system and enjoy!

          HTH <====BDQ

---

### Post by Kickinthedoor on 2012-08-13
Thanks for the info, im gunna give it a shot. the drive is only 80gb so hopefully it goes a bit quicker then your 500. ill post my results

---

### Post by Bashing-om on 2012-08-13
Kickin;

  Just checking in see how it is going ... let us know ...if all goes good you'll be up and running tonight.
[INDENT]Best of luck <===BDQ
[/INDENT]

---

### Post by Kickinthedoor on 2012-08-14
just about ready to run that comand. crossing my fingers and hoping for the best. ill post my progress thanks again

---

### Post by Kickinthedoor on 2012-08-14
ok so based on your time of 2 hours im guna say something went wrong. heres what i have from terminal 1

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=1M
dd: writing `/dev/sda': No space left on device
240+0 records in
239+0 records out
250974208 bytes (251 MB) copied, 19.7607 s, 12.7 MB/s
ubuntu@ubuntu:~$
```

and i ran the command to see the progress and got this

```
ubuntu@ubuntu:~$ ps -ef | grep dd
root         2     0  0 23:34 ?        00:00:00 [kthreadd]
root      1310     2  0 23:35 ?        00:00:00 [pccardd]
ubuntu    3727     1  0 23:37 ?        00:00:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 9 --session
root      3847  3809  0 23:37 ?        00:00:00 hald-addon-input: Listening on /dev/input/event4 /dev/input/event2 /dev/input/event1 /dev/input/event6 /dev/input/event5 /dev/input/event0
root      3857  3809  0 23:37 ?        00:00:00 /usr/lib/hal/hald-addon-generic-backlight
root      3867  3809  0 23:37 ?        00:00:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      3869  3809  0 23:37 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
108       3870  3809  0 23:37 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
ubuntu    4140  4123  0 23:46 pts/1    00:00:00 grep --color=auto dd
ubuntu@ubuntu:~$
```

also not sure what the process numbers are, i hope your hanging around your computer. i dont want to loose any progress if ive even made any

---

### Post by Bashing-om on 2012-08-14
Kickin ...
the output from dd is as shud be upon completion of zeroing out the disk......

uuuhhh I hope it ran about 20 minutes...if the dd command had finished then the kill command had nothing but garbage in ... is this what happened ??? I hope!

---

### Post by Bucky Ball on 2012-08-14
This might be off the ball but are you sure you're attempting to install Ubuntu, desktop or alternative, and not Wubi, which is intended for installation inside Windows?

If you don't have Win up and running, it will be impossible to install Wubi, if this is the scenario.

---

### Post by Kickinthedoor on 2012-08-14
heres how it went down. i started the dd comand. as you can see it only took about 19 seconds to complete. i then checked the progress with a second terminal. (also posted the results. i havent killed the process yet because im unsure of the PID. i tried looking up some more info to help me out but honestly it might as well be written in russian

---

### Post by Kickinthedoor on 2012-08-14
@bucket ball yea im sure. Ive used this disk multiple times to install ubuntu on laptops and desktops

---

### Post by Bucky Ball on 2012-08-14
> **Kickinthedoor said:**
> @bucket ball yea im sure. Ive used this disk multiple times to install ubuntu on laptops and desktops

Goodo. ;) Just checking.

---

### Post by Kickinthedoor on 2012-08-14
> **Bucky Ball said:**
> Goodo. ;) Just checking.

good lookin out. any chance you could pull the pid out of the results i posted before? im just trying to wrap this up. im assuming that the drive is dead but i just wana make sure

i wana say its 5 based on this line:

"pid 5 --print-address 9 --session"

---

### Post by Bashing-om on 2012-08-14
Kickin:
  No sweat yet. .....if you do not have a prompt in the 1st terminal (the one ya ran dd in) do ctl-c to interrupt the process and return ya a prompt....
that drive may be toast ...but I am not willing to give up yet....
try this one from mips suggestion:
```

**[COLOR=Red]WARNING[/COLOR], use this information with extreme caution!**
You can repair the MBR from the Windows install media using the **fixmbr** command.

In linux you can erase the mbr using dd
# dd if=/dev/null of=/dev/sdX bs=446 count=1

# dd if=/dev/null of=/dev/sdX bs=512 count=1 will not only erase the mbr but also the **partition table** [COLOR=red]**You have been warned!**[/COLOR]
```

try that and see what haps.

[INDENT]BDQ
[/INDENT][COLOR=red][/COLOR]

---

### Post by Kickinthedoor on 2012-08-14
no luck

```
dd: opening `/dev/sdX': Permission denied
```

im boned huh?

---

### Post by Bucky Ball on 2012-08-14
> **Kickinthedoor said:**
> no luck

```
dd: opening `/dev/sdX': Permission denied
```im boned huh?

Are you using 'sudo' before the command?

---

### Post by Kickinthedoor on 2012-08-14
good call, i didnt even notice that lol

---

### Post by Kickinthedoor on 2012-08-14
ran it again

```
ubuntu@ubuntu:~$ sudo dd if=/dev/null of=/dev/sdX bs=446 count=1

0+0 records in
0+0 records out
0 bytes (0 B) copied, 1.1454e-05 s, 0.0 kB/s
```

---

### Post by Bashing-om on 2012-08-14
Kickin ... in that last the X in sdX is a place holder ,,, shub be replaces with "a" ... to read sda...ok?..lemme see if there is a pid in any of yoyr results,(don't see how as dd ran out before ps command cud look for it).
BDQ

---

### Post by Kickinthedoor on 2012-08-14
ran it as "sda" and got "bus error" as a result then terminal closed and wont re open.

---

### Post by Bashing-om on 2012-08-14
OK kicken....reboot the system and try the wipe the MBR code sequece again and catch the exact error if the buss error results.
BDQ

---

### Post by Bashing-om on 2012-08-14
Hey you are doing all this from the live CD .. are you not?

---

### Post by Kickinthedoor on 2012-08-14
no errors but still no dice

```
ubuntu@ubuntu:~$ sudo dd if=/dev/null of=/dev/sda bs=446 count=1
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000802197 s, 0.0 kB/s
```

---

### Post by Bashing-om on 2012-08-14
Kickin:

 I am surprised that dd can not do what the other apps cud not either. DD is about as low as it gets. For the present I am stumped ... that trying to write to the MBR was my last possible solution I might have had.....

 As and when I have time tomorrow, will see what else I can come up with (if for nothing else for future reference!) Do not know what else to say but get ready to replace that disk.

[INDENT]CU tomorrow ?..............BDQ
[/INDENT]

---

### Post by Bashing-om on 2012-08-14
Kickin:

 I have had another thought... KillDisk! .. I have used it in the past and it is both informative and powerful ! But, it is not native to Ubuntu; You would have to download the .iso and burn to cd disk... here is the link if you want to devote more time and effort to this enterprise (it has been a learning experience, no ?)
[http://soft.udm4.com/downloading/active_kill_disk_ubuntu/](http://soft.udm4.com/downloading/active_kill_disk_ubuntu/)

There is lots of helps/and guides for this program on the net! 
It is a useful tool to have in your arsenal !

[INDENT]I hope this helps too <===BDQ

[/INDENT]

---

### Post by Kickinthedoor on 2012-08-15
I will try using kill disk when i get home from work tonigh. I have deff learned alot, i love messing around with computers and rooting cell phones. I may not know alot but to me, trying to get them running again is more fun to me then having a working computer. I love the challenge! Thanks for all the help, cheers mate...

---

### Post by Kickinthedoor on 2012-08-16
I havent had much time to try using kill disk. If i get no results im guna give up on this one and give her a viking funeral, thanks for all the help ladies and gents.

---

