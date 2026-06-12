---
title: "HOWTO Enable Windows Live Mail"
date: 2006-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by hpklett on 2006-07-28
I know what you're thinking, who the hell uses Microsoft mail services?  I do.  I've had the account for too long to switch.  Anyway.

Windows Live Mail, though it supports Firefox, seems to do a dumb user agent check.  Here's a deadly easy fix:

1. [Download User Agent Switcher]("https://addons.mozilla.org/firefox/59/")
2. In Firefox, go to Tools->User Agent Switcher->Options->Options...
3. Click User Agents on the Left, then click the Add button.
4. Description: "Mozilla Firefox 1.5.0.4 (Windows XP)"
5. User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.0.4) Gecko/20060508 Firefox/1.5.0.4
6. Click OK, and OK again.
7. User Agents are listed under Tool->User Agent Switcher

Now you can switch to Mozilla Firefox (Windows XP) when you want to check your mail.  It's also handy for websites that check for Internet Explorer for no reason.

---

### Post by disciple on 2006-08-22
thx!!! it worked!

i also am still attached to my hotmail account, (had it since pre-MS buyout)

though i find it extremely silly that its functionality under linux firefox  is curtailed simply 'just because'

---

### Post by AirRaven on 2006-08-22
Excellent tip- I'd been annoyed about the lack of functionality under Linux for a while.

Thanks a lot!

---

### Post by pneaveill on 2006-08-27
> **AirRaven said:**
> Excellent tip- I'd been annoyed about the lack of functionality under Linux for a while.

Thanks a lot!
Might want to consider whether this is truly a linux problem or M$ protecting us from ourselves sort of motif? Is the fault of the people not being able to hack the M$ or is the fact that linux is being fought on every ground.  I believe that the linux people do an excellent job at what they do. Please keep in mind that by using linux, we are choosing to fight an uphill battle. Please let's not attack ourselves and each other.

With all that said, let me say this: I don't like the M$ crap any more than the next person. However, I am looking for work arounds and such. Until they come through, then I will go to the website and play the game.

---

### Post by GeorgeNorton on 2006-09-19
It's nothing to do with Linux. Livemail doesn't know about vendor and vendorSub strings. To fix it type about:config in the address bar and delete the values of *general.useragent.vendor* and *general.useragent.vendorSub*.

-George

---

### Post by Toxicity999 on 2006-09-24
Don't give them too much credit they constantly find off the wall ways to knock us down a peg. Of course they do it in way where people can defend it like stated before. Maybe it wasn't 'intentional' on there part but they surely can easily fix it.

---

### Post by SamsamTS on 2008-11-04
Here is a better way :
- type **about:config** in adressbar
- Add/Modify **general.useragent.override** option:
  32 bits : Mozilla/5.0 (X11; U; Linux x86; en; rv:1.9.0.3) Gecko/2008092510 Firefox/3.0.3
  64 bits : Mozilla/5.0 (X11; U; Linux x86_64; en; rv:1.9.0.3) Gecko/2008092510 Firefox/3.0.3

The new livemail don't like the "Ubuntu/x.xx (distname)" part in useragent variable so we just need to remove it.

To know your useragent (see Résultat) : [http://www.toutjavascript.com/reference/reference.php?iref=69](http://www.toutjavascript.com/reference/reference.php?iref=69)

---

### Post by xarroyo on 2008-11-04
Thanks, it worked nice for me.!!

---

### Post by MastroPino on 2008-11-19
> **xarroyo said:**
> Thanks, it worked nice for me.!!


Work for me too, really thanks man!

---

### Post by ken_do_san on 2008-11-19
This is an even easier way to got live mail to work, install flock browser, its basically built on Firefox, I have no problems getting into Hotmail, I don't even suffer the 'upgrade your browser' page.

---

