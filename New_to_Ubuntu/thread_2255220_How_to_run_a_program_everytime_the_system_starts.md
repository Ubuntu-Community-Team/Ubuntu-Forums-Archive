---
title: "How to run a program everytime the system starts?"
date: 2014-12-03
forum: New to Ubuntu
---

### Post by black8 on 2014-12-03
Hey,
I want a commandline program(jtr) to be run everytime the system is awake. If I simply add the command to start it in /etc/profile, will it work? I am asking this question because I want to know if ubundu will launch the program and then continue with booting, or will it launch it, and then wait for it to finish before continuing with booting. If this is not the correct method to do, please guide me through how to do it. I want it to be run in the baground everyrtine the system is on.

I am new to Linux, and am not from an english speaking country. So please excuse me. 

Thanks

---

### Post by Bucky Ball on 2014-12-03
> **black8 said:**
> ... commandline program(jtr) 

What is the fullname of the program 'jtr'?

---

### Post by alket on 2014-12-03
Just open ubuntu menu and write "Startup ..."

---

### Post by JKyleOKC on 2014-12-03
> **black8 said:**
> I want a commandline program(jtr) to be run everytime the system is awake. If I simply add the command to start it in /etc/profile, will it work?Adding it to **/etc/profile** will cause it to be run **each time a user logs in**, but will not run it during the power-up process until someone logs into the system.

To run automagically as the final step of powering up, add the command to the **/etc/rc.local** file, just before the "exit 0" line. The whole purpose of this file is for launching such programs during the boot process; each such program will run as the superuser so no "sudo" is needed, and nobody will be logged in yet so all path references must be absolute rather than relative.

---

### Post by bapoumba on 2014-12-03
> **Bucky Ball said:**
> What is the fullname of the program 'jtr'?

Bump, please answer to this question, thanks.

---

### Post by black8 on 2014-12-03
Jtr stands for John The Ripper. So launching it from rc.local will launch jtr in a non-interactive shell and complete the boot and reach the welcome screen, while jtr is running in the background?

---

### Post by bapoumba on 2014-12-03
Thanks, that is what we thought.
Sorry but we wont support cracking applications here. Thread closed.

---

