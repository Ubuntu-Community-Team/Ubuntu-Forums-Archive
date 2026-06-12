---
title: "Remote Compiling"
date: 2010-10-19
forum: Programming Talk
---

### Post by talguy on 2010-10-19
I am going to be starting my dual masters program in Comp Sci and EE-Control Systems.  I'm working out a strategy on how I'll be able to do some homework while at work.  The EE stuff is pretty easy since its all textbook work but the computer science work is a little more difficult since I don't have any compilers on my work computer and nor will I probably ever I also don't have the ability to ssh or ftp into any other computer. So my strategy is can I setup a gmail account that is monitored by my server to download any new mail that has a zip file for an attachment.  unzip the file using some kind of shell script, compile the program and run it.  The the script will get the compiler's output and/or the programs output and email it back to me.  Does this seem possible what would be the best way to do it?  Can I use evolution mail to do an automated compiling system like this?  I have a limited amount of linux experience but love the system.  

I expect that the languages I will be dealing with will be java and c/c++

---

### Post by amauk on 2010-10-19
this seems over complicated, and a huge security flaw (compiling and running arbitrary code obtained through an email)

Any reason you can't install GCC on the machine?

You could even install a VM (using virtualbox) and run a small Linux server install for compiling and running stuff

---

### Post by talguy on 2010-10-19
I work for a defense contractor so we are only allowed to run the software that was preinstalled on the when we sat down at our desk.  maybe to help with the security problem I can encrypt the zip file so only files that are encrypted and are able to be decrypted with a certain passwor will work, but at the same time I really don't care about the security problem since it will be small nettop i'm thinking that is dedicated to this task.

---

### Post by dwhitney67 on 2010-10-19
> **talguy said:**
> I work for a defense contractor so we are only allowed to run the software that was preinstalled on the when we sat down at our desk.  maybe to help with the security problem I can encrypt the zip file so only files that are encrypted and are able to be decrypted with a certain passwor will work, but at the same time I really don't care about the security problem since it will be small nettop i'm thinking that is dedicated to this task.

Why not SSH (Secure Shell) to your home computer?

I agree that blindly accepting code, via email, and then running it is setting yourself up for trouble.

---

### Post by talguy on 2010-10-19
> **dwhitney67 said:**
> Why not SSH (Secure Shell) to your home computer?

I agree that blindly accepting code, via email, and then running it is setting yourself up for trouble.

I don't have an ssh client on my work computer

---

### Post by worseisworser on 2010-10-19
> **talguy said:**
> I don't have an ssh client on my work computer

Get a laptop.

---

### Post by worseisworser on 2010-10-19
..or use a web based SSH-client (AJAX or Java).

---

### Post by talguy on 2010-10-19
> **worseisworser said:**
> Get a laptop.
FYI, I work in the defense industry. We're not allowed to bring in personal computer and are limited to the types of electronics we can bring into the building

> **worseisworser said:**
> ..or use a web based SSH-client (AJAX or Java).
Didn't know the had these just searched around and found a free ssh java applet. 

Thanks for the suggestion

---

### Post by MadCow108 on 2010-10-19
if your not allowed to have an ssh client on your pc I kind of doubt you are allowed to use a web based version. I'd better ask before you get executed for treason.

concerning the mail solution (which should only be the last resort), there are many tools for sending and receiving mail on the command line which would simplify your approach.
I have never set up such a system, so I don't know the details but you could have a look at the mailutils and sendmail package.

---

### Post by talguy on 2010-10-20
I was able to launch the ssh java applet client yesterday while at work.  But haven't had a server address to test that I can make a connection.  My thoughts are that the firewall is probably blocking the ssh connections to outside sources.

---

### Post by dwhitney67 on 2010-10-20
Probably so.  To access my home computer, I had to configure my router to forward any data coming in to port 22 to my computer.

Btw, if you are able to use a different port than 22, you should.  Or consider installing [denyhosts]("http://denyhosts.sourceforge.net/"), or similar tool, on your system to thwart unwelcome folks from attempting to connect to your system.

---

