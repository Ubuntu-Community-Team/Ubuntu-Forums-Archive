---
title: "Muon Software Center"
date: 2011-09-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by maverickaddicted on 2011-09-17
Whenever I open Muon Software Center from Application Launcher and try to install any application it gives me this error
" This operation cannot continue since proper authorization was not provided ". This clearly means that it doesn't have any privileges, but how can I make this program to run as root.

I am using ubuntu 11.10. Please help me.

I am not able to install any application from software center, since default Ubuntu Software Center crashes every time I open it, I have also submitted the bug report regarding that in launchpad.

---

### Post by raja.genupula on 2011-09-17
try to launch the application with **gksudo application_name** 
it will ask you for root password and use it 
all the best .

---

### Post by howefield on 2011-09-17
Thread moved to development forum "*Ubuntu +1 (Oneiric Ocelot)*"

---

### Post by maverickaddicted on 2011-09-17
Thank you for replying, I know that command. However, It is a default software center for kubuntu( I think), why it does not get automatically launched via root privileges like ubunt software center OR
It can ask the root password, when I install any application.

---

### Post by dino99 on 2011-09-17
muon is badly buggy, install and use synaptic instead (more friendly) if you dont care about some gnome packages :(

---

### Post by maverickaddicted on 2011-09-20
Software Center runs perfectly using gksu software-center or sudo software-center.

Problem arises only while opening it via Application Launcher.

---

### Post by sumski on 2011-09-20
do you have polkit-kde installed?

---

### Post by gunksta on 2011-09-20
I would also try updating your system manually. It could be that something got out of whack. I just tried to install something with Muon and it worked fine.

```
 sudo aptitude update; sudo aptitude upgrade
```
or
```
 sudo apt-get update; sudo apt-get upgrade
```

---

### Post by maverickaddicted on 2011-09-23
I have updated my system several times, but the issue is still there. However, I need to check this polkit-kde package, I am on Windows; I do not want to, there is a problem with Dreamweaver 8.
I cannot paste data from my word file into the Design view section of Dreamweaver.

---

### Post by thatguruguy on 2011-09-23
> **maverickaddicted said:**
> I have updated my system several times, but the issue is still there. However, I need to check this polkit-kde package, I am on Windows; I do not want to, there is a problem with Dreamweaver 8.
I cannot paste data from my word file into the Design view section of Dreamweaver.

What?

---

### Post by Murz on 2011-09-26
I have the same problem after upgrade to Kubuntu 11.10: before I can install and upgrade packages via kpackagekit (it asks password), but now with Muon he didn't asked me the password, but show the message:
This operation cannot continue since proper authorization was not provided

---

### Post by effenberg0x0 on 2011-09-26
> **thatguruguy said:**
> What?

+1.

Regards,
Effenberg

---

### Post by maverickaddicted on 2011-09-30
Well, That is a Dreamweaver issue in Ubuntu. I will open the new thread for that with the screenshots.

---

### Post by maverickaddicted on 2011-10-09
Thank you, all of you for helping me. Now the Ubuntu Software Center works perfectly.

---

