---
title: "Ubuntu hardware problems, suggest other distro"
date: 2007-05-20
forum: Other OS Talk
---

### Post by krypto_wizard on 2007-05-20
I have a Toshiba Satellite A70-S249 laptop. I had previously dapper on it and it ran so smooth. Now  I am dual booting it with windows and Ubuntu Feisty and there is something wrong in my Feisty installation ( i have done it 4 times already), my computer hangs after a while (in both kde and gnome).

I am so tired with my laptop not running feisty properly (tho feisty runs well on my desktop).

Now, I am ready to move to another OS for my laptop. Please suggest me some options.

I want to try debian but not sure of its complexity. I am an average linux user who tries to find his way thru google and asking in forum.  I heard that debian's APT is the asset but the community is not the best as it if gor Ubuntu. I want to try Opensuse but heard that its package manager is pathetic. I have no clue of fedora. Heard some good tails of Mepis thru forums.

Please help me shortlist the OS for my laptop.

1. Debian
2. Opensuse
3. Fedora
4. Mepis
5. Slackware

Every help is appreciated.

Thanks

---

### Post by SunnyRabbiera on 2007-05-20
Toshibas are not good with linux sadly.
But i suggest Mepis, or PClinux...
But avoid Microsoft Suse.

---

### Post by exploder on 2007-05-20
MEPIS and PCLinux have very good hardware support. The mepislovers site is the best place for help with MEPIS if you need it. 

PCLinux is very good. Texstar has been noted in many reviews as being a perfectionist. PCLinux has things working in KDE that still do not work properly in other distributions

Fedora is good with problematic hardware in my experience. Multimedia does not work "out of the box", but some googleing and a couple of good guides will get things going. The community is not as friendly as smaller distributions, they do not like to answer the same old questions.

MEPIS would be my first choice simply because Warren went above and beyond for hardware support and because I know how far the mepislovers community will go to help you if you ask.

PCLinux .94 is still at beta 4 but the final will be released soon. If you ask a question on the PCLinux Forum you might get a response from texstar himself! texstar is an active participant on the forums. something that really impressed me!  

These are my suggestions. Please post back with your results.

---

### Post by FishRCynic on 2007-05-20
you can try feisty - this worked for me

[http://ubuntuforums.org/showthread.php?t=417819&page=2&highlight=toshiba+a70](http://ubuntuforums.org/showthread.php?t=417819&page=2&highlight=toshiba+a70)

---

### Post by vanden12 on 2007-05-20
I really like Sabayon it worked with everthing out of the box ex the wifi card but that can easy be install.And i am on a 

Other to look out for it suse,PCLinuxOS,Fedora

To me Sabayon comes dam near better than ubuntu all they got to get wifi cards oftb and a bit faster boot and they will be better than ubuntu, it also buit on gentoo.

---

### Post by krypto_wizard on 2007-05-21
How about Knoppix as an OS with installation rather than as Live CD ?

Can you throw some light as to how Knoppox works as an installed OS ?

---

### Post by bonzini on 2007-05-27
Fellow A70 user;

I had rock-solid Dapper, occasional hangs in Edgy with no log messages, and regular hangs in Feisty with no log messages.

It turns out that booting with noapic fixed it.  Here is the diff for my /boot/grub/menu.lst:

clh@clh-laptop:/boot/grub$ diff menu.lst~ menu.lst
128c128
< kernel                /boot/vmlinuz-2.6.20-15-generic root=UUID=0f1fa16f-05cd-4130-b86c-360facbbcb0c ro quiet splash
---
> kernel                /boot/vmlinuz-2.6.20-15-generic root=UUID=0f1fa16f-05cd-4130-b86c-360facbbcb0c ro quiet splash noapic
clh@clh-laptop:/boot/grub$ 

I hope this works for you.  Believe me I understand your frustration!!!

---

### Post by kerry_s on 2007-05-27
Just try the debian it's not that hard, use installgui for the pretty installer->

xfce4-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

kde-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso)

net installer/gnome-> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-netinst.iso)

---

### Post by manutdfan2850 on 2007-05-28
i am also a user of Toshiba Sattelite A70 laptop. as others have stated. dapper was great, edgdy was Ok and fiesty hangs wayy to frequently for it to be usable. 

i tried PcLinusOs 2007 the other day when it came out and i have been instantly hooked to it. Its hardware support is the best i've ever seen. It detected everything in my a70 laptop perfectly no additional configuration needed. Desktop effects is working out of the box and it already has beryl and compiz preinstalled. Wireless card was detected also and it connects to it automatically wheniver i turn it on. 

to sum it up, imho PCLinuxOS 2007 is fast, looks sweet, and works amazingly well on my toshiba a70 laptop

after using ubuntu for the past year, ive decided pclos is the best for me now. 

hope this helps. 


OFF TOPIC: you guys know about the lawsuit against toshiba for the A70/A75 model right?

---

### Post by juxtaposed on 2007-05-28
> suggest other distro

Debian.

---

### Post by powerpc64 on 2007-06-17
is straight Debian with superb laptop support, try the live CD and see if you like.

---

