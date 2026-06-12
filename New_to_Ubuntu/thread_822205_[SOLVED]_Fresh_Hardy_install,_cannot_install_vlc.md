---
title: "[SOLVED] Fresh Hardy install, cannot install vlc"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by tstack77 on 2008-06-08
This is what I get:

xxxxx@xxxxx:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libiso9660-5 but it is not installable
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: libvcdinfo0 (> 0.7.23) but it is not going to be installed
       Depends: ttf-dejavu but it is not installable
       Depends: vlc-nox (= 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3) but it is not going to be installed
       Depends: vlc-plugin-pulse but it is not going to be installed
E: Broken packages


Any ideas?

---

### Post by aysiu on 2008-06-08
Sounds as if there's something wrong with your software repositories.

Paste these commands into the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.not.working.list
gksudo gedit /etc/apt/sources.list
``` A blank text document should appear. In that blank document, paste the following: ```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hardy universe
deb-src http://archive.ubuntu.com/ubuntu hardy universe

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted

deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe

deb http://archive.ubuntu.com/ubuntu hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy multiverse

# deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu hardy partner

# deb http://packages.medibuntu.org/ hardy free non-free
``` Save the document and close it. Then ```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by avtolle on 2008-06-08
I have gotten the same error message on 8.04 ppc when trying to install vlc. I thought I'd read something a while back about vlc being broken, but aysiu's post makes me doubt my memory. I'm trying this again, and will report back if successful.

---

### Post by tstack77 on 2008-06-08
That worked, thanks. So all I did there was erase my sources and install new ones?

---

### Post by Bubba64 on 2008-06-08
Have you put medibuntu in the3rd party repository section of software sources. Vlc is not in mediuntu but I think associated packages that may fix your problems are.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
When you put this in and reload you ill get some downloads install them and try Vlc again. This is all assumption but a quick look at Google and vlc medibuntu brings this answer this mind. Ah yes and at the bottom of the list is medibuntu posted by aysiu

---

### Post by avtolle on 2008-06-08
I was successful in installing vlc from Synaptic just now, using the ppc repositories which are different from those for other releases. Now, to see if this install, with the Pulse Audio plugin, will give me sound, and not the "white noise" I'm getting on the other ppc machine/installation.

---

### Post by tstack77 on 2008-06-08
I did have medibuntu installed. The only other repository I added was for AWN. Should I not try to add the AWN repository again?

---

### Post by aysiu on 2008-06-08
Yes, my instructions renamed your previous sources to something else and then gave you a fresh set.

Even though I made Medibuntu available, I didn't enable it (the # sign in front of that line means it is deactivated).

VLC isn't in Medibuntu anyway. It's in Multiverse.

I don't know if AWN caused the problem or not.

---

### Post by pfeels on 2008-06-17
I did the above and installed vlc, the problem is it or movie player won't play my dvd's, I'm searching on the how to's to install new codecs but as of yet haven't found any ... Also and I don't know if this matters but on my vista side of the computer the dvd's won't play in windows media and the tech support couldn't fix the problem, they had me download vlc and that works fine (but only on the vista side, I'd like to have the same on the Ubuntu side) ...

Any help would be a ppreciated

---

### Post by dash4g on 2008-10-18
> **aysiu said:**
> Sounds as if there's something wrong with your software repositories.

Paste these commands into the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.not.working.list
gksudo gedit /etc/apt/sources.list
``` A blank text document should appear. In that blank document, paste the following: ```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hardy universe
deb-src http://archive.ubuntu.com/ubuntu hardy universe

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted

deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe

deb http://archive.ubuntu.com/ubuntu hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy multiverse

# deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu hardy partner

# deb http://packages.medibuntu.org/ hardy free non-free
``` Save the document and close it. Then ```
sudo apt-get update
sudo apt-get install vlc
```

Thank you aysiu you are a god amongst men, this solved my problem as well.

---

