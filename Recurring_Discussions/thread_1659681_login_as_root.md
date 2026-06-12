---
title: "login as root"
date: 2011-01-04
forum: Recurring Discussions
---

### Post by suryak on 2011-01-04
I'm new to Ubuntu and as i need to install a software and in the installation steps.. first step is to login as root.
i searched for it and i got two different answers. .

1. in terminal type "su - "
you'll be asked root password and enter it .. you'll be logged into it.
I tried this and i found that my user password is not working for it and i don't know how to do it.. 

2. in terminal type " sudo su"
you'll be asked user password for entering root..
i typed it ..and i for entered.. 

what exactly is the difference between 1 & 2
I was never asked to setup a password for root while installation.
how come i will be asked for a root password in 1 which i don't know and how to find it ?

Please explain me !!

---

### Post by Elfy on 2011-01-04
If asked for a root password - use sudo instead of su and use your normal password.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Zzl1xndd on 2011-01-04
Ubuntu's security disables the root account by default. That being said you don't really need to be root you just need the privileges associated with it. 

Just entering Sudo before the command should do the job. 

Check out the link for a more in-depth explanation 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Verbeck on 2011-01-04
> 
I was never asked to setup a password for root while installation.
how come i will be asked for a root password in 1 which i don't know and how to find it ?#1 would not work because the root account is disabled/locked in ubuntu by default. so to get root permissions (not becoming root), *sudo* is used with YOUR password, if you are in the sudoers file, thus #2 works

read more about it on  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Zoandar on 2011-01-04
But in order to work in the GUI, one needs to log in as root, right? So how does one enable the root account login?

---

### Post by sisco311 on 2011-01-04
> **Zoandar said:**
> But in order to work in the GUI, one needs to log in as root, right? So how does one enable the root account login?

No. Most modern GUI application will prompt you for a password when they need root privileges to perform an operation. And you can use gksu to run any other GUI application as root.

---

### Post by Zoandar on 2011-01-04
Oh. Well perhaps you can tell me what to do to get the file properties / permissions tab on one of my folders to ask me for the root password, so I can change it from being owned by "root" to owned by "me" so I can copy it?

The file is on an EXT2 partition on the SD card in my Android OS phone. I created the partition when setting up the card by using GParted. Once the card was put to use in the phone, somehow the folder got "owned" by root. As such, when I mount the card in Ubuntu so as to make backups of all the data on it, I am 'not allowed' to copy that folder (which is named Lost+Found). The other two folders on that partition are owned by me, so not a problem. 

I prefer to work in the GUI whenever I can. :)

---

### Post by coffeecat on 2011-01-04
Why do want to copy the lost+found folder? It should be empty. It's only used for recovering file fragments after repair of a damaged filesystem. Best leave it alone. It should be owned by root. And even if you change the ownership, it will probably get changed back to root at the next filesystem check.

---

### Post by bodhi.zazen on 2011-01-04
> **Zoandar said:**
> Oh. Well perhaps you can tell me what to do to get the file properties / permissions tab on one of my folders to ask me for the root password, so I can change it from being owned by "root" to owned by "me" so I can copy it?

The file is on an EXT2 partition on the SD card in my Android OS phone. I created the partition when setting up the card by using GParted. Once the card was put to use in the phone, somehow the folder got "owned" by root. As such, when I mount the card in Ubuntu so as to make backups of all the data on it, I am 'not allowed' to copy that folder (which is named Lost+Found). The other two folders on that partition are owned by me, so not a problem. 

I prefer to work in the GUI whenever I can. :)

For graphical applications use gksu.

You should also read about Linux permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

You can change ownership and permissions of anything in your home directory, but you should not, especially as a new user, change ownership and / or permissions of system files.

There is almost never a need to log into gnome or KDE as root and you should not run network applications, such as firefox, as root.

---

### Post by htrp on 2011-01-04
It is more than a bit strange that the root is disabled by default. Anyway, it can (and should in my opinion) easily be activated however.

chers
Tomas

---

### Post by Crazedpsyc on 2011-01-04
For future notice, to change file permissions on a file owned by root, use:
```
gksudo nautilus /path/to/file/
```
(without the actual file name) (nautilus is the file browser)
or to directly change it without opening nautilus,
```
sudo chown [NEW OWNER] /path/to/file.name
```
to change the owner, or:
```
sudo chmod a+[PERMISSION] /path/to/file.name
```
where [PERMISSION] is one or more of the following:
- r: read
- w: write
- x: execute

---

### Post by Hippytaff on 2011-01-04
> **bodhi.zazen said:**
> 

You should also read about Linux permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

  
+1
It's an excellent security feature ;-)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2011-01-04
> **htrp said:**
> It is more than a bit strange that the root is disabled by default. Anyway, it can (and should in my opinion) easily be activated however.

chers
Tomas

It may seem strange at first if you are new to Ubuntu, but it is how Ubuntu manages security and in general it works well.

There is almost never a need to activate the root account and you should not do so unless there is not other option.

Use sudo and gksu.

> **Crazedpsyc said:**
> For future notice, to change file permissions on a file owned by root

That is extremely bad advice to give to new users. There is almost never a need to change ownership or permission on any file or directory outside of $HOME.

---

### Post by sisco311 on 2011-01-04
> **htrp said:**
> It is more than a bit strange that the root is disabled by default.

I think, the term "root is disabled" is a little bit confusing. It's a shorthand for "the root account is disabled for login" or in other words "the root account password is locked".

---

### Post by Hippytaff on 2011-01-04
When I first started using ubuntu I found the sudo thing strange and annoying until I read up on it. ;-)

---

### Post by Zoandar on 2011-01-04
> **coffeecat said:**
> Why do want to copy the lost+found folder? It should be empty. It's only used for recovering file fragments after repair of a damaged filesystem. Best leave it alone. It should be owned by root. And even if you change the ownership, it will probably get changed back to root at the next filesystem check.

The only reason I addressed this issue is that, before I flashed the alternate ROM to the phone, that Lost+Found folder on the SD card's EXT partition was never locked. I was able to simply copy "all" the files from that partition, as well as the root partition of the card, to keep a backup. I was not fully aware of its purpose or any reason it might be better to have it locked down. I just knew it "changed" and so I wanted to change it back :)

Actually, it has always been empty. I just wanted to be 'thorough' in my backup routines. Thanks for explaining what it is for. I won't worry about it anymore. 

I should point out that, although I know and understand the reasons for these 'permissions' issues, I do not like them at all. I do not like them in Windows 7, nor in Linux. One of the reasons I moved from Windows Mobile to Android was the whole issue of 'freedom' to not be fenced in and spoon fed. I am more than willing to accept that if I screw something up, it was my fault. I don't like someone ever telling me I 'can't' access a file on my own computer. :) It just goes against my nature. I am sure it works for some people, but I am just not one of them. :grin:

Thanks to all of you who chimed in and helped me figure out what is going on here. However, in the interim, I found what I needed to know and the problem has been rendered solved. It will be interesting to see if the permissions on the folder get reassigned to root in the future, as you mentioned. If it does I won't concern myself with it again.

---

### Post by Crazedpsyc on 2011-01-05
> **bodhi.zazen said:**
> 
That is extremely bad advice to give to new users. There is almost never a need to change ownership or permission on any file or directory outside of $HOME.
Sorry, but I think most people on here are eager to *learn* not find out it is often a bad thing to do. I should have said it is not wise to change ownerships without the complete knowledge of what it will effect, but I forgot.

How can a user move past the "new user" stage without *learning*? I certainly would have wanted to know that bit of information even on my first day using my new UNIX box, not only for changing the ownership of Root's files, but for changing ownerships between normal users.
Note to PO: you should not use "sudo" when changing ownerships on your own files ;)

---

### Post by Zoandar on 2011-01-05
Speaking of new users and learning things, why does it always seem to be that whenever a new user asks for help they are always directed to use terminal commands instead of the GUI? Being new, one certainly has far less understanding of how to use the terminal, much less the strange looking commands that are used there, than they understand how to use a GUI? 

Case in point. - I wanted to format the SD card for my Android phone to make an EXT partition when I rooted it. I had two choices. Follow some online TWELVE PAGE (not kidding here) set of instructions on how to do it in terminal. OR - Burn and use a GPARTED boot disc, which has a GUI, which I completed in less time than it would take to even READ those 12 pages? 

The choice was clear. 

I did find instructions to enable the root user account for Ubuntu by searching online. It solved my problem in minutes, rather than the much longer time it would have taken me to figure out how to do what I wanted to do in terminal. 

Ubuntu has a GUI. It puts a friendly face on Linux. I prefer to use the friendly face. :)

Zoandar

---

### Post by Chesamo on 2011-01-05
> **Crazedpsyc said:**
> How can a user move past the "new user" stage without *learning*?
"Learning" doesn't always have to mean "learn the hard way".

> **Zoandar said:**
> Case in point. - I wanted to format the SD card for my Android phone to make an EXT partition when I rooted it. I had two choices. Follow some online TWELVE PAGE (not kidding here) set of instructions on how to do it in terminal. OR - Burn and use a GPARTED boot disc, which has a GUI, which I completed in less time than it would take to even READ those 12 pages?
You can install and run GParted just fine in an Ubuntu install -- no need to burn a boot CD. It just won't let you format the OS disk, for obvious reasons.

> **Zoandar said:**
> I did find instructions to enable the root user account for Ubuntu by searching online. It solved my problem in minutes, rather than the much longer time it would have taken me to figure out how to do what I wanted to do in terminal.
The problem here is that *you will never need to log in as root in Ubuntu*. Ubuntu includes the gksudo and kdesudo (for KDE) front-ends that make needing to log in graphically as root a completely moot point. Additionally, most applications that need root permissions (such as the Users and Groups applet) have an "unlock" button that will ask for permissions.

You can browse and use the graphical Properties manager by executing the code ```
gksudo nautilus .
``` which will open a Nautilus window, with root permissions, in your home directory. The only, *only* time I have ever had to log in as root was to perform hardware signal echoing on my laptop. Leaving root disabled closes a massive security hole in GNU/Linux. There is no reason to make graphical login possible.

It is also against the rules of this forum to tell users how to activate graphical login as root.

---

### Post by TechWiz2100 on 2011-01-05
Zoander I think you will just have to come to terms with file permissions because every operating system in existence uses them in some way, shape, or form... Even android which is based on a linux kernel uses permissions because that's just how things work best. It would be rather stupid to leave system critical files open to be modified by any random stranger (e.g hackers) or application (e.g viruses) and it would be even worse to allow someone to log in with the power to royally screw up everything in the system because they totally own everything. Permissions are not for noob proofing and they certainly have their benefits.

And in response to your comment about people listing off commands vs GUI, you have to realize that the objective of linux is to have a "free" OS where you can modify anything and everything on your own at your own risk and/or benefit. There are several GUI libraries out there like Gnome, KDE and XFCE which all can have the same UI for each program or can be radically different (check out the Gnome and the KDE versions of nvclock in Ubuntu Software Center). The programs that are run by those GUI on the other hand, rarely change from linux to linux unless the user personally made modifications to source in which case they would already know how the app works anyway.

I personally feel that if you really want to get into what linux is, you need to learn to get down and dirty with terminal because one way or another, linux is just a bunch of programs running on a terminal console anyway. Go ahead, press Ctrl + Alt + F1 thru 7 and see what linux looks like without the GUI and get a feel for what the system is at the core.

---

### Post by aysiu on 2011-01-05
Seems to really be more a discussion than a technical support thread. Moved to the Cafe.

---

### Post by Zoandar on 2011-01-05
Thanks for all the info. You good folks are reminding me why I didn't like Linux the last time I gave it a go. I always thought it was all about being free from being caged in (as my M$) but it really is just another set of restrictions. :)

OK, I did get gksudo nautilus to work, but also in the process 3 error messages were generated within the still open terminal window. If these are "normal" when entering those commands then I won't be concerned. If they indicate something is 'broken' in this Ubuntu installation I would like to know about it. 

They are:

(nautilus:1937): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
eedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '1937'

(nautilus:1937): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

---

### Post by Zoandar on 2011-01-05
> **aysiu said:**
> Seems to really be more a discussion than a technical support thread. Moved to the Cafe.

It only seems that way to someone who is comfortable and used to using the terminal to do everything on their computer. For me, it was a way of saying "when I ask for help, please don't give me terminal commands". :)

---

### Post by aysiu on 2011-01-05
> **Zoandar said:**
> It only seems that way to someone who is comfortable and used to using the terminal to do everything on their computer. Actually, no, since I am not comfortable with and used to using the terminal to do everything on my computer.

If you have a specific task you want to accomplish that you need help with, start a thread on that. As you can see from the last few pages of this thread, it really has just ended up as a discussion.

---

### Post by Kalimol on 2011-01-06
The errors you got in the terminal are normal. Anyway, I always get them. I actually have a couple of Nautilus scripts set up for launching Nautilus and Gedit with elevated privileges, so that I don't have to type when I'm tweaking things - just right click the item, select the script, and enter my password. Terminal's necessary and efficient for a lot of things, but I still try to avoid it as much as I can.

I dispute the assertion that a new user can't possibly encounter a situation where he or she might need to change permissions on a file - I had a read-only file stuck in my trash bin once, very embarrassing - but admittedly, even that *was* inside Home, and changing system files without a very clear idea of what they do can *only *lead to pain.

Seriously, though, Zoandar, don't take it *personally* that you have to type a password for some things. It doesn't mean you're being "restricted." You can edit anything. You just need to know what you're doing, first. = ) The fact that you can't edit those files from your normal, non-elevated login means that other applications can't, either, which is a protection not just from malware but from sloppy code in third-party apps. (Any stupidity sufficiently advanced qualifies as malice....) 

It doesn't make any sense to compare that to commercial software excluding options for exclusion's sake, like your Windows Phone experience. You're not going to encounter that in Ubuntu. Technically, you have far worse in Android unless it's rooted, because *exactly these permissions we're discussing* are *inaccessible* by design on a stock Android phone.

And as for why tutorials often use the terminal rather than the GUI - because in *most* cases, it's actually faster, because two words in the terminal can translate to finding a particular app, selecting it, navigating to a particular tab, and making a change; simultaneously, it *does* give the user a better sense of what's actually going on in the background, because the GUI is just an interface for those values. 

And never mind that some system applications just don't have a GUI at all, partly because you're likely to use them once in a lifetime and can probably be bothered to type a couple of words into them if need be. = )

---

### Post by oldos2er on 2011-01-06
> **htrp said:**
> It is more than a bit strange that the root is disabled by default. Anyway, it can (and should in my opinion) easily be activated however.


It is; a google search will attest to that. Giving that information to newbies is frowned upon for obvious reasons.

---

### Post by bodhi.zazen on 2011-01-06
> **oldos2er said:**
> Giving that information to newbies is frowned upon for obvious reasons.

This ^^

We do not mind if you teach new users and if you want to post on how to enable the root account be sure to include the risks and how to reverse it.

It is easier and less typing to simply refer them to the "RootSudo" page :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Doing so keeps everyone happy - new users get educated .

There is no need for you to "look smart" by posting an abbreviated command or two and data loss is seriously not funny.

The point is to educate new users without using the school of hard knocks.

---

### Post by perspectoff on 2011-01-06
OMG. Lots of misinfo here.

The root password is not set by default. You have to set it to be able to use the root account:

sudo passwd root

Then you can login as root:

su

or

sudo su 

or using one of the other methods already mentioned.

There are many many things in Linux that must be done with root privileges. Being the root user is useful if you are doing many of them at once, but is otherwise generally not needed.

Don't listen to the crazies who say you'll fry your system logging in as root -- that's nonsense. It's better not to do it routinely, but for large scale changes it's sometimes worthwhile.

Plus, there's fakeroot which negates a lot of the security supposedly gained by using sudo most of the time, and lots of other bad habits that can compromise your system.

Login as root only when absolutely necessary, but don't fear it like some crazed old nanny goat.

More info:

Ubuntuguide.org
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Assign_a_root_password](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Assign_a_root_password)

---

### Post by cariboo on 2011-01-06
> Don't listen to the crazies who say you'll fry your system logging in as root -- that's nonsense. It's better not to do it routinely, but for large scale changes it's sometimes worthwhile.

Didn't the op say earlier in the thread that he wanted to change ownership of all the files on the system to his user name? Isn't that a perfect way to bork the system?

The way I look at it, if a new user has to come to the forum to ask how to enable the root account, then they aren't ready for it. The information is readily available with a quick google search.

---

### Post by hawkmage on 2011-01-06
I can understand the mindset of logging in as root but it is not a good idea.  I deal with configuring and maintaining Linux/AIX/Solaris servers every day and I do not log into any of them as root.  I use sudo for everything that requires elevated permissions.  

Will logging in as root destroy your system? No, but it will allow minor mistakes to trash your system where as if it was done as a non-privileged account you would just get an access denied error.

---

### Post by TechWiz2100 on 2011-01-08
I have to agree with all who suggest keeping root off. While not the worst thing you can do to a setup, I personally feel its pretty far up there because in most cases, sudo works just fine and its not like the average user is going to be sudo-ing 24/7.

If you do need to be in root mode all the time, you can enable the root account but its rarely ever needed on a constant basis. I ran Fedora 5 on my PS3 under the root account because thats all there was and I was too lazy to make another account. The system ran fine but there was no need for me being in root all the time.

For the average user, the root account isn't needed for login in any case.
For average commands theres sudo, for everything else theres sudo su

---

