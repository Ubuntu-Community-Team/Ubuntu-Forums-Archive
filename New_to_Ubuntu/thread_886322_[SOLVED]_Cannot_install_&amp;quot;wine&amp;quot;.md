---
title: "[SOLVED] Cannot install &amp;quot;wine&amp;quot;"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by eternalnewbee on 2008-08-11
Hi everybody.
Can somebody help me out? I'm trying to install wine via synaptic and get the following error: [COLOR="Red"]Depends: winbind but it is not going to be installed[/COLOR]****
Thanks

---

### Post by wenuswilson on 2008-08-11
Wine's also in Add/Remove. Maybe that will be more successful?

---

### Post by eternalnewbee on 2008-08-11
thanks for your reply, I tried that first and was directed to synaptic.
Thanks anyways

---

### Post by wenuswilson on 2008-08-11
> sudo apt-get install wine

What is the output if it's unsuccessful?

---

### Post by eternalnewbee on 2008-08-11
> **wenuswilson said:**
> What is the output if it's unsuccessful?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: winbind but it is not going to be installed
E: Broken packages

---

### Post by wenuswilson on 2008-08-11
get winbind and see... it's in synaptic. then see if you can install wine.. good luck.

---

### Post by eternalnewbee on 2008-08-11
winbind:
  Depends: samba-common (=3.0.28a-1ubuntu4.4) but 3.0.28a-1ubuntu4.5 is to be installed

---

### Post by Novus on 2008-08-11
was samba-common installed?
and you still can't install winbind?

---

### Post by eternalnewbee on 2008-08-11
Thanks for your reaction.
That's right. I don't understand it either, because I installed Ubuntu 8.04 from the same cd on my own computer and wine works just fine...

---

### Post by eternalnewbee on 2008-08-11
I've just had an idea:
I'm going to remove samba-common and install it again and see what happens

---

### Post by eternalnewbee on 2008-08-11
OK, it worked!

---

