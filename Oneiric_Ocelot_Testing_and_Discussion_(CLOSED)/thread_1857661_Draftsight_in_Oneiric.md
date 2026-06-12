---
title: "Draftsight in Oneiric"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mateoarmenta on 2011-10-10
Hello,

Today I made a fresh install of Oneiric Ocelot, using the daily build. It is working flawlessly. I am just having one issue.

Draftsight. As usual I downloaded the .deb file from the Draftsight page. Now, when I double click it the Ubuntu Software Center launches and says a dependency (libxcb-render-util0) is not available: the program won`t install.

I installed Synaptic and looked for the package. Not there.

I tried sudo apt-get install libxcb-render-util0, but the package is not found either.

I looked for it in launchapad, founded it, and downloaded it. Installed it through the Ubuntu Software Center. Now I can install Draftsight. But ultimately the installation is not succesful. ([https://launchpad.net/ubuntu/oneiric/i386/libxcb-render-util0/0.3.6-1build1](https://launchpad.net/ubuntu/oneiric/i386/libxcb-render-util0/0.3.6-1build1))

Has somebody got any ideas of what I can do to get Draftsight running?

Thanks,

---

### Post by cariboo on 2011-10-10
Has the program been updated to work with GTK-3 libraries?

---

### Post by IanW on 2011-10-11
Probably not. The system requirements list Ubuntu 9.10.
Since it's closed source, a bug will have to be raised with Dassault Systémes (the suppliers of Draftsight).

EDIT: I've raised just such a bug on their forum (they don't have a bugtracker).

---

### Post by wgarcia on 2011-10-11
Another possibility is that "multiarch" is affecting it. Some libraries have now a different location because of the multi architecture changes coming from Debian.

---

### Post by mateoarmenta on 2011-10-11
Thanks for your responses.

So I guess this is an issue that will have to be taken care of by Dassault themselves. I will be installing Draftsight for Windows through Wine meanwhile.


Now, I found something. It is written in Chinese, but well, that`s for what Google Transalte is, right?

[http://translate.google.com/translate?hl=es&sl=auto&tl=en&u=http%3A%2F%2Fwww.ubuntu-tw.org%2Fmodules%2Fnewbb%2Fviewtopic.php%3Fpost_id%3D200590](http://translate.google.com/translate?hl=es&sl=auto&tl=en&u=http%3A%2F%2Fwww.ubuntu-tw.org%2Fmodules%2Fnewbb%2Fviewtopic.php%3Fpost_id%3D200590)

So it is necesary to install libxcb-util0_0.3.8-1_i386.deb

However, when I try to re-install it through the USC (apparently it is already installed) a pop up appears saying that if I install the package (wasn`t it installed already?) any future updated won`t include new elements of the Ubuntu desktop.

I didn`t reinstall it after reading that, of course.

Regards,

---

