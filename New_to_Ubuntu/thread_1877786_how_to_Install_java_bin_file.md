---
title: "how to Install java bin file"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by davesmith on 2011-11-08
Hi

Could someone please explain how to install the <  jre-6u29-linux-i586.bin > file available for Linux on the sunJava  website? The instructions with the file are generic Linux and not  specifically Ubuntu. 

The java available in the natty repos is < jre-6u26-linux-i586.bin > and I sorta like to keep ahead of the game if i can

Thanks in advance

---

### Post by Paqman on 2011-11-08
On Ubuntu the first place you should always go to for software is the Ubuntu Software Centre. You'll find the Sun Java package can be installed from there in a couple of clicks.

Manually downloading things from various websites and handling the installation yourself is the Windows way. On Linux we don't bother with all that.

---

### Post by davesmith on 2011-11-08
Ok, here is how its done

d/l the < jre-6u29-linux-i586.bin > file from the java website to a Downloads directory in your Home folder. Open a terminal and type:-

Code

< cd ~ /Downloads >

then make the bin file executable:-

Code

< sudo chmod 755 jre-6u29-linux-i586.bin >
 
[FONT=monospace]finaly run it:-

Code

< ./[/FONT]jre-6u29-linux-i586.bin

Sorted!

---

