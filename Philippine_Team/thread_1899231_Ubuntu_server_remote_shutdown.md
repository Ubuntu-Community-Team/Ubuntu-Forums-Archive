---
title: "Ubuntu server remote shutdown"
date: 2011-12-23
forum: Philippine Team
---

### Post by inzaneGOD on 2011-12-23
Papatulong lang po sana ako gumawa ng script para mag-automatic shutdown yung ubuntu server, gumagamit po kami ng UPS and may software na po ako for windows and linux, ang problema ko na lang ay yung script na kapag nagkaron ng power failure mag eexecute ng script yung UPS na low battery na sya at i-sshutdown nya na yung mga server, familiar po ako sa mga linux commands pero pagdating po sa programming mahina ako, patulong naman po please.. salamat

---

### Post by lukeiamyourfather on 2011-12-23
This will shutdown Ubuntu (or any other Linux).

```

sudo shutdown -h now

```

---

### Post by inzaneGOD on 2011-12-23
yap yan  nga po kapg mag shutdown ka , pero ibig ko po sabihin yung script na iaupload ko sa UPS para mag execute kung sakaling may power failure na mangyari

---

### Post by inzaneGOD on 2011-12-25
up ko lang po

---

### Post by JCyberinux on 2011-12-25
did you try to google it :D or relevant post you be this link : [http://blog.mansonthomas.com/2008/10/setting-up-ups-link-with-ubuntu-server.html](http://blog.mansonthomas.com/2008/10/setting-up-ups-link-with-ubuntu-server.html)

i hope it helps you! :D

---

### Post by inzaneGOD on 2012-01-05
> **JCyberinux said:**
> did you try to google it :D or relevant post you be this link : [http://blog.mansonthomas.com/2008/10/setting-up-ups-link-with-ubuntu-server.html](http://blog.mansonthomas.com/2008/10/setting-up-ups-link-with-ubuntu-server.html)

i hope it helps you! :D

Sir thanks po! pero it only shutdown where the ups attached, yung nais ko po sana ay yung i-sshutdown nya yung server over the network. Meron na po akong software for UPS (WinPower) naka install sa ubuntu pc at sa pc na rin ito naka attached yung UPS

---

### Post by kiminaiseah on 2012-01-25
ssh root@serverip '/sbin/poweroff -f'

---

### Post by pinoyskull on 2012-01-26
baka merong management software ang UPS for linux that will do 'shutdown'

---

### Post by kiminaiseah on 2012-01-26
depende sa UPS kung anong remote capability meron siya

if ever meron sya snmp v2 

pwde magsent ng magic packet to command a shutdown

same command sa IPMI cards used sa Datacenters

---

### Post by inzaneGOD on 2012-03-04
salamat sa mga tumulong, solved ko na po yung problem.

---

