---
title: "Problem with the EEEPC and it wifi"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Periswell on 2008-10-19
hello

ok ive trued everything. i have installed the kernal from array.org on both ubuntu eee and eeebuntu and i have installed the wadwifi and ndiswrapper on both of them also i have installed the eeecontrol tray thingy on both and STILL after all of this the wifi (wireless) is not working!!!!!! the furthest point i have got is up to this point (see attachments for image) and i do not know what to put in the boxes. i do not know what type i have (701, 900 ect) as it does not say anywhere. please help me.

-joshua

---

### Post by jamaas on 2008-10-19
How to make the wifi work depends on which model you have ... did you just get it new ?  

J

---

### Post by Periswell on 2008-10-19
we got it of pc world. this is the website > [http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@0071592910.1224423891@@@@&BV_EngineID=ccggadefheffhgecflgceggdhhmdgmj.0&page=Product&sku=305071](http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@0071592910.1224423891@@@@&BV_EngineID=ccggadefheffhgecflgceggdhhmdgmj.0&page=Product&sku=305071)
you can tell me what type it is as i haven't a clue.

-joshua

---

### Post by richg on 2008-10-19
It is a Asus EEE PC 4g model according to the link. Look on the bottom of the PC. Mine says 701, thwe sallest EEE PC model. I have the same one but not pink.  Ugh. Go to the link and click on Full Product Information.

I decided to stay out of trouble and use the Xandros Linux OS it comes with.
There are issues with the wifi using the default linux OS but since you use Ubuntu, I have no idea.
Go to the EEE OPC forums and ask.
[http://forum.eeeuser.com/](http://forum.eeeuser.com/)

Rich

---

### Post by zaivala on 2008-10-29
I, too, have an Eee PC 701 (aka 4G Surf)... I have been looking into using Ubuntu on it, but everything I read says that Ubuntu Netbook Remix is only for machines with an Atom processor, and the 701 has a VIA...  Does anyone have any information on using Remix with a 701?

---

### Post by macogw on 2008-10-29
According to Wikipedia, the 701 has a Celeron-M, and that is definitely Remix-compatible.

If it really is a VIA...what model VIA is it exactly?  You can post the output of "cat /proc/cpuinfo" if you like.

---

### Post by swisscow on 2008-10-29
Alternatively put mandriva on it. I did on my 901 and it works out of the box, as the advertising says. I put the gnome version on and it isn't that much different from Ubuntu

---

### Post by zaivala on 2008-10-29
> **macogw said:**
> According to Wikipedia, the 701 has a Celeron-M, and that is definitely Remix-compatible.

If it really is a VIA...what model VIA is it exactly?  You can post the output of "cat /proc/cpuinfo" if you like.

That's the new 701SD, not the 701 (aka 4G Surf)... hmmm guess you're right, Celeron M 353, whatever that means.

Even so, the Ubuntu official page for Remix says it is ONLY for the Atom.

---

### Post by macogw on 2008-10-29
> **zaivala said:**
> That's the new 701SD, not the 701 (aka 4G Surf)... hmmm guess you're right, Celeron M 353, whatever that means.

Even so, the Ubuntu official page for Remix says it is ONLY for the Atom.

It'll still work.  The reason they do that is because *certain* VIAs lack a specific CPU instruction that it needs.

---

