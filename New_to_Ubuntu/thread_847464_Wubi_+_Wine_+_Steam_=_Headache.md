---
title: "Wubi + Wine + Steam = Headache"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by AJCF on 2008-07-02
:frown:I've been trying to install Steam with Wine all day but to no avail. I've tried with the .msi, with the .exe but nothing works. Is it even possible to do this?

Has anyone succeeded? I'm *really* interested in having Ubuntu (Wubi) but would also like to have Steam working :frown:

Any and all help would be appreciated :cry:

---

### Post by tmcarson1 on 2008-07-02
Here's a post on it, not sure if it will help or not, but perhaps.


[http://thepemberton.com/posts/archives/13](http://thepemberton.com/posts/archives/13)

---

### Post by AJCF on 2008-07-02
> **tmcarson1 said:**
> Here's a post on it, not sure if it will help or not, but perhaps.


[http://thepemberton.com/posts/archives/13](http://thepemberton.com/posts/archives/13)

The thing is I can't even seem to change the directory on the terminal, I always get "file not found" :confused:

> alexandrefonseca@alexandrefonseca-laptop:~$ cd ~/desktop
bash: cd: /home/alexandrefonseca/desktop: No such file or directory



PS - I'm an ubuntu noob, sorry :oops:

---

### Post by avtolle on 2008-07-02
That should be ```
cd ~/Desktop
```note capital "D".

---

### Post by AJCF on 2008-07-02
> **avtolle said:**
> That should be ```
cd ~/Desktop
```note capital "D".

I still get the same error, oh boy :(

> alexandrefonseca@alexandrefonseca-laptop:~$ cd ~/Desktop
bash: cd: /home/alexandrefonseca/Desktop: No such file or directory

---

### Post by AJCF on 2008-07-02
Anyone? :oops:

---

### Post by AJCF on 2008-07-03
> **tmcarson1 said:**
> Here's a post on it, not sure if it will help or not, but perhaps.


[http://thepemberton.com/posts/archives/13](http://thepemberton.com/posts/archives/13)

Well, I tried this guide again and I got this on the terminal :(

> preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\steaminstall.exe": Module not found
alexandrefonseca@alexandrefonseca-laptop:/home$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


Sorry for the triple-posting!

---

### Post by strongboww on 2008-07-03
> **AJCF said:**
> Well, I tried this guide again and I got this on the terminal :(



Sorry for the triple-posting!
[http://wiki.winehq.org/FAQ#head-f008d57967dd5f8aa3f374c27540c1b5f4815947](http://wiki.winehq.org/FAQ#head-f008d57967dd5f8aa3f374c27540c1b5f4815947)

> 
4.5. ISSUE: "preloader: Warning: failed to reserve range 00000000-60000000"

[http://bugs.winehq.org/show_bug.cgi?id=12516](http://bugs.winehq.org/show_bug.cgi?id=12516) is the bug following this issue.

This issue is appearing due to a kernel setting. cat /proc/sys/vm/mmap_min_addr as root, if it does not equal 0 then "sysctl -w vm.mmap_min_addr=0" as root can be used to temporary fix issue or for every reboot after adding the line vm.mmap_min_addr=0 to /etc/sysctl.conf can be done. Please record if you do this alteration the area Wine needs may change.

See PreloaderPageZeroProblem


plz always check the wine-hp also for FAQ and support

edit: and dont start the game with the parameters above, just add at the end of the link "-opengl", i dont know if it is for the starter but to be sure also do this in the steam-menu to all your games

---

