---
title: "I cant seem to install Google video chat on Ubuntu 11.10"
date: 2011-09-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by 10Digits on 2011-09-14
Hi,
I have just downloaded google video chat support and it isnt installing.
I have 64-bit Ubuntu 11.10 and it says in the software centre that dependancies are not met. The file dependencies are lib32v4l-0.
I have tried to find it on synaptic and tried to find on terminal by running sudo apt-get install lib32v4l-0. but it says its replaced by a file. 

Here is the output from my terminal:

sayan@sayan-Compaq-Presario-CQ50-Notebook-PC:~$ sudo apt-get install lib32v4l-0[sudo] password for sayan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lib32v4l-0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ia32-libs

E: Package 'lib32v4l-0' has no installation candidate

I have installed ia32-libs but to no effect. Video chatting is something I do almost everyday so it would be great if you could help me out.

               Thanks in advance.

---

### Post by pressureman on 2011-09-14
Sounds like another refugee from the pre-multiarch era.

Search this forum for threads about installing 32-bit Skype on amd64, and try applying that method to your problem.

---

### Post by sgo. on 2011-09-14
Hi! Maybe [this]("http://www.google.co.uk/support/forum/p/chat/thread?tid=3d7135d6578b73c2&hl=en") can help you.

In short, you'll have to make sure that the 'v4l-utils' package is installed, install the *.deb dummy file I added in the .zip archive and happily upgrade your google-talk-plugin! :-) If you don't trust me, just build your dummy *.deb yourself, as described in the link. Will take you 5-10min, if you never did it before.

Hope that helps!

---

### Post by sammiev on 2011-09-14
> **pressureman said:**
> Sounds like another refugee from the pre-multiarch era.

Search this forum for threads about installing 32-bit Skype on amd64, and try applying that method to your problem.

[This]("http://ubuntuforums.org/showthread.php?t=1831998&highlight=skype+solved") maybe what you are looking for. :)

---

### Post by 10Digits on 2011-09-15
Thanks to pressureman and sammiev for your replies.
 

         Thanks Sgo. your solution worked perfectly. it installed perfectly with the google video chat debs. thank you again.

---

### Post by nanonils on 2011-09-15
I have the same problem but can't open your zip file. I get the error message: "End-of-central-directory signature not found.  Either this file is not a zipfile, or it constitutes one disk of a multi-part archive.  In the latter case the central directory and zipfile comment will be found on the last disk(s) of this archive."

Would much appreciate your advice! Guess I'm paying again for prematurely upgrading a production machine ... Just can't resist.

> **sgo. said:**
> Hi! Maybe [this]("http://www.google.co.uk/support/forum/p/chat/thread?tid=3d7135d6578b73c2&hl=en") can help you.

In short, you'll have to make sure that the 'v4l-utils' package is installed, install the *.deb dummy file I added in the .zip archive and happily upgrade your google-talk-plugin! :-) If you don't trust me, just build your dummy *.deb yourself, as described in the link. Will take you 5-10min, if you never did it before.

Hope that helps!

---

### Post by cariboo on 2011-09-15
Try the solution in sammiev's post, post #[4]("http://ubuntuforums.org/showpost.php?p=11252716&postcount=4").

---

### Post by erguille on 2011-09-15
Thank you guys for the solution it worked like a charm!!!!
step by step instructions:
open terminal and type the following:

mkdir tmp
cd tmp
sudo apt-get install --yes equivs
equivs-control lib32v4l-0
gksudo gedit lib32v4l-0

once the file opens change the following values:
*** I would recomend to use the latest version number and dependencies found here:
[http://packages.ubuntu.com/natty/lib32v4l-0]("http://packages.ubuntu.com/natty/lib32v4l-0")

Package: lib32v4l-0
# Version: 0.8.3-1
# Depends: libc6-i386 libv4l-0

save changes

on terminal again run:

equivs-build lib32v4l-0
sudo dpkg -i lib32v4l-0_1.0_all.deb

install google-talk as you wish or use

source: [http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html")

Saludos

---

### Post by grappler on 2011-09-21
Brilliant - thanks! Worked perfectly.

---

### Post by nanonils on 2011-09-22
Perfect. erguille - thanks for the written out instructions! Life saver!

---

### Post by JSchultheis on 2011-10-09
> **erguille said:**
> Thank you guys for the solution it worked like a charm!!!!
step by step instructions:
open terminal and type the following:

mkdir tmp
cd tmp
sudo apt-get install --yes equivs
equivs-control lib32v4l-0
gksudo gedit lib32v4l-0

once the file opens change the following values:
*** I would recomend to use the latest version number and dependencies found here:
[http://packages.ubuntu.com/natty/lib32v4l-0]("http://packages.ubuntu.com/natty/lib32v4l-0")

Package: lib32v4l-0
# Version: 0.8.3-1
# Depends: libc6-i386 libv4l-0

save changes

on terminal again run:

equivs-build lib32v4l-0
sudo dpkg -i lib32v4l-0_1.0_all.deb

install google-talk as you wish or use

source: [http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html")

Saludos

Any ideas about a 32bit installation?

---

### Post by JSchultheis on 2011-10-11
meanwhile [***_[COLOR="Blue"]Pidgin[/COLOR]_***]("http://www.pidgin.im/") seems to be going over well  ^___^

---

