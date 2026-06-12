---
title: "apt-get consider recommended as dependencies?"
date: 2006-07-12
forum: Repositories &amp; Backports
---

### Post by cstudent on 2006-07-12
In Synaptic I have my preferences set to consider recommended packages as dependencies so it goes ahead and installs those too when I install some program. Is there any way to do the same thing using apt-get at the command line?


.

---

### Post by mazirian on 2006-07-12
You may use aptitude instead of apt-get, which is generally the preferred method of invoking apt according to Debian docs.  PLease read aptitude's man page for instructions on having it automatically install reccomended or suggested packages.  Basically there is a command line flag that I now forget, and there is a setting you may make in a file in /etc/apt/ somewhere that accomplishes the same thing.  Hope that's helpful.

---

### Post by asimon on 2006-07-12
AFAIK apt-get doesn't support this. But you could use aptitude instead.

You can use aptitude just like apt-get, i.e. 'aptitude update', 'aptitude dist-upgrade', 'aptitude install kubuntu-desktop' all work like the apt-get commands. aptitude considers recommends per default as dependencies. It also has the options --without-recommends, --without-suggests, --with-recommends, --with-suggests.

EDIT: Oops, seems I was too slow. ;-)

---

### Post by cstudent on 2006-07-12
Thanks Mazirian. I was reading through the apt-get man pages when you responded. Looking up aptitudes man I found it right away. I just need to use aptitude with the --with-recommends switch. I can also use --with-suggests.

---

### Post by cstudent on 2006-07-12
> **asimon said:**
> AFAIK apt-get doesn't support this. But you could use aptitude instead.

You can use aptitude just like apt-get, i.e. 'aptitude update', 'aptitude dist-upgrade', 'aptitude install kubuntu-desktop' all work like the apt-get commands. aptitude considers recommends per default as dependencies. It also has the options --without-recommends, --without-suggests, --with-recommends, --with-suggests.

EDIT: Oops, seems I was too slow. ;-)


LOL. Thanks anyhow asimon.

---

