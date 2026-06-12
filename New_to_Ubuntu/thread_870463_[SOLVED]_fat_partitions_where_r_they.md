---
title: "[SOLVED] fat partitions where r they"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by im new here on 2008-07-25
hi everybody
 im havin a veeeery big problem now i installed xubuntu but i dont know where r the fat partitions ? dosnt xubuntu support fat ? what can i do to work on my fat partitions 

thanks all

---

### Post by neurostu on 2008-07-25
when you say you don't see the fat partitions does that mean that they are not mounting automatically?  or they aren't detected at all?

I'm guessing that XFCE doesn't auto mount the partitions like gnome does.

search on google for "How to mount fat in ubuntu" and it will show you how to do it.

I'm pretty sure your partitions aren't being mounted but are present... They are probably SDB1 or HDB1 or something like that....

---

### Post by Bucky Ball on 2008-07-25
If you install gparted you will be able to see all partitions on your machine and what they are called. Go to a terminal and type;

> sudo gparted

If it is not installed already, you will get instructions on how to install. Once it is installed, repeat the instruction above and you will get a friendly GUI with all the info you need to get those drives mounted (sda or hda, names you need to mount).

Good Luck ... :)

---

### Post by arpanaut on 2008-07-25
could you please post the output of this command from a terminal.

```
sudo fdisk -l
```

That's a lower case L not the #1
enter your password (no it won't seem to register) hit enter anyway :)

Can you explain a little more what's going on?
How are you trying to locate your partitions?

---

### Post by im new here on 2008-07-26
sudo gparted 

it says command not supported so what now?  ? 

when i entered sudo fdisk -l  ... it gave me a list of partitions 

i still dont know where should i find my partitions and how can i explore them they r not in filesystem icon which is on the desktop and xubuntu is saying that there i 0 megabytes free space because its only using the ext3 partition

---

### Post by boblemur on 2008-07-26
my ubuntu does strange things with my fat usb stick....


it sees them as about 4 different partitions for some odd reason

but when i mount the entire thing /dev/sdb rarther than dev/sdb1 it will load the drive... its odd, im not sure if fat32 does this... but i know fat does...


gparted isnt installed by default

use:

```
sudo apt-get install gparted
```

then run 

```
sudo gparted
```

fdisk should show you the partition if its detected, but gparted is easier to read than fdisk

---

### Post by boblemur on 2008-07-26
also... 

if you want to view your partitions gparted is a very good tool, however it wont let you explore the partitions, this one of my small qualms with ubuntu, you dont seem to get a very good view of your disks and hard drive space etc, without looking in multiple places...

---

### Post by neurostu on 2008-07-26
Ok so GParted is gnome based right?  He is running XFCE so which can't be installed without installing all the gnome libraries...

I think...

to list your partitions open a terminal and type:
```

sudo fdisk -l 

```

---

### Post by drs305 on 2008-07-26
> **im new here said:**
> 
when i entered sudo fdisk -l  ... it gave me a list of partitions 

i still dont know where should i find my partitions and how can i explore them they r not in filesystem icon which is on the desktop and xubuntu is saying that there i 0 megabytes free space because its only using the ext3 partition

Your fat32 partitions should mount when you click on them. Here is a way to temporarily get access to your fat partition:

Make a mount point for it - I will use "**/media/fat32**" but you can name it anything you want:
```
sudo mkdir /media/fat32
```

Look at the results of the "fdisk -l" command and find the listing that describes one of the partitions as FAT 32. Here is an example of what you might see:
```
**/dev/sdc3**  1161 1245  682762+   b  W95 **FAT32**
```

Mount that partition to the folder you created above. Change the "/dev/sdc3" to whatever fdisk gave as your FAT32 partition. This command assumes you are user id 1000. If you aren't, type "id" in terminal to find your user id:
```
sudo mount -t vfat /dev/**sdc3** **/media/fat32** -o uid=1000
```

Use your file browser to navigate to "/media/fat32" to view the contents of that partition.

If you get an error saying the partition is already mounted run the "mount" command to see where it is and use your browser to inspect it.

If you are still having problems it would help if you posted the results of "sudo fdisk -l"

---

### Post by im new here on 2008-07-26
whats wrong here ?????

1-xfce menu dosnt open 

2-the partitions which i use in windows which r fat ? i cant see them in xubuntu where r they how colud i open them i only have file system on my desktop which contains the ext3 partition which i created while installing xubuntu and now i have 0 megabytes free space on the ext3 and i cant install anything cant i use my other disapearing partitions which have free space 
 
3- firefox's forward and backward buttons are not working 

4- when i type any thing in the google search box in firefox and press enter nothing happens as if i dont press enter 


pleeeeeeeeeeease help its driving me mad

---

### Post by halitech on 2008-07-26
have you checked your other threads you have open in regards to the same problem? Posting multiple threads about the same issues is not going to get you assistance any faster. Go check your other thread that you started earlier and see what you need to do to get help.

---

### Post by im new here on 2008-07-26
dear ....... 
i cant go back to see ure  name sorry 
 u know that backward button isnt working 
i made a new thread because there r other problems i didnt mention in the other thread but i added the problem in the previous caz maybe somebody could solve it when he sees the new problems 

please help me im in a serious problem here

---

### Post by overdrank on 2008-07-26
> **im new here said:**
> dear ....... 
i cant go back to see ure  name sorry 
 u know that backward button isnt working 
i made a new thread because there r other problems i didnt mention in the other thread but i added the problem in the previous caz maybe somebody could solve it when he sees the new problems 

please help me im in a serious problem here

Hi and I have merged the threads. If you are having that bad of issues, do you have another system you can use to respond to the info given you?

---

### Post by im new here on 2008-07-26
drs305 u said: If you are still having problems it would help if you posted the results of "sudo fdisk -l"


ok please tell me how to copy and paste the result from the terminal to firefox please

---

### Post by drs305 on 2008-07-26
> **im new here said:**
> drs305 u said: If you are still having problems it would help if you posted the results of "sudo fdisk -l"


ok please tell me how to copy and paste the result from the terminal to firefox please

You run the 'sudo fdisk -l' command in terminal. Then, unlike windows, to copy from terminal you highlight it with your mouse and select it with CTRL-**SHFT**-C (all three keys at once). Then in the post you are writing, click on the **#** symbol near the top right of the post. This will generate: code  /code  entries (I can't put the brackets due to formatting issues). Put the cursor between the two and paste using the standard CTRL-V.

However, as mentioned by *overdrank* your issues appear to be more general than just having a mount problem.

---

### Post by im new here on 2008-07-26
but there is no mouse in the terminal how could i minimize it to use the mouse its in fullscreen

---

### Post by neurostu on 2008-07-26
what you can do is:
```

sudo fdisk -l > file.txt

```
this will output the fdisk into the file named ** file.txt **

you can then upload this file to the forum if you can't figure out the copy and paste thing.

---

### Post by drs305 on 2008-07-26
> **im new here said:**
> but there is no mouse in the terminal how could i minimize it to use the mouse its in fullscreen

Are you not even able to boot into xubuntu? Do you just have a terminal? If you have only a terminal, you could run the command and direct the output into a file, then open a text editor and use you cursor to highlight and copy text (normal CTRL-C & CTRL-V). I don't know what xbuntu's default terminal text editor is, so substitute yours if you can't or don't want to use 'nano'.

```
sudo fdisk -l > fdisk.txt
nano fdisk.txt
```

However, if you can't boot normally into xbuntu then this line of attacking your problems is not going to easily solve anything. I'd start a new thread describing your main problem, which is not mounting the fat partitions.

Hope this helps.

---

### Post by im new here on 2008-07-26
hey u got it wrong

i can boot in xubuntu and im already in it 
but i open the terminal by pressing ctrl+shift+f1
not fromm applications caz applications wont give responce by pressing on it

---

### Post by im new here on 2008-07-26
now where can i find th fdisk.txt file to paste it for u 
i know its begun to be boring sorry for that drs

---

### Post by lordadi on 2008-07-26
Hi,


This is a gnome thing but if it works for xubuntu, you'll be able to take the easy way out of mounting your partitions. Right click on a panel > Add to panel > Disk mounter and drag it to your panel somewhere. After that, to mount a disk, left click on the icon in the disk mounter and select mount. After that, one of two things should happen: either a browser will open up and allow you to view the partition **OR** the volume icon will appear on your desktop.

If none of the above happens, then there is some other problem which I do not know how to tackle.


Cheers,


Lordadi.

---

### Post by im new here on 2008-07-26
there isnt any disk mounter 
thanks Lordadi.

---

### Post by lordadi on 2008-07-26
Then I'm stuck!

Lordadi.

---

### Post by im new here on 2008-07-26
but there is device mounter

---

### Post by drs305 on 2008-07-26
> **im new here said:**
> now where can i find th fdisk.txt file to paste it for u 
i know its begun to be boring sorry for that drs

You aren't boring me. It's just I don't know anything about xubuntu ... 

Since we didn't change any directories with the fdisk command followed by the text editor command, if your editor opens to the directory it was commanded from it should just be in whatever directory that is. In fact, assuming you haven't changed the directory/folder since you ran the command, you should be able to get it open with:
```
sudo nano fdisk.txt
```

If it can't find it or produces an error, you can use this command to find it:
```
sudo find / -type f -iname fdisk.txt
```

---

### Post by im new here on 2008-07-26
hey drs look what i got here 



Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf84b5805

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         969     7783461    b  W95 FAT32
/dev/sda2             970        4865    31294620    f  W95 Ext'd (LBA)
/dev/sda5             970        1942     7815591    b  W95 FAT32
/dev/sda6            1944        2917     7823623+   b  W95 FAT32
/dev/sda7            2918        3891     7823623+   b  W95 FAT32
/dev/sda8            3892        4620     5855661    b  W95 FAT32
/dev/sda9            4621        4846     1815313+  83  Linux
/dev/sda10           4847        4865      152586   82  Linux swap / Solaris


i guess this should help u 

lets do this

---

### Post by drs305 on 2008-07-26
I don't really understand what your system status is and probably can't help you there. I think you are running in terminal without getting to the desktop? 

I know your multiple threads were combined by one of the moderators but the thing you should concentrate on if the first paragraph is true is to solve that problem first. The moderators were not liking multiple threads being run simultaneously. Unfortunately the only one remaining discusses mounting vfat partitions. 

I will reply to mounting partitions in this thread but your more major issue should be started over, explaining what your situation is like you did in post #10.

So finally, it appears you have all sorts of fat partitions. You would normally be able to mount any of them with the following command (although normally you would just be able to click in your file manager to see the contents). Substitute /dev/sdc3 with /dev/sdaX, with X being any number 1,5,6,7, or 8. Don't forget to have the mount point already created (such as /media/fat32). If you are only able to see a terminal this will be of limited usefulness...

```
sudo mount -t vfat /dev/sda**5** /media/fat32 -o uid=1000
```

**Added:** If you have success with this and want to put entries into fstab so they automount on boot let us know.

---

### Post by im new here on 2008-07-26
drs thank u very much i just want to tell u that im not in a terminal im in xubuntu an i have colors here i understand what u mean but im not in a terminal i boot into xubuntu withh no prblems its just the problems i mentioned in #10

---

### Post by im new here on 2008-07-26
oh god i entered the command and nothing happens i dont know 
in windows u just open double click on ure partition here how is the partition opened ?????? thats my question where r my partitions c: f: e: etc ........ and how do i open them i have something called file system i guess here where i should find my partitions but where r they ????

---

### Post by drs305 on 2008-07-26
> **im new here said:**
> oh god i entered the command and nothing happens i dont know 
in windows u just open double click on ure partition here how is the partition opened ?????? thats my question where r my partitions c: f: e: etc ........ and how do i open them i have something called file system i guess here where i should find my partitions but where r they ????

Your partitions are normally mounted in /media or /mnt . Whichever one you listed in the command you just ran should be available for viewing in /media/fat32. You can see them when you open a file browser such as nautilus. 

I've sent you a Private Message.

---

### Post by im new here on 2008-07-26
drs heeeeeeeey we got somthing done here yea they exist in media now its how to use free space on those fat partitions caz i cant do anything due to ext3 is full

---

### Post by im new here on 2008-07-26
when will the time come when i could have everything running here and i could and im and chat i dont even have a messenger

---

### Post by drs305 on 2008-07-26
Okay, well, do you want to explore why your ext3 is full or do you know? If you don't know why it is full, have you deleted a lot of large files? Have you emptied your trash?

Here are some things you can do to free up some space:

Eliminate trash: This will find the Trash folders on your linux partition. Use the second command to navigate to those folders and delete the 'files' and 'info' folders. If you don't use nautilus, replace it with your file browser name. I included the normal location of user trash in the second command.

```
sudo find / -type d -iname Trash
gksu nautilus $HOME/.local/share/Trash
```

Eliminate archived packages which you can download again if you need to:
```
sudo aptitude clean
```

See what free space you have now:
```
sudo df -Th
```

Also, you seem to have a lot of fat32 partitions. If you don't need them all have you considered deleting one or more of them and expanding your ext3 partition?

---

### Post by im new here on 2008-07-26
y deleting them cant i use the fat partition as it is ?  ? ?

---

### Post by drs305 on 2008-07-26
> **im new here said:**
> y deleting them cant i use the fat partition as it is ?  ? ?

Yes you can although fat32 isn't a great system for linux to work with. Mostly because it doesn't support linux permissions - and in your case - mounting seems to be a problem ;-)

When you said you had no room on your linux partition and couldn't get anything done with it I thought you wanted to get some more space for that partition.

---

### Post by im new here on 2008-07-26
there is something i cant get here 
cant i work on the ext3 with the fat at the same time and use the fat just like the ext3 and copy files from this one to that one do u understand what i mean ?

---

### Post by im new here on 2008-07-26
when i tried sudo aptitude clean it told me that there is no space hahaha how y does it need space whilr im trying to free space ?

---

### Post by drs305 on 2008-07-26
> **im new here said:**
> there is something i cant get here 
cant i work on the ext3 with the fat at the same time and use the fat just like the ext3 and copy files from this one to that one do u understand what i mean ?

yes, you can do that. as long as you can see it and write to it. sometimes root can take over and you can't read or write to a fat32 partition - that is a permission problem. as long as that doesn't happen, have at it.

there are also some file size limitations with fat32 but i'd have to look it up to tell you what the limits are.

---

### Post by im new here on 2008-07-26
ok now how do i use the space of thoses fat drives
when i right click on file system and choose properties i get the th free space is 0 mb how does this happen ?

---

### Post by drs305 on 2008-07-26
> **im new here said:**
> ok now how do i use the space of thoses fat drives
when i right click on file system and choose properties i get the th free space is 0 mb how does this happen ?

I am not sure what you mean by 'file system'. The partitions are mounted on folders. If you mounted /dev/sda5 on /media/fat32, then you would right click on /media/fat32, select Properties, to see what space you have available and used.

Here are 2 commands to run.
To check partition size and usage:
```
sudo df -Th
```

To see which partitions are actually mounted, and where:
```
mount
```

---

### Post by im new here on 2008-07-26
file system is that icon on my desktop which i open explore the partitions through ? isnt it supposed to be there or should i have a program manager instaed ?

---

### Post by drs305 on 2008-07-26
> **im new here said:**
> file system is that icon on my desktop which i open explore the partitions through ? isnt it supposed to be there or should i have a program manager instaed ?

I'm just not familiar enough with xubuntu. Someone who runs it is going to have to step in. Best wishes...

---

### Post by im new here on 2008-07-27
somebody help me please the problem is not solved

---

### Post by JKyleOKC on 2008-07-27
If you right-click anywhere on the xubuntu desktop, does a menu of applications appear? It does on all four of my xubuntu systems. If it does for you, you can select the "Accessories" item to get a pop-out menu that should show terminal. This will get you the terminal program in a window, so that you can easily copy from it and paste into FireFox for posting.

The ctrl-alt-F1 terminal is the same one that's running your desktop, so using it can easily mess up what happens on the desktop.

If you get the application menu as I described above, you can select the system item on it to get access to all of the system configuration tools. This will help you install additional software if you need to. Right-clicking on a panel (the toolbars at the top and bottom of the screen) will give you a menu of options for adding items to the panel, which I've found to be the equivalent of putting shortcuts on a Windows desktop.

If you don't get the application menu I'd suspect that something is wrong with your xubuntu installation, and suggest re-installing it from scratch. 

On all of my installations, the FAT32 partitions are NOT mounted by default; I have to explicitly mount them in order to see their content. Before we try to do that, though, let's get you a little more comfortable with xubuntu's interface. It's not like either unbuntu or kubuntu, so many of the suggestions from users of those systems can just add to the confusion!

---

### Post by im new here on 2008-07-28
thanks everyone nothing worked so  i formated and reinstalled

---

