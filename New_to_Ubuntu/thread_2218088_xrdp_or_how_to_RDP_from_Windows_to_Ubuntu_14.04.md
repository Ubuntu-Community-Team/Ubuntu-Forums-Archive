---
title: "xrdp or how to RDP from Windows to Ubuntu 14.04"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by daveygabc on 2014-04-19
Hi all,

I am considering dual booting my Win8 machine with Ubuntu. The way I currently operate is by using my lower spec laptop to RDP to my higher spec desktop both running Win 8 (64).
Before trying Ubuntu I found a few pages describing how to RDP from windows to Ubuntu using xrdp. So, I downloaded 14.04 and ran it as "try" live CD. I search app center for xrdp and also tried the apt command to install with no matches.

Can this still be done ?

So, I want to use mstsc to connect to Ubuntu.

Any suggestions are welcome :)

Thanks
Dave

---

### Post by HermanAB on 2014-04-19
Howdy,
The better way is to install Cygwin with OpenSSH on Windows, and sshd on Linux, then open an X window shell on Windows, ssh to Linux and run whatever you want directly.

---

### Post by Double.J on 2014-04-19
Hi there!

A warm welcome to the forums!

I would recommend remmina to connect to the windows desktop. If you don't already have it, you can install remmina from the software centre. Of course, if you got xrdp working from the live CD and were happy with it, then there is no reason you can't use xrdp as before!

There's a pretty detailed on remmina from [here]("http://www.7tutorials.com/connecting-windows-remote-desktop-ubuntu"), but to be honest, If you're used to RDP it should be pretty straight forwad!

Jj

---

### Post by daveygabc on 2014-04-19
HI,

Thanks both for the reply.

Herman, would that method allow use a GUI or would it all be command line?

Double.J , I am after operating the other way around. RDP from Windows to Ubuntu.

Thanks,
Dave

---

### Post by Double.J on 2014-04-19
> **daveygabc said:**
> 
Double.J , I am after operating the other way around. RDP from Windows to Ubuntu.

Thanks,
Dave
Sorry my mistake!

You could also just use ubuntu's VNC server - set up vino on ubuntu then download real VNC on the windows machine?

Jj

---

### Post by daveygabc on 2014-04-19
> **Double.J said:**
> Sorry my mistake!

You could also just use ubuntu's VNC server - set up vino on ubuntu then download real VNC on the windows machine?

Jj

Sounds like a plan. Will test it in "try" mode. I have 100gb partitioned ready to install for when I get it sussed.

Do you have any idea why xrdp is not showing up on repo ?

Thanks
Dave

---

### Post by Double.J on 2014-04-19
> **daveygabc said:**
> 
Do you have any idea why xrdp is not showing up on repo ?

Thanks
Dave

That is strange, as far as I know it's still in the standard repos - it may be worth checking the sources in synaptic to check it's not just searching the CD (i had this bug in an earlier build of 14.04)

JJ

---

### Post by daveygabc on 2014-04-19
> **Double.J said:**
> That is strange, as far as I know it's still in the standard repos - it may be worth checking the sources in synaptic to check it's not just searching the CD (i had this bug in an earlier build of 14.04)

JJ


I was able to install java and another couple of apps from the GUI (Application App). search for rdp returned matches but search for xrdp never. Are you on 14 ? Do you return matches for xrdp ?

Also, is 14 (latest version on site) a good version for n00b ? Well, n00b ish. I need to work on RHL at work sometimes, but just to install files and navigate around. 

Thanks
Dave

---

### Post by daveygabc on 2014-04-21
Kind of given up Ubuntu for now as I can't get xrdp to work,, tried a few configs but still get a kind of a gridded screen with a black X for mouse pointer,, tried a few 2D gnome commands I found on sites but still same issue.
VNC is no good due to screen resolution and scrolling.
Has anybody successfully used xrdp with 14.04 ?

Thanks

---

### Post by Anders_Olofsson on 2014-04-24
> **daveygabc said:**
> still get a kind of a gridded screen with a black X for mouse pointer
Has anybody successfully used xrdp with 14.04 ?


Bump, exactly my problem!

---

### Post by Anders_Olofsson on 2014-04-24
After some googling I found: [http://c-nergy.be/blog/?p=5305](http://c-nergy.be/blog/?p=5305)
Trying that now.

---

### Post by Anders_Olofsson on 2014-04-25
> **Anders_Olofsson said:**
> After some googling I found: [http://c-nergy.be/blog/?p=5305](http://c-nergy.be/blog/?p=5305)
Trying that now.

Works.

---

### Post by zemega on 2014-04-25
Well, it works, but I guess the you cannot xrdp into the Unity interface anymore then?

---

### Post by matt_fussell2 on 2014-04-25
> **zemega said:**
> Well, it works, but I guess the you cannot xrdp into the Unity interface anymore then?

As far as I have read, Unity won't work in xrdp. I would actually recommend LXDE for remote access; it isn't nearly as heavy as Unity. Should you decide to give it a try with xrdp (assuming you don't already have it installed:

```
apt-get install lxde xrdp
```

Then make sure to add the .xsession file as so:

```
echo "lxsession -s LXDE -e LXDE" > /home/[your_username]/.xsession
```

---

### Post by monkeybrain20122 on 2014-04-25
> **matt_fussell2 said:**
> As far as I have read, Unity won't work in xrdp. I would actually recommend LXDE for remote access; it isn't nearly as heavy as Unity. Should you decide to give it a try with xrdp (assuming you don't already have it installed:

```
apt-get install lxde xrdp
```

Then make sure to add the .xsession file as so:

```
echo "lxsession -s LXDE -e LXDE" > /home/[your_username]/.xsession
```

In 13.10 pdf reader (evince) crashes in remote lxde session, does it work now in 14.04?

---

### Post by 5-tim on 2014-04-25
> **matt_fussell2 said:**
> As far as I have read, Unity won't work in xrdp. I would actually recommend LXDE for remote access; it isn't nearly as heavy as Unity. Should you decide to give it a try with xrdp (assuming you don't already have it installed:

```
apt-get install lxde xrdp
```

Then make sure to add the .xsession file as so:

```
echo "lxsession -s LXDE -e LXDE" > /home/[your_username]/.xsession
```
I get an error when I need admin access when using this.  It won't prompt for the sudo password, and I get an error.

Authentication Error
Software can't be installed or removed because the authentication service is not available (irg,freedesktop.PolicyKit.Error.Failed: 9'system-bus-name', {'name':'1.64'}): org.debian.apt.install-or-remove-packages.

---

### Post by matt_fussell2 on 2014-04-25
> **monkeybrain20122 said:**
> In 13.10 pdf reader (evince) crashes in remote lxde session, does it work now in 14.04?

I don't know - I haven't had the occasion to try it out. I'll give it a shot next week (the machine I'm working with is in the office).

---

### Post by matt_fussell2 on 2014-04-25
> **5-tim said:**
> I get an error when I need admin access when using this.  It won't prompt for the sudo password, and I get an error.

Authentication Error
Software can't be installed or removed because the authentication service is not available (irg,freedesktop.PolicyKit.Error.Failed: 9'system-bus-name', {'name':'1.64'}): org.debian.apt.install-or-remove-packages.

Did you install this as root? If you did, you might try uninstalling it as root and re-installing the packages as your user. Forgive me if my code was misleading; I've been writing server scripts all day. There is also a thread on the Ubuntu forums related to this error that can be found [here]("http://ubuntuforums.org/showthread.php?t=2099334").

---

### Post by cwmoser on 2014-04-26
How does xrdp compare with nxserver?
When I was working at a job administrating Microsoft systems, I used an nxclient on Win XP to
remote desktop into my home Ubuntu PC.  Worked great, was fast, and used ssh underneath.

---

### Post by yannella on 2014-04-26
> **Anders_Olofsson said:**
> After some googling I found: [http://c-nergy.be/blog/?p=5305](http://c-nergy.be/blog/?p=5305)
Trying that now.

This works!  Sweet.

---

### Post by 5-tim on 2014-04-26
> **matt_fussell2 said:**
> Did you install this as root? If you did, you might try uninstalling it as root and re-installing the packages as your user. Forgive me if my code was misleading; I've been writing server scripts all day. There is also a thread on the Ubuntu forums related to this error that can be found [here]("http://ubuntuforums.org/showthread.php?t=2099334").
I installed it normally I think.  I had the same problem with XFE4 (or whatever that other desktop was).  I think it's more an issue with the sudo plugin that prompts you for your password for your admin access.  You also can't change desktop resolution from inside the app because the desktop resolution app is too new (yes, you get a version error expecting 1.1 when it's 1.2).  

I managed to get X11VNC to run at startup and stay up, which gives me the unity desktop if I connect using VNC, which seems to work better than any RDP options.  I'll writeup what I did for others later.

---

### Post by matt_fussell2 on 2014-04-27
> **5-tim said:**
> I installed it normally I think.  I had the same problem with XFE4 (or whatever that other desktop was).  I think it's more an issue with the sudo plugin that prompts you for your password for your admin access.  You also can't change desktop resolution from inside the app because the desktop resolution app is too new (yes, you get a version error expecting 1.1 when it's 1.2).  

I managed to get X11VNC to run at startup and stay up, which gives me the unity desktop if I connect using VNC, which seems to work better than any RDP options.  I'll writeup what I did for others later.

I'm glad you found a solution to your problem.

---

### Post by Matthew_Rutledge-T on 2014-04-29
> **Anders_Olofsson said:**
> Bump, exactly my problem!

I'm not an expert, but I can share what I was able to do to get xrdp in 14.04 working.  Basically, I just had to use a different desktop-environment for xrdp sessions.

I installed Mate 1.8: [http://www.webupd8.org/2014/03/how-to-install-mate-18-in-ubuntu.html](http://www.webupd8.org/2014/03/how-to-install-mate-18-in-ubuntu.html)

Then edited .xsession to include the line

mate-session

Then I restarted xrdp.

---

