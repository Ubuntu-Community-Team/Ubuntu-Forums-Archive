---
title: "shrink the main drive"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by mandar2 on 2014-04-09
Hello all,

I am completely newbie to Ubuntu OS. I turned to this OS because of a disaster with Windows 8. I had so much fade up with it that doing the installation of Ubuntu i chose replace Win8 and now i have 978.....GB of single drive....


Please tell me how can i make partitions? Will i have to install it again?:( :confused:

---

### Post by Mark Phelps on 2014-04-09
> Will i have to install it again?Install what? Win8 or Ubuntu?

> Please tell me how can i make partitions?Since you said you replaced Win8 with Ubuntu, why do you NOW see the need to change the partitioning on the drive?

---

### Post by m-dw on 2014-04-09
So you seem to be saying that you have done a default Ubuntu install on a PC that used to have Windows on it.  Firstly, welcome to the world of real operating systems.  It's a bold step but rewarding, if a little addictive.

If you've installed Ubuntu across your entire hard disk you have effectively lost your windows installation, and all the data you had on it.  There are methods to recover any data that's not been overwritten, but they're best left to the data recovery experts.  Since you didn't ask about that, I will assume that's not your problem.

In the long run, it is best to put /home onto a separate partition because it means you can do a fresh install without losing your application settings and personal data.  How you partition is personal choice and depends if you have a shared data area, whether the PC is also a server and so on.

The good news is that there ARE tools that can resize partitions, and they are on the Ubuntu install DVD.  The bad news is that you cannot safely resize root (the top level directory of the filesystem also referred to as /) while it is in use. And since root partition is the whole hard disk you'll need to run the tools from the Ubuntu install CD.

In all honesty though if you only installed a few days ago and haven't actually used it, you'd be better off reinstalling as you won't have that much data accumulated yet.  Might also be worth waiting until 14.04 comes out next week.

Read the install guide at [https://help.ubuntu.com/13.10/installation-guide/amd64/index.html](https://help.ubuntu.com/13.10/installation-guide/amd64/index.html) particularly Section 6 and Appendix C.It's also a good idea to make all the non-root partitions extended (i.e. virtual) because it gives you more flexibility later.  Good luck with it.

---

### Post by ajgreeny on 2014-04-09
No you will not need to install the OS again, though as m-dw says it may be the quickest way to get to where you want, rather than trying to edit and move partitions, and the files and folders within those partitions, which can be a long and tedious operation..

Tell us what you  would prefer and whether you just want to keep your data files separate  from the OS or are considering something more complicated.  As a new  user you may not have even thought about any details of what you want, or  even what is possible, but many users, including myself, like a separate  /home partition; others leave /home within the root partition but have a  separate /data partition, both of which can be set up post  installation, but both of which will need a live DVD or USB.  Using that  you can run gparted to manage the current partitions and resize what  you have, make new partitions, and then copy over the files and data  that will from then on belong in another partition to the present.

---

### Post by mandar2 on 2014-04-10
@Ajgreeny: Thanks for the reply. I have the USB through which i installed 12.04 LTS and want to be working with this OS. I can use the same PD i suppose tell me how can i run partition tool and divide the root drive in the way as said below:

Firstly yes to be clear about it now i have 925gigs of home drive and no Data drive... so what i want to do is to make data drives of 250 250 250 by leaving behind a seperate drive of Ubuntu OS root drive just like C:/ of windows analogy.

now.... i prefer not to reinstall because i have transfered sufficient data which was necessary for my current work.

Thanks all, please have some mercy i don't want to go back to Windows, i just need some time to get used to Ubuntu and the terminologies!!!

---

### Post by sotiris2 on 2014-04-10
Welcome to the fold mandar2. 
What I would consider necessary for a 'good' install of Ubuntu would require:
[LIST=1]
[*] A root/system partition which will house the OS's files and your installed programs. Mine uses 12GB but I would recommend 30-40 just to have headroom.
[*] A home partition which will contain the users' personal files as well as configurations of programs for each user i.e. Firefox's preferences bookmarks etc.
[*] A swap partition, more important if you have few RAM, less if you have a lots. If it is a laptop and you want suspend to RAM to be possible it must be at least as big as your RAM.
[/LIST]

May I in inquire why you would want two data partitions ? I do have two different data partitions but this is because I dual boot and i have a 'data' partition for Ubuntu (my /home actually) and an extra NTFS partition for Win7 and sharing between Ubuntu/Win. Otherwise I would have just one since I 've had the problem of having enough free space to download something I wanted , but the space being spread in quite a few partitions. File juggling was not fun. Nevertheless if you want two data partitions it's as easy to do. 

**EXECUTION**

Three parts.

[LIST=1]
[*]Making the partitions
[*]Copying files to the new partitions.
[*]Configuring Ubuntu to use the files from the new partitions.
[/LIST]

**Part One**
Boot from a live cd. Select 'Try Ubuntu'. 
Open up Gparted.
Right click on your partition, select 'Information'
Write down the **UUID** (not on a file in the desktop because it won't 'stay')
Close the information window and right click on the partition again, this time pick '**Resize/Move'**
Type in a new size (it will be the root/system partition I described above). Press '**Resize/Move**'.
Nothing is happening yet so press the green 'checkmark'  on Gparted's toolbar. Press apply.
Make sure there is no error. Then right click on the new shrunk partition and select 'information'.
UUID should not have changed. If so continue, otherwise get to this forum by using firefox, _**DO NOT REBOOT**_.

You should have 'unallocated' space to the right of your partition. Right click on it. Select NEW.
Make sure it is created as an **Extended** partition and make take up ALL the free space. This is because Extended partitions can contain more partitions inside them helping us past the 4 partition limit. 
Right click on the Extended partition, select new. Pick *ext4* as filesystem and give as much space as you want your home partition to be, give it a label if you like (makes no difference). You will see it can only be a **'logical'** partition. 
Repeat the process to make more partitions as you 've decided, use ext4 for data partitions , linux-swap for swap partition. 
After you are satisfied click on the green checkmark again. Select apply, let it work , confirm all ok. 
Right click on each data partition, go to information and write down their UUID's, don't mix em up. **ALSO NOTE THEIR name as in sda1 sda2 etc**
You don't need to get swap's UUID. 

Now Reboot to your normal system.

---

### Post by sotiris2 on 2014-04-10
Part Two

We are going to use the terminal to copy your files to your new home partition. If you have decided to have more data partitions and move some data there I suggest you do so after you are done with all 3 parts of my guide, copying them from the new home partition wherever you wish to. This in order to avoid making my instructions more complicated.

Press Ctrl+Alt+T . You will get a black and white window you can write commands in. More usefully you can paste commands in it via middle mouse button (aka mouse wheel), which makes it easier to do things correctly.

Start by typing in

```
whoami
```

It will respond. Lets pretend it responds [COLOR=#00ff00]*user*[/COLOR]. From now on wherever you see *user* in my post , even in commands, you will replace it with whatever you got from the whoami command. In order to do so to commands simply copy paste them to gedit (a notepad like program) do the replacement there and then copy paste the corrected version to the terminal. 

Moving on type 

```
sudo mkdir /mnt/new
```

You will see it asking for a password, type it normally, it will not show you any feedback that you are writing , such as *** or ### but it is accepting your input. Press enter. This will always happen when you first use a sudo command in a terminal. 

Now look at your notes and see the name of the partition you want to copy home to. It will be something like sda5 or sda3, in short sda and a number. Adjust the following command and run it.(replace # with the number of the partition), there is one space after the number. 

```
 sudo mount /dev/[COLOR=#00ff00]sda#[/COLOR] /mnt/new
```

If it works it will show nothing. If so proceed

```
sudo cp -rp /home/[COLOR=#00ff00]*user*[/COLOR] /mnt/new
```

Again if it completes correctly it will not show you anything. Remember to replace [COLOR=#00ff00]*user*[/COLOR]

Then again.
```
sudo chown -R [COLOR=#00ff00]*user*[/COLOR] /mnt/new/[COLOR=#00ff00]*user*[/COLOR]
```

Again if everything works you should get no output. Replace [COLOR=#00ff00]*user*[/COLOR] in command again. We 're done copying. 
The following are checks.

```
ls -l /mnt/new
```
You should get a line like this:
```
drwrx---- 64 *[COLOR=#00ff00]user[/COLOR] [COLOR=#00ff00]user[/COLOR]* 4096 month day year/hour [COLOR=#00ff00]*user*[/COLOR]
```
The only thing you care about is to have *user* appear three times, if root appears in front instead of *user* then re-run the command that includes **chown**.

Then
[code]ls -la /mnt/new/[COLOR=#00ff00]*user*[/COLOR][code]
You should get a big list with entries like the previous command, again you should see *user* and not root. Also you should have some folders (right most column) beginning with a dot , such as .local If you have none like this it's possible a mistake has happened and do not continue with part 3

---

### Post by Impavidus on 2014-04-10
In part 1, note that you already have an extended partition (/dev/sda2). Instead of creating a new extended partition you should expand the existing one.

There is also a wiki page describing how to move your home directory to a separate partition: [URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]https://help.ubuntu.com/community/Partitioning/Home/Moving
[/URL]
Referring to existing documentation instead of writing new saves typing and ensures quality.

---

### Post by sotiris2 on 2014-04-10
Part 3 

We have created the newpartitions , copied your home folder to the new home partition and are now ready to configure Ubuntu to use it. However it's important to be sure that part 2 was done correctly and that you know the correct UUID for the partition you copied your home folder to. Run Gparted to check again if you wish. 

Also at no point beyond here should you REBOOT unless the instructions specifically say so. It's could lead you to a non bootable system.

Let's start. 

```
sudo cp /etc/fstab /etc/fstabold
```

Making a backup.

```
gksudo gedit /etc/fstab
```

A window will pop-up asking for your password, and then gedit will open with a file. Do not change anything and go to the last line. There write:

```
UUID=[COLOR=#00ff00]XXXXXXXX-XXX-XXXX-XXXX-XXXXXXXXXXXX[/COLOR] /home           ext4    defaults        0       2
```

Replace  XXXXXXXX-XXX-XXXX-XXXX-XXXXXXXXXXXX with the actual UUID.

If you have mad a swap partition make another line with 

```
UUID=[COLOR=#00ff00]UUUUUUUU-UUUU-UUUU-UUUU-UUUUUUUUUUUU[/COLOR] none            swap    sw              0       0
```

Replace  UUUUUUUU-UUUU-UUUU-UUUU-UUUUUUUUUUUU with the swap's partition UUID (I mistakenly told you in part one you don't need to note it down sorry).

Save the file and exit.

Now its time to delete the existing home folder in the system partition. Do

```
sudo rm -R /home/[COLOR=#00ff00]*user*[/COLOR]
``` 
Replace *user* again but please doublecheck it's correct before pressing enter.
Now you can reboot. If something went bad you will get a screen telling you that the /home partition is not ready, and to press S to skip or M to mount manually. Press M. You will get a fullscreen terminal. Just write:

```
cp /etc/fstabold /etc/fstab
```
To copy back our backup file. 
And then 
```
reboot now
``` 
If it doesn't reboot, reboot it via power cycle. It should get you back to before starting part 3 with a usable system so you can try it again or ask for help in the forum.

---

### Post by mandar2 on 2014-04-10
Hi Sotiris2, Impavidus,

 thanks for your input....


Hope i succeed 

> May I in inquire why you would want two data partitions ?

Answer: I have to install Win7 for implementation of other tools which run only on windows.

Currently i have Ubuntu 12.04 LTS only. Once i succeed in making partitions i l install Win7 on one of the data partitions.

Thanks again, I hope you guys reply again if i get myself into problems.

Adios

---

### Post by sotiris2 on 2014-04-10
Wait wait wait. I think that Win7 will not install in logical partitions (partitions inside an extented one). So you should probably leave space for the win partitions outside the EXTENTED one. You will hit the partition limit though since you have ubuntu root as , an extented and win 7 creates 2 partitions.

EDIT: You may actually be able to install windows to a logical partition but it's boot files need to be on a primary partition which unfortunately is something i can't help with.

---

### Post by mandar2 on 2014-04-10
So end effect is that in order to have a primary partition i have to install Win7 first and then install Ubuntu to enjoy benefits from both sides.... RIGHT???:confused:

---

### Post by sotiris2 on 2014-04-11
It's not really much of an order problem. Just do not make the extented partition occupy the whole disk but only as much as you want to use for data partitions (both your /home partitions and maybe an ntfs partition to share data between windows/ubuntu like D:\ ). And leave as much unallocated space as you want windows to use for their C:\ partition (They will also create a smaller partition 70-100 MB ). You want have any problems, just if you need to make any more partitions you will have to shrink the partitions inside the extented one and create it there as a logical one.

---

### Post by Impavidus on 2014-04-11
It is said that Windows wants to install in a pre-existing primary ntfs partition with boot flag (or two of them, one for the recovery partition), if not available it will wipe the entire drive. Windows is rather selfish. So if you want to install Win7, use gparted to create the partitions and then install it. Format the ntfs partitions as part of the Windows installation nonetheless. Then repair the boot loader with [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair).

---

### Post by mandar2 on 2014-05-02
Hi guys,


Any how i ended up solving the issue by installing everything again. I started windows 7 installation, whilst i couldn't get 4 seperate drives for my requirement. Anyway i some space as raw and when i was done installing Win7 i made partitions thro' disk management. So i had kept 75gigs for UB and then i installed UB again!

While installing UB the first time i had just made a guess that it would have something like win7 and 8 to shrink d drive from a larger volume to smaller. But itsn't tht simple and god knows why there are so many ways and methods and types and........ to shrink/extended drives!

Cheers!

have a nice day!

---

### Post by LastDino on 2014-05-02
> **mandar2 said:**
> Hi guys,


  But itsn't tht simple and god knows why there are so many ways and methods and types and........ to shrink/extended drives!



Because this is the Linux world and here different people have different needs and ways to solve/approach the same problem. Btw, congrats on successfully managing to dual boot!

---

### Post by Mark Phelps on 2014-05-02
> why there are so many ways and methods and types and........ to shrink/extended drives!

You're not shrinking or extending "drives"; those are "partitions".  Drives are physical hardware devices and can be neither shrunk nor enlarged. Partitions are chunks of space allocated in drives.

As to why so many ways -- simple - there are a number of different apps and commands that can do the same thing.  Same is true in both Linux and Windows.

But ... and this is IMPORTANT -- you should always use Linux apps/commands to shrink/extend Linux filesystem partitions, and use Windows apps/commands to shrink/extend Windows filesystem partitions.

---

