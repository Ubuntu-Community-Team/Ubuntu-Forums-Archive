---
title: "How do I execute programs with tar.gz"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by teslman98 on 2012-11-24
Hello!!!
I was wondering if anyone out there would be so kind as to help me figure this out.
I am new to Ubuntu and REALLY like it, but there is one program that I must have in order to use this great OS.

Thanks a lot,
N00b

---

### Post by qamelian on 2012-11-24
File names ending in tar.gz are just archives, like zip files. They can contain executables, source code, or just about anything. If you tell us what you're trying to install, you are more likely to get useful assistance.

---

### Post by mlentink on 2012-11-24
It depends...

.tar.gz is basically a compressed file format, that can either contain binaries with an installer (usually a '.bin' or somesuch), but could also be source code that would need to be compiled.  Take a look here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
 and maybe here:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by papibe on 2012-11-24
Hi teslman98. Welcome to the forums ):P

You can't, but...

A tar.gz file is equivalent to rar file. You first uncompress it, and then you see what was inside. Right click on the file and select 'Extract here'.

After that, there's no rule, but usually there's a README file with instructions on how to proceed further.

I hope that helps. Let us know how it goes.
Regards.

---

### Post by teslman98 on 2012-11-24
Ok, so I am trying to download a program called ZoneMinder.
When I open it up I see this:

---

### Post by teslman98 on 2012-11-24
that was supposed to be a screen shot...
Does the forum allow pictures?

---

### Post by teslman98 on 2012-11-24
I think it is in an attachment.

---

### Post by snowpine on 2012-11-24
Zoneminder is in the Ubuntu repositories, so you can easily install it with a few mouse clicks in the Software Center. :)

[http://packages.ubuntu.com/quantal/zoneminder](http://packages.ubuntu.com/quantal/zoneminder)

If you must install it from the tar.gz for whatever reason, then start by reading the README as was already suggested to you. ;)

---

### Post by monkeybrain2012 on 2012-11-24
zoneminder is in the respository. Just install it with the software centre.


If you get a tarball the instructions to install is in a file called Install if it exists (or Readme if it doesn't)

---

### Post by teslman98 on 2012-11-24
Snowpine,

I went to the link and then to ubuntu software center,
it gave me this error message:

---

### Post by snowpine on 2012-11-24
A properly configured Ubuntu system should not show that error. Please copy & paste the results of the following Terminal commands:

```
sudo apt-get update
sudo apt-get install zoneminder
```

---

### Post by teslman98 on 2012-11-24
There was another link and when I installed I got another error message.

---

### Post by snowpine on 2012-11-24
> **snowpine said:**
> A properly configured Ubuntu system should not show that error. Please copy & paste the results of the following Terminal commands:

```
sudo apt-get update
sudo apt-get install zoneminder
```

 .

---

### Post by teslman98 on 2012-11-24
So now on the terminal it says :

---

### Post by snowpine on 2012-11-24
> **teslman98 said:**
> So now on the terminal it says :

Recommend to do what it suggests, then try my suggestion above.

---

### Post by teslman98 on 2012-11-24
Ok snowpine,
when I manually ran it, it gave me this message.

---

### Post by snowpine on 2012-11-24
You can fix the CD-ROM error by commenting that line out in your /etc/apt/sources.list file (type a # symbol at the beginning of the line).

I have no idea what the I/O error is all about, sorry. One explanation might be the hardware failure of your drive.

---

### Post by monkeybrain2012 on 2012-11-24
Apparently there is a bug. 

[https://bugs.launchpad.net/ubuntu/+source/zoneminder/+bug/940632](https://bugs.launchpad.net/ubuntu/+source/zoneminder/+bug/940632)

There are some workarounds on the page you can try.

---

### Post by teslman98 on 2012-11-24
Can we go back to post number 12 and see if we can fix that prob?
And by the way pinetree, thank you so much for being so responsive!

---

### Post by monkeybrain2012 on 2012-11-24
> **teslman98 said:**
> Can we go back to post number 12 and see if we can fix that prob?
And by the way pinetree, thank you so much for being so responsive!

Not really, as you can see there is a bug in the repository package, you may want to try the tarball route.

Read Install and see what it says.

---

### Post by snowpine on 2012-11-24
Recommend you read either [the bug report]("https://bugs.launchpad.net/ubuntu/+source/zoneminder/+bug/940632") (if you wish to install from the repos) or the README (if you wish to install from the tarball).

---

