---
title: "how do I know which version of Linux is installed on computer?"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by Beautymist on 2013-06-21
Hi,

Sorry if this has been asked before, I haven't found anything about it here yet.

OK, this is my absolute beginner question:

I have access to multiple computers, all under Linux - not installed by me, but different variants (xUbuntu and others) and versions.

Where (in which folder) is hidden the valuable information about what variant and version of Linux is installed on any given computer?

Once I know which variant/version I'm dealing with, I will be able to ask more specific questions on this forum.

Thank you!

-BM

---

### Post by Cheesemill on 2013-06-21
There is no one command that will work on all the different versions of Linux but try the following couple of commands...
```
cat /etc/issue
lsb_release -a
```

---

### Post by siddharth007 on 2013-06-21
```
uname -a
```

This will tell you a lot more than the previous commands.

---

### Post by user_of_gnomes on 2013-06-21
> **siddharth007 said:**
> ```
uname -a
```

This will tell you a lot more than the previous commands.

Not under Ubuntu.

---

### Post by Grenage on 2013-06-21
> **siddharth007 said:**
> ```
uname -a
```

This will tell you a lot more than the previous commands.

Agreed, but for the true newcomer, the previous command is a lot friendlier with the output (A nice full name, no verbosity).   I'll also throw in another option:

```
cat /proc/version
```

---

### Post by Beautymist on 2013-06-21
Thank you all so much!

I tried the last suggested code and it worked just fine.

This is what I got:

> 
Linux version 3.5.0-26-generic (buildd@lamiak) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013

Now I wonder why it doesn't say I am using xUbuntu?

Thanks again,

-BM

---

### Post by Beautymist on 2013-06-21
the LSB code yielded the following result:

> Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal



Stiil, no (at least not clear to me) mention of xUbuntu there. Any idea why?

-BM

---

### Post by varunendra on 2013-06-21
> **Beautymist said:**
> Now I wonder why it doesn't say I am using xUbuntu?

For that try what Cheesemill suggested. Or just-
```
lsb_release -d
```
For only the 'Distribution and version' of Ubuntu you have.

**PS:**
Saw your intro in the intro thread, quite interesting, and even more interesting seems the task you are going to handle. :P

---

### Post by varunendra on 2013-06-21
> **Beautymist said:**
> Stiil, no (at least not clear to me) mention of xUbuntu there. Any idea why?

Because it is basically Ubuntu, with only the "Desktop Environment" being a different one (XFCE).

---

### Post by grahammechanical on 2013-06-21
Another command is

```
cat /etc/os-release
```

On the the version of Ubuntu I am using now (I have several) I get this

> NAME="Ubuntu"
VERSION="13.04, Raring Ringtail"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 13.04"
VERSION_ID="13.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"

If you are curious about the actual hardware in all those machines and you would like to have a record of what is there, run

```
sudo lshw -html >hardwareprofile.html
```

Give it a little time and it will produce a profile of the hardware in HTML format that can be opened in a web browser. The file name will be hardwareprofile.html. You can give each one a distinctive name according to the machine.

From this link you can learn how to visually identify the different desktop environments

[http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available)

```
env | grep DESKTOP_SESSION=
```

gives this on my machine

DESKTOP_SESSION=ubuntu

What does is give for the other flavours of Ubuntu?

Regards.

---

### Post by vasa1 on 2013-06-21
Also,
```
env | grep XDG_CURRENT_DESKTOP
```

---

### Post by Beautymist on 2013-06-21
> **varunendra said:**
> Because it is basically Ubuntu, with only the "Desktop Environment" being a different one (XFCE).

Right, yes, I knew that. Thanks for reminding me of that fact!

I nickname XFCE "the cute & fat little mouse" - :lolflag:

---

### Post by Beautymist on 2013-06-21
> **varunendra said:**
> Saw your intro in the intro thread, quite interesting, and even more interesting seems the task you are going to handle. :P

Thanks, varunendra!

Actually I *enjoy* learning new stuff, I'm a "curiosity killed the cat" type. ;)

---

### Post by oldfred on 2013-06-21
Some more:

fred@fred-Precise:~$ env | grep XDG_CURRENT_DESKTOP
XDG_CURRENT_DESKTOP=GNOME
fred@fred-Precise:~$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm
fred@fred-Precise:~$ echo $DESKTOP_SESSION
gnome-fallback
fred@fred-Precise:~$  gnome-shell --version
GNOME Shell 3.4.1

You can also dump lots of internal data.

 If using sudo, run any sudo command like ls first. Sometimes sudo & redirect have issues.
sudo ls
Files saved in your home folder
To save it as a file use
sudo lshw > hw.txt

   HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

   udevadm info --export-db > file.txt
udevinfo -a -p $(udevinfo -q path -n /dev/sdd)

   Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

   Internal efi details
ls /sys/firmware/efi/vars

---

### Post by varunendra on 2013-06-21
> **Beautymist said:**
> I nickname XFCE "the cute & fat little mouse"
:lolflag:

> **Beautymist said:**
> Actually I *enjoy* learning new stuff, I'm a "curiosity killed the cat" type. ;)
Hope you've realized by now that there are a lot of friendly people here to save you from being killed :P

Just ask whatever questions you have.

As a side note, if one of your systems have enough RAM (2GB or more is recommended), you may find Virtual Machines (using virtualbox, vmware etc. platforms) a very good option for safely testing and even productively running multiple operating systems at once. Although I suspect, by the hint of your experience so far, that you know about them as well ! :)

---

### Post by Beautymist on 2013-06-21
> **oldfred said:**
> 
   Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

Thank you, oldfred!

That dmidecode thingy seems like a very interesting command. will definitely try & tell you about it.

-BM

---

### Post by Beautymist on 2013-06-21
Thank you all for the invaluable information and friendly advice! \\:D/

-BM

---

### Post by Beautymist on 2013-06-21
OK, did the dmidecode command with sudo and got my bios.txt - what a neat file!
Definitely a keeper!

Thank you, oldfred!

Btw, what does DMI mean?


-BM

---

### Post by oldfred on 2013-06-21
I had not idea.

But 
man dmidecode

> SMBIOS stands for System Management BIOS, while DMI stands for  Desktop
       Management  Interface. Both standards are tightly related and developed
       by the DMTF (Desktop Management Task Force).


---

### Post by Beautymist on 2013-06-21
> **oldfred said:**
> I had *no* idea.

But 
man dmidecode

Aaaah! the infamous "man" command! I *always* forget that one! Silly me.

Thanks again, oldfred!

-BM

---

### Post by HiImTye on 2013-06-21
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
```
man
``` is one of my most used commands, one can't possibly know every switch to every command ;)

---

### Post by Beautymist on 2013-06-22
> **HiImTye said:**
> ```
man
``` is one of my most used commands, one can't possibly know every switch to every command ;)


...Exactly!

;)

---

