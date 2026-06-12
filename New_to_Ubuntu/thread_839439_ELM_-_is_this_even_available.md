---
title: "ELM - is this even available?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by protogenesis on 2008-06-24
Not new to Linux but new to Ubuntu....

Installed the latest and greatest server edition for web service, email, etc.  So far, everything is working great and I have configured the system to do what I need.  However, since I don't use GUI on this server and I don't necessarily use pop/imap when I'm working at the console/ssh, I'd like to use a more attractive email program.  I'm used to the good ole days of UNIX and elm mail.  Sadly, using apt-get (from as much as I understand it) I cannot find this package.  

The server uses postfix, and I know elm relies (or at least, used to) on procmail.  So, here's the questions:

a) Is elm availble -- and if so, how do I go about getting it (if it's not a package I can just install), and
b) If elm IS available, would it be compatible with the newest server edition running postfix?

I haven't admined my own system since the days of UNIX System III and a very young Linux kernel, thus I'm still a newbie!

Much thanks to those who can assist!

---

### Post by cariboo on 2008-06-24
Have a look here:

[http://en.wikipedia.org/wiki/Elm_(e-mail_client](http://en.wikipedia.org/wiki/Elm_(e-mail_client))

Jim

---

### Post by protogenesis on 2008-06-24
Nope, that didn't do the trick.  Sadly :-(

---

### Post by Fremont_Cunningham on 2008-10-16
Elm is available and works on Ubuntu HardyHeron 8.04
As of October 16 2008 the correct wiki link is
[http://en.wikipedia.org/wiki/Elm_email_client](http://en.wikipedia.org/wiki/Elm_email_client)
Elm home page with info on where to get the sources is
[http://www.instinct.org/elm/](http://www.instinct.org/elm/)
To get the source:
ftp.virginia.edu appears to be broken, so use (on one line)

wget http://www.instinct.org/elm/files/tarballs/elm2.5.8.tar.gz

gunzip elm2.5.8.tar.gz
tar -xvf elm2.5.8.tar
cd elm2.5.8
more Instruct
   which tells how to make elm etc. The only thing I had to fix was edit configure.h to 
#define I_STDARG
then make worked fine.
To install use
sudo make install

Enjoy!

---

### Post by alidee on 2010-12-09
Very belated thanks to Fremont_Cunningham for his tip which helped me get elm compiled.  Just wanted to add another couple of bits of info in case anyone else goes searching for this.  

I had to install packages linux-headers-`uname -r` (currently linux-headers-2.6.24-28-generic), build-essential and libncurses5-dev.  Without the libncurses5-dev package installed, running "make" gave numerous errors like:
    undefined reference to `tgetstr'
    undefined reference to `tputs'

I hope that might help someone!

Ali

---

