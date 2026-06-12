---
title: "Help in using virtualbox"
date: 2008-06-24
forum: Philippine Team
---

### Post by ache109 on 2008-06-24
Hello Guys,

I'd just installed virtualbox in my system. Gumagana naman sya, but when I inserted the winxp cd and opened it via virtual box, lalabas ang installer nya pag boot ang gamit mo (o fresh install). Ok naman sa simula, but when it's installing the OS, minsan pag you configure the partition it hangs up. Kaya hindi ko sya ma-install. Please help me with this.

**Pasensya na at laging problema ang hatid ko sa inyo, I'm just a newbie in ubuntu talaga eh,

I'll attach nalang ung pics.


Thanks, 
ache109

---

### Post by pendletone on 2008-06-24
> **ache109 said:**
> Hello Guys,

I'd just installed virtualbox in my system. Gumagana naman sya, but when I inserted the winxp cd and opened it via virtual box, lalabas ang installer nya pag boot ang gamit mo (o fresh install). Ok naman sa simula, but when it's installing the OS, minsan pag you configure the partition it hangs up. Kaya hindi ko sya ma-install. Please help me with this.

**Pasensya na at laging problema ang hatid ko sa inyo, I'm just a newbie in ubuntu talaga eh,

I'll attach nalang ung pics.


Thanks, 
ache109

No need to worry, lahat naman tayo naging newbie at some point. Ako nga newbie rin eh...relatively speaking. :)

Ok back to topic, how much drive space did you allocate for your virtual machine? Baka naman mas malaki yung in-allocate mong size for your virtual disk compared sa *actual* remaining disk space mo. Or pwede ring masyadong malaki yung in-allocate mong base memory for your guest OS that you don't have sufficient memory left for your host. At what part exactly siya nag-hang? During formatting ba or sa installation mismo?

Did you use a dynamically-expanding drive? If it hangs during partition allocation/formatting, try to use a fixed-size one. Make sure that 'Enable IO APIC' is disabled. If it hangs naman during installation, try executing this in the terminal before installing windows:

```
vboxmanage setextradata [virtual machine name] "VBoxInternal/Devices/piix3ide/0/Config/IRQDelay" 1

```

If installation worked, execute this to revert it back:

```
vboxmanage setextradata [virtual machine name] "VBoxInternal/Devices/piix3ide/0/Config/IRQDelay" 0

```

Hope that helps.

:popcorn:

---

### Post by king leoric on 2008-06-25
Additional: it may help. I set up my virtualbox and XP by following this sites:

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html)

[http://www.ubuntu-unleashed.com/2007/10/howto-integrate-windows-xp-desktop-into.html](http://www.ubuntu-unleashed.com/2007/10/howto-integrate-windows-xp-desktop-into.html)

but since on the first one talk about the old virtual box, I download yung debian package sa site na ito:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

goodluck..mine is beautfully up and running

---

### Post by ache109 on 2008-06-25
> **pendletone said:**
> No need to worry, lahat naman tayo naging newbie at some point. Ako nga newbie rin eh...relatively speaking. :)

Ok back to topic, how much drive space did you allocate for your virtual machine? Baka naman mas malaki yung in-allocate mong size for your virtual disk compared sa *actual* remaining disk space mo. Or pwede ring masyadong malaki yung in-allocate mong base memory for your guest OS that you don't have sufficient memory left for your host. At what part exactly siya nag-hang? During formatting ba or sa installation mismo?

Did you use a dynamically-expanding drive? If it hangs during partition allocation/formatting, try to use a fixed-size one. Make sure that 'Enable IO APIC' is disabled. If it hangs naman during installation, try executing this in the terminal before installing windows:

```
vboxmanage setextradata [virtual machine name] "VBoxInternal/Devices/piix3ide/0/Config/IRQDelay" 1

 

```

If installation worked, execute this to revert it back:

```
vboxmanage setextradata [virtual machine name] "VBoxInternal/Devices/piix3ide/0/Config/IRQDelay" 0

```

Hope that helps.

:popcorn:

Sir I have only 256 MB of memory/RAM. I'd asked Mr.Google about this and he said that it requires a 512 MB of ram (1GB Reccomended). I have mah 1GB RAM, kaso hindi nya supported ang board ko (nag bo-boot syang mag-isa). Please help me w/ this. Or should I use "UBCDforWIN" instead??

Thanks, 
Ache109

At pahabol, dis is not a kinda problem but everytime I visit this forum page my HDD drive is getting into "critical thinking" (In other words halos hindi na umaalis ang LED ng HDD Drive ko?? Sa iba naman, (tulad ng virtualbox) hindi naman sya ganun, (puwera lang kung nag-hung na ung system when I install the xp thing pati ung drive ko nag-hung na...) 

And I tried it on fluxbuntu and it works!! It just stated that it's low on memory....

UBUNTU ROckS
:guitar::guitar::guitar::guitar:

---

### Post by pendletone on 2008-06-25
Sa pagkakaalam ko, you can *still* run virtualbox even if you only have 256 MB of RAM.  The only thing to watch out for is allocating too much memory for your guest OS that your host OS has little RAM left, or allocating too little to your guest that it doesn't meet its system requirements anymore (for XP, 64 MB is the *bare* minimum).

But of course, it's nicer to have as much RAM as possible para walang hassle sa pag-virtualize. :)

About UBCD4Win naman, I think we're better off trying to make virtualbox work for you kasi yung UBCD4Win is a bootable disc for diagnostic purposes at sa tingin ko that's not what you're looking for.

Kung ayaw talaga gumana ng virtualbox sa system mo, you can try [VMWare Player]("http://www.vmware.com/products/player/") and download a pre-configured Windows XP machine at their site.  Or better yet, just use wine.

---
Hmmm, nde ko na alam kung bakit umiilaw ang LED ng HDD drive mo pag binibisita mo tong forum natin.  Dito lang ba sa forum nangyayari yan?  Baka naman nagpapa-hiwatig ang PC mo na gusto nya parati kang bumisita dito. :lolflag:

---

