---
title: "Skip Sudo command asking password?"
date: 2005-03-11
forum: Programming Talk
---

### Post by Tubuntu on 2005-03-11
How I can skip sudo command asking password in a script or in a program launchers? Example so k3b would not ask everytime sudo password when i start the program? 

I would only like to disable sudo password in my own script and in a couple of programs, so no permanent disable option..

-Thanks

---

### Post by bored2k on 2005-03-11
[QUOTE=Tubuntu]How I can skip sudo command asking password in a script or in a program launchers? Example so k3b would not ask everytime sudo password when i start the program? 

I would only like to disable sudo password in my own script and in a couple of programs, so no permanent disable option..

-Thanks[/QUOTE]
 Try this
[http://ubuntuguide.org/#usesudowithoutpasswordprompt](http://ubuntuguide.org/#usesudowithoutpasswordprompt)

---

### Post by Burgundavia on 2005-03-11
You can also very control sudo to a specific command. So you could have k3b ask for no password, while leaving it for all other programs.

Corey

---

### Post by Tubuntu on 2005-03-11
[QUOTE=Burgundavia]You can also very control sudo to a specific command. So you could have k3b ask for no password, while leaving it for all other programs.

Corey[/QUOTE]

--> Sorry, but how I can do that?   (very control sudo?)



bored2k: I dont want to disable Sudo asking password for all  program
only disable it from k3b..
Thank you anyway T

---

### Post by toojays on 2005-03-11
You control sudo through the "sudoers" file. To edit this file, run "sudo visudo".

I haven't tested this, but I think the following would allow all users in the "cdrom" group to run "sudo k3b" without needing a password:```

%cdrom    ALL = NOPASSWD: /usr/bin/k3b

```
For more information, see the sudoers man page.

---

### Post by Tubuntu on 2005-03-13
Best thanks to you toojays  :)

---

### Post by jdong on 2005-03-14
Use extreme caution with granting all-trusting sudo access:

1. Any script running under your name can try to sudo to root -- Malicious programs can easily gain root access under your account, if you have passwordless sudo.

2. A program running as root easily allows other programs to be run as root. Don't grant sudo -- even on individual programs -- to all users. It's pretty easy to turn K3b into a text editor, then grant more sudo privs!

---

### Post by steffen on 2005-04-20
This works for me:

> sudo visudo
add: > %steffen        ALL = NOPASSWD: /usr/bin/k3b
%steffen        ALL = NOPASSWD: /usr/bin/amarok

(note: I am in group 'steffen'. Look in your User and Groups section in Gnome preferences)

---

### Post by phantom74 on 2008-02-06
hi all,

iv tried to find documentation on re-enabling the sudo password and i couldnt find it out. everything is to vage and link that was posted "http://ubuntuguide.org/#usesudowithoutpasswordprompt" its like the frikin Bible, so i couldnt find what i needed its just too mutch info for this specific subject.

first off, im running gutsy on Gnome not kde, so, for my understanding this is done diferently.

a friend of mine did this in my computer, he told me i wouldnt have to type in the password everytime i run a sudo command, so i let him do that (it was another thing i could learn to) but i dont want my box exposed to this weekness.

Can somebody please leed me to the readings were this is done, or just post the code so i can do it quikly please? i dont feel confortable with this weekness in my box! i think he edited 2 diferent files, cant remember witch ones!

Help!

---

### Post by jken146 on 2008-02-06
He probably edited /etc/sudoers.  You can edit this yourself by typing ```
sudo visudo
```

Look for anywhere that says NOPASSWD and remove those bits or comment them out (put a # in front of them).

---

### Post by phantom74 on 2008-02-06
i dont think this is it, i remember that my friend edited tow files i think, and this is my sudoers file:



# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL






all lines are comented out, so i dont understand!

ps: i do remember my friend edited the group files, something with the weel group.

help please!

---

### Post by jken146 on 2008-02-06
Well, I'm no expert on sudo, but I do know that some distros use the wheel group in a similar way to how Ubuntu uses the admin group.  I see that only the admin group is mentioned in your sudoers file.  Otherwise the file looks very much like mine.  You could try removing the wheel group, if it exists.

Check out the man page for sudo for a proper treatment of the subject.

---

### Post by RezoApio on 2009-01-12
Hi everybody,

I am struggling with the same problem and no matter what I do it does not work.

This is my sudoers file part with the modifications

```
# User privilege specification
root    ALL=(ALL) ALL
william ALL=(root) NOPASSWD: /usr/sbin/g15daemon
william ALL=(root) NOPASSWD: /usr/sbin/visudo
```

the sudo -l command gives 
```
william@attigliano:~$ sudo -l
User william may run the following commands on this host:
    (root) NOPASSWD: /usr/sbin/g15daemon
    (root) NOPASSWD: /usr/sbin/visudo
    (ALL) ALL
william@attigliano:~$ 
```

And still when I do sudo visudo I am asked for a password ?

Where is my mistake ?
(I have read and reread all the man sudo pages and still no ideas....)

Thanks a lot.

---

### Post by RezoApio on 2009-01-12
Ok Gotcha !! 
With the help of a good friend that found the ref to [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/131399](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/131399)

Problem is that the last line is uncommented and it overrides what I have done.

that last line 
 # Members of the admin group may gain root privileges

%admin ALL=(ALL) ALL

allow members of the amdin group to run any command BUT with a password. 

So removing password for some command before this one will not work !!

Have a very happy new year !!

---

### Post by majedaly on 2010-08-24
> **RezoApio said:**
> Hi everybody,

I am struggling with the same problem and no matter what I do it does not work.

This is my sudoers file part with the modifications

```
# User privilege specification
root    ALL=(ALL) ALL
william ALL=(root) NOPASSWD: /usr/sbin/g15daemon
william ALL=(root) NOPASSWD: /usr/sbin/visudo
```

the sudo -l command gives 
```
william@attigliano:~$ sudo -l
User william may run the following commands on this host:
    (root) NOPASSWD: /usr/sbin/g15daemon
    (root) NOPASSWD: /usr/sbin/visudo
    (ALL) ALL
william@attigliano:~$ 
```

And still when I do sudo visudo I am asked for a password ?

Where is my mistake ?
(I have read and reread all the man sudo pages and still no ideas....)

Thanks a lot.
This approach worked for me on ubuntu Desktop, but did not work on Ubuntu server, I don't know why

---

### Post by chrisTGc on 2010-11-22
> **majedaly said:**
> This approach worked for me on ubuntu Desktop, but did not work on Ubuntu server, I don't know why

Hi, just had the same problem here, to get over it i had first to add me to group root EG, in a terminal;

sudo usermod -a -G root chris


Then i had to hash out %ADMIN line in the sudoers file and all mods to sudoers to allow passwordless sudo commands where of the form, EG;

chris ALL = (ALL) NOPASSWD: /sbin/shutdown, /sbin/reboot

Be prepared next to boot into a live CD and remove the hash from the %ADMIN line if you get into trouble. I did but my system is working just as it should  even with the reversion.

Chris

---

### Post by rp88 on 2011-02-18
> **toojays said:**
> You control sudo through the "sudoers" file. To edit this file, run "sudo visudo".

I haven't tested this, but I think the following would allow all users in the "cdrom" group to run "sudo k3b" without needing a password:```

%cdrom    ALL = NOPASSWD: /usr/bin/k3b

```
For more information, see the sudoers man page.



Sorry to bring back a dead thread but I think I figured out why this wasn't working for a lot of people. The entry you put needs to be at the end, not at the top. Since the addition you make gets over-rid by another entry lower on in the sudoers file.

Here's what I did to run a specific program as sudo without prompting for a password in Meerkat:

Run this in terminal: sudo visudo
At the _**END**_ of the file, type in: "%yourusername ALL=NOPASSWD: /app/you/want/to/run/as/sudo" without the quotes

Hope this helps someone looking to run something as sudo without prompting for a password.

---

### Post by hakermania on 2011-02-19
```
echo "passwd" | sudo -S synaptic
```

---

