---
title: "Setting up an HP Laserjet 4M Plus Printer"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by johnlvs2run on 2008-07-27
I have seen this "don't run as root" message quite a few times, with the suggestion to set up a user account.
A few times this has been on instruction links on the net, but nothing was said of how to set up a different user account.

For example, this happened last night when I downloaded a driver for the printer.

Could someone tell me (1) why not run as root and (2) how to set up a different user account.

I'm the only one who uses this computer.  

Thanks.

---

### Post by gjoellee on 2008-07-27
When you are root, something happens (don't really know what), but it has something with the security to do.

SETTING UP A USER...
System->Administration->Users and Groups click on one account and unlock it. Then click add user. And fill in the fields...if you still are root click on manage groups and set to users.

(I am not 100% sure if this helps but it is worth a try)

---

### Post by Vakman on 2008-07-27
They say not to do things as root because if you are root you can end up modifying your system in a harmful way because root has access to things that non-root does not. And basically as stated above, to setup an account for another user go to System > Administration > Users And Groups and then click Unlock, tenter password, and then click "Add User".

---

### Post by halitech on 2008-07-27
by default the "root" account is disabled but your main user has the rights to "become" root if need to do admin work like install drivers and software.

it is a security issue because when you run as the root user, a hacker only needs to guess your password to get complete access to your system. With the root account being disabled, they now need to guess your username and password in order to gain access to the system. At worse if you get a virus or run a malicious command, the most damage that can be done without entering the root password is your home directory gets wiped out.

---

### Post by johnlvs2run on 2008-07-27
> **Thisislaw said:**
> go to System > Administration > Users And Groups and then click Unlock, tenter password, and then click "Add User".

Thanks.  Root is showing up, and one user (me).
I'm not usually signed in as root, but otherwise I think they're the same.

Should they be different, or should I make a 2nd user name that is different?

---

### Post by perlluver on 2008-07-27
> **johnlvs2run said:**
> Thanks.  Root is showing up, and one user (me).
I'm not usually signed in as root, but otherwise I think they're the same.

Should they be different, or should I make a 2nd user name that is different?

That isn't neccesary as long as you just use sudo for root things.  And your account should be just a normal account, not a root account.

---

### Post by aysiu on 2008-07-27
You shouldn't have to create a new user or log in as root.

With the first user created, you can temporarily escalate to root privilege using the command *sudo* (for command-line applications) or *gksudo* (for graphical applications).

Most likely, if you need to install a printer driver, you'll be using *sudo* - probably something like ```
sudo ./*blahblahblah*.bin
``` What printer is it? What's the driver installation's file name?

As for the why business, read [Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by johnlvs2run on 2008-07-27
> **perlluver said:**
> That isn't neccesary as long as you just use sudo for root things.  And your account should be just a normal account, not a root account.

It has root listed, then me listed under that.  I guess that's a normal account?

> **aysiu said:**
> You shouldn't have to create a new user or log in as root.

With the first user created, you can temporarily escalate to root privilege

What printer is it? What's the driver installation's file name?

Thanks.  It's an HP Laserjet 4M Plus 
[http://ubuntuforums.org/showthread.php?t=854787](http://ubuntuforums.org/showthread.php?t=854787)

I tried the hplip-2.8.6 file from a similar printer. 
[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4M_Plus](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4M_Plus)

The terminal said I had to log in as root, then when I logged in as root it gave me the warning.  :o

P.S. - The input was >> sudo sh hplip-2.8.6.run

---

### Post by halitech on 2008-07-27
I installed that earlier and it said not to run as sudo but it would ask for root password during the install

---

### Post by aysiu on 2008-07-28
I didn't see a driver in either of those links or anything about not using *sudo*.

In any case, I went to the [Ubuntu Wiki page on HP printers](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp), and they said it should work automatically except there was this little note: [quote=Wiki]Don't choose LaserJet 4M when installing the printer. The postscript driver won't work. Instead choose the LaserJet 4, which brings up the working hpijs driver.[/quote] So it seems you should just use the regular Add Printer dialogue and select HP Laserjet 4 instead of HP Laserjet 4M, and it should work.

---

### Post by johnlvs2run on 2008-07-28
Printer comments moved to printer thread here.
[http://ubuntuforums.org/showthread.php?p=5483780#post5483780](http://ubuntuforums.org/showthread.php?p=5483780#post5483780)

---

### Post by snowpine on 2008-07-28
I don't know if this is necessarily the case here, but the whole 'sudo' thing is a feature of Ubuntu, not all flavors of Linux. So sometimes if you are reading instructions or tutorials written for other types of Linux, they will tell you to log in as root. As others have pointed out, Ubuntu users can use sudo to temporarily have root privilages.

---

### Post by bodhi.zazen on 2008-07-28
With Ubuntu, to obtain a root shell (in a terminal) use:

```
sudo -i
```

---

### Post by johnlvs2run on 2008-07-28
Printer comments moved to printer thread here.
[http://ubuntuforums.org/showthread.php?p=5483780#post5483780](http://ubuntuforums.org/showthread.php?p=5483780#post5483780)

---

### Post by johnlvs2run on 2008-07-28
> **bodhi.zazen said:**
> With Ubuntu, to obtain a root shell (in a terminal) use:

```
sudo -i
```

What would be the command to close the root shell?

I've been reading some online guides, and am interested to do much more from command line.

---

