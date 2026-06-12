---
title: "Ubuntu and Debian"
date: 2008-11-06
forum: Other OS Talk
---

### Post by frank.zappa on 2008-11-06
I was thinking of testing out Debian 4.0 in a virtual machine and was wondering something. I've heard that Ubuntu is pretty much based on Debian so would that mean that in the case that I did switch to Debian, that I could still use this forum for help?

What are some of the big differences in the two distros? 

Is there a any difference in the command line of the two? (just wondering because I just started learning how to use it in Ubuntu and wouldn't want to waste my time).

---

### Post by kerry_s on 2008-11-06
yes, i use these forums and use debian etch.

the difference is in design. they just do the same things in a different way.

no, not really a difference in commands.

---

### Post by frank.zappa on 2008-11-06
So would the package manager be the same? Could I download the same packages that I use for Ubuntu?

Just wondering, is it harder to find packages for programs on the internet for Debian?

And if you have the knowledge of the subject, could you shed some light on the difference between the use of root in the distros. I read somewhere that there's a difference but I didn't really understand it.

---

### Post by kk0sse54 on 2008-11-06
Debian has a huge repo and they both use APT, check this link out for somewhat of a comparison [http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Debian](http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Debian)

---

### Post by OutOfReach on 2008-11-06
The package manager are the same for both Debian and Ubuntu, apt.
I've been using Ubuntu .debs meant for Intrepid on Lenny and I haven't really seen anything negative happen. But generally, I can usually find .debs for Debian since it is still very known and supported.

Here are some differences that I could notice:
[LIST][*]Debian is somewhat lighter and faster than Ubuntu[*]They come with different applications (Debian coming with GNOME default applications)
[/LIST]
Those are just examples of differneces you can see, I am sure there are dozens more.

---

### Post by Sorivenul on 2008-11-07
The default Debian install is more sparse than the default Ubuntu install.  By this I mean there are fewer "extras" weighing down the machine.  However, this leads to more manual configuration on a fresh setup, but once things are going it should be smooth sailing.  I am running Debian Lenny right now.

---

### Post by notwen on 2008-11-07
Both have the capabilities of using apt-get or aptitude as far as CLI package managements goes.  Depending on which version of Debian you get(stable, testing, unstable) you will also see some package versions lag behind due to packages being frozen for the upcoming release.  So while Ubuntu's repos may get a newer version of X application, Debian stable may not see this updated version of X application in it's repos for some time.  I use both Debian and Ubuntu and you learn to appreciate the pros/cons of both in their slight differences.  I'd highly recommend trying it.  Best of luck to you.  =]

---

### Post by init1 on 2008-11-08
> **frank.zappa said:**
> So would the package manager be the same? Could I download the same packages that I use for Ubuntu?

Just wondering, is it harder to find packages for programs on the internet for Debian?

And if you have the knowledge of the subject, could you shed some light on the difference between the use of root in the distros. I read somewhere that there's a difference but I didn't really understand it.
You'll find that Debian and Ubuntu are very similar. Almost all apps that work in Ubuntu will work in Debian.
The difference in root is that (by default) Ubuntu uses sudo for root access and Debian just uses su. You can configure Debian to use sudo though.

---

### Post by AvixK7 on 2008-11-08
I've been thinking about trying Debian as well recently. Never really understood the difference between su and sudo. could someone elaborate?:)

---

### Post by Sorivenul on 2008-11-09
> **AvixK7 said:**
> I've been thinking about trying Debian as well recently. Never really understood the difference between su and sudo. could someone elaborate?:)

[su vs. sudo]("http://www.tuxmagazine.com/node/1000148")
[sudo manual]("http://www.sudo.ws/sudo/man/sudo.html")

---

### Post by dizee on 2008-11-09
> **AvixK7 said:**
> I've been thinking about trying Debian as well recently. Never really understood the difference between su and sudo. could someone elaborate?:)
you can always install sudo anyway if you prefer it.

---

