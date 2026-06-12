---
title: "Installation of an .rpm file: &quot;the package cannot be built on this system&quot;"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by leandrolsguedes on 2013-10-25
I need to install a .rpm file and I'm trying to convert it using alien. But the command

alien FILE-1tb.i586.rpm

gives me the output:

FILE-1tb.i586.rpm is for architecture i386 ; the package cannot be built on this system

I'm using Ubuntu 13.04, 64-bit. I've never seen this message from alien before. Am I loosing something from the i586 information on the file's name? Is there ANY way to go around this issue?? I really need this package installed... Thank you very much!

---

### Post by The Cog on 2013-10-25
I'm no expert but the error message says quite clearly that the rpm is for i386 (i.e. 32 bit) architecture. I am sure that .i586 is still 32-bit architecture. 
I would suggest that you try these things in order:
1: Look in the Ubuntu repositories for the program
2: look for a 64-bit .deb package file
3: look for a 64-bit .rpm package file
4: install a 32-bit OS to install it into (perhaps as a virtual machine guest in your real machine).

I guess you have already done most of these, but I list them for anyone else reading this thread for guidance.

---

### Post by leandrolsguedes on 2013-10-25
Thank you The Cog.
 
I didn't realize that it was about the 32/64-bit. I'm gonna try the virtual machine, that was a great idea.

---

### Post by The Cog on 2013-10-25
OK. You might want to install fedora rather than an ubuntu version. Fedora and red hat use rpm (Red Hat Package Manager) packages where ubuntu variants (based on debian) use .deb packages. So rpm is really meant for red-hat and derivitives like fedora.

---

### Post by Baldrick_NZ on 2013-10-26
Hi there,

.rpm files are for RedHat derivitives of linux. By themsleves they won't work in debian (.deb) based systems like Ubuntu.

So, there are three options for you, easiest first..

1/ check in the Ubuntu Software Centre for the same program (often thereis a .deb version if there is an .rpm version around). If not, google for a .deb version.

2/ Failing that, there is a tool called 'Alien', which allows .rpm files to be converted to .deb, and vice versa. I've never had to use this tool, so can't recommend it, but I'm sure many have. Try googling 'Linux Alien' to find out more, and perhaps a tutorial or two. It might even be in the software centre as well.

3/ The only other option, which may seem a little extreme, would be to download and install a RedHat derivative, like Fedora. Fedora uses .rpm files natively, but be aware the architecture is different to Ubuntu as well.

Hopefully that helps!

---

