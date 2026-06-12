---
title: "The Install Paradox"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-16
I am comfortable using 11.10 except that I have not connected to a home work-group and its printer.

I am at another computer and I cannot install, let alone extract the driver for a Gsky USB wifi adapter.

In Ubuntu 11.10 I can easily install Chromium, change the screen, etc.  To get to this point, Ubuntu and a CD program Plop had automatic installs that were user friendly and easy to use.

I would imagine that there are other like-minded beginners that would love to have a driver installation program.

Something like:  Download driver
                 Place it [here]
                 Plug in hardware
                 Press enter.

11.10 sees my Gsky adapter but it just indicates that there is a hidden (to me) hardware switch that needs to be switched???

I am 73 and as of today, Alzheimer's has not completed its installation in my CPU.  After reading many similar posts, I am sure that I am not alone.

Does installing a driver have to be so difficult?

---

### Post by Zill on 2012-04-16
> **Boyntonstu said:**
> ...I would imagine that there are other like-minded beginners that would love to have a driver installation program...
...Does installing a driver have to be so difficult?
This link may help explain things...

[Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by QIII on 2012-04-16
I don't think he is asking for Linux to be like windows, nor do I think he was asking for a trite answer.

Boyntonstu -

Yes, that would be quite nice for your case.  Unfortunately there are only so many people willing to work for peanuts to do what OEMs do to make sure their installers work in Windows.  (Microsoft doesn't care if the installer is no good.  If it's not, the driver doesn't go in the driverbase and the OEM starves.)

You can't really blame the OEMs.  It's just good business to concentrate on the market segment where the big money is.

Sometimes we have to make do and come to places like this for help.  Not a perfect world.  Alas.

There's a poster by the handle wildemanne39 who usually patrols the forums looking for people facing  wifi issues.  Hopefully he will be by soon.

---

### Post by Boyntonstu on 2012-04-16
> **QIII said:**
> I don't think he is asking for Linux to be like windows, nor do I think he was asking for a trite answer.

Boyntonstu -

Yes, that would be quite nice for your case.  Unfortunately there are only so many people willing to work for peanuts to do what OEMs do to make sure their installers work in Windows.  (Microsoft doesn't care if the installer is no good.  If it's not, the driver doesn't go in the driverbase and the OEM starves.)

You can't really blame the OEMs.  It's just good business to concentrate on the market segment where the big money is.

Sometimes we have to make do and come to places like this for help.  Not a perfect world.  Alas.

There's a poster by the handle wildemanne39 who usually patrols the forums looking for people facing  wifi issues.  Hopefully he will be by soon.

Thanks,

Your response is exactly what I needed to hear.

Actually, I was not thinking about an installer of a program.

Are drivers installed like programs?

After hunting around, this is my concept for installing 3rd party adapter drivers:

Install the JDK
Download he 32bit or 64bit Linux "compressed binary file" - it has a ".tar.gz" file extension i.e. "[java-version]-i586.tar.gz" for 32bit and "[java-version]-x64.tar.gz" for 64bit
Uncompress it

tar -xvf jdk-7u2-linux-i586.tar.gz (32bit)

tar -xvf jdk-7u2-linux-x64.tar.gz (64bit)

JDK 7 package is extracted into ./jdk1.7.0_02 directory. - Now move the JDK 7 directory to /usr/lib

sudo mv ./jdk1.7.0_02 /usr/lib/jvm/jdk1.7.0

Is this what I need to do?

Could it be automated?

---

### Post by QIII on 2012-04-16
I understood that you were talking about drivers.  I'm sorry if my answer was not clear on that account.

Can driver installations be automated?  Yes.

Sometimes OEMs make their driver installation easy, even for Linux.

Sometimes the installation is not straight forward and requires a lot of downloading, un-tarring, chmod'ing, moving, etc -- all of which can be intimidating, even inscrutable, to new users.  

Sometimes someone has kindly taken their time voluntarily to automate the thornier installation processes.  That is the "I have your back" nature of much of the Linux community.

There are some drivers that are made available for easy installation of various Linux distributions' repositories and others that are already part of the kernels and require no further installation. 

Generally, it is easiest to install drivers made available in the package managers of the various distros -- as long as those drivers are kept reasonably up to date.

Your USB wifi adapter may be available in the repos, or it may be a simple matter of activating/inserting the proper module into the kernel.

It's a mixed bag.

Like i said, you have to remember that OEMs are businesses and they make business decisions.  For some, that means not bothering to make a nice installation package for their Linux drivers -- or just not making a Linux driver for their product at all.  In the latter case, there are often those who write open source drivers with varying levels of success.  Remember that they are essentially backward engineering into a black box.

And now, for a recommendation...

Your thread title is not likely going to catch the right person's eye.  Your title should be something specific, but also concise.  "Can't install driver for XYZ USB wifi" would probably draw flies.

I myself only stopped by here out of curiosity, and stayed only because I didn't like the first unhelpful answer you got.  I really don't have any specific knowledge about this particular issue.

I don't usually start threads, so I don't remember how to do it, but I think you can modify the subject line.  If you can, try something along the lines of my suggestion.

---

### Post by cortman on 2012-04-16
Really admire your tenacity OP. When you start a new thread PM me a link and I'll have a look at it myself. Good luck!

---

