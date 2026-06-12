---
title: "new server setup"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by drrwhistle3 on 2008-05-20
I may be posting this in the wrong forum but here it goes anyway.  I have a new server at work that was built about a year and a half ago.  The operating system that was istalled is xp professional edition.  As I am converting my personal (home) computer to Ubuntu and have the ability to decide what the new server will have I am tending towards making it Ubuntu (or some other form of Linux).  
I will be asking many questions because I don't know the answers.  I have setup the original server, windows server 2000, but not at all familiar with setting up a Ubuntu server.
1) Is there a guide to do it?
2) What version/distro is recommended and why?
3) All the current workstaions are running XP, how do I connect them and give permissions?
4) The current windows server has a couple of domains as this server is used for 2 businesses, can this be done with Ubuntu?
5) We are currently using M$ Mail as our internal mail server, what options will I have as I convert?
6) What info do you need to help me make the correct decision to sucessfully accomplish this transistion?

I probably will have many questions to follow so bare with me.

Thanks

---

### Post by superprash2003 on 2008-05-20
this is going to be quite a task, but it sure is possible.There are many guides on the internet to setup ubuntu server , a google search would give you good results.. you could use ubuntu server or red hat server, red hat is supposed to be one of the best linux server OS, ubuntu server is also good..Since you are new to ubuntu you might want to start with a GUI so you can install the gui on the ubuntu server.For domains you can use samba, i think they do support that.there are many mail servers for linux but since you are planning to shift im not sure whether all these mail servers have an option to import from MS mail server..

---

### Post by BDNiner on 2008-05-20
Since this is a production environment do you plan on paying for support? 
1) There are various tutorials all over this site and the internet on how to setup a basic LAMP server. 
2) I would stick to the latest LTS release if going with ubuntu. 
3) The LDAP server will take care of the domains, and network shares. you will also need Samba
4) I don't know about installing 2 domains on one linux server, i have not tried it.
5) There is open exchange which one of the techs i work with is currently trying to setup. He said that he would recommend paying for support if our company is serious about replacing our exchange servers with open exchange.

The hardest thing i feel is getting used to the command line. There is no GUI installed when you setup ubuntu server, so if don't know a lot about linux this could be a sticking point.

---

### Post by AstralliS on 2008-05-20
Look at following web address, maybe you'll find something you're looking for.

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")

---

### Post by BDNiner on 2008-05-20
Great link, that covers some of the OP points.

---

### Post by AstralliS on 2008-05-20
Yeah. I found some really good stuff on that website. Recommend to visit it. ;)

---

### Post by drrwhistle3 on 2008-05-20
Ok,  I will start reading.  I thought I would mention that the server has Dual Core AMD 270 2.0GHZ processor with 2GB RAM.  Will I still use the i386 version of hardy or the other for AMD?  Does it matter?  I also think there are 2 processors.  Not sure of that though.

---

### Post by BDNiner on 2008-05-20
In order to use 2 processors with a Dual Core AMD you need to use the AMD_64 version of ubuntu. if you use the i385 version the system will only detect and use one of the processors.

---

### Post by drrwhistle3 on 2008-05-21
Is there a way to tell for sure how many processors I have and what bit rate they are running, 32 or 64?

---

### Post by BDNiner on 2008-05-21
Yes by the model number. From what you say you have two cores on your processor. You can run this command to find the full specs on your processor
```

lshw -C CPU

```
It will list each core on your CPU separately and the processor's features.

---

### Post by hyper_ch on 2008-05-21
1) Many guides on the net
2) As server in a production area I'd use Debian. - Debian has proven to be rock-stable and Ubuntu is based on Debian. So what you learn in Ubuntu you can also apply do Debian.
3) How specific do permissions have to be? Generally the fileserver for sharing documents with windows clients is SAMBA
4) What kind of domains? Just normal internet domains for webpages and email? If so, do they use ASP to create dynamic sites? Databases?
5) There are many mail servers... I love postfix.

And don't use a gui :)

---

### Post by drrwhistle3 on 2008-05-21
Ok,  I can't connect the server to the net yet so I am using another to write what it says: 
```
*-cpu:0
    Product: Dual Core AMD Opteron(tm) Processor 270
    vendor: Advanced Micro Devices [AMD]
    physical id: 1
    bus info: cpu@0
    version: 15.1.2
    size: 2GHz
    width: 64 bits
    capabilities: fppu fpu_exception wp vme de psse tsc pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mnx fxsr sse sse2 ht syscall nx mmxext fxsr opt x86-64 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp

*-cpu:1
    Product: Dual Core AMD Opteron(tm) Processor 270
    vendor: Advanced Micro Devices [AMD]
    physical id: 3
    bus info: cpu@1
    version: 15.1.2
    size: 2GHz
    width: 64 bits
    capabilities: fppu fpu_exception wp vme de psse tsc pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mnx fxsr sse sse2 ht syscall nx mmxext fxsr opt x86-64 3dnowext 3dnow pni lahf_lm cmp_legacy ts fid vid ttp
```

I take it there are 2 processors.  So correct me if I am wrong but I should use the Hardy version of AMD 64-bit?

---

### Post by BDNiner on 2008-05-21
yes you should use the AMD 64bit version of Hardy.

---

### Post by drrwhistle3 on 2008-05-21
I have the ubuntu-8.04-dvd-amd64 3.64GB downloaded.  Is this the correct one or is there a different one for the server setup?
When I start to set up the server, particularly installing Ubuntu do I need to be hooked to internet?

---

### Post by drrwhistle3 on 2008-05-21
> **hyper_ch said:**
> 1) Many guides on the net
2) As server in a production area I'd use Debian. - Debian has proven to be rock-stable and Ubuntu is based on Debian. So what you learn in Ubuntu you can also apply do Debian.
3) How specific do permissions have to be? Generally the fileserver for sharing documents with windows clients is SAMBA
4) What kind of domains? Just normal internet domains for webpages and email? If so, do they use ASP to create dynamic sites? Databases?
5) There are many mail servers... I love postfix.

And don't use a gui :)

Please explain why Debian would be better?  I know so little about Ubuntu that I won't realize the difference.  I am not opposed to using either.  I just don't want to do things twice, especially when it is up and running.  

The current server acts more as a file sharing devise.  Whereas, the files are put there for access by whomever needs it.  There is an M$ Access database file there also.  However that is mainly it.  Trying to bring it around to the 21st century but the current server isn't capable.  One step a at time.  OH yeah, also an accouting package, Peachtree, I think.

The current mail (inner office) is done with M$ Mail.  This is no longer supported with any M$ OS's.  I will probably have to abandon it although I would hope to archieve and pull the contact list into a new package.  I am not sure if there is a compatable email package available in Linux though.

---

### Post by BDNiner on 2008-05-21
no that is wrong image, there is an ubuntu-8.04-server-amd64 ISO that you need to download to run the server edition. They should all be CDs and not DVDs. you will need to connect to the internet at some point. if you know all network information (which you should) then you can add this during the setup and connect to the internet once you are done. you will need to install upgrades once the server has been setup.

---

### Post by drrwhistle3 on 2008-05-21
Why no GUI? Is it possible to use GUI? I guess I just need to cowboy up and learn the code, huh?  It will get me further in the future I bet.

---

### Post by BDNiner on 2008-05-21
Well for linux and unix servers, yopu normally don't install a GUI since that would create unnessesary overhead. They would normally run headless (i.e. no monitor attached) and you use ssh to connect to the server from another computer. There are several ways to install a GUI, the easiest being
```

sudo apt-get install ubuntu-desktop

```
That will install the GUI that comes with ubuntu desktop edition but it has a lot of desktop software that is not necessary on a server. You could also try: 

```

sudo apt-get install xorg gdm gnome-core synaptic

```
this will install the basic gnome desktop, xorg, gdm and synaptic. the system will complain when you log in that there are some packages missing but you can then use synaptic to install any other packages that you need.

---

### Post by drrwhistle3 on 2008-05-21
Is there any reply to the Debian v. Ubuntu?  I am now downloading the Ubuntu pkg. but could do the same for Debian.  Although, which version?  Space isn't really an issue.  I think it is an internal battle for learning the code.  I have been doing more and more and feeling a lot more comfortable yet, unsure.

---

### Post by BDNiner on 2008-05-21
they are very similar, you can follow any guide for debian on an ubuntu computer and vice versa. Debian is supposed to be more stable, you can keep the servers running forever, or until you want to upgrade or patch the kernel. ubuntu is a child of debian, just like linux mint and linspire are also a childs of debian.

---

### Post by drrwhistle3 on 2008-05-21
Any idea which one will install for AMD -64 bit server?
```
Official torrents for the &#8220;stable&#8221; release
CD:
[alpha] [amd64] [arm] [hppa] [i386] [ia64] [mips] [mipsel] [powerpc] [sparc] [s390] [source] [multi-arch] 
DVD:
[alpha] [amd64] [arm] [hppa] [i386] [ia64] [mips] [mipsel] [powerpc] [sparc] [s390] [source] [multi-arch]
```

---

### Post by BDNiner on 2008-05-21
you should download the amd64 version of either the CD or DVD. The DVD has a lot more packages on it so you may not have to connect to the internet to install most of the software. I personally would download the CD version since it would be quicker and i would use the internet to install the extra software that i need that is not on the CD. The less useless software you have the better your server will run.

---

### Post by drrwhistle3 on 2008-05-21
Here are my choices, could there really be 21 cd's?  Or am I reading this wrong?[HTML]http://cdimage.debian.org/debian-cd/4.0_r3/amd64/bt-cd/[/HTML]

---

### Post by BDNiner on 2008-05-21
yes there are 21 cds. you should download the minimal bootable CD image since it has the fewest disks. installing Debian can seem daunting for people using linux for the first time. You should cut your teeth on ubuntu before attempting to install debian. The commands will be the same so you wont have to relearn anything.

---

### Post by drrwhistle3 on 2008-05-21
Ubuntu is stable enough?  I will be facing great opposition here when doing this and people will be looking for the opportunity to "I Told You SOOOOOO!!".  The only people that seem excited about the change are the MAC users who don't seem to mind the learning curve.  If it buggers up......

---

### Post by hyper_ch on 2008-05-21
If you want to go really stable the FreeBSD ;)

Else I'd use Debian for server... there's not really a difference in settin up - just a few things to remember:

(1) install openssh-server
(2) create another user
(3) disable root-login for root
(4) install denyhosts ;)

then do the rest ;)

---

### Post by BDNiner on 2008-05-22
ubuntu is stable enough to accomplish what you are trying to do. it just won't be easy. and it could be frustrating if you can't figure out a problem when something goes wrong. There is a steep learning curve with linux.

---

