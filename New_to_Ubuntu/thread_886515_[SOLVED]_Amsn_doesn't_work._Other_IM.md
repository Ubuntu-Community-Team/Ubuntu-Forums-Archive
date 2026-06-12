---
title: "[SOLVED] Amsn doesn't work. Other IM?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by speedzor on 2008-08-11
hi,

when I try to start amsn, it just keeps trying to log me in, without succes.
Is this a known bug? And how can this be fixed?

Or maybe you guys advise me another IM-program to chat with my msn-contacts?

---

### Post by kestrel1 on 2008-08-11
You could try Pidgin, should have been installed by default.

---

### Post by speedzor on 2008-08-11
I already use that for IRC, but can't figure out how to use it for msn..
Aren't there any good alternatives for msn?

---

### Post by hyper_ch on 2008-08-11
do you have updated amsn lately? there was a change in the msn protocoll.

---

### Post by speedzor on 2008-08-11
I think I did, but I'm not 100% sure..
Should I update it if I didn't?

---

### Post by Bölvaður on 2008-08-11
> **speedzor said:**
> 
when I try to start amsn, it just keeps trying to log me in, without succes.
Is this a known bug? And how can this be fixed?

Or maybe you guys advise me another IM-program to chat with my msn-contacts?

I also had this problem. The source of it is probably the same as the guy above me said. Which can be fixed by moving to newer version of aMSN, but it isn't in the repositories yet.

You might want to do the lazy mans fix like me. Use pidgin while it can't be found in synaptic.

How To msn in pidgin:

- Open Pidgin
-> Accounts -> Manage
- Add
- fill in Protocol as MSN and the rest accordingly
- Save
-> Accounts -> Enable Account -> [email]speedzor@msn.uk.co[/email]


I find the transfer faster in pidgin than in aMSN and the MSN clients but I miss many features from aMSN :(

---

### Post by Ryadt on 2008-08-11
> **speedzor said:**
> I think I did, but I'm not 100% sure..
Should I update it if I didn't?
Try removing the one in the repos and then download it from the amsn and install it.
website.[http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)
Make sure you choose the Tcl/tk 8.4 installer.

---

### Post by hyper_ch on 2008-08-11
there's an updated version in the hardy repos that work.

---

### Post by tuxxy on 2008-08-11
MSN updated their protocol, you need to update your aMSN to the new 0.97.2 version to access the network, download the 32/64bit update package here; [http://www.getdeb.net/app/aMSN](http://www.getdeb.net/app/aMSN)

---

### Post by Joeb454 on 2008-08-11
I'm suprised nobody has mentioned [emesene]("apt://emesene"). It's in the repo's :)

Those of you running Ubuntu, just click the link and it should install it for you :)

---

### Post by speedzor on 2008-08-11
well, tuxxy's link made things work again, so I didn't try emesene.
Next time I've got a problem, I'll try emesene ;)

---

