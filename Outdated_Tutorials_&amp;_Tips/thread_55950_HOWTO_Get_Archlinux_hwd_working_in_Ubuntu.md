---
title: "HOWTO: Get Archlinux hwd working in Ubuntu"
date: 2005-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by i3dmaster on 2005-08-10
hwd is the Archlinux No.1 hardware scan and display tool. I found its really nice and wanted to get it working under ubuntu, and it turns out to be pretty simple.
1. Get hwd binary file from [http://amlug.net/new-projects/hwd/hwd.html](http://amlug.net/new-projects/hwd/hwd.html) . you will need the source package (hwd-4.7.1.bin.tar.gz) not the Archlinux one.
2. The nice thing is even its called a source package, its actually not. Everything has been compiled already, we just need to copy them to the corresponding dirs. What I did was copying everthing from the "etc" dir to the system "/etc" dir and everyhing under "usr" dir to system "/usr" dir, so hwd command will be at /usr/bin/hwd finally.
3. Get the lshwd source code (its really a source package this time) from [http://user-contributions.org/projects/lshwd/source/](http://user-contributions.org/projects/lshwd/source/) . I grabbed the latest 2.0-rc4 one.
4. Extract it and compile it by ```
make
``` under the extracted dir. After that you will see a lshwd binary generated. Move/copy that binary to /usr/bin.
5. Done. Issue ```
hwd -h
``` to see the help and ```
hwd -s
``` to view your system info and more... The nice features that I like are: 1. color output. 2. tells you the kernel module for each device. I wasn't exactly sure what module my NIC is using until I found this tool. 

Can't be earier right? :) Enjoy!

---

### Post by i3dmaster on 2005-08-11
[QUOTE=i3dmaster]Can't be earier right?[/QUOTE]
Should be easier, not earier... sorry for the typo.

---

### Post by Hamman on 2005-08-11
[QUOTE=i3dmaster]Should be easier, not earier... sorry for the typo.[/QUOTE]
 Nice! Should be added to the repos. Useful when you're trying to help someone with similar hardware, but don't know what modules that are used for what.

---

### Post by i3dmaster on 2005-08-11
[QUOTE=Hamman]Nice! Should be added to the repos. Useful when you're trying to help someone with similar hardware, but don't know what modules that are used for what.[/QUOTE]
Thanks! That's actually a good idea.

---

### Post by kwadroke on 2007-06-29
I know this is an old post, but I came across this while looking for info on hwd. I figured I'd add to the info in-case anyone else comes to this thread.

The link [http://amlug.net/new-projects/hwd/hwd.html](http://amlug.net/new-projects/hwd/hwd.html) is broken.
Use [http://user-contributions.org/projects/hwd/hwd.html]("http://user-contributions.org/projects/hwd/hwd.html") instead

---

