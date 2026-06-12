---
title: "Can't install softwares."
date: 2011-11-07
forum: New to Ubuntu
---

### Post by Keshav2050 on 2011-11-07
When I try to install any software 

when I click the button 'Install' it gives messages 
[B]
"failed to download package files[/B]
  check your internet connection[B]"

[/B]and then,

[B]"Requires Installation Of untrusted Packages
[/B]The action would require the installation of packages from not authenticated sources.**"**

and in details it gives**"**libcddb2 libdvbpsi7 libebml3 libiso9660-7  libmatroska4 libsdl-image1.2 libtar0 libupnp3 libva-x11-1 libvcdinfo0  libxcb-keysyms1 libxcb-randr0 libxcb-xv0 videolan-doc**"**

What are untrusted packages and to what sources I should use(if I have to change) so that computer will be safe or I'll not have any problem?

---

### Post by dileepm on 2011-11-07
Well untrusted sources will be those which are not Ubuntu Repositories, ubuntu hosts repos that includes both canonical and third party developed packages. You may have to use Synaptic Package Manager for this. May I know in particular which package u r trying to install.

---

### Post by raja.genupula on 2011-11-07
> **Keshav2050 said:**
> When I try to install any software 

when I click the button 'Install' it gives messages 
[B]
"failed to download package files[/B]
  check your internet connection[B]"

[/B]and then,

[B]"Requires Installation Of untrusted Packages
[/B]The action would require the installation of packages from not authenticated sources.**"**

and in details it gives**"**libcddb2 libdvbpsi7 libebml3 libiso9660-7  libmatroska4 libsdl-image1.2 libtar0 libupnp3 libva-x11-1 libvcdinfo0  libxcb-keysyms1 libxcb-randr0 libxcb-xv0 videolan-doc**"**

What are untrusted packages and to what sources I should use(if I have to change) so that computer will be safe or I'll not have any problem?

you can use terminal , then its gonna ask you for the confirmation to install . By giving Y you can get them for installing .

all the best.

---

### Post by williamts99 on 2011-11-07
Sounds like you had a temporary internet timeout.  This happens sometimes, you should wait a few min, refresh the repos, and try again.

---

### Post by Keshav2050 on 2011-11-08
I am not able to Install any applications from ubuntu software center of ubuntu 11.10.
Internet connection's all right, I am able to open websites.  But I'm getting message to check the Internet connection and the installation failed. And then-

**Requires installation of untrusted packages**
The action would require the installation of packages from not authenticated sources.
details:
libcddb2 libdvbpsi7 libebml3 libiso9660-7 libmatroska4 libsdl-image1.2 libtar0 libupnp3 libva-x11-1 libvcdinfo0 libxcb-keysyms1 libxcb-randr0 libxcb-xv0 videolan-doc

In the terminal when I typed the command 'sudo apt-get update' I got

**"**Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.**"**


I've also tried to look in the link below, but nothing worked. What should I do?


[http://www.ubuntugeek.com/fix-for-gp...k-release.html]("http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html")

---

### Post by oldos2er on 2011-11-08
```
sudo apt-get clean

cd /var/lib/apt

sudo mv lists lists.old

sudo mkdir -p lists/partial

sudo apt-get clean

sudo apt-get update
```

---

### Post by Keshav2050 on 2011-11-09
Thank you very much, now there are no errors when I type the command 'sudo apt-get update'.:)

---

### Post by oldos2er on 2011-11-09
You're welcome!

---

### Post by Keshav2050 on 2011-11-15
Solved in another thread 
 				[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] 				**Can't install from software center**

---

### Post by lisati on 2011-11-15
Threads merged. Please do not start multiple threads for the same problem, it dilutes the community's efforts.

---

### Post by ntanitime on 2012-02-01
Thanks you!:D:D
I have the same problem!

I want to understand the problem.

Can you explain it ?

Maybe there is a old list of update, it is right?

---

### Post by ntanitime on 2012-02-04
There is anybody???

---

