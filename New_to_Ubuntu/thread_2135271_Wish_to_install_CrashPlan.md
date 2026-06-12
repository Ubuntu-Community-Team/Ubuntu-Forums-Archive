---
title: "Wish to install CrashPlan"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by docJ on 2013-04-13
So I googled it and came up with this: [http://sajanp.com/531/how-to-install-crashplan-with-ubuntu-12-04-unity/](http://sajanp.com/531/how-to-install-crashplan-with-ubuntu-12-04-unity/)
There a video in there, I watched it and my head is spinning since...
Just under the video is this phrase: > Installing Crashplan on Ubuntu is an absolute breeze
 
OK, so at least he's not saying it is moderately hard or even difficult, I surely would have fallen inconscious then.
Should I watch this in slow-mo for a day or two or is there something easier out there?

PS: I have one week experience on Ubuntu 

Thanks

---

### Post by Frogs Hair on 2013-04-13
Much of what was done can be done with the GUI.

cd downloads = open the downloads directory/ folder.

extract file = right click package and select extract here 

Running the start.sh can be done opening the folder and double clicking in most cases.

There are graphical ways to create launchers also. 

I have never worked with the application though.

---

### Post by docJ on 2013-04-14
I am running 12.04 64bits

From the CrashPlan website, here are the software requirement: 
> 2.6.13 or newer 2.6 series kernel
 Oracle (Sun) Java version 1.6+
 glibc 2.4+, cpio, Xorg, SWT

I know it requires Java, but what are the other things mentionned. Because of the way its formatted, I'm not even sure how many sftwr requirements I'm looking at.

2.6.13 or newer 2.6 series kernel:  does this refers to Ubuntu itself

Oracle (Sun) Java version 1.6+: on Ubuntu Software Centre and search "Java", the first 2 results are: > OpenJDK Java 7 Runtime and OpenJDK Java 6 Runtime
The description isnt even close to the requirements. 
Java.com website offers either Linux or Linux RPM, both in 32 and 64 bits version.

glibc: what is it and where do I get it from

cpio: a program to manage archive of files, according to Ubuntu Software Centre

Xorg: seems offered on Ubuntu Software Centre as a "x windows system" (???) 

SWT: what is it and where do I get it from

---

### Post by wickedpuppy on 2013-04-14
Lets do things step by step

Here is the command to see the kernel you have

```
uname -r
```

Java version 
```
java -version
```

glibc (GNU C Library). This should install the headers 
```
sudo apt-get install build-essential
``` 

cpio , if you are not sure if you have it , just do a sudo apt-get install cpio (It works 95% of the times for me) 

Xorg
Unless you installed the server version , you have it.

SWT - Standard Widget Toolkit (From googling)
The package you are looking for seems to be : libwebkitgtk 

If try them. Above all , try them. If they don't work , pls come back to let us know.

---

### Post by docJ on 2013-04-14
> **wickedpuppy said:**
> Lets do things step by step

Perfect, That's how I prefer it too !;)

> Here is the command to see the **kernel** you have

     Code:
     
uname -r 

My result: ```
3.5.0-27-generic


```

**Java** version 
```
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>
```

**glibc** (GNU C Library). This should install the headers
It gave a boatload of code, and asked y/n about space, answered yes seem ok

**cpio** , if you are not sure if you have it , just do a ```
sudo apt-get install cpio
``` (It works 95% of the times for me) 

result: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cpio is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-23-generic linux-headers-3.5.0-23
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

**Xorg**
Unless you installed the server version , you have it.

I have desktop version

**SWT** - Standard Widget Toolkit (From googling)
The package you are looking for seems to be : libwebkitgtk

Not sure what I'm supposed to do here

---

### Post by wickedpuppy on 2013-04-14
Ok so you have no java. You can install Java in many ways , too many if you ask me. 

Here is a wiki page on Java , [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

I am not sure you need a JRE or JDK , so lets get JDK. Install this package , from one of the suggestions , openjdk-7-jre-headless.

As for swt , I have given you the package name. Basically a executable file name. Think of it like me saying "Hey dude , you got doc file , you need word!" Install it. 

Normally , this is how I go about

1) I need to run this program which is called this (eg swt)
2) I go google and look for the name (swt .. it will give me the full name)
3) Then I google with specific Distro (Ubuntu swt) for people asking for how to install the same thing as I am trying to on Ubuntu
4) I look at a few forums and try to repeat what people did
5) If I managed to get a package name , then I try to install the package (apt-get)

One all is done , then try installing the CrashPlan.

---

### Post by docJ on 2013-04-14
openjdk-7-jre-headless
this is now installed, making good progress.

All that's left is this SWT
You suggested I need libwebkitgtk
If I go to Ubuntu Software Centre and search it, it gives me 14 results

I wish CrashPlan's SWT requirements would have been more specific
I might have to drop them a line...

Thank you for helping me!

---

### Post by wickedpuppy on 2013-04-14
No prob. I was and still a noob in a lot of areas. 

Here is a tip. Learn these two commands

- apt-cache
- apt-get 

Try this code

```
apt-cache search libwebkitgtk
```

You will see a lot of options. Only two of them are what you need. Try it.

Once you get the right name , use sudo apt-get to install it.

---

### Post by docJ on 2013-04-14
Oddly enough, if I go to their download page using Chrome instead of Firefox, the software requirements are slightly different.

From Firefox (same as post#3 above):
> 2.6.13 or newer 2.6 series kernel
 Oracle (Sun) Java version 1.6+
 glibc 2.4+, cpio, Xorg, SWT

From Chrome: > Oracle (Sun) Java version 1.6+, 
Glibc 2.4+, 
GTK, 
Xorg

Gone is SWT (and cpio and kernel), but there is this new guy "GTK"
Searching GTK on Ubuntu software centre gives all kind of seemingly unrelated results
Wiki/googling points to Gimp (!?!?), why on earth would I need a picture editor to run backup sftwr:lolflag:

---

### Post by wickedpuppy on 2013-04-14
You sure googling "GTK" points to GIMP? I see gtk.org as the first result in Google. Anyway , Just install CrashPlan. If it fails then we see why and we go from there.

---

### Post by docJ on 2013-04-14
> You sure googling "GTK" points to GIMP? I see gtk.org
You're right, my bad: gtk.org is the real thing, they do offer a Linux download; I haven't tried it

tried you're suggestion for ```

apt-cache search gtk
```
gives a gazillion results, same for gtk+ (as per gtk.org)

> Just install CrashPlan. If it fails then we see why and we go from there.
I almost did, but...while I must have installed a million (really) programs on windows, this would be my very first time on Ubuntu.

At the "what should Firefox do with this file" step, it default to Open with: Archive manager (default) with no other choice in the dropdown menu
I have also option to Save File (but I don't have a clue where it's going to be saved)
I dunno which option to pick

I do know lots of people that click here and there without a second thought; I could earn a living fixing their (windows) computers.
I am in terra incognita with Linux and this tends to slow me down
 Thanks for being patient with me

---

### Post by wickedpuppy on 2013-04-14
Eh ah , I didn't say apt-cache search gtk , its apt-cache search libwebkitgtk. It shouldn't give you more than 10. 

Ok first , we download the file. Or save as. Actually , its the same on Windows. If I am downloading a zip file , Windows will pop up asking if I want to open it in winzip or save it.

---

### Post by docJ on 2013-04-14
> **wickedpuppy said:**
> Eh ah , I didn't say apt-cache search gtk

Of course not, but you did suggest I learn to use "apt-cache search"; that's just what I tried, but for gtk that time

---

### Post by wickedpuppy on 2013-04-14
GTK will gives a lotttttt of results. Its a very generic name for Gnome packages/libraries. Let us know how the install went. :)

---

### Post by docJ on 2013-04-14
The other issue was where would it download the file to. Firefox on Ubuntu is different than the one I'm used to on Windows. I poke around and managed to get firefox menu, then Preferences.
So now at least I know the default location for saving a file is a folder called download which I can browse to.

---

### Post by docJ on 2013-04-14
OK so its downloaded
I'm trying to follow the video instructions (see post# 1), but I am stuck at:```
jlr@ub3:~$ cd downloads/
bash: cd: downloads/: No such file or directory
jlr@ub3:~$ cd Downloads/
jlr@ub3:~/Downloads$ ls
CrashPlan_3.5.2_Linux.tgz
jlr@ub3:~/Downloads$ tar -xf CrashPlan_3.5.2_Linux.tgz
jlr@ub3:~/Downloads$
```

As you see I did not capitalize Downloads at first
According to the video, the tar command is suppose to create the install folder
It does not for me, but am I using same unzip app as in the video(?)

---

### Post by docJ on 2013-04-14
Then again, maybe I dont need to do it like in the video, as per Frogs Hair post#2 

> **Frogs Hair said:**
> Much of what was done can be done with the GUI.

cd downloads = open the downloads directory/ folder.

extract file = right click package and select extract here 

Running the start.sh can be done opening the folder and double clicking in most cases.

There are graphical ways to create launchers also. 

I have never worked with the application though.

If I open the Downloads folder... Wait ! ! !
 The CrashPlan-Install folder _has_ been created, just beside the .tgz package
CrashPlan-Install folder contains 8 files, the one I need is install.sh

---

### Post by docJ on 2013-04-14
I had to "enter" right through the EULA, and near the end, I noticed a bummer: It seems I cannot use CrashPlan to devellop Nuclear arsenal or biological weapon...:-(

It defeats the whole purpose of backup software...

---

### Post by docJ on 2013-04-14
On a more serious note, I am asked in which directory I want to install, default being usr/local/crashplan
I accept
It does not exist. do I wish to create it, yes
Then what directory do you wish to link the executable to: usr/local/bin is default, I accept

Now the trick question; in what directory do I wish to store backup? default is usr/local/var/crashplan

This is absolutely not OK; I have close to 4TB than needs to backup to a NAS. But If I'm not mistaken, I could accept default for now and change it from the program gui later (?)

---

### Post by docJ on 2013-04-14
Cool, I now have the shortcut appeared on the desktop, which I just dragged it to the launch bar

The moment of truth; I click the shortcut, I get the splashscreen but after a while, it says: "Unable to connect to the backup engine, retry?" with Yes or No choice
 I clicked Yes and after a while, the same error appeared.

It might have to do with not taking care earlier of SWT and/or GTK?

---

### Post by wickedpuppy on 2013-04-14
Seems you are doing just fine :P 

Btw you can start using tab for auto completion. Try typing 'D' then press tab , it will give you Document and Download. To close down on the Download , add ow. So now you have 'Dow' and no other directories share the name starting with Download so bash will give you Download. 

Also after you have untar , you are not sure what happened. Try ls again. In fact , try to do ls every now and then. Linux or Unix rule is 'No news is good news' so if you are not seeing anything , it probably means whatever you did went right. 

As for CrashPlan , I can't help with that since I have never used it before. But why not give it your backup directory?

---

### Post by docJ on 2013-04-14
Never mind, I rebooted and now I have the account connection screen, so for now, all seem well.
Wicked Puppy, thanks a ton for helping me out, it went better than anticipated

Its amusing to think a total Linux noob such as I is happy to have managed to install a program in, say, 6 hours...
On Windows turf, anything over 5 minutes is killing me

---

### Post by docJ on 2013-04-14
> **wickedpuppy said:**
> But why not give it your backup directory?

This new Ubuntu computer is being used for media storage purpose, I have one "small" 750Gb drive for os partitions and about 600gb left for "home"
Then 3 more hard drives totalling 7 Tb where my media is stored. I can't back it up to "home", but I also have a NAS that can hold 8Tb on its own, hence I will set Crashplan to backup Ubuntu media drives to the NAS 

I expect the initial backup to last a little short of a week, then its gonna do differential only

---

### Post by docJ on 2013-04-14
> **wickedpuppy said:**
> 
Btw you can start using tab for auto completion. Try typing 'D' then press tab , it will give you Document and Download. 


I thought the guy in the video was typing mighty fast, now I know why...:)
I kind of discovered the feature by accident, I was pressing enter and I was seeing stuff cycling on next line of terminal.
Discovered, but neither understood nor mastered

Will try it later

---

### Post by wickedpuppy on 2013-04-14
Great it worked out in the end. It was pretty complicated though. Talking of backup , Linux has plenty of backup options as well. RSync , dd comes to mind. May not as feature-rich as CrashPlan though.

---

### Post by docJ on 2013-04-14
I think I will squeeze in one last UberNoob question in here.
On the left side of the screen, on the launch bar, I now see 3 CrashPlan icons, plus one on the desktop.

No idea how I managed to do that. Just one on the launch bar and none on desktop would be good for me.

---

### Post by wickedpuppy on 2013-04-14
Right click , choose the unlock option.

---

### Post by war59312 on 2013-06-10
Ugh, got to love JAVA.

 Crashplan is crashing after upgrading to ubuntu 13.04. Was fine before the upgrade.
 ```
rob@RobsUbuntuServer:~/Desktop$ uname -r
3.8.0-23-generic
rob@RobsUbuntuServer:~/Desktop$ java -version
java version "1.7.0_21"
Java(TM) SE Runtime Environment (build 1.7.0_21-b11)
Java HotSpot(TM) 64-Bit Server VM (build 23.21-b01, mixed mode)
```

Crash:> java crashed with SIGABRT in soup_session_feature_detach()
**Update**: See attached log [ATTACH]243745[/ATTACH] please.

---

### Post by incurablegeek on 2013-06-11
I can't offer much here in the way of technical - just to say that CrashPlan is a super good choice. I've used it for about a year, very easy setup on Win7 64 bit - and, most importantly, CrashPlan tech support **responds instantly**!

And, like everything I do, I read reviews, lots and lots of them and focus mostly on the complaints. After a week of daily reading, I feel comfortable that **CrashPlan is a solid choice**. :)   I have over 1.5 TB backed up thus far and more to come.

Best of luck to you.

---

