---
title: "Can`t set my root password"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Lakeside on 2008-10-20
I am quite a noob at this, so I am amazed I got this far (even had to get to my setup menu to change the bios so it would boot from the Ubuntu boot disk). After installing Hardy Heron on here, I thought I would start to learn how to actually use the server and following a tutorial I read, tried to set the password for the root (sudo password root, in the terminal).  The same username that I entered in the dialogue box while installing Hardy Heron appeared in the command line, but when I entered what I had set up as the password,(during same procedure) it said `error`or something like that.  I tried many times but it would not except that password, I even tried just using some other password there, but it didn`t like that either.  I would hate to do it all over again (I might tho, when 8.10 comes out lol).  Is there a work around.. Please could someone tell me what I did wrong thanks very much

---

### Post by timandjulz on 2008-10-20
Ubuntu does not set a root password and by default you cannot login as root.  You should sudo to get to root.

Google for Ubuntu and "root password" to find articles if you are interested in logging in as root.

[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)

Tim

---

### Post by Lakeside on 2008-10-20
Ooops, it finally let me do it (at least it says  unix password updated successfully). I just had to keep messing around with it.

---

### Post by PointyWombat on 2008-10-21
Becuase you should be using 'sudo', you don't really need to know the root password, let alone change it. The password you provided for your account during creation will grant you the priviledge of root when used with the sudo command. If you MUST change the root password, then you can use sudo for this.

```

user@box:~$ sudo passwd root
[sudo] password for user: <your normal password> 
Enter new UNIX password: <password you want for root>
Retype new UNIX password: <password you want for root>
passwd: password updated successfully
user@box:~$ su -
Password: <password you entered for root>
root@box:~#

```

I would suggest however, that you not even bother changing root's password. There's nothing that you can't do as root using sudo. If you do need to 'be' root though, you can just 'sudo -s' to root.

---

### Post by Lakeside on 2008-10-21
Fuzzy Wombat: I saw your reply just after I posted a second ago..I don`t really know what I`m doing, just following tutorials I find, it had as a first step `sudo passwd root`(to set root password) which I finally managed to do. I just want to use my server to host a website :-) is this step required then thanks and for the code.
*edit*  ok, I`m slow, but I just reread your post and I get it now. thanks
Timandjulz: thanks for the links :)

---

### Post by drakeman007 on 2008-10-21
Glad to read that Lakeside, im newbie too and i amazed with ubuntu, i tried mandriva, fedora before but ubuntu is the top por mi i feel much more comfortable with this... ubuntu is the best!

---

### Post by alphacrucis2 on 2008-10-21
> **Lakeside said:**
> Fuzzy Wombat: I saw your reply just after I posted a second ago..I don`t really know what I`m doing, just following tutorials I find, it had as a first step `sudo passwd root`(to set root password) which I finally managed to do. I just want to use my server to host a website :-) is this step required then thanks and for the code.
*edit*  ok, I`m slow, but I just reread your post and I get it now. thanks
Timandjulz: thanks for the links :)


Generally you should not set a password on root as it is not needed. Too late now though :) Just prefix the command you want to run as root with  sudo. This will prompt you for your own password. If you want to do a succession of commands as root just type sudo -i. You can then do a series of commands as root without typing sudo again in that session. I take it that you have installed the server version of Hardy?

---

### Post by hyper_ch on 2008-10-21
forum policy ([http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)) is not to ask and tell how to enable the root account.

---

### Post by jerome1232 on 2008-10-21
To get back to the way it was (root disabled) you would need this command it disables root's password again.

```
sudo passwd -l root
```

---

### Post by Lakeside on 2008-10-22
Wow, what an active, helpful forum! I love it :)  I was away from computer for a bit.. I see now that I should have asked `should I change the root password...`, not `how` as a tut had suggested I do so, and I would have read all this good advice before I went and did it!  But now I got to learn a useful thing about using `sudo` and `sudo -i`, thank you to alphacrucis2, PointyWombat, timandjulz, and jerome1232 for your helpful replies  (jerome, do you think this is something I should do, because I will try to do it then :) ) and hyper_ch, I want to apologize if I have mis-stepped by asking about the root..I don`t know all the rules yet, thanks for being patient with me.  I will be asking as to what tutorials I use from now on, because changing the password was actually in a tutorial :( Thanks for the encouragement drakeman007, Ubuntu is the best!

---

### Post by aimpau on 2008-10-22
> **hyper_ch said:**
> forum policy ([http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)) is not to ask and tell how to enable the root account.

Remember this always.

> **jerome1232 said:**
> To get back to the way it was (root disabled) you would need this command it disables root's password again.

```
sudo passwd -l root
```

You better do this now. Next time, use the sudo.

---

### Post by Lakeside on 2008-10-23
Yes, I will do that.  Leave it to me to commit a huge mistake with my first posting in this forum! (enquiring about the root.). I do not want to talk further about this, as it seems to be not a good subjectÉ (my question mark appears this way after new Hardy Heron install...) so I am going to ask permission first, if a mod wants me to pm them with the link to the tutorial which suggested to change the root..

---

### Post by Lakeside on 2008-10-23
ok, maybe I`m not understanding..but I took your advice, and entered  sudo passwd -l root, and it said `password changed`, then I typed in the password I had previously, and it said  `gdbm fatal: lseek error` I don`t know why.. And I just tried out a command (install ssh) : :~$ apt-get install ssh openssh-server and it replied like this:  E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?` I tried entering both passwords, but neither worked.

---

### Post by drowner on 2008-10-23
> **Lakeside said:**
> ok, maybe I`m not understanding..but I took your advice, and entered  sudo passwd -l root, and it said `password changed`, then I typed in the password I had previously, and it said  `gdbm fatal: lseek error` I don`t know why.. And I just tried out a command (install ssh) : :~$ apt-get install ssh openssh-server and it replied like this:  E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?` I tried entering both passwords, but neither worked.

Once you have disabled the root password, then log in as yourself.

You can run a command with root privileges by prefacing it with 'sudo'

so, in your instance, it would be

```
sudo apt-get install ssh openssh-server
```

It will then ask you for your normal password

---

### Post by bodhi.zazen on 2008-10-23
> **jerome1232 said:**
> To get back to the way it was (root disabled) you would need this command it disables root's password again.

```
sudo passwd -l root
```

LOL

This is the problem with setting a root password, it can break things.

This is not the way to re-lock the root account, please use usermod :

```
sudo usermod --lock root
```

See this bug report : [https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/238755)

---

### Post by jerome1232 on 2008-10-23
aren't they the same? or is it just a bug that one isn't functioning correctly 
```
       -l, --lock
           Lock the named account. This option disables an account by changing
           the password to a value which matches no possible encrypted value,
           and by setting the account expiry field to 1.

```

```
       -L, --lock
           Lock a user´s password. This puts a ´!´ in front of the encrypted
           password, effectively disabling the password. You can´t use this
           option with -p or -U.
```

---

### Post by bodhi.zazen on 2008-10-23
> **jerome1232 said:**
> aren't they the same? or is it just a bug that one isn't functioning correctly

It is a (nasty) bug. See the link I gave you for information.

I ran into this on a server install, the root account was enabled (by someone else I might add) and when I locked it with passwd -l root.

In my case, users could not log in at all, Big Ouch :(

---

### Post by Lakeside on 2008-10-23
Thanks guys (or girls, whichever :) I have things back to normal, I think.  Was able to use Jerome and Aimpu`s code, I just forgot to put `sudo` before my command..(as drowner had suggested- thanks) I was still catching on to what root really was, but now I know, to use the password assigned to my user (me) which I use when rebooting the computer (username and password) and that `sudo` makes you the root. I think. thanks for the help everyone. I just saw the previous post, but only after I`d just posted this one.. I wonder why sudo passwd -l root worked for me.. It seems to be, as I just used `sudo` and a command (to install ssh) and used my password for logging on as a user, and not the previous root password I had set..

---

### Post by mik_se7 on 2009-04-22
Hi, I'm new to Linux and i have been reading through loads of posts but as yet i have not found one that helps me with my root password problem.
 
I enabled root as instructed from another webpage using sudo passwd root ,but then this is where it falls apart, from what i have read it should then ask me what i want the new root password to be but it doesnt it just comes up with:
 
passwd: password updated successfully - everytime so now i have no idea what it is setting the password to?
 
can anyone help me all i wanted to do was edit the nsswitch.conf file but that says i dont have enough privilages when opening it in file manager and the terminal say edit/etc/nsswitch.conf - no such file or directory
 
this is my first time using linux and so far im wondering what all the fuss is about i tell windows what to do and it does it, but so far linux is like edit this and edit that just to do something simple getting very disheartend can anyone help :confused:

---

### Post by mlentink on 2009-04-22
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

