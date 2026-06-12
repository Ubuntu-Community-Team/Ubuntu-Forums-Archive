---
title: "Eclipse installation not working"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by bistro on 2008-08-25
Hi

I decided to try Eclipse 'Ganymede' so downloaded the archive file and unpacked it. I get the splash screen but it just hangs there, and in the processes list Eclipse is 'sleeping'. So I wonder if I installed it incorrectly - I did as follows as root:

cd /opt
tar zxf eclipse-reporting-ganymede-linux-gtk.tar.gz

then ran
/opt/eclipse/eclipse

Many thanks

Dave

---

### Post by phidia on 2008-08-25
Normally you wouldn't unpack the source file as root.
But ignoring that for a moment was there a directory created from unpacking and if so is there a README or INSTALL file there?

---

### Post by bankg3 on 2008-08-25
> **bistro said:**
> Hi

I decided to try Eclipse 'Ganymede' so downloaded the archive file and unpacked it. I get the splash screen but it just hangs there, and in the processes list Eclipse is 'sleeping'. So I wonder if I installed it incorrectly - I did as follows as root:

cd /opt
tar zxf eclipse-reporting-ganymede-linux-gtk.tar.gz

then ran
/opt/eclipse/eclipse

Many thanks

Dave
can you try running it not as root in the terminal so you can post the messages it gives back to you, if any.

Thanks!

---

### Post by bistro on 2008-08-25
Hi

thank you both for answering.

I installed it into my home directory as non-root user and it started but with the message "GCJ has been detected as the current Java virtual machine.  Use of GCJ is untested and unsupported." 

Answer to this was in the readme as you suggested, I installed sun-java and ran ./eclipse -vm /usr/lib/jvm/java-6-sun-1.6.0.06/bin/java

and everything seems fine so far!

Best wishes

Dave

---

