---
title: "Unmet dependencies"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by fairbrother89 on 2014-03-09
Please help me.
I use Ubuntu for everything and now it wont work.
I have a dual boot system and am in my Windows 7 partition at the moment.
I always automatically install all updates in Ubuntu without checking what they are.
I have never had a problem till now.
On this occasion 3 packages did not install.
i have a red stop sign in my toolbar.
it reads as follows;

"a[I]n error has occurred. run package manager from the right click menu or apt - get in a terminal to see what is wrong. the error message was;
"error. brokencount > 0 "  this usually means you have unmet dependencies. "[/I]

can anyone instruct me. step by step. what to do. remembering that i am not technically minded. please dont assume i even know what a terminal is.

i dont want to lose my ubuntu partition. this would be a disaster.

thanks
phil

---

### Post by Vladlenin5000 on 2014-03-09
Please post the results (messages) from the following commands:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Impavidus on 2014-03-09
> **fairbrother89 said:**
> please dont assume i even know what a terminal is.Is that a somewhat roundabout way of telling that you don't know what a terminal is? It's where you enter commands and where the system replies to you. You can open one with ctrl+alt+t and paste Vladlenin5000's commands in it. It will ask for your password. Type your normal login password. It won't give you any visual feedback, but just type the password and hit enter.

---

### Post by Vladlenin5000 on 2014-03-09
> **Impavidus said:**
> Is that a somewhat roundabout way of telling that you don't know what a terminal is? It's where you enter commands and where the system replies to you. You can open one with ctrl+alt+t and paste Vladlenin5000's commands in it. It will ask for your password. Type your normal login password. It won't give you any visual feedback, but just type the password and hit enter.


Oh, I'm sure he already knows that, he had to use it a few times back in 2010, just take a quick look at his other thread.

---

### Post by ibjsb4 on 2014-03-09
And we all remember the commands we used in 2010 :)

Update and upgrade is good, but also a couple of maintenance commands.
```

sudo dpkg --configure -a
sudo apt-get -f install
```

Could fix dependencies or broke packages.

---

### Post by fairbrother89 on 2014-03-09
thanks guys. yrs sorry i'm a complete numpty with all this. i cant remember what i did back in 2010. i could always check back of course as you have. ;)  i have managed to get chrome working in ubuntu even with this problem by opening it b4 the no entry sign appears after logging in. i love ubuntu and continually recommend it, though its hard work weening people off the idea that if its free its no good. they just cant fathom that its actually better.

ok i have put the first 2 commands into a terminal with the following results;

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by ibjsb4 on 2014-03-09
Open a terminal and enter:

```
sudo dpkg --configure -a
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by fairbrother89 on 2014-03-10
thanks. did that with the following result;

phil@phil-PDSG4:~$ sudo dpkg --configure -a
[sudo] password for phil: 
sudo: unable to open /var/lib/sudo/phil/1: No space left on device
dpkg: error: failed to open '/var/lib/dpkg/status' for writing status database: No space left on device


frustrating as it would appear this is just some translation package that i'm never going to use anyway. :(
not sure what no space on device means. i have plenty of hd space.

---

### Post by Vladlenin5000 on 2014-03-10
Please run
```
df -i
```
 I suspect it has something to do with inodes and not the actual free space on the drive.

---

### Post by ibjsb4 on 2014-03-10
Could be WUBI

```
df -h
```

---

### Post by fairbrother89 on 2014-03-10
```
Filesystem      Inodes   IUsed  IFree IUse% Mounted on
/dev/sda5      1177344 1177344      0  100% /
udev            214824     474 214350    1% /dev
tmpfs           218469     390 218079    1% /run
none            218469       3 218466    1% /run/lock
none            218469      11 218458    1% /run/shm
phil@phil-PDSG4:~$

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        18G   14G  3.4G  81% /
udev           1000M  4.0K 1000M   1% /dev
tmpfs           403M  744K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  4.2M 1002M   1% /run/shm

```
hope this helps. many thanks again. i am able to run chrome and surf the net with this problem. so long as i open it before the package tries to instal.
however i am unable to save anything in any other application.

---

### Post by ibjsb4 on 2014-03-10
And its inodes

Back to you V_5000

---

### Post by Impavidus on 2014-03-10
Could be old kernel headers. Check the contents of /usr/src/:```
ls /usr/src/
```It may require some cleanup.

Your partition is not very large and you don't have a lot of inodes, but as I use about 400000 of them in my root partition it should be doable with 1.1 million.

---

### Post by fairbrother89 on 2014-03-11
linux-headers-3.2.0-29              linux-headers-3.2.0-45-generic-pae
linux-headers-3.2.0-29-generic      linux-headers-3.2.0-49
linux-headers-3.2.0-29-generic-pae  linux-headers-3.2.0-49-generic
linux-headers-3.2.0-30              linux-headers-3.2.0-49-generic-pae
linux-headers-3.2.0-30-generic      linux-headers-3.2.0-51
linux-headers-3.2.0-30-generic-pae  linux-headers-3.2.0-51-generic
linux-headers-3.2.0-31              linux-headers-3.2.0-51-generic-pae
linux-headers-3.2.0-31-generic      linux-headers-3.2.0-53
linux-headers-3.2.0-31-generic-pae  linux-headers-3.2.0-53-generic
linux-headers-3.2.0-32              linux-headers-3.2.0-53-generic-pae
linux-headers-3.2.0-32-generic      linux-headers-3.2.0-54
linux-headers-3.2.0-32-generic-pae  linux-headers-3.2.0-54-generic
linux-headers-3.2.0-34              linux-headers-3.2.0-54-generic-pae
linux-headers-3.2.0-34-generic      linux-headers-3.2.0-55
linux-headers-3.2.0-34-generic-pae  linux-headers-3.2.0-55-generic
linux-headers-3.2.0-35              linux-headers-3.2.0-55-generic-pae
linux-headers-3.2.0-35-generic      linux-headers-3.2.0-56
linux-headers-3.2.0-35-generic-pae  linux-headers-3.2.0-56-generic
linux-headers-3.2.0-36              linux-headers-3.2.0-56-generic-pae
linux-headers-3.2.0-36-generic      linux-headers-3.2.0-57
linux-headers-3.2.0-36-generic-pae  linux-headers-3.2.0-57-generic
linux-headers-3.2.0-37              linux-headers-3.2.0-57-generic-pae
linux-headers-3.2.0-37-generic      linux-headers-3.2.0-58
linux-headers-3.2.0-37-generic-pae  linux-headers-3.2.0-58-generic
linux-headers-3.2.0-38              linux-headers-3.2.0-58-generic-pae
linux-headers-3.2.0-38-generic      linux-headers-3.2.0-59
linux-headers-3.2.0-38-generic-pae  linux-headers-3.2.0-59-generic
linux-headers-3.2.0-39              linux-headers-3.2.0-59-generic-pae
linux-headers-3.2.0-39-generic      linux-headers-3.2.0-60


how to i clean up ? is there anything i can delete ? how can i increase this capacity ? 
thanks for your input :D

---

### Post by fairbrother89 on 2014-03-11
[B]
It is possible to use up a device's set of inodes. When this happens, new files cannot be created on the device, even though there may be free space available. For example, a mail server may have many small files that don't fill up the disk, but use many inodes to point to the numerous files.[/B]

i have plenty of image files that i could delete. but will this free up i-nodes. i feel i need more guidance here if anyone can help i would very much appreciate it. ;) thanks.
phil.

---

### Post by ian-weisser on 2014-03-11
> **fairbrother89 said:**
> linux-headers-3.2.0-29              linux-headers-3.2.0-45-generic-pae
linux-headers-3.2.0-29-generic      linux-headers-3.2.0-49
linux-headers-3.2.0-29-generic-pae  linux-headers-3.2.0-49-generic
[...]
linux-headers-3.2.0-38-generic      linux-headers-3.2.0-59
linux-headers-3.2.0-38-generic-pae  linux-headers-3.2.0-59-generic
linux-headers-3.2.0-39              linux-headers-3.2.0-59-generic-pae
linux-headers-3.2.0-39-generic      linux-headers-3.2.0-60


how to i clean up ?

You use the package manager to remove the old ones. Each item on that list is a package.
Example:
```
sudo apt-get remove linux-headers-3.2.0-29
```
Do not remove the current kernel's headers, if you use them.

---

### Post by fairbrother89 on 2014-03-11
> **ian-weisser said:**
> You use the package manager to remove the old ones. Each item on that list is a package.
Example:
```
sudo apt-get remove linux-headers-3.2.0-29
```
Do not remove the current kernel's headers, if you use them.

thanks. i do not know what a header is. therefore i do not know whether i use the current headers.
is the package manager the same thing as the terminal ?
which ones would you remove using the code you mention if it were your installation.
many thanks and please excuse my ignorance.

---

### Post by ibjsb4 on 2014-03-11
I like this one

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by ian-weisser on 2014-03-11
> **fairbrother89 said:**
> thanks. i do not know what a header is.
If you don't know, then go ahead and remove all of them that you are not using.
As newb85 points out below, DO NOT remove the currently running kernel.
Use the command *uname *to find out the current version.


 > **fairbrother89 said:**
> is the package manager the same thing as the terminal ?
The package manager is an application that manages your software packages.
In Ubuntu, it's the application called 'apt'
Software Center is a fancy frontend that uses apt under the hood.
Synaptic is a different fancy frontend that also uses apt under the hood.
The terminal's apt-get command is an easy and predictable way to use apt. It has the added benefits of availability across all versions of Ubuntu, similar appearance on all releases of Ubuntu, few changes across releases, and clear warning and error messages.

So in this forum, most package management instructions use the terminal. Everyone has a terminal, and the commands are much clearer than 'scroll down to the plus-symbol (maybe yours looks different, I don't know how far you need to scroll)' type of GUI-based instructions.

It doesn't matter which package manager frontend you use to uninstall the linux-header-* packages. Use whatever you are comfortable with.

---

### Post by newb85 on 2014-03-11
It's usually best to keep p the latest kernel and the previous one as a backup. Keep all the packages numbered [s]3.2.0-38 or 3.2.0-39[/s] 3.2.0-59 or 3.2.0-60.  You shouldn't need the rest.

---

### Post by Impavidus on 2014-03-11
Correction, keep the packages with numbers 3.2.0-59 and 3.2.0-60. Remove all packages with version numbers 3.2.0-29 to 3.2.0-58.

It's difficult to see, but the posted output has two columns.

---

### Post by newb85 on 2014-03-11
Oops!  You're right.  The quoted output didn't preserve the columns at all.  Post corrected.

---

### Post by fairbrother89 on 2014-03-13
thanks a lot guys.

so if i type;
**sudo apt-get remove linux-headers-3.2.0-58**

that will free up some inodes so the uninstalled package will install and i will get my ubuntu system back ??

do i need to uninstall each header/kernel individually or can i for example input;

remove linux headers 3.2.0-45-58    or something similar to remove a whole slew of them ?

and presumably its good housekeeping to remove old headers on a regular basis. is there a way of finding out how many old kernels i have installed.
thanks very much again. apolgies for delay in replying. ;)

---

### Post by JKyleOKC on 2014-03-13
> **fairbrother89 said:**
> do i need to uninstall each header/kernel individually or can i for example input;

remove linux headers 3.2.0-45-58    or something similar to remove a whole slew of them ?You can type, or better yet copy and paste, "sudo apt-get remove linux-headers-3.2.0-5*" to get rid of 10 such files at once, then repeat it with "4" in place of "5" to get a few more. Since the current one is 3.2.0-60 it won't be affected.

The header files are necessary for processing updates in some, but not all, cases. You probably also have the "image" files for each of those versions, and they also can be deleted to free up more inodes.

In general, each file uses at least one inode as part of its internal bookkeeping; the number of inodes in a filesystem is fixed when the system is first created, and cannot be changed without reformatting the partition -- which would totally wipe out all of your files. Once you're out of inodes, nothing else can be written to that partition but there's no problem in reading or running what is already there.

There's a program called "Ubuntu Tweak" that's included in the Software Center which you can use to do the housekeeping more easily than we're showing you in this thread. However you cannot download or install it until you've made enough inodes available to do so! It's a sort of "chicken or egg" situation...

---

### Post by fairbrother89 on 2014-03-14
ok thanks. b4 i do anything i like to make sure i understand as i dont wish to jeapordise my installation

the placing of the asterisk after 5 will remove 50 through 59. is that correct ??

i was advised earlier to keep 59, which is why i ask.
can i safely remove 1* 2* 3* and 4* in the same manner ?

many thanks once more.
phil

---

### Post by Impavidus on 2014-03-14
the 5* will remove 59 too. It's generally best to keep one old kernel, but it shouldn't really harm in this case. The same way 1*, 2*, 3* and 4* will remove the others, except that you don't have any 1* header packages installed.

---

### Post by JKyleOKC on 2014-03-14
> **fairbrother89 said:**
> the placing of the asterisk after 5 will remove 50 through 59. is that correct ??Yes; the * will match all following characters, not just the 0-9. Your earlier list showed additional characters in the package names. To match just a single character, use "?" instead of "*".

I realized that it would also take out 59, but it has been several days since 60 replaced 59 and I've not seen any reports of problems with it so felt that it would be safe to remove it. Actually, for the "header" files it would always be safe since they are needed only during the install process, and then only when you have certain additional modules needed (in my case, for an Nvidia video card and for VirtualBox, a virtualization package; you might not even need them at all but it's best to have them on hand anyway). However you probably also have the "image" files for each of those versions, and the advice to keep the next-to-last DOES apply to them until you are sure the newest version is working properly.

If you install the "Ubuntu Tweak" program I mentioned earlier, it will provide a set of checkboxes allowing you to decide individually for each program that it offers to remove. That's much easier, and much safer. I run it after each major update, and any time I suspect a system is getting crowded.

---

### Post by newb85 on 2014-03-14
I don't think my system even installed the headers automatically. Every time the kernel upgrades, I have to manually install the headers for it to get VB working again.

---

### Post by JKyleOKC on 2014-03-14
> **newb85 said:**
> I don't think my system even installed the headers automatically. Every time the kernel upgrades, I have to manually install the headers for it to get VB working again.Install the "linux-headers-generic" package, and you will then get the latest header automagically. This package is always updated to depend upon the latest header file. You can install it from the Software Center, or by using "sudo apt-get install linux-headers-generic" from the command line.

---

### Post by mörgæs on 2014-03-15
In case someone is watching, thinking that Buntu is too complicated to maintain:

In 13.10 and beyond the command **sudo apt-get autoremove** is all that's needed to remove old kernels and headers.

---

### Post by fairbrother89 on 2014-03-16
apologies for delay in replying. i have been using my windows partition lately.
however this morning i went to my ubuntu partition and now i can't even log in.
previously i had been able to log in and open a browser if i clicked the icon before the no entry sign appeared.
then i was unable to do even this. hence my time in windows.
now i cannot get beyond the password screen. i can not open a guest session either.
i cannot open a terminal without logging in.
i have the option of safe mode. or previous linux versions.
i will try one of these next time.
i will then open a terminal and enter;
sudo apt-get remove linux-headers-3.2.0-4*
i will then try to log in once more.
thanks again.

---

### Post by mörgæs on 2014-03-16
Now you have been struggling with this for a week. Did you consider taking a backup and doing a fresh install of 13.10?

---

### Post by fairbrother89 on 2014-03-16
no, i wouldnt know how to do that.
i've not done anything yet, apart from retrieving the information above from the system
now i'm, for some reason locked out completely. i can only hope safe mode works . 
although that presumably needs a password as well. and as i said above, i enter the password and it just goes back to the password screen.
by the way, on boot up my system is 3.2.0-59.   not 60.
i do have the option of previous linux versions. so maybe that will work.
the main thing i dont want to lose are my bookmarks in chrome.

---

### Post by mörgæs on 2014-03-16
I don't know about Chrome, but in Chromium your bookmarks are in the file .config/chromium/Default/Bookmarks under the /home directory. You need to enable 'view hidden files' first.

You could take a look and see if the same file exists for Chrome.

---

### Post by Impavidus on 2014-03-16
You're booting 3.2.0-59 because the installation of 3.2.0-60 failed.

From the grub menu, boot into recovery mode. You'll get a menu. Select "Drop to root shell prompt". Then remount the file system read-write:```
mount   -o   rw,remount   /
```(I exaggerated the number of spaces. You only need one at each location, although more doesn't harm.)
It's the same as explained [here]("http://www.psychocats.net/ubuntu/resetpassword"), with screenshots, up to and including the remount command. No passwords involved.

Next remove some old packages. apt-get may not work, because it will only uninstall the old packages after the package system has been fixed, but apt-get can only fix it after some old packages have been uninstalled. I think calling dpkg directly should work:```

dpkg   --purge   linux-headers-3.2.0-3{0,1,2,4,5}{,-generic,-generic-pae}
apt-get   -f   install

```(I don't think dpkg does any expression matching here, so that's why the braces construct is there.)
This should fix your package manager and install the dependencies you need. Then cleanup by removing all remaining header packages and kernels up to (and including) version 3.2.0-58

---

### Post by fairbrother89 on 2014-03-17
phew. ok thankyou impavidus.
i'm currently in windows so i cannot C/P your commands.
i have jotted them down and will now write them out from my notes.
this is to make sure i do not make an error .
 1  i coose recovery mode
2  i chosse drop to shell prompt
3 i enter         mount **space** -o **space** rw,remount **space** /           
question; is that an o or an 0. a lower case o looks like 

question.... where do i enter the next command, will i need to open a terminal ?

4 next i enter (where ?)

dpkg **space** --purge **space** linux-headers-3.2.0-3{0,1,2,3,4,5}{,-generic,-generic-pae}
apt-get** space** --f **space **install


what should happen then please ????



thanks again. i dont want to make an error here.

---

### Post by newb85 on 2014-03-17
Yes, that's a lowercase o.  You will still be dropped to a full screen terminal, which is where you enter the next commands.  Those will clear up your package management issues. You can then proceed to upgrade the kernel, which you can do in that same terminal, or you can just wait for the software updater to do it.

---

### Post by Impavidus on 2014-03-17
Almost correct. The **apt-get -f install** command has a single dash preceding the f, not a double dash.

The dpkg ... command will remove some old packages, making some inodes available. The apt-get ... command will fix your dependencies by installing some packages. Then do the cleanup by removing all remaining old kernels and headers. You can do it from the same root shell, but you can also reboot and do it in the GUI, which will hopefully work again. To reboot, use the **reboot** command.

---

### Post by fairbrother89 on 2014-03-18
ok thanks guys i will try this soon. with fear and trepidation. hope to be back soon with a success report.

---

### Post by jaspreet on 2014-03-18
If you are used to hibernating your windows and then booting into Ubuntu, you might like to shutdown the windows first and then boot into Ubuntu. Windows would leave the disk in dirty state if not performed a graceful shutdown.

---

### Post by fairbrother89 on 2014-03-18
sorry guys i'm still not altogether sure what is supposed to happen after i enter
apt-get -f install

i know from experience that i'm going to be staring at some screen not knowing what to do next.

for instance taking the above instruction you have kindly provided. what does ;
**you can reboot using the reboot command** mean please.

will i end up still in a terminal type screen with a flashing cursor. and then i type **reboot.**

i'm guessing nothing will happen automatically.

how long is this going to take ??

sorry but i'm nervous about attempting this procedure.
its like sending a normal person up to the space station and telling them how to do a space walk.
i'm no astronaut.

---

### Post by Impavidus on 2014-03-18
**apt-get -f install** will try and determine which packages should have been installed but have not been completey installed. It will then install those packages. It will only ask for confirmation. After it has run you'll get your command prompt back. It shouldn't take to long. A couple of seconds, a minute maybe. Just watch the output scroll by. To get out of recovery mode (and into the latest kernel, if apt-get installed a new one), you can reboot. You can instruct the computer to reboot by issuing the **reboot** command. Sounds logical, doesn't it?

Many people we send up to the space station and tell to do a spacewalk have never done that before either. If you do something new, there always is a first time.

---

### Post by fairbrother89 on 2014-03-19
it certainly sounds logical impav;
issuing the reboot command just means typing the word reboot at the command module (flasing cursor prompt) i suppose.
if it ends up houston we have a problem, i'll blame myself.
back soon.;)

---

### Post by fairbrother89 on 2014-03-22
are you sure this is correct guys as nothing happened when i put this in. with one space after mount another after o another after remount.

mount     -o     rw,remount      /

a cursor opened this time beneath the menu screen. root@phil.
then just went to another cursor when i hit enter. maybe i'll try again later.
thanks again guys.

---

### Post by Ubi_one_2014 on 2014-03-22
are you still dealing with unmet dependencies?
what shows apt-get update && apt-get dist-upgrade?

---

### Post by Impavidus on 2014-03-22
> **fairbrother89 said:**
> are you sure this is correct guys as nothing happened when i put this in. with one space after mount another after o another after remount.

mount     -o     rw,remount      /

a cursor opened this time beneath the menu screen. root@phil.
then just went to another cursor when i hit enter. maybe i'll try again later.
thanks again guys.

If it doesn't give you an error, it worked.

---

### Post by JKyleOKC on 2014-03-22
> **fairbrother89 said:**
> are you sure this is correct guys as nothing happened when i put this in. with one space after mount another after o another after remount.

mount     -o     rw,remount      /

a cursor opened this time beneath the menu screen. root@phil.
then just went to another cursor when i hit enter. maybe i'll try again later.
thanks again guys.To elaborate on what *impavidus* said, **bash** (the command-line processor) is not at all chatty, nor are most of the programs you can invoke with it. If there's no error to report, they don't report anything.

In the case of the **mount** command with the **rw,remount** option, the only effect is to change the specified partition from read-only status to read-write status, allowing following commands to write needed changes to the disk. Without this command, any commands that followed would result in "access denied" errors when they tried to write to the disk.

In the case of just hitting enter, you in effect told **bash** "don't do anything" and it replied "gotcha, boss; I didn't do anything and that didn't cause any errors." It takes a bit of getting used to, but soon becomes what one expects -- in the meantime it's quite confusing to anyone not familiar with command-line actions. Something quite similar happens in the Windows command line, although other Windows commands tend to be a bit more vocal in responding if they succeed.

---

### Post by fairbrother89 on 2014-03-22
oh, sorry i was expecting pages of code to go flashing up.
so i dont need to re enter that remount code again then ?? or do i ?

i can then proceed with the dpkg code given earlier ??

no it didnt give an error message it just opened another command line.

---

### Post by JKyleOKC on 2014-03-22
> **fairbrother89 said:**
> oh, sorry i was expecting pages of code to go flashing up.
so i dont need to re enter that remount code again then ?? or do i ?

i can then proceed with the dpkg code given earlier ??If you've restarted the system,  then you would need to do the remount again, otherwise not. Doing it again won't hurt anything, though, so if in doubt, re-do it.

Basically when you change/restart the system, it initially comes up as read-only. The purpose of the remount command is to change that to read-write, and once changed it won't change back during the current session.

---

### Post by fairbrother89 on 2014-03-22
understood. thanks.

---

### Post by fairbrother89 on 2014-03-23
hi all.
i inputted the dpkg code given earlier after i'd done the romount.
however before i had the chance to write the final piece of code   **apt-get space -f space install**  i got an error message.
i got this message before i'd even had a chance to hit the enter button;

**dpkg;error; failed to open '/var/lib/dpkg/status' for writing status database: no space left on device**

i then decided, rather than simply proceeding after this error, to abort by typing reboot.

question; shalll i ignore this message and continue with the apt-get code ??

many thanks.

---

### Post by Impavidus on 2014-03-23
Then let's try it the dirty way. Reboot into recovery mode and use the following commands:```

mount    -o   rw,remount   /
rm   -r   /usr/src/linux-headers-3.2.0-2*
rm   -r   /usr/src/linux-headers-3.2.0-3*
apt-get   -f   install
apt-get   purge   linux-headers-3.2.0-2*
apt-get   purge   linux-headers-3.2.0-3*
apt-get   purge   linux-headers-3.2.0-4*
apt-get   purge   linux-image-3.2.0-2*
apt-get   purge   linux-image-3.2.0-3*
apt-get   purge   linux-image-3.2.0-4*
reboot
```Should clean up everything at once.

---

### Post by fairbrother89 on 2014-03-24
thanks.
i'm starting to annoy myself here for not seeing ever so slight issues b4 they arise.
as u know i cant copy paste these codes so have to jot them down

i got to the end of the first line and realised that to open a new line would mean hitting the enter button
which would execute the first line of code only.
is it ok to do this.
sorry for the continued confusion.

---

### Post by Impavidus on 2014-03-24
Yes, execute the lines one by one. That's why I put them on separate lines.

---

### Post by JKyleOKC on 2014-03-24
Yes, it's intended to be that way when one of us puts multiple command lines into a single "code" block. It simply saves space.

Execute each line in turn, and if it gives an error then stop short, let us know what happened, and wait for a response.

Good luck!

---

### Post by fairbrother89 on 2014-03-25
i got as far as the apt get purge lines but each one including the install one gave the following;
[B]
E: dpkg was interrupted, you must manually run 'dpkg--configure-a' to correct the problem[/B]

not too sure if there were spaces between the dashes but maybe you can help with this.

many thanks again.

---

### Post by ibjsb4 on 2014-03-25
The correct code is:

```
sudo dpkg --configure -a
```

Run that

---

### Post by fairbrother89 on 2014-03-25
hi thanks. at what point should i run that line please ?? something like this perhaps ??

```
mount    -o   rw,remount   /
rm   -r   /usr/src/linux-headers-3.2.0-2*
rm   -r   /usr/src/linux-headers-3.2.0-3*
**dpkg -- configure - a**
apt-get   -f   install
apt-get   purge   linux-headers-3.2.0-2*
apt-get   purge   linux-headers-3.2.0-3*
apt-get   purge   linux-headers-3.2.0-4*
apt-get   purge   linux-image-3.2.0-2*
apt-get   purge   linux-image-3.2.0-3*
apt-get   purge   linux-image-3.2.0-4*
reboot
```

---

### Post by ibjsb4 on 2014-03-25
Run that command by its self; open a terminal and enter only that command.

---

### Post by Impavidus on 2014-03-25
```
mount    -o   rw,remount   /
**dpkg   --configure   -a**
apt-get   -f   install
apt-get   purge   linux-headers-3.2.0-2*
apt-get   purge   linux-headers-3.2.0-3*
apt-get   purge   linux-headers-3.2.0-4*
apt-get   purge   linux-image-3.2.0-2*
apt-get   purge   linux-image-3.2.0-3*
apt-get   purge   linux-image-3.2.0-4*
reboot
```
You already ran the **rm** commands, you don't need them again. They would just give you an error without doing anything. You only need the **mount** command again if you rebooted, but using it anyway won't harm. Stop if you encounter any errors.

You should now have enough inodes available to run the package manager. To be sure, you can run```
df   -i
```It should no longer list /dev/sda5 at 100%. The disk space problem has been fixed, now the package manager.

@ibjsb4: This is in recovery mode, so no sudo or terminal windows.

---

### Post by fairbrother89 on 2014-03-26
i got as far as apt-get when suddenly a lot of code and error messages appeared the only problem was i wasnt quick enough to write it all down.
it settled and i wrote down some of what i could see.

```
dpkg- dependency problems prevent configuration of linux-generic
linux generic depends on linux-headers-generic (=3.2.0.60.71) however: package linux headers generic is not configured yet dpkg error processing
 linux generic (--configure) dependency problems - leaving unconfigured setting up openjdk - 6 - jre - headless (6b30 - 1.13.1 - 1ubuntu2~0.12.04.1)...
installing new version of config file / etc/ java - 6 openjdk/security/java.security/java.policy.
setting up
setting up
setting up
setting up
setting up
errors encountered while processing linux-headers-generic-pae
linux-headers-generic
linux-generic
```

i then deleted the unfinished apt-get -f install command and typed reboot instead.

nb; after each "setting up" line above there was a long line of code which i did not write down as i thought it would take too long.

also a lot of what went before the above i did not catch. i was wondering if i should try this again and maybe video it so the entire code could be captured.
how does one scroll back to the begining of a few screens worth of code. do you think this will have done something permanent to my installation ???

many thanks for your continued help.

---

### Post by ibjsb4 on 2014-03-26
> **Impavidus said:**
> [CODE]@ibjsb4: This is in recovery mode, so no sudo or terminal windows.

apologies

---

### Post by Impavidus on 2014-03-26
> package linux-headers-generic is not configured yetPeculiar, as```
dpkg   --configure   -a
```should have taken care of that. If you're positive you gave the right command, try to configure that package explicitly:```
dpkg   --configure   linux-headers-generic
```You can also try other package names the system complains about. To list the packages that haven't been installed properly, try```
dpkg   --list   |   grep   -v   -e   '^ii'   -e   '^rc'
```This should list all packages that are not in a proper state.

@ibjsb4: No apologies needed.

---

### Post by fairbrother89 on 2014-03-26
will it do any harm to try the first one again do you know ?? i'm pretty sure i entered it correctly.
```
dpkg space --configure space -a
```
i may video it. theres no real hurry. i would like to get my ubuntu partition back though.

---

### Post by Impavidus on 2014-03-26
There's no harm in trying any of the commands again. Worst that can happen is "Cannot do this because it was already done."

---

### Post by Navneet_Kumar on 2014-03-27
Using apt-get install with -f option fixes the broken packages and you will be able to met all the dependencies,..........
Otherwise it is always recommended to use a package manager and Synaptic Package Manager is the best......:D

---

### Post by fairbrother89 on 2014-03-27
strange goings on here guys. i was about to scroll down to log into windows when i noticed two things.
1;ubuntu was now showing .60 instead of .59
2;the countdown clock to automatic boot into the highlighted OS was missing.

i booted into ubuntu and here i am using it now. i am back to where i was when i first opened the thread. able to log in and open chrome so long as i open it before the no entry sign with the unmet dependencies message appears. it has now appeared. but clearly terminal is now available. so i will try some of the earlier suggestions in terminal. good work guys, thanks. ;)

---

### Post by fairbrother89 on 2014-03-27
hmmm. looking through this thread again. if i go;
```
sudo  apt-get remove linux headers-3.2.0-4*
```
that will also remove the 50's and 60 will it not.?
so i'm thinking maybe just remove one set of headers just to free up enough i nodes for the packages to be able to install.
or something like adding a ? instead of * after 4. as suggested in an earlier post.

hmm well without me doing anything 29 through 39 seem to have disappeared;
[I]
linux-headers-3.2.0-40              linux-headers-3.2.0-53-generic-pae
linux-headers-3.2.0-40-generic      linux-headers-3.2.0-54
linux-headers-3.2.0-40-generic-pae  linux-headers-3.2.0-54-generic
linux-headers-3.2.0-41              linux-headers-3.2.0-54-generic-pae
linux-headers-3.2.0-41-generic      linux-headers-3.2.0-55
linux-headers-3.2.0-41-generic-pae  linux-headers-3.2.0-55-generic
linux-headers-3.2.0-44              linux-headers-3.2.0-55-generic-pae
linux-headers-3.2.0-44-generic      linux-headers-3.2.0-56
linux-headers-3.2.0-44-generic-pae  linux-headers-3.2.0-56-generic
linux-headers-3.2.0-45              linux-headers-3.2.0-56-generic-pae
linux-headers-3.2.0-45-generic      linux-headers-3.2.0-57
linux-headers-3.2.0-45-generic-pae  linux-headers-3.2.0-57-generic
linux-headers-3.2.0-49              linux-headers-3.2.0-57-generic-pae
linux-headers-3.2.0-49-generic      linux-headers-3.2.0-58
linux-headers-3.2.0-49-generic-pae  linux-headers-3.2.0-58-generic
linux-headers-3.2.0-51              linux-headers-3.2.0-58-generic-pae
linux-headers-3.2.0-51-generic      linux-headers-3.2.0-59
linux-headers-3.2.0-51-generic-pae  linux-headers-3.2.0-59-generic
linux-headers-3.2.0-53              linux-headers-3.2.0-59-generic-pae
linux-headers-3.2.0-53-generic      linux-headers-3.2.0-60[/I]

hmm and my i nodes are down to 64% yet i'm still getting the error sign about unmet dependencies;

[I]Filesystem      Inodes  IUsed  IFree IUse% Mounted on
/dev/sda5      1177344 747598 429746   64% /
udev            214826    478 214348    1% /dev
tmpfs           218471    391 218080    1% /run
none            218471      3 218468    1% /run/lock
none            218471     11 218460    1% /run/shm[/I]

---

### Post by Impavidus on 2014-03-27
The rm commands you used removed header directories 29 through 39 and freed some inodes, so that was to be expected. You now have enough inodes available to login to the GUI. The apt-get -f install or dpkg --configure -a commands installed the new kernel, which explains why you see 3.2.0-60 in the grub menu, so that's a good sign too.

Let's try to find out what's wrong with the package manager. You're back in the GUI instead of recovery mode, so you don't have to remount the file system any more, but you do have to use sudo. What do these commands report:```
sudo  dpkg  --configure  -a
sudo  apt-get  -f  install
```As soon as it doesn't report any errors, properly uninstall the old headers and kernels:```

sudo  apt-get  purge  linux-headers-3.2.0-2*
sudo  apt-get  purge  linux-headers-3.2.0-3*
sudo  apt-get  purge  linux-headers-3.2.0-4*
sudo  apt-get  purge  linux-image-3.2.0-2*
sudo  apt-get  purge  linux-image-3.2.0-3*
sudo  apt-get  purge  linux-image-3.2.0-4*
```
You removed the files belonging to header packages 29 - 39, but they may not be properly uninstalled, so the package manager may think they are still installed.

Edit: **sudo apt-get purge linux-headers-3.2.0-4***will not remove the 50s and 60, but it will remove some dependencies like linux-headers-3.2.0-40-generic. So, you really want the *, not a ?.

---

### Post by JKyleOKC on 2014-03-27
The difference between "*" and "?" in these commands is that "?" matches just **one** character, no matter what it is, while "*" matches **all** following characters. The reply from Impavidus implies as much, and is correct, but I feel that you may find a more in-depth explanation helpful in getting comfortable with the command line...

---

### Post by fairbrother89 on 2014-03-28
config a output

```
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-60-generic-pae; however:
  Package linux-headers-3.2.0-60-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-60-generic; however:
  Package linux-headers-3.2.0-60-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 3.2.0.60.71); however:
  Package linux-headers-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic-pae
 linux-headers-generic
 linux-generic
```

---

### Post by fairbrother89 on 2014-03-28
f install output. i did not continue..
```
sudo  apt-get  -f  install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29-generic linux-headers-3.2.0-55-generic
  linux-headers-3.2.0-55-generic-pae linux-headers-3.2.0-29
  linux-headers-3.2.0-55 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-60-generic linux-headers-3.2.0-60-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-60-generic linux-headers-3.2.0-60-generic-pae
0 upgraded, 2 newly installed, 0 to remove and 43 not upgraded.
3 not fully installed or removed.
Need to get 0 B/1,955 kB of archives.
After this operation, 22.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

---

### Post by Impavidus on 2014-03-28
OK, so the packages linux-headers-3.2.0-60-generic and linux-headers-3.2.0-60-generic-pae have to be installed. Running
```
sudo  apt-get  -f  install
```may do the trick.

---

### Post by fairbrother89 on 2014-03-28
```
(Reading database ... 1139472 files and directories currently installed.)
Unpacking linux-headers-3.2.0-60-generic (from .../linux-headers-3.2.0-60-generic_3.2.0-60.91_i386.deb) ...
Unpacking linux-headers-3.2.0-60-generic-pae (from .../linux-headers-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb) ...
Setting up linux-headers-3.2.0-60-generic (3.2.0-60.91) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-60-generic /boot/vmlinuz-3.2.0-60-generic
Setting up linux-headers-generic (3.2.0.60.71) ...
Setting up linux-generic (3.2.0.60.71) ...
Setting up linux-headers-3.2.0-60-generic-pae (3.2.0-60.91) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae
Setting up linux-headers-generic-pae (3.2.0.60.71) ...
```

should i now run the apt get autoremove command as suggested in the earlier output as it appears to have re installed the old headers doesn't it ??

**sudo  apt-get autoremove**

---

### Post by Impavidus on 2014-03-28
Looking good.

It hasn't reinstalled old headers, it just hasn't realised yet you removed them. So uninstall the old headers and kernels.
```
sudo  apt-get  purge  linux-headers-3.2.0-2*
sudo  apt-get  purge  linux-headers-3.2.0-3*
sudo  apt-get  purge  linux-headers-3.2.0-4*
sudo  apt-get  purge  linux-image-3.2.0-2*
sudo  apt-get  purge  linux-image-3.2.0-3*
sudo  apt-get  purge  linux-image-3.2.0-4*
#Following should also be safe to remove, but maybe you want to keep 59
sudo  apt-get  purge  linux-headers-3.2.0-5*
sudo  apt-get  purge  linux-image-3.2.0-5*
```I don't know which of these are actually installed, but asking for their removal again can't harm.

Edit: the autoremove to remove old kernels or headers only works in 13.10, not in 12.04.

---

### Post by fairbrother89 on 2014-03-28
ok thanks a lot.
i ran that and quite a bit of output answered. most of it said, its not installed so could not be removed. so i aborted. 
the current state of play is;
the no entry sign has gone. and i have 45 updates waiting to be installed. so it's looking good. i won't install these updates straight away i think i'll wait until i reboot later on. many thanks. i'm half thinking maybe i should wait for the invitation to upgrade to the next version of ubuntu before i do anything else.

---

### Post by Impavidus on 2014-03-28
Some warning like that were to be expected, no reason to abort there. You can run your normal updates. Just remember to uninstall old headers and kernels. You can mark this thread as solved. Click thread tools near the top of the page.

---

### Post by fairbrother89 on 2014-03-29
thanks impavidus and others who have taken the time to help with this. yes it is now solved and i have learnt a fair amount also. :)

---

