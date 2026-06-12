---
title: "Disk Utility"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by RH9R on 2012-11-04
Having formatted an external Hitachi usb drive, I use 'check file system' and it returns a msg: File System is NOT clean. The text under the function "Check Filesystem" says check & repair. Apparently, its finding something odd, but the 'repair' side is not really doing anything. 
 
Is there another disk utility app or method I should try - to find what's wrong and possibly fix it?

---

### Post by superdaveozzborn on 2012-11-04
perhaps GPARTED may do the trick, I have found it to be a little better then Disk Utility. 
sudo apt-get install gparted

just an idea....

---

### Post by ibjsb4 on 2012-11-04
Got some hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=File+System+is+NOT+clean&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=File+System+is+NOT+clean&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by RH9R on 2012-11-05
Grr. software center changes are making me nuts.
 
I go to install gparted and get a msg about needing a package from an untrusted source. (libgtkmm-2.4-1c2a) The choices are 'okay' and 'repair' - neither indicating what desired action is taken by either.  

I try it with both choices and it has the same affect (none) with either choice. I try loading just the gtk lib by itself & get the same song & dance. 'Very frustrating. 
 
I appreciate your kind help, superdave & ibjs. I'm just hitting obstacles that remind me of the 'dependency hell' days of the 90s.

I found the apt-get commands for installing synaptic, which made gparted alot easier. I sure don't remember this many warnings and disclaimers about 'untrusted' software sources. Gparted has been around since dirt. The App center has been very little use.
 
Gparted has been running for over an hour. 'Have no feel for if that's way too long or about right for a 250g drive. I'll let it go & see if it returns anything.

---

### Post by NikTh on 2012-11-05
Hi , 
if the disk has NTFS filesystem it would be better to repair from within Windows. Do you have Windows ? 

A utility exists for NTFS repair in Linux , but personally I told you what I suggest.
See here for the program ntfs-3g and the tool ntfsfix
[http://manpages.ubuntu.com/manpages/precise/man8/ntfsfix.8.html](http://manpages.ubuntu.com/manpages/precise/man8/ntfsfix.8.html)

but I'm not suggest it.

Thanks

---

