---
title: "Upgrade to 15.10 failed"
date: 2016-02-07
forum: New to Ubuntu
---

### Post by chris-burmajster on 2016-02-07
Hi Everybody,

My upgrade to 15.10 failed. See picture:  Can you see the writing? It's haphazard. Also, it doesn't let me log on.

Chris

---

### Post by Bashing-om on 2016-02-07
chris-burmajsterl Hello;

No the image is of little help .
How far did the upgrade process go ?
Did you arrive at 15.10?
From  the login screen, does the key combo ctl+alt+F1 yield a console interface ?
then post back the results of terminal commands:
```

cat /etc/apt/sources.list | nc termbin.com 9999
sudo apt update | nc termbin.com 9999
sudo apt -y upgrade | nc termbin.com 9999

```
the result is a URL back in terminal, pass these links back here, we then access the files at the paste site .
From these results we get an idea of where the system stands, and what needs to be done .

[INDENT][INDENT]look'n to see
[/INDENT][/INDENT]

---

### Post by chris-burmajster on 2016-02-07
Hello Bashing-om,

The upgrade process seemed to complete. I arrived at a 15.10 login screen, but could not enter my details. Yes, the CTL+ALT+F1 yielded a console interface, but it allowed me to login, just that. I'm going to try the sources.

Chris

Hello Bashing om,

The console interface says "The CLI interface is unstable".

Chris

---

### Post by Bashing-om on 2016-02-07
chris-burmajster; And .... 

Is this console interface usable ? You are able to login to the system ?

If so provide please the requested files .


[INDENT][INDENT]we see then
[INDENT][INDENT][INDENT]where we go from here
\[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris-burmajster on 2016-02-08
No, it's not usable. I'm not able to login to the system. What do I type to login to the system? If it's just username and password then that's OK, but where do I go from there?

---

### Post by monkeybrain20122 on 2016-02-08
Did you make a separate /home. If you did the easy way is to just reinstall and forget about "upgrade" in the future. It is a problematic process that takes a long time. A fresh install takes about 15 minutes.If you don't have a separate /home backup your data (you can boot into a live usb and then from it access your home and move the data) repartiton, create a /home and do a fresh install.  It may take long because of transferring your data to the backup and transferring it back after fresh install. But I would still prefer doing that than trouble shooting a blotched upgrade.

If your system is prestine (i.e without a lot customisation and third party apps) you can do a fresh install a lot faster than upgrade; if your configuration deviates significantly from default  "upgrade"  may be tempting because you don't want to spend the time on recreating your configuration,  but the rub is in that  case upgrade very likely will  fail with some errors,  so again fresh install is the way to go. So really "upgrade" is neither here nor there, new users should be warned.

---

### Post by chris-burmajster on 2016-02-08
No I didn't make a separate /home. It looks as if I will have to re-install.

Right. I've just re-installed. Same problems. I can't login to either my own or the guest. I get an error message that's so quick that I don't have time to view it.

---

### Post by Bashing-om on 2016-02-08
chris-burmajster; Ouch !

Well ...
> 
Right. I've just re-installed. Same problems.

What release did you re-install ? We boot this time to terminal, and the process differs depending on the initiate system ( 14.04 == upstart; 15.10 == systemd ) . We will find out what is not taking place.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by chris-burmajster on 2016-02-08
I re-installed 15.10, given that 15.04 was not of any use. Presumably 15.10 has systemd and I don't know anything about it at all.

---

### Post by Bashing-om on 2016-02-08
chris-burmajster; Yeah ... 

Release 15.10 is systemd.
In small steps, let's see what condition the condition is in.
I am going to "assume" that you verified the .iso file and also verified the burn .. the foundation thus secured.

Let us boot to terminal (TTY1).

Reboot to the grub menu ; 'e' key for edit mode -> boot parameters screen;
arrow down to the line starting with linux and across to "quiet splash" replace these terms and all after  with " systemd.unit=multi-user.target " - without the quote marks .
key combo ctl+x to continue the boot process to TTY1.

can you login here with username and password ? no response to the screen when password is entered, enter pass word blindly and hit the enter key

If you can get this far .. next from here we see what happens when we start the GUI from terminal .

[INDENT][INDENT]open our tool box
[INDENT][INDENT][INDENT][INDENT]see what fits
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris-burmajster on 2016-02-09
You can assume that I verified the iso file and the burn. I booted to tty terminal. How do I re-boot to the grub menu? I'm not very experienced here.

---

### Post by Bashing-om on 2016-02-09
chris-burmajster; Sheesshhh ...

Now I am the one that is confused:
> 
You can assume that I verified the iso file and the burn. [color=green]I booted to tty terminal[/color].

At this TTY (terminal) are you able to log into the system - username and password ? There will be no response to the screen when pass word is entered .

Not a thing we can do until such time as we have a terminal from either the install or from the liveDVD(USB). We re working hard to gain a terminal ; In some shape form or fashion. Depending on what terminal from where is the determining factor of what we must do to gain access to effect a resolution to your situation.

Be aware, that "not to know" is not a sin . None of us were born with knowledge .. takes time and effort to learn. We have all been at the start of the learning curve and we do understand.

We need this terminal in order to determine what condition the system is in. 

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by chris-burmajster on 2016-02-09
Hi Bashing-om,

I have found that I cannot always boot into the tty with username and password. I have UEFI and I wonder if that is stopping me. 

Chris

---

### Post by Bashing-om on 2016-02-09
chris-burmajster; Welp;

> **chris-burmajster said:**
> Hi Bashing-om,

I have found that I cannot always boot into the tty with username and password. I have UEFI and I wonder if that is stopping me. 

Chris

I have limited experience with UEFI. from what I am aware of . one must boot in the same configuration as that of the install. Else the boot code will not be located .


We continue this when you are at a usable terminal .

[INDENT][INDENT](C)ommand (L)ine (I)interface
[INDENT][INDENT][INDENT]so we can have a conversation with the system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris-burmajster on 2016-02-10
Ready at the CLI!

---

### Post by Bashing-om on 2016-02-10
chris-burmajster; Ho Kay !


Then, when you are comfortable run the terminal commands:
```

cat /etc/apt/sources.list | nc termbin.com 9999
sudo apt update | nc termbin.com 9999
sudo apt -y upgrade | nc termbin.com 9999

```

Remember, the result is a URL back in terminal .. pass these links back here and we can get an assessment of the state of the system, and go from there .


[INDENT][INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT][/INDENT]

---

### Post by chris-burmajster on 2016-02-10
First line: no such file or directory. Use netcat.
Apt does not have a stable CLI interface yet. Use with caution in scripts.
[http://terbin.com/icdc](http://terbin.com/icdc)

These are the lines indicated.

---

### Post by Bashing-om on 2016-02-10
chris-burmajster; Ouch (??)

On that 1st command, my return:
[http://termbin.com/wyoe](http://termbin.com/wyoe)

Which begs the question that:
> 
First line: no such file or directory. Use netcat.

does the control file even exist on your system ? IT must be to do !
What returns:
```

ls -al /etc/apt/sources.list

```

Your update status :
> 
[color=red]119 to upgrade[/color], 0 to newly install, 0 to remove and 0 not to upgrade.

indicates the system was not updated prior to the upgrade attempt . Houston, we may have a problem. We change our focus and see if we can get this system updated. In order to do this we must have a valid sources.list file and now I certainly want to see this file .

[INDENT][INDENT]package management
[INDENT][INDENT][INDENT]how great thou art
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by chris-burmajster on 2016-02-10
I have tried again and got the following from the system: -r -  -r-- 1 root root 2  Feb 1  1 :  /etc/apt/sources.list

---

### Post by Bashing-om on 2016-02-10
chris-burmajster; Ouch !!
> 
-r - -r-- 1 root root 2 Feb 1 1 : /etc/apt/sources.list


what have you done ?
As a reference; my output:
```

sysop@1404mini:~$ ls -al /etc/apt/sources.list
-rw-r--r-- 1 root root 3508 Dec  4 14:00 /etc/apt/sources.list
sysop@1404mini:~$

```
note that on the 1st field root has write ( -rw-r-) the 'w' - access - your's does not ... AND my file size is '3508' and your file is extremely meager at '2' bytes .

Maybe a typo on your part ? show us that complete file:
```

sudo cat /etc/apt/sources.list | nc termbin.com 9999

```
where here as we do not know that 'you' can access the file we elevate your privileges to Super User DO it .

If we have no sources.list file . I am very skeptical of fixing this upgrade . With no foundation, how can we push in any direction ? Others input here are very welcome !

[INDENT][INDENT]what to do OH
[INDENT][INDENT][INDENT]What to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

