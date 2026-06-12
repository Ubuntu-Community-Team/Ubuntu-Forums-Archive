---
title: "[SOLVED] How to configure firestarter"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by phoenix_abhi on 2008-05-25
How can I configure my firestarter ? In Ms windows it is pretty easy ? But here I am facing difficulty ? Pls some one help ?

By default it has inbound traffic policy. Here my net works bothway
When I shifting to outbound policy Traffic stops entirely. Is it supposed to be stop only out bound traffic ? I may be asking silly Qs but not aware about the PROTOS

---

### Post by shifty_powers on 2008-05-25
why do you need to touch firestarter?

never even bothered to install it and everything just works as ti should ;)

---

### Post by phoenix_abhi on 2008-05-25
I have read a lot about hacking and cracking etc..and sure that windows are more Vulnerable. But what about Ubuntu ? If it is not necessary, how can I scan my ports ?

---

### Post by shifty_powers on 2008-05-25
tbh, just don't stress it.

ubuntu is not invulnerable, no, but it is FAR more secure than windows.

just leave firestarter alone and get used to the fact that you have a pretty safe and useable os ;)

(though it's not impossible to crack ubuntu, it is pretty damn hard ;))

---

### Post by sayakb on 2008-05-25
I find Firestarter useful, just because it somewhat stops ubuntu from transferring packets to Packet capture and password stealing apps (that use WinPCap driver).

---

### Post by phoenix_abhi on 2008-05-25
Yes, I too want same protection specially from password stealing apps. My email ID had been hijacked and password changed, by some good fellows, forced me to create and distribute another one. It made me rethink and I shifted to Ubuntu, but the possibilities are here too. So back 2 my Q, How can I configure that ?

---

### Post by Nepherte on 2008-05-25
The documentation on their website is self-explanatory and pretty complete:
[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

I don't really understand the question here. Under the policy tab, just block all incoming connections and allow only outgoing connections on the ports you specify (http(s), pop3, smtp, etc...).

---

### Post by sayakb on 2008-05-25
> **phoenix_abhi said:**
> Yes, I too want same protection specially from password stealing apps. My email ID had been hijacked and password changed, by some good fellows, forced me to create and distribute another one. It made me rethink and I shifted to Ubuntu, but the possibilities are here too. So back 2 my Q, How can I configure that ?

Unless you add any port/host to Allow list, Firestarter would by default block all incoming connections. The blocked connections would be shown in the Events list. To allow services from a specific port, right click on the event and select  "Allow inbound services on port"

---

### Post by zetetic on 2008-05-25
> **phoenix_abhi said:**
> How can I configure my firestarter ? In Ms windows it is pretty easy ? But here I am facing difficulty ? Pls some one help ?

By default it has inbound traffic policy. Here my net works bothway
When I shifting to outbound policy Traffic stops entirely. Is it supposed to be stop only out bound traffic ? I may be asking silly Qs but not aware about the PROTOS

Don't use Firestarter.

Learn IPTables and make your own IPTables script.

---

### Post by phoenix_abhi on 2008-05-25
Hi
Linuxisinnovation. That was helpful. My firestarter has stopped 100s of connexions after I had upload the image with my ip add. Ha ha it is essential, now I will use it when ever I login

---

### Post by sayakb on 2008-05-25
You need to run firestarter with root privileges (ie with a sudo). To your session startup, add:
```
sudo firestarter --start-hidden
```That would start the app in tray icon mode.

EDIT: Sorry, adding firestarter with a sudo to sessions will not work for you (Though does work on laptops having fingerprint recognition when sudo waits quietly for the finger to be swiped, as in my case)
You might have to start firestarter manually each time you log in.

---

### Post by phoenix_abhi on 2008-05-25
> **LinuxIsInnovation said:**
> You need to run firestarter with root privileges (ie with a sudo). To your session startup, add:
```
sudo firestarter --start-hidden
```That would start the app in tray icon mode.

EDIT: Sorry, adding firestarter with a sudo to sessions will not work for you (Though does work on laptops having fingerprint recognition when sudo waits quietly for the finger to be swiped, as in my case)
You might have to start firestarter manually each time you log in.

:)
Usually I do it with every login. But today I decided to learn more  


):P):P):P

---

