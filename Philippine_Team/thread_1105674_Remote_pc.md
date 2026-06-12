---
title: "Remote pc"
date: 2009-03-24
forum: Philippine Team
---

### Post by guitar_man on 2009-03-24
mga sir,



Gusto ko lang matuto ng remote access,yung ubuntu to XP box.


Wala ako masyado alam sa remote.:(

---

### Post by daxumaming on 2009-03-25
I've been using TightVNC and accessing them using Remote Desktop Viewer. It works fine and fast. The only problem is, it doesn't work behind NAT. You'll have to use external services for that like GoToMyPC.

---

### Post by Script Warlock on 2009-03-25
i am currently using vnc and nx machine thru ssh.....ubuntu to xp or vice versa

---

### Post by guitar_man on 2009-03-25
> **daxumaming said:**
> I've been using TightVNC and accessing them using Remote Desktop Viewer. It works fine and fast. The only problem is, it doesn't work behind NAT. You'll have to use external services for that like GoToMyPC.

sir **daxumaming**


tama po ba?may bayad po GoToMyPC?



sir **Boyet**


pwede po konti instruction?
pwede po ba yun kahit hindi static ip?

---

### Post by Script Warlock on 2009-03-25
pwede kahit naka dynamic kung panandalian lang ang koneksyon at kung kinakailangan lang kc di safe ang RD kung walang tamang proteksyon.

hmmm assuming your a power user wala na dami ratrat...

ubuntu to xp:

**forget ubuntu kc nga meron built-in RD(remote desktop viewer)**

- download free real vnc sa xp box mo
- install it
- start it
- tapos go to firewall settings sa may advance tab check muna kung naka patong na nga ang vnc viewer
- tapos add ka din ng port 5900 pangalanan mo lang anything
- tapos ng lahat.....
- go to canyouseeme.org and check if your port 5900 is open
- if then, well time to make xp the slave for ubuntu

mas mabagal to kaysa nx machine pero ok na rin for educational purpose nga lang...

---

### Post by daxumaming on 2009-03-25
> **guitar_man said:**
> tama po ba?may bayad po GoToMyPC?

You could also try [LogMeIn]("https://secure.logmein.com/home.asp?lang=en"), it works great behind Firewalls and NAT. It doesn't even matter if you have Dynamic IP.
Been using that when I was still employed at a Call Center.

---

### Post by guitar_man on 2009-03-25
sige mga big boss,salamat...paglalaruan ko lang sandali to...hmmm

---

### Post by pinoyskull on 2009-03-25
i used Logmein when I was in Accenture before  :D

---

### Post by kiminaiseah on 2009-03-26
teamviewer, it works with wine

---

### Post by guitar_man on 2009-03-26
ngayon ko lang naisip wala pala ako ireremote na pc para magawa ko to..haay..:(

---

### Post by Script Warlock on 2009-03-26
sometimes kung wala akong dala na lappy going to bohol internet cafe ang pinpasokan ko to browse the server of my inet cafe shop sa cebu using nx machine web companion....

---

### Post by dodimar on 2009-03-26
> **guitar_man said:**
> ngayon ko lang naisip wala pala ako ireremote na pc para magawa ko to..haay..:(

NYAK??

hehehe... kung gusto mo mag practice... gawa ka ng virtual machine (via virtualbox or vmware server),, tapos yun ang i remote mo...

---

### Post by guitar_man on 2009-03-26
> **dodimar said:**
> NYAK??

hehehe... kung gusto mo mag practice... gawa ka ng virtual machine (via virtualbox or vmware server),, tapos yun ang i remote mo...


pwede pala yun???

---

### Post by dodimar on 2009-03-26
> **guitar_man said:**
> pwede pala yun???

pwede.. kaya lang... parang mawawala din yung sense ng remote desktop kung di naman talaga "remote" yung control mo.. pero at least ma pag practice ka kung pano mag connect....

---

### Post by Nhatz on 2009-03-27
Pwede na rin yun!!! hehehe :P

ASTIG!!! :guitar:

---

