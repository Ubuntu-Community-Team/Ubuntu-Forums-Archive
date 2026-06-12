---
title: "Run a Program"
date: 2016-10-05
forum: New to Ubuntu
---

### Post by poisonfor3 on 2016-10-05
Sorry for what must be a brainless question but I have googled it and can not find how to run my programs. Posting questions for me is a last resort because if the question has been answered no need to ask it again but I can not seem to find the answer by googling it maybe because it is so simple that no one talks about it. Kinda like trying to google "How do you use a light switch" . . .  I just did that and nope no one is talking about how to use one LOL


There must be a command line to run a program but I have no idea how to do that. Most times I use one of the download programs (Like Ubuntu software center, app grid, software  boutique, and one just called software) to install my programs and I find them in the menu box. But when I use the sudo thing they download (or sure seems like it) or when I just download the program as a file then  . .  . nothing. They are not like the .exe programs in Windows. Not complaining just frustrated.

Should not mater for this question but I have 16.04.1 with Mate. 

I will give 2 examples
Example #1 - I click download and download a program and now have a file in my inbox called "multibit-unix-0.4.1.sh" (a bitcoin wallet) but how do I run it.

Example #2 I follow the very friendly directions 
sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update

in the command line and it seems to download but then nothing. How do I execute the program?

Thanks

---

### Post by howefield on 2016-10-05
> **poisonfor3 said:**
> I click download and download a program and now have a file in my inbox called "multibit-unix-0.4.1.sh" (a bitcoin wallet) but how do I run it.

Is that as far as you have gotten, a file like that would generally need to be run to install it, are you following a tutorial ?

> ```
sudo add-apt-repository ppa:bitcoin/bitcoin
sudo apt-get update
```

All the above would do is set up the repository information so that your system knows about the software packages that it contains, you would then need to *sudo apt install packagename* to have an application to run ?

---

### Post by clymbon on 2016-10-05
Hi Poison, I feel your pain :-)

In my opinion, the people who put together the Ubuntu distribution have done a great job of making the system user friendly, but there are so many different ways to do things on Linux, and often you will want to install some software that isn't packaged specifically for Unbuntu.  That's when things get confusing.

First, there's the ubuntu software installer thingy.  I'm talking about the icon in the launcher area on the left of the screen that looks like a little briefcase and has an "A" looking thing on it.  If you hover the mouse over it you'll see "Ubuntu Software".  If you use that, then any software installed should show up when you use the search thingy.  I'm talking about the icon that shows up in the upper left of the screen that, when you hover over it, shows "Search your computer and online sources". 

But in your first example, it looks like you have downloaded a shell script.  On a windows system, that would be like a .bat file, and you might open a command shell and run it from the DOS prompt.  On Linux, you need to open a terminal window and execute the script.  To open a terminal window, right click on the desktop background and select "Open Terminal".  Then you can start typing in commands.  Hopefully, the source that you downloaded the software from will tell you what commands you need to type.  Probably you need to "cd" to the directory that contains the file, then mark it executable, then just type it's name.  (I'm assuming that when you said the file is in your "inbox" you really meant the file was downlaoded into your home directory or your download folder, or someplace else.)  But again, follow directions.  Post details here if you are stuck.

The "sudo apt..." commands you show would also need to be typed into a terminal window.   Do the same as above to open a terminal window, and then cut and paste, or follow instructions from wherever you are getting the software.

And send me some bitcoins when you are done!  :-)

Good luck.

Duncan

p.s. One of the problems I have with Ubuntu is that it's hard to know the right names of things.  Would be nice if there was a way to find out the right names for all the things that show up in the launcher,.

p.p.s. With windows, you can execute an .exe file by locating it with the file explorer, then double clicking it.  With most Linux distributions you can do something similar - use a graphical tool to explore the file system, locate an executable file, then double click it, and have it run.  Unfortunately (in my opinion) this is hard to set up on Ubuntu.  You can navigate to your .sh file with the "File" thingy (again, how do I find the name of this application?) but, even if the sh file is executable, you can't execute it by double clicking on it.  At least not without jumping through a bunch of complicated hoops, as far as I know.

---

### Post by DogMatix on 2016-10-05
To run a shell script.sh in a terminal

Make it executable
```

sudo chmod +x /path/to/multibit-unix-0.4.1.sh

```

Then to run it
```

/path/to/multibit-unix-0.4.1.sh

```

---

### Post by clymbon on 2016-10-05
DogMatix, I think there is a typo in your command to run a script (extra "dot").

And be aware that you can and should omit the "sudo" unless you really want to run the command with root privileges.  Often when installing software you need to use "sudo".  For example, you need to use sudo to install software in system directories.  Just be aware that "sudo" means "I give this software total power to do anything it wants to my system".  Use it only when you need to. 

Duncan

---

### Post by DogMatix on 2016-10-05
> **clymbon said:**
> DogMatix, I think there is a typo in your command to run a script (extra "dot").

And be aware that you can and should omit the "sudo" unless you really want to run the command with root privileges.  Often when installing software you need to use "sudo".  For example, you need to use sudo to install software in system directories.  Just be aware that "sudo" means "I give this software total power to do anything it wants to my system".  Use it only when you need to. 

Duncan

Yep, you're right ./ is current directory and I hadn't changed to that directory. I'll amend the above post.

---

### Post by poisonfor3 on 2016-10-05
@howefield I was trying to follow the directions here :
[https://launchpad.net/~bitcoin/+archive/ubuntu/bitcoin](https://launchpad.net/~bitcoin/+archive/ubuntu/bitcoin)
I was trying to get bitcoin core wallet there when that did not work I tried to get the MultiBit Wallet here"
[https://multibit.org/](https://multibit.org/) and that is where I downloaded the "multibit-unix-0.4.1.sh" file from but I do not know what to do with it. LOL

There was more directions I found on the first site:
Technical details about this PPA

This PPA can be added to your system manually by copying the lines below and adding them to your system's software sources.
Display sources.list entries for
deb [http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu](http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu) xenial main 
deb-src [http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu](http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu) xenial main
But when I tried to do them I got back this:

No command 'deb' found, did you mean:
 Command 'dab' from package 'bsdgames' (universe)
 Command 'deb3' from package 'quilt' (universe)
 Command 'dex' from package 'dex' (universe)
 Command 'xdeb' from package 'xdeb' (universe)
 Command 'derb' from package 'icu-devtools' (main)
 Command 'debc' from package 'devscripts' (main)
 Command 'debi' from package 'devscripts' (main)
 Command 'dub' from package 'dub' (universe)
deb: command not found


@clymbon I do not have a thing on the left, so nothing that "looks like a little briefcase and has an "A" looking thing on it". I am using Mate. Plus I locked out all icons from going to my desktop. I use to put to much crap there so I just locked it from having anything at all on it. Just a nice photo of my son. But I think I know where your going. I did click menu and in the search box that shows up on the pop out, I tried to search there for the program. You go on to say "On Linux, you need to open a terminal window and execute the script" sounds good to me. :) When I tried to click on the .sh file it would not do anything but put up a red warning saying "Could not open the file /home/miss/Downloads/bit&#8230;ct/multibit-unix-0.4.1.sh pluma has not been able to detect the character encoding. Please check that you are not trying to open a binary file. Select a character encoding from the menu and try again."


@[**[COLOR=#000000]DogMatix[/COLOR]**]("https://ubuntuforums.org/member.php?u=293407")      
Yep that did it. I put this into the Term:
sudo chmod +x /home/miss/Downloads/bit_coin_project/multibit-unix-0.4.1.sh
/home/miss/Downloads/bit_coin_project/multibit-unix-0.4.1.

and it started right up. I now have a bitcoin wallet. No money but a wallet. And on top of using Linux one more reason for the NSA to spy on me. :P


Still would like to know why I could not get the other wallet to work. Why is it that it tells me "No command 'deb' found" seems like a nice command to me :)
And thanks to all of you for your help.

---

### Post by oldos2er on 2016-10-05
> Still would like to know why I could not get the other wallet to work. Why is it that it tells me "No command 'deb' found"

Those aren't commands; they are lines meant to be added to /etc/apt/sources.list. That's why they're referred to as "sources.list entries." 

To add that PPA you'd run ```
sudo add-apt-repository ppa:bitcoin/bitcoin

sudo apt-get update
```

---

### Post by CantankRus on 2016-10-05
There are a couple of ways to add a launchpad repository.
**1)** Run in terminal
```
sudo add-apt-repository [COLOR="#808080"]ppa:<ppausername>/<ppaname>[/COLOR]
```

[SIZE=3]**or**[/SIZE]

**2)** Add source using the "software and updates" GUI making sure to use your release name for "YOUR_UBUNTU_VERSION_HERE". 
You probably don't  need to add the deb-src source unless you want to modify or look at the source code.
With this method you also need to add signing keys.

#1 is the easiest method for launchpad ppas.

Then in terminal, refresh sources with....
```
sudo apt update
```
and install the package you want...
```
sudo apt install [COLOR="#808080"]<packagename>[/COLOR]
```

---

### Post by poisonfor3 on 2016-10-06
@[**[COLOR=#C61919][B]oldos2er**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=338320") and @[**[COLOR=#000000]CantankRus[/COLOR]**]("https://ubuntuforums.org/member.php?u=1938181")
  Thanks for helping here is what I tried. Here is a copy and past from my terminal.


root@big-bot:/home/miss#** [COLOR=#ff0000]sudo add-apt-repository ppa:bitcoin/bitcoin[/COLOR]**
 ```
Stable Channel of bitcoin-qt and bitcoind for Ubuntu, and their dependencies
 More info: [https://launchpad.net/~bitcoin/+archive/ubuntu/bitcoin](https://launchpad.net/~bitcoin/+archive/ubuntu/bitcoin)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpjg_pzb88/secring.gpg' created
gpg: keyring `/tmp/tmpjg_pzb88/pubring.gpg' created
gpg: requesting key 8842CE5E from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpjg_pzb88/trustdb.gpg: trustdb created
gpg: key 8842CE5E: public key "Launchpad PPA for Bitcoin" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
```
root@big-bot:/home/miss# [COLOR=#ff0000]**sudo apt-get update**[/COLOR]
```
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease               
Hit:3 [http://ppa.launchpad.net/appgrid/stable/ubuntu](http://ppa.launchpad.net/appgrid/stable/ubuntu) xenial InRelease    
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]
Hit:5 [http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu](http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu) xenial InRelease
Hit:6 [http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu](http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu) xenial InRelease
Hit:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease     
Hit:8 [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) xenial InRelease
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [395 kB]
Hit:11 [http://ppa.launchpad.net/unit193/encryption/ubuntu](http://ppa.launchpad.net/unit193/encryption/ubuntu) xenial InRelease
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [390 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [335 kB]
Hit:14 [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) xenial InRelease
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [331 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [82.6 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [62.9 kB]
Fetched 1,787 kB in 7s (242 kB/s)                                              
Reading package lists... Done
```
root@big-bot:/home/miss#**[COLOR=#ff0000] deb [http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu](http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu) xenial main[/COLOR][COLOR=#0000ff] [/COLOR]**[COLOR=#0000ff](ok ok I know now I do not need this at all)[/COLOR]
```
No command 'deb' found, did you mean:
 Command 'dab' from package 'bsdgames' (universe)
 Command 'dex' from package 'dex' (universe)
 Command 'dub' from package 'dub' (universe)
 Command 'debc' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
 Command 'derb' from package 'icu-devtools' (main)
 Command 'deb3' from package 'quilt' (universe)
 Command 'debi' from package 'devscripts' (main)
deb: command not found
```
root@big-bot:/home/miss# **[COLOR=#ff0000]deb-src [http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu](http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu) xenial main[/COLOR][COLOR=#0000ff] [/COLOR]**[COLOR=#0000ff](ok ok I know now I do not need this at all)[/COLOR]
```
deb-src: command not found
```
root@big-bot:/home/miss# **[COLOR=#ff0000]sudo apt install bitcoin[/COLOR]**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bitcoin
root@big-bot:/home/miss#
``` 

I also tried:
**[COLOR=#ff0000]sudo apt install bitcoin/bitcoin[/COLOR]**
**[COLOR=#ff0000]sudo apt install bitcoin/bitcoin/ubuntu[/COLOR]**

OK so it looks like ir read the package, made a nice tree for me, read the state information (whatever that is) but then just can not find the package. 

Have no idea how to "add signing keys"

Thanks for helping I have tried many times in the past to download/install programs from the terminal and just gave up. It should be so simple.
I am not new to computers I use to have a commodore 64 and save my programs with a cassette player, sadly I jumped onto the Windows bandwagon. :icon_frown:
Thank you all for helping me jump off of the windows bandwagon!

---

### Post by deadflowr on 2016-10-06
There is no standalone bitcoin package, but rather several bitcoin related packages.
Common packages to install are bitcoin-qt and bitcoind.
bitcoin-qt is the graphical interface for you and bitcoind is the daemon.
so with that try;
```
sudo apt install bitcoin-qt bitcoind
```

referenced from here:[https://bitcoin.org/en/full-node#ubuntu-1410]("https://bitcoin.org/en/full-node#ubuntu-1410")

---

### Post by poisonfor3 on 2016-10-06
Wow that did it. So I learned that the command I was missing was the simple "install" and that I needed to install one of "several bitcoin related packages". 

-Thanks

---

### Post by CantankRus on 2016-10-06
You may want to have a read of this page if you are going to use launchpad ppas.
[**_[COLOR="#B22222"]HOW TO USE A LAUNCHPAD PPA (ADD, REMOVE, PURGE, DISABLE) IN UBUNTU[/COLOR]_**]("http://www.webupd8.org/2012/02/how-to-use-launchpad-ppa-add-remove.html")

---

