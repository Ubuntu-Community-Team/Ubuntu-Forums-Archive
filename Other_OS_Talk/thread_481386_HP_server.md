---
title: "HP server"
date: 2007-06-22
forum: Other OS Talk
---

### Post by Dekunuts on 2007-06-22
Hi,

My father designs SDH networks and the company where he works is going to upgrade some servers and throw the old ones away. He is going to bring one home for me, but i don't know what to expect really. It' s a HP L2000 server with 2 PA-RISC  processors 4 gig ram and four scuzi (spelled right?) 9 GB drives that are copies of each other for data protection. That's RAID something.

so, my questions are

1. It's just a server, how do i connect to it (there is no gpu) or well yeah, use it
     could i use my regular computer to connect to it. I thought maybe 'boot from network' in the bios, once everything is set up accordingly.
2. it's running hp ux11, can i use that for anything 
3. I saw there is a pa-risc version of debian, could i run it on this machine (dual cpu, scsi and whatnot)
4. what is the difference between raid0 1 etc ?

anything else i should know ?

---

### Post by mips on 2007-06-23
> **Dekunuts said:**
> Hi,

My father designs SDH networks and the company where he works is going to upgrade some servers and throw the old ones away. He is going to bring one home for me, but i don't know what to expect really. It' s a HP L2000 server with 2 PA-RISC  processors 4 gig ram and four scuzi (spelled right?) 9 GB drives that are copies of each other for data protection. That's RAID something.

so, my questions are

1. It's just a server, how do i connect to it (there is no gpu) or well yeah, use it
     could i use my regular computer to connect to it. I thought maybe 'boot from network' in the bios, once everything is set up accordingly.
2. it's running hp ux11, can i use that for anything 
3. I saw there is a pa-risc version of debian, could i run it on this machine (dual cpu, scsi and whatnot)
4. what is the difference between raid0 1 etc ?

anything else i should know ?

It's called SCSI (pronounced scuzzi).

1. I suspect it will have a connector for a monitor on the back. Else you could access it via the serial port or telnet if you know it's current ip, user & password information.

2. Yes, works well as a server or a workstation. Dunno how many free apps you will find though unless you compile the linux stuff for it. Head on over to the hp website and see what they have to offer in terms of free software.

3. I don't see whay not. Just check all your hardware beforehand and see if it is supported. Ubuntu also has a port for PA-RISC, [http://cdimage.ubuntu.com/ports/releases/6.06/release/](http://cdimage.ubuntu.com/ports/releases/6.06/release/)   ,   [http://ubuntu-hppa.pateam.org/install.php](http://ubuntu-hppa.pateam.org/install.php)

4. Raid0 stripes (splits) the data across two drives, you gain space,  if a drive fails you loose your data. Raid1 mirrors data across two drives, if a drive fails you still have a copy of the data on another drive. [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

Does your dad work with Siemens SDH equipment ? If 'yes' ask him if they support tcp/ip on the management interface yet or still using crappy iso protocol.

---

### Post by Dekunuts on 2007-06-23
ah, thank you for the information, you seem te be a knowledgable person

As far as I know he's always talking about lucent technologies devices (now merged with alcatel i think), but I guess they could be using other brands as well. He favours Lucent, but that could be  because he used to work at lucent and develop the machines. But I will ask him your question and post what he said in a day or so.

Considering your reply, I think i will check out  ux11 first (once i figure out how to communicate with the machine:p) and decide on the linux install afterwards. Good to know there is also an ubuntu available, but for some reason i'd like to try another distro (broaden horizons etc);)

I have never set up raid stuff, but that's an opportunity to learn

I would also like to know what you think about the speed of the machine. We have a 233MHz strong arm risc pc with 96MB RAM at home with riscOS Select and that feels  faster than a 600 MHz PIII with win98se. So i know riscs are faster  (and so cold 0.5 Watt:D) than x86 stuff, but would this still be true about 'modern' cpu architecture. I have a socket A athlon 3000+ barton cpu. Do you think 2x500 MHz pa-risc cpu's would be faster than this or not?

thanks again

BTW I would like to study software engineering at university 3 months from now and thought this hp computer could help me learn a lot about computers that I do not  know yet.  I also bought a book about C so I can get started with that in advance as well. 

I assemble computers, configure dual boot (i sometimes use xp to check out a game demo, apart from that i have found linux alternatives for everything i do), make websites and have been using linux since ubuntu 5.10 and have learned a lot from that, but there is so much left to learn.

 oh and sorry about the spelling/grammar errors.

---

### Post by mips on 2007-06-24
> **Dekunuts said:**
> 
I would also like to know what you think about the speed of the machine. We have a 233MHz strong arm risc pc with 96MB RAM at home with riscOS Select and that feels  faster than a 600 MHz PIII with win98se. So i know riscs are faster  (and so cold 0.5 Watt:D) than x86 stuff, but would this still be true about 'modern' cpu architecture. I have a socket A athlon 3000+ barton cpu. Do you think 2x500 MHz pa-risc cpu's would be faster than this or not?


I honestly cannot comment on the speed of the machine as I have never worked with that machine. I have worked on a HP j5000 and that seemed plenty fast running hp-ux. One cannot really compare risc & cisc architecture based on clock speed as the design is so different and you have noticed this yourself with your arm risc machine (I would not mind having one of those).

It's even harder comparing older risc cpus to modern cisc cpus but I suspect in most cases the newer cisc will outperform the older risc cpu. The best way to test is to run benchmarks on them but a more subjective measurement would be to simply go with feel, if it feels fast to you then it ok.

Please keep us posted on your experiences with this server, would be interesting to hear your opinions on performance etc.

[http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=322777&lang=en&cc=us&taskId=135&prodClassId=-1&prodTypeId=15351&prodSeriesId=2512033](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=322777&lang=en&cc=us&taskId=135&prodClassId=-1&prodTypeId=15351&prodSeriesId=2512033)
[http://h21007.www2.hp.com/portal/site/dspp/menuitem.1b39e60a9475acc915b49c108973a801/?chid=6dc55e210a66a010VgnVCM100000275d6e10RCRD](http://h21007.www2.hp.com/portal/site/dspp/menuitem.1b39e60a9475acc915b49c108973a801/?chid=6dc55e210a66a010VgnVCM100000275d6e10RCRD)
[http://www.openpa.net/](http://www.openpa.net/)
[http://www.openpa.net/opsys.html](http://www.openpa.net/opsys.html)  You have a choice of operating systems.
[http://www.openpa.net/systems/rhapsody.html](http://www.openpa.net/systems/rhapsody.html)  Looks like it has a separate ethernet port to provide acces to the web console. another option is a remote X-session ?
[http://www.parisc-linux.org/](http://www.parisc-linux.org/)

I would start by upgrading all the machines firmware to the latest versions.

Edit: If you don't get the original HP-UX cd's with the machine I suggest you mirror the OS partition for backup purposes so you could restore the OS at a later stage if you need to.

---

### Post by Dekunuts on 2007-06-25
thanks again, i'll have it tomorrow (26th) and will remember to share my experiences. Still have to ask my father that question btw, will do though. ;)

BTW when I still used the acorn risc pc full time, I used this program called 'publisher' to write texts. It is frame based and works incredibly well and while open office works nice, it's way more complicated. Do you know of any frame based text editors that are easy to use and also 'powerful'? I have not found anything that can compare.

---

### Post by mips on 2007-06-25
> **Dekunuts said:**
> 
BTW when I still used the acorn risc pc full time, I used this program called 'publisher' to write texts. It is frame based and works incredibly well and while open office works nice, it's way more complicated. Do you know of any frame based text editors that are easy to use and also 'powerful'? I have not found anything that can compare.

Are you referring to Impression Publisher, a DTP package ?
[http://www.xat.nl/en/riscos/sw/imp/index.htm](http://www.xat.nl/en/riscos/sw/imp/index.htm)
[http://www.cconcepts.co.uk/products/publish.htm](http://www.cconcepts.co.uk/products/publish.htm)

Only Linux DTP packages I know about are [Scribus]("http://www.scribus.net/"), [Passepartout]("http://www.stacken.kth.se/project/pptout/"), [PageStream]("http://www.grasshopperllc.com/")

---

### Post by Dekunuts on 2007-06-26
Hello,

Thanks again, I'll check out those programs soon as I was indeed referring to Impression Publisher.

 I now have the server and I must say it's incredibly big. So big that I have yet to find a suitable space for it. I wanted to add a picture to the post, but the limit on attachment size is there so I'll rescale them and put them in an archive. 

The server is still sitting in the car at the moment so that's what you can see in the pictures. 

As you can see, there is no vga port, so I'll have to login remotely. It does have a dvd drive so that's that already.  The cpu's are  PA-8500 440MHz with 512/1024KB on-chip I/D L1 cache each , as stated on the website you linked to. 

Another problem are the power cables, it needs two power outlets, but the cables that came with it do not fit standard Belgian power plugs so I'll have to find some sort of converter for that as well. 

As for the question you asked, my dad says the SDH equipment uses OSI (you asked for iso but maybe that's a typo) and he says it does have advantages over tcp ip because it handles information by default that 'they later patched onto tcp ip'. It's easyer to define areas or something because the information is in the adress and therefore not every computer needs a really large routing table. Only the computers in his area and the one for a gateway to another area.

He also went on to say that 'the industry' deems it necessary to replace the current tcp ip protocol because they are runnig out of IP adresses. He also said IP was something like 4 bytes (or eight, can't remember) and OSI 24. I hope i somewhat transmitted that information correctly but I'm not sure.:(

voila. and I'll be back :)

---

### Post by jinx099 on 2007-06-27
You probly dont need to plug in both power cables, there are 2 power supplies for redundancy.  Also you should be able to use a standard PC power cable instead of the ones in the pics.  Hope this helps!

---

### Post by mips on 2007-06-27
> **jinx099 said:**
> You probly dont need to plug in both power cables, there are 2 power supplies for redundancy.  Also you should be able to use a standard PC power cable instead of the ones in the pics.  Hope this helps!

The connectors might be 'keyed' or 'notched' in which case you would have get keyed/notched cables. This is pretty common on Sun psu from what I recall. Dunno why they do it, have seen people cutting a normal pc connector with an angle grinder to create a notch.

---

### Post by jinx099 on 2007-06-27
> **mips said:**
> The connectors might be 'keyed' or 'notched' in which case you would have get keyed/notched cables. This is pretty common on Sun psu from what I recall. Dunno why they do it, have seen people cutting a normal pc connector with an angle grinder to create a notch.

Well, depends.  The keyed cables are heavier duty than the non-keyed ones, so you can use them in a normal power supply if you want, but I wouldn't go the other way around.  I cant see the PSUs in those pics, but if a normal power cable fits, go for it.  I work on HP Integrity (Itanium2) servers and I've yet to see a PSU that required the keyed cables.

---

### Post by Dekunuts on 2007-06-28
Hi,

The inputs in the server PSU's are indeed notched. I have a lot of spare power cables so I could cut some plastic out and hope it works. I'll post again once I have. 

As for connecting to it, my dad gave me the software they use at work, but that runs on XP. Since I still have XP on a second HDD, that's no problem. I would like to switch to a linux app as soon as possible so once I know what the general idea behind the winxp software is, I'll search for an alternative. I don't think finding that will be hard considering all the links and info you (plural) have already posted.

I'm going to clear some space right now so I can put the server somewhere 'permanently'. I'll post once i've tried the cable thing.

---

