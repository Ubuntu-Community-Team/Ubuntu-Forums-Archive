---
title: "Why i get undefined references for all pcap functions?"
date: 2016-02-29
forum: Packaging and Compiling Programs
---

### Post by artss2 on 2016-02-29
I have just installed codeblocks on xubuntu. It works. the libpcap was 1.0, then I upgraded to 1.1 or just returned to it after I installed libpcap-0.8-dev.
But I got such errors:
<<--undefined references to:
[COLOR=black]pcap_lookupdev
pcap_loop ....>>
etc
what should I do? I installed the dev extension.
But it show such error.
Should I use some more installation or just configuring in codeblocks?[/COLOR]

Should I launch it not by Codeblocks Run, but with terminal command line in (x)ubuntu?
Despite I would like to use just codeblocks menu or other IDE

---

### Post by steeldriver on 2016-02-29
Regardless of whether you build your project using an IDE or command line tools, you need to specify the appropriate libraries

See for example [http://stackoverflow.com/questions/5862757/how-do-i-link-to-a-library-with-codeblocks](http://stackoverflow.com/questions/5862757/how-do-i-link-to-a-library-with-codeblocks)

---

### Post by artss2 on 2016-02-29
I use my test code from internet. So it is probably workable, and have all nessesary headers, so what libraries I need include, and why if it probably used by headers and installed libpcap 1.1.1? I have read that i need to just note some compiler options. Should it to be enough? And is it possible to use just CD menu of build options?

Adding: pcap  to linker variable in build setting solved the issue. Despite no suitable device after running code. Despite ifconfig shows standart eth0 and lo interfaces are present?// And of course to solve <pcap.h no such file or directory> you need additionally install - sudo apt-get install libpcap-dev

---

