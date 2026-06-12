---
title: "Toshiba Satellite A100 - no fan"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by pierreu1 on 2012-08-20
This is related to this thread: [http://ubuntuforums.org/showthread.php?p=12184018#post12184018](http://ubuntuforums.org/showthread.php?p=12184018#post12184018)

It was running, but then not so much to keep the laptop cool. I am not too sure when my fan decided not to work as it should, but it could have been related to some Kernel upgrade or some other deletion I made in synaptic (of modules I thought I could get rid of). Not sure which is it, though. Maybe the hot temp fried things! Not sure! I did upgrade for Oneiric hoping that would clear the problem. During the install I had a lot of Kernel error messages (all of the same type), indicating pretty well all the same kind of message: linux image 3.2.0-29-generic ... not in working state exit status 2 (same image but 14 to 20).

I am not even sure if my fan is done or not. Is there a way to test for that?

Not sure if lmsensors is needed to be installed.

The thread above might be helpful, but I am not sure which fix to follow.

I would appreciate the help.

I have attached [a few result of tests]("https://docs.google.com/document/d/1z0XqFBj6fkJsOzjkfC4RzEwiAFRiI9DvDKUKTEhmDuY/edit") I did to help.

Not sure if [this]("https://docs.google.com/document/d/1e2EdsFA2esRAfnyLhOun58QHYwA0fSxzk3wqGCLST30/edit") helps.

Thank you.

---

### Post by llamabr on 2012-08-20
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Yes, if you havn't installed lmsensors, then you will need to

---

### Post by pierreu1 on 2012-08-20
> **llamabr said:**
> [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Yes, if you havn't installed lmsensors, then you will need to

Oh! Thanks! I guess I was afraid to finish running the whole lmsensors script.

I just did, saying yes to everything and then inputting:

sudo service module-init-tools restart

and I got,...

stop: Unknown instance: 
module-init-tools stop/waiting

Not sure what that means!

 did sensor and it returned this:

acpitz-virtual-0
Adapter: Virtual device
temp1:        +56.0°C  (crit = +106.0°C)
temp2:        +54.0°C  (crit = +96.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +54.0°C  (high = +65.0°C, crit = +85.0°C)


I also did this:


To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

pierre2@Pierre-Vancouver:~$ service module-init-tools start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.54" (uid=1001 pid=4612 comm="start module-init-tools ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")


Not sure if I messed up!

I have one more reading in the psensor,... of course: core.

But no fan!

---

### Post by pierreu1 on 2012-08-20
I restarted the laptop, but no fan.

---

### Post by pierreu1 on 2012-08-20
I noticed on a report I ran that I have:

ACPI PM1a_EVT_BLK
1004-1005	ACPI PM1a_CNT_BLK
1008-100b	ACPI PM_TMR
1010-1015	ACPI CPU throttle
1020-1020	ACPI PM2_CNT_BLK
1028-102f	ACPI GPE0_BLK

Can this help?

I have attached a detailed system's report to help.

---

### Post by pierreu1 on 2012-08-21
Okay I found [a post]("http://ubuntuforums.org/showthread.php?p=9197545#post9197545") on a thread that might help me (because it helped a lot of people), but I am getting an error message:

E: Unable to locate package sensors-applet

I have the psensor applet installed ( a K applet). Maybe that is the problem!

after I did:

sudo update-grub

Error

/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found

---

