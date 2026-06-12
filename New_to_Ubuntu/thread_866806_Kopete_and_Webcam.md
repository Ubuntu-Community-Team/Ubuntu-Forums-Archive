---
title: "Kopete and Webcam?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by gfern on 2008-07-22
Hi guys, I've been trying to find a software to use as a MSN messenger capable of sending and receiving webcam streams. Kopete seems to do the trick better than aMSN cause aMSN is very unstable as to typing. When I type fast in aMSN, letter come in the wrong orders (depending if the have a special character ' ` ^)... its a mass. 

Anyway, here's the problem: Kopete recognizes my camera fine. Once in the configuration menu, I can see my camera working fine in that little window and everything seems to be ok. BUT, when I'm talking to a contact and I try to send or receive cam, nothing happens. I mean, really, nothing happens. I press the button to send my webcam and everything stay still, as if I had never pressed anything, not an error message, not a response whatsoever, the program just goes on working with total disregard for my attempt to send webcam... 

Any ideas?

---

### Post by Jukka-Pekka on 2008-08-02
Hello! I have exactly this same problem... with amsn everything works.

---

### Post by bigbrovar on 2008-08-02
try installing libjasper runtime   from synaptic  .. that might help

---

### Post by student21 on 2008-08-02
Hi guys

Sorry to piggyback on this thread but I need some help with this kopete or aMSN.

I've posted my problems in the following thread:

[http://ubuntuforums.org/showthread.php?p=5389781#post5389781](http://ubuntuforums.org/showthread.php?p=5389781#post5389781)

My requirement is I want to have voice, video, text chat like I did in YM on windows.  People say Linux YM is archaic and have suggested Kopete and aMSN.

With kopete, it just shows all contacts offline from my YM id.  Don't know how to sort out.  Only after that I can think if voice and webcam works.

In aMSN, I've created an account, but don't know how to fetch YM buddies or to contact them and simple things don't work.

---

### Post by Jukka-Pekka on 2008-08-02
> **student21 said:**
> Hi guys

With kopete, it just shows all contacts offline from my YM id.  Don't know how to sort out.  Only after that I can think if voice and webcam works.

In aMSN, I've created an account, but don't know how to fetch YM buddies or to contact them and simple things don't work.

aMSN is working with the WML-network, so it is probably not compatible with YM.

Ubuntu really needs some working solution for video messaging.

---

### Post by trash on 2008-08-17
it should be noted that libjasper and libjasper-runtime are NOT the same package and you may have libjasper installed, but libjasper-runtime is in the universe repository.
NOT exactly evident since libjasper in synaptic says it's a runtime library!

---

### Post by gatoguts on 2009-05-05
i have the same problem and installed libjasper-runtime to no avail :(  is jasper necessary for both msn and yahoo?  anyway, i'm not getting webcam support in either.  fortunately, skype works well for me and i use aMSN as a last resort

---

### Post by trash on 2009-05-07
> **gatoguts said:**
> i have the same problem and installed libjasper-runtime to no avail :(  is jasper necessary for both msn and yahoo?  anyway, i'm not getting webcam support in either.  fortunately, skype works well for me and i use aMSN as a last resort

libjasper-runtime is only used by kopete yahoo, i think for kopete and msn you have to use another program that handles video and voice but i'm not to sure(ekiga or gizmo maybe), i think it will tell you when you setup the account.

---

### Post by Toriam on 2009-11-15
Hola,
Kopete does the same thing as in the opening post to me. I'm running kubuntu netbook. I've installed and compiled everything JasPerish exept the Jasper vampire on Twilight. Nothing. Configure on Kopete sees ans uses my cam. I have a builtin cam on an acer aspire one a110. Any suggestions?

---

### Post by gordintoronto on 2009-11-15
> **Toriam said:**
> Hola,
Kopete does the same thing as in the opening post to me. I'm running kubuntu netbook. I've installed and compiled everything JasPerish exept the Jasper vampire on Twilight. Nothing. Configure on Kopete sees ans uses my cam. I have a builtin cam on an acer aspire one a110. Any suggestions?

Skype!

---

### Post by Toriam on 2009-11-15
I downloaded Cheese, which I enjoyed playing with on ubuntu. It works fine, but does nothing for Kopete.

---

### Post by Toriam on 2009-11-15
I have Skype, just inst last night. Gonne try that out. But programs not working as they should bugs the crud outta me.

---

### Post by Toriam on 2009-11-15
I just installed something called lucview, thinking it would help, and I don't see  that it does. BUUUUTTTT>>> I thought to run kopete under sudo in konsole, and it spat out this... (I also entered passwords) Can anyone translate?
toriam@Acer:~$ sudo kopete
Error: "/var/tmp/kdecache-toriam" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-toriam" is owned by uid 1000 instead of uid 0.         
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Calling appendChild() on a null node does nothing.
Error: "/tmp/ksocket-toriam" is owned by uid 1000 instead of uid 0.
Calling appendChild() on a null node does nothing.
toriam@Acer:~$ Unknown signature value:  0
Object::connect: No such signal ClientStream::disconnected()
Object::connect:  (receiver name: 'yahooclient')
Transfer ACCEPTED by: LoginTask
Transfer ACCEPTED by: LoginTask
Object::connect: No such signal ClientStream::disconnected()
Object::connect:  (receiver name: 'yahooclient')
Transfer ACCEPTED by: LoginTask
Transfer ACCEPTED by: LoginTask
Object::connect: No such signal ClientStream::disconnected()
Object::connect:  (receiver name: 'yahooclient')
Transfer ACCEPTED by: LoginTask
Transfer ACCEPTED by: LoginTask
Unknown signature value:  0
MMX: 1, SSE: 1, SSE2: 1, MMX-SSE: 1, 3dNow: 0, 3dNow+: 0
^C
toriam@Acer:~$ ^C
toriam@Acer:~$

---

### Post by Toriam on 2009-11-16
bump

---

