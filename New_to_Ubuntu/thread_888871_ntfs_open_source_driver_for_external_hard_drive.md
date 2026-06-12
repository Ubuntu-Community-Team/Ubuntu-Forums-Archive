---
title: "ntfs open source driver for external hard drive"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by anthonyglamis on 2008-08-13
Hi,
  I have posted recently about not having a internet connection.   So I am basically trying to download packages and install them manually. I was previously trying to install VLC and have since put that on the back burner.  I am trying to install an open source ntfs driver since I have a maxtor 1 gig drive that i would like to transfer movies to.  Well Ubuntu see's this drive just fine but I do not have any write priveledges....go figure.  I thought by downloading this package and using the install instructions I would be good to go.  Can someone please let me know where I have gone wrong.  Here is what happend.

  I downloaded the NTFS-3G open source driver for my external HD from here.  [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

  I extracted the files to a directory /media/sda1/temp

  While logged in as root and in that current directory I typed..
./configure  
this command was good as some other files were created in that directory.  I then typed...
  make  
nothing happend with this it says make: *** no taregts specified and no make file found.  stop.  I also tried...
  make install
this says no rule to make target "install"  stop.  

A little help would be fantastic.  Thanks all.

---

### Post by logos34 on 2008-08-13
no, Hardy already has ntfs-3g installed. 

What you want is the **ntfs-config** gui tool

install it and run

**sudo ntfs-config**

---

