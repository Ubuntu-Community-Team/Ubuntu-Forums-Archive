---
title: "Wake on Lan and Shutdown"
date: 2006-05-03
forum: Programming Talk
---

### Post by krypto_wizard on 2006-05-03
I am using 8 computers on a small network. I have one Main computer
which should be able to remotely start other computers and shutdown them.
I used Wake on LAN technology to successfully start them all.

My Main computer is Linux.

Other 4 are Windows and 3 are Linux.

How can I shutdown Windows box from my Main (Linux) ?

Also, How can I shutdown other Linux terminals from my Main (Linux) ?

Help is appreciated.

---

### Post by simplyw00x on 2006-05-03
To shutdown other linux terminals, you can use SSH to login to them and then sudo shutdown.

---

### Post by krypto_wizard on 2006-05-04
Thanks, I had figured out a way.

How can we shutdown remotely a Windows box from a Linux box ?



[QUOTE=simplyw00x]To shutdown other linux terminals, you can use SSH to login to them and then sudo shutdown.[/QUOTE]

---

### Post by simplyw00x on 2006-05-04
Run SSH on the windows box through cygwin :p

Windows has a shutdown command that can remote shutdown other computers; not sure if it's implemented in Samba somehow.

---

### Post by johnnymac on 2006-05-05
Run telenet on each of your windows box and write yourself a perl script that runs from the Linux box.  If you use 

Net::SSH::Perl

from cpan this will allow you to ssh into anybox (other than windows) without it stopping to ask for a password (you provide the password when writing the script).  

For the windows side, you can use Perl/Expect and automate the interactive telenet sessions.

GL

---

### Post by cwaldbieser on 2006-05-06
[QUOTE=simplyw00x]Run SSH on the windows box through cygwin :p

Windows has a shutdown command that can remote shutdown other computers; not sure if it's implemented in Samba somehow.[/QUOTE]
The PsTools suite from system internals [http://www.sysinternals.com/Utilities/PsTools.html]("http://www.sysinternals.com/Utilities/PsTools.html")
makes it easy to do command line driven stuff on Windows.  I'd suggest you set up one Windows box with the tools and an SSH server  (ala Cygwin).  Then you can ssh into that box and kick off scripts to manipulate any of the other boxes (reboot them, execute programs remotely, etc).

---

