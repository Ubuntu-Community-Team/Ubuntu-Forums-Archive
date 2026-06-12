---
title: "Does Ubuntu need a app like Firewall and Anti Virus"
date: 2014-01-23
forum: New to Ubuntu
---

### Post by Victor_Jackson on 2014-01-23
Sorry I am so new to this OS but can or does ubuntu need a firewall or Anti Virus ?. I used Advanced System Care and Kaspersky IS on windows 7 ..does this os like that ? Thank you

---

### Post by GrouchyGaijin on 2014-01-23
The few anti-virus programs for Linux are basically for catching Windows viruses that could be passed on to Windows users.
It is my understanding that unless you are running a mail server, you don't need one.

The firewall setting I use is: (paste this command into a terminal)

```

sudo ufw default deny

```
which by default denies all incoming.

---

### Post by coldcritter64 on 2014-01-23
There is quite a bit of information in [[COLOR=#0000ff]--this thread--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=510812") by bodhi.zazen.

The section "Windows mindset" (scroll down the page some) covers antivirus. Firewalls are also covered there.

My experience is **no** for antivirus, except if sharing with windows machines (for their protection not Linux's) Other threats do exist and applications for security are available in the repositories. Most if not all third party applications like Avast or AVG for linux only really look for windows problems that are no threat to Linux.

A well set up firewall is also a very good idea on any system, depends on your tolerance of risks. I regularly use Ubuntu and Debian without one but am always very careful about what I install and stick I to the repositories for doing so where possible as first option.

If services/programs, that listen for connections or open ports, are **not** installed by the user then Ubuntu is reasonably safe in the hands of a careful user.

Ubuntu comes by default with a firewall (though disabled by default, as no ports are open after initial installation), UFW  or uncomplicated firewall.  There is also gufw, a frontend for ufw, that can also be added from the repositories if needed.

The code,

```
sudo ufw status
``` will show if it is enabled or disabled.

To enable,
```
sudo ufw enable
``` or ```
sudo ufw disable
```to shut it down.

see ```
man ufw
``` for more on the inbuilt firewall. Cheers

---

### Post by slooksterpsv on 2014-01-23
Does Ubuntu need an Antivirus? Not yet, but it may in the future. I don't foresee viruses really becoming a problem in Linux for a bit longer. Granted Android has viruses, spyware, etc.; I don't see regular distro's needing one yet.

---

### Post by mastablasta on 2014-01-23
android works in different way. it uses Linux kernel but heavily modificed one (part of it is not even opensource i believe). and as for user interface - it used something entirely different than Ubuntu. and let's nto forget that manufacturers don't really patch the firmware eventhought the new verison of Android is out.

while here system get's patches once, twice or even more times a week.

---

### Post by EnglishElectricAndy on 2014-01-23
FWIW here is my newbie's understanding so far, of Linux security:

- There are no known instances of Linux viruses "in the wild". By virus I mean a malicious data package capable of covert self-replication and onward transmission. Proof-of-concepts have been developed for the purposes of hardening potential vulnerabilities.

- Windows- specific malicious .exe's are inert in a Linux environment. I cannot speak for their functionality in WINE or Windows versions running in a VM as I do not use these.  As other posters have commented, if sharing between Linux and Windows a consistent policy of defence is essential.

- Malware that gives the appearance of affecting Linux distros is highly likely to be webpage based, exploiting weaknesses in, among others, Flash, Java, Acrobat and ActiveX. Configure your browser extensions accordingly.

- In a single user, single machine scenario the default ufw should be a sufficient firewall. Serving a LAN or remote machines will need attention to be paid to Inbound and Outbound rule configuration.

- Do not run as root, keep your password secure.

- Make regular backups. In the event of something untoward happening this procedure should reduce loss and inconvenience. Also keep a pristine copy of your distro on removable storage media.

- Last but by no means least, always act promptly upon software update notifications from your distro provider.

I' sure more experienced users will be able to fill in gaps in the above list as I'm still in the early stages of learning as well.

---

