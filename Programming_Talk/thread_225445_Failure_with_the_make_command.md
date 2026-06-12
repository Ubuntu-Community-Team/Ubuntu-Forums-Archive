---
title: "Failure with the make command"
date: 2006-07-29
forum: Programming Talk
---

### Post by theDentist on 2006-07-29
Hi all,
I'm not new to programming but I am new to linux programming.  I have been trying to use Glade but cannot make an executable file.  The "make" command doesn't seem to be recognised by the bash terminal,(nor is it recognised ever, whatever I use it for!!). Because of this I never get to the "make install" command.  Could someone tell me how to get to the executable file. :-x 

Peter

---

### Post by ifokkema on 2006-07-29
> **theDentist said:**
> Hi all,
I'm not new to programming but I am new to linux programming.  I have been trying to use Glade but cannot make an executable file.  The "make" command doesn't seem to be recognised by the bash terminal,(nor is it recognised ever, whatever I use it for!!). Because of this I never get to the "make install" command.  Could someone tell me how to get to the executable file. :-x 

Peter
You're missing the 'make' program. Install the basic compiling stuff you need:
```
sudo apt-get install build-essential
```

---

### Post by theDentist on 2006-07-30
Thanks for the advice. just done it install OK

Peter

---

### Post by theDentist on 2006-07-30
Hi again,

I seem to have another problem, I am using Ubuntu 6.06 which I have found to be the best of all I've tried by the way,  I'm having a problem to login as root.  I am at this moment trying to update glib by installing 2.12.1 version.  I've got to the last stage "make install" which I need to be logged in as root.  How do I do this from the bash terminal??.  In fact how do I log in as root at the boot up, with other distros you type "root" and you password.  This doesn't work.  I am the only user.  When I'm in gnome, and want to do something which needs root login, it askes me and I just type the password in and it's OK.  But how do I get into root permnantly, From boot up and also from the terminal???   :( 

Peter

---

### Post by xtacocorex on 2006-07-30
For compiling I do:
```
./configure --prefix=/usr && make && sudo "make install" && make clean
```

That one line will build the entire source.

Hope this helps.

---

### Post by ifokkema on 2006-07-30
> **theDentist said:**
> Hi again,

I seem to have another problem, I am using Ubuntu 6.06 which I have found to be the best of all I've tried by the way,  I'm having a problem to login as root.  I am at this moment trying to update glib by installing 2.12.1 version.  I've got to the last stage "make install" which I need to be logged in as root.  How do I do this from the bash terminal??.  In fact how do I log in as root at the boot up, with other distros you type "root" and you password.  This doesn't work.  I am the only user.  When I'm in gnome, and want to do something which needs root login, it askes me and I just type the password in and it's OK.  But how do I get into root permnantly, From boot up and also from the terminal???   :( 

Peter
Ubuntu is slightly different using the root account. Are you familiar with the 'sudo' command? It allows you to run commands as root, using your password.
```
sudo make install
```
is what you're looking for. It'll run 'make install' as root.

If you really want to have a root terminal, use:
```
sudo su -
```

Have fun!

---

### Post by theDentist on 2006-07-30
Thanks, I'll give it a try 

Peter

---

