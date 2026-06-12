---
title: "Amsn failing to connect"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by geekyhawkes on 2008-11-29
Hi,

ive been using amsn on my netbook (running hardy) with no problems.  Ive finally decided to bin windows on my main PC and have installed 8.10.  Generally everything is working fine (albeit that the Samba issues are driving me crazy!), but for some reason amsn isnt working.

The Amsn logon screen loads fine, and will sit there until you enter your logon details.  Once you try to connect to MSN it simply disappears as if it has been minimised.  I have tried removing amsn from Synaptic package manager and reinstalling, but the same thing is happening.  

Can someone steer me through how i might fix this issue I really like amsn and find pidgins lack of webcam support frustrating.

Thanks;

Andy

---

### Post by beno1990 on 2008-11-29
Open the terminal in your home directory (where the terminal is when you first open it by default) and type:

```

rm -rf .amsn

```

That'll delete your aMSN configuration files but if there's an error in there which is causing aMSN to quit on login, it should fix it.

Let me know if that works for you. :)

---

### Post by geekyhawkes on 2008-11-29
Thanks for the quick reply.  Sadly this hasnt fixed the issue.  I also tried removing amsn from synaptic and the config files as you described before reinstalling, same fault is present.  Wierd really as appart from trying to connect to my NAS with SMB i havent changed anything and it used to work.

---

### Post by geekyhawkes on 2008-11-29
I have changed my swapiness to 20 and am about to restart so i will let you know if this helps.  (The system is a P4 2.8Ghz with 512mb ram 30gb HDD)   

Edited:  Sadly swapiness hasnt changed anything

---

### Post by geekyhawkes on 2008-11-29
Any other ideas guys?

---

### Post by htmlland on 2008-11-29
I know this sounds a bit extreme but have you thought about changing your messenger client? I got fed up with aMsn in the end and now i jsut use Pidgin; but many do many diffrent things so just have a look around.

---

### Post by geekyhawkes on 2008-11-30
Im thinking i might have to, the problem i have with pidgin is it doesnt support webcam/audio very well (at all)

---

### Post by fr.theo on 2008-11-30
I tried AMSN for a while and had many problems also, I found Pidgin to be a more reliable instant messenger program, doesn't look as flash but does the job, although it does not support web cam and audio. Sorry I know that it does not answer the question just giving an opinion.

---

### Post by geekyhawkes on 2008-11-30
No problems, there fact amsn is so glitchy is probably why pidgin is included with the ubuntu distro as well.  

Thanks all for your help, looks like il be switching to pidgin.

---

