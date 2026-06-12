---
title: "(sudo rm /usr/bin/*)urgent help --please"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by mokkai on 2008-05-10
please urgent help needed
my os ubuntu 7.04

i made a mistake that i deleted all those files from /usr/bin/*
sudo rm /usr/bin/*

how to recognize that 
any thing from my system is not working

please guys do you have any idea 
how to save those (/usr/bin/*) files into that directory

   thank you

---

### Post by EdThaSlayer on 2008-05-10
Well, since you have deleted those files from /usr/bin/*, it's basically...gone. But you could get it back by using a live-cd and copying the bin files on the live-cd to your linux partition(hard drive linux). Then you might have to reinstall all the other not-out-of the box software. Hopefully this gives you some ideas. :)

---

### Post by Canis familiaris on 2008-05-10
> **mokkai said:**
> please urgent help needed
my os ubuntu 7.04

i made a mistake that i deleted all those files from /usr/bin/*
sudo rm /usr/bin/*

how to recognize that 
any thing from my system is not working

please guys do you have any idea 
how to save those (/usr/bin/*) files into that directory

   thank you
What were you thinking mate!

Try to copy the files from the live CD.

---

### Post by Joeb454 on 2008-05-10
I think the best option may to be back up your /home folder and reinstall the OS :(

---

### Post by nofrendo on 2008-05-10
Seconded. Try putting your /home folder in a separate partition.

This way, if you need to reinstall your OS, you can migrate all your settings and files way more easily.

---

### Post by Chayak on 2008-05-10
> **mokkai said:**
> please urgent help needed
my os ubuntu 7.04

i made a mistake that i deleted all those files from /usr/bin/*
sudo rm /usr/bin/*

how to recognize that 
any thing from my system is not working

please guys do you have any idea 
how to save those (/usr/bin/*) files into that directory

   thank you

The 'sudo rm' combo is like playing with nitroglycerin in the back of a truck going down a gravel road littered with potholes there's nothing you should be deleting outside of your home or a very few special cases in /var

The fix?  If your technical enough you can copy the /usr/bin directory from the live cd but it may not include things you've installed in the past.

The best thing to do is learn not to play with 'sudo rm' and reinstall your system.

---

### Post by ajmorris on 2008-05-11
the following is for recovering deleted partitions: [http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk) .... it could perhaps be used also to recover data..... but basically, if the block sectors that the files were on, have not been overwritten, the data should be able to be recovered, its just a matter of digging around for it, which can be very difficult to accomplish.

AJ

---

### Post by sp00n on 2009-01-27
I have just done the same - is there anything like dpkg-reconfigure -a that will reinstall all files for all installed packages via apt? that way I can copy files from the live cd's /usr/bin, and then anything extra will be reinstalled using apt?

---

### Post by arjuntank on 2009-01-27
after reading all the above posts you can either try to recover data by using testdisk or copy /usr/bin from live cd or the last option simply format the whole thing ( backup first! )
:(

---

### Post by sp00n on 2009-01-27
I may have a solution to own problem.

I have executed the following on the stricken PC, in order to get a list of installed packages:

```
dpkg --get-selections > installed-software
```

I happen to have another PC, also running Ubuntu Hardy. I transferred the file generated above to the working PC via usb stick, then, on the working PC, ran:

```
dpkg --set-selections < installed-software
dselect
```

Then in dselect, I chose the option to install all wanted packages.

This launched apt-get, passing it the list of packages that are installed on the poorly system that are not on the good PC.

once this completed, I copied the contents of /usr/bin on the good pc onto usb stick, then unmounted the stick and remounted in the poorly PC. then copied the files over into /usr/bin.

Some of the files will not copy - these are dangling symlinks (I dont think i need to worry about these, as they point back to other files in this directory, which have been copied), and open files.

run ps -A |grep filename, where filename is a file that did not copy overas it was open, to get the PID of all open instances - kill them, and then copy  the file over.

 Voila!

---

