---
title: "Why when question is asked, every one answers the opposite?"
date: 2018-02-12
forum: New to Ubuntu
---

### Post by ridky on 2018-02-12
I'd like to to know how to assign permission to everything on the machine.
every answer I find is, how to cancel permissions....

What gives?

---

### Post by QIII on 2018-02-12
Before I say anything, let me express this in no uncertain terms:  ***You** should **not** assign permissions for **everything** on your machine.  The OS should be setting the vast majority of permissions -- which is generally done at install time.*  The system is designed in such a manner that certain file permissions are required for operation.  If you change those permissions, you will probably render your machine inoperable.

Now, to answer the question of changing the permissions assigned to *some* files that can -- and sometimes should -- be changed, you might want to read [this]("https://help.ubuntu.com/community/FilePermissions").  That probably will cause you to have even more questions, so please feel free to come back here to ask them.

---

### Post by ridky on 2018-02-12
Hi,
trying to install java. Want to move the folder 'jdk-9.0.4' to 'usr/lib' where, what I believe, it has to be before install.

It's now in 'downloads'.

Sure, I don't have a permission to move it there. How can I move it, and is it the right move for Java install?

ThanQ

---

### Post by QIII on 2018-02-12
Where did you download it from?

---

### Post by ridky on 2018-02-12
oracle.com

here we go - questions...
 anyhow, now i get this 'sudo: error in /etc/sudo.conf, line 0 while loading plugin "sudoers_policy"sudo: /usr/lib/sudo/sudoers.so must be only be writeable by owner
sudo: fatal error, unable to load plugins'

 how to get back?
 would you know?

---

### Post by QIII on 2018-02-13
I would suggest a much easier approach.

Andrei at webupd8.org has put together a package of scripts that handles downloading and installing Oracle Java for you.  He updates the package as Oracle releases new updates to Java, so it will be updated along with your normal OS updates.

webupd8.org does not keep the actual binaries because Oracle no longer allows that.  The scripts provided by webupd8.org simply automate the process for you.

Please follow the instructions [here]("http://www.webupd8.org/2015/02/install-oracle-java-9-in-ubuntu-linux.html").

---

### Post by ridky on 2018-02-13
Great!

Working well. thnx

---

### Post by Impavidus on 2018-02-13
> **QIII said:**
> The system is designed in such a manner that certain file permissions are required for operation.  If you change those permissions, you will probably render your machine inoperable.

> **ridky said:**
> anyhow, now i get this 'sudo: error in /etc/sudo.conf, line 0 while loading plugin "sudoers_policy"sudo: /usr/lib/sudo/sudoers.so must be only be writeable by owner
sudo: fatal error, unable to load plugins'

There you see how changing permissions messes up your system. The rule on this forum is that whenever a user asks how to disable security on his computer and turn it into a bot running DDoS attacks, we don't give a straight answer and instead tell that user that's not a good idea.

---

### Post by TheFu on 2018-02-13
Linux and Unix are multi-user operating systems from the bottom up.  It is part of the core to the OS. Programs run with different accounts (userids) as part of the security model for the entire system.  File permissions are the core of that security.  So .... changing the file and directory permissions for files is usually a really bad idea and will break things.

I'm a believer in providing a warning that doing something is a bad idea, but still trying to answer the question asked.  A few days ago, someone wanted to read an SD card that wasn't working, so I suggested they copy the data off using a lower level tool, known to be good at data recovery.  That person seemed to copy/paste some instructions they found and completely wiped the SD card data. It is gone, never coming back.  He could have just as easily copied the SD card data into the start of the hard drive with the OS, effectively wiping his OS completely. It would have been really bad.  I felt bad for the guy that he lost important data.  He chose what to enter and did it wrong.  Linux let him do something stupid.

Linux will let you do something stupid. Linux doesn't know when the command you tell it is genius or total stupidity. YOU are expected to know.

Almost every OS on the planet is based on Unix and file/directory permissions are a key skill to have for all those operating systems. Learning and understanding these will pay off over and over during your life.

---

### Post by ridky on 2018-02-14
ThankQ guys.
Now a new problem........

I installed Plank and when starting it shows a gtrey screen with diff  loogo and my  password wll not get me in.
Screen goes blank for few secs and then back to sign up screen,

What gives?

thnx

---

### Post by coffeecat on 2018-02-14
@ridky, a new problem needs a new thread. Preferably with a title that refers to the technical problem you need help with.

So, please start a new thread, giving as much relevant information as possible. Are you using Ubuntu or one of the Ubuntu flavours? Which release number? How did you install Plank? What is Plank? I've never heard of it, but some googling tells me it could be either a lump of wood or a simple dock. I doubt you are referring to the former, and a dock shouldn't need a password, so details please.

Good luck!

---

### Post by oldrocker99 on 2018-02-14
Remember that the command line assumes that **you know exactly what you are doing.** It is very easy to completely hose your system if you're careless, which is why sudo (SuperUserDO, which, BTW, is pronounced Soo-Doo, not Su-doh) expires after a few minutes and requires that you enter your password again to keep going. Read this:[https://www.tecmint.com/10-most-dangerous-commands-you-should-never-execute-on-linux/](https://www.tecmint.com/10-most-dangerous-commands-you-should-never-execute-on-linux/).

---

