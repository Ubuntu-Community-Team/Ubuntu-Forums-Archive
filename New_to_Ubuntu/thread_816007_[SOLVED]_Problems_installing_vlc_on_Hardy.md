---
title: "[SOLVED] Problems installing vlc on Hardy"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Beaker Boy on 2008-06-02
Dear all

I'm trying to install vlc as my default DVD player in Hardy Heron but whilst following the how to posted by 'reassuringly offensive' on this matter, when I type in 'sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc' I get back 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.'  So when I type in 'dpkg --configure -a' I get back 'dpkg: requested operation requires superuser privilege'.  How am I not a superuser on my own laptop?  Can anyone help?

Many thanks

Newbie Mk2 - The return of the Heron

---

### Post by sdennie on 2008-06-02
I think you'll need to proceed dpkg command with "sudo".

---

### Post by rraj.be on 2008-06-02
The reason for your error is you have terminated an installation in the middle.

To get root rights

open terminal

 type

```
sudo -i
```

This will ask for your password.

enter it.

now you will be taken into your root acount and now you can run that command to clear the cache.

---

### Post by ukripper on 2008-06-02
Do this should be fine -

```
sudo dpkg --configure -a
```

enter your password.

---

### Post by derred on 2008-06-02
> **Beaker Boy said:**
> ...
'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.' 

Whenever you run an administrator command you have to preface it with the sudo command. This tells the system that you want to run the command as root

sudo dpkg --configure -a
This command will reconfigure all the programs installed on your system and it is extremely useful when a system update was interrupted (power cut off or the update was otherwise canceled at a inopportune time)

On a final note once you reconfigure the installed packages you probably should also run sudo apt-get update and sudo apt-get upgrade one more time. It can't hurt :)

Hope this helps,
Happy Herroning :-D

---

### Post by Beaker Boy on 2008-06-02
Thanks!  Sheesh I know nothing yet!  Also thanks to rraj.be!

---

### Post by derred on 2008-06-02
> **Beaker Boy said:**
> Thanks!  Sheesh I know nothing yet!  Also thanks to rraj.be!

No fret Beaker Boy. Just be sure to mark the thread as solved ;)

---

### Post by rraj.be on 2008-06-02
Just read this.

[digg.com/linux_unix/How_to_install_ANYTHING_in_Ubuntu_3]("digg.com/linux_unix/How_to_install_ANYTHING_in_Ubuntu_3")

It will help you a lot.

Further use synaptic package manager to install any thing because it will find all dependencies automatically in a GUI view.

---

