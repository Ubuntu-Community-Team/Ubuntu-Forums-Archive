---
title: "VLC un-installed and re-install matter"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by czgirb on 2012-10-05
Today, I don't know what button was pressed by my lovely boy, the VLC was un-installed. Now when I wish to re-install the VLC :

* via USC the following warning was displayed:
> Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Details:
The following packages have unmet dependencies:
vlc: Depends: fonts-freefont-ttf but it is not going to be installed
     Depends: vlc-nox (= 2.0.3+git20121005+r392-0~r42~precise1) but 2.0.3+git20121005+r392-0~r42~precise1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.3ubuntu0.12.04.1+medibuntu1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.3ubuntu0.12.04.1+medibuntu1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.2 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.2 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.2 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed


* via Terminal :
> czgirb@czgirb:~$ sudo apt-get install vlc vlc-plugin mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vlc-plugin
czgirb@czgirb:~$ 

* via Terminal with other command :
> czgirb@czgirb:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: fonts-freefont-ttf but it is not installable
       Recommends: vlc-plugin-notify (= 2.0.3+git20121005+r392-0~r42~precise1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.3+git20121005+r392-0~r42~precise1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
czgirb@czgirb:~$ 

Please help

---

### Post by androssofer on 2012-10-05
> **czgirb said:**
> Today, I don't know what button was pressed by my lovely boy, the VLC was un-installed. Now when I wish to re-install the VLC :



try:

```
sudo apt-get install fonts-freefont-ttf vlc-plugin-notify vlc-plugin-pulse vlc
```

---

### Post by czgirb on 2012-10-05
> **androssofer said:**
> try:

```
sudo apt-get install fonts-freefont-ttf vlc-plugin-notify vlc-plugin-pulse vlc
```

Still. There is no VLC installed
> czgirb@czgirb:~$ sudo apt-get install fonts-freefont-ttf vlc-plugin-notify vlc-plugin-pulse vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fonts-freefont-ttf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'fonts-freefont-ttf' has no installation candidate
czgirb@czgirb:~$ 


---

### Post by ParetoCDF on 2012-10-05
Hello,

same problem as czgirb here, I have updated my Ubuntu 12.04 yesterday and VLC disappeared. When I try to reinstall I get:

E: Unable to correct problems, you have held broken packages.

I have not been able to localize which packages are broken. The VLC installation via the Package Manager doesn't work either. I then tried to install the fonts-freefonts-tff but:

E: Package 'fonts-freefont-ttf' has no installation candidate

I think it is a problem of third party sources packages (restricted-extras, libdvdcss2 or others) I had "added" to VLC.

Thanks in advance for any help or suggestion!

---

### Post by hugh.st on 2012-10-05
> **ParetoCDF said:**
> Hello,

same problem as czgirb here, I have updated my Ubuntu 12.04 yesterday and VLC disappeared. When I try to reinstall I get:

E: Unable to correct problems, you have held broken packages.

I have not been able to localize which packages are broken. The VLC installation via the Package Manager doesn't work either. I then tried to install the fonts-freefonts-tff but:

E: Package 'fonts-freefont-ttf' has no installation candidate

I think it is a problem of third party sources packages (restricted-extras, libdvdcss2 or others) I had "added" to VLC.

Thanks in advance for any help or suggestion!

I had the same problem but I fixed it by completely removing vlc, including vlc-nox and vlc-data. Since I was using the vlc repo I removed that as well. Then I just updated the packages and reinstalled and vlc works fine again.

---

### Post by czgirb on 2012-10-05
> **hugh.st said:**
> I had the same problem but I fixed it by completely removing vlc, including vlc-nox and vlc-data. Since I was using the vlc repo I removed that as well. Then I just updated the packages and reinstalled and vlc works fine again.

Would you mind for sharing the detail with us?
**Thank you.**

---

### Post by wamai on 2012-10-05
Here it is 

*sudo apt-get install ppa-purge *

 ppa-purge  - disables a PPA and reverts to official
       packages

[I]sudo ppa-purge ppa:videolan/stable-daily
[/I]

This worked for me

---

### Post by mordalo on 2012-10-06
> **wamai said:**
> Here it is 

*sudo apt-get install ppa-purge *

 ppa-purge  - disables a PPA and reverts to official
       packages

[I]sudo ppa-purge ppa:videolan/stable-daily
[/I]

This worked for me

Purging the PPAs (I found two in Synaptic...really should clean house more often, but I get lazy at times) worked for me as well.  Once I deleted the PPAs, I used Synaptic to reinstall and it worked fine.

FYI, I found [this]("https://answers.launchpad.net/ubuntu/+question/210401") thread while trying to find a solution.  Basically, it says that package *fonts-freefont-ttf* may be called *ttf-freefont* in Precise.

---

### Post by czgirb on 2012-10-07
> **wamai said:**
> Here it is 

*sudo apt-get install ppa-purge *

 ppa-purge  - disables a PPA and reverts to official
       packages

[I]sudo ppa-purge ppa:videolan/stable-daily
[/I]

This worked for me
So ... is it means that I should type the following command in Terminal?
> *sudo apt-get install ppa-purge *
in order to disables the PPA and reverts to official packages
and followed with:
> *sudo ppa-purge ppa:videolan/stable-daily*
Please guide me ... for my ubuntu knowledge is not good
Thank you

---

### Post by androssofer on 2012-10-08
> **czgirb said:**
> So ... is it means that I should type the following command in Terminal?

in order to disables the PPA and reverts to official packages
and followed with:

Please guide me ... for my ubuntu knowledge is not good
Thank you

yeah just run:

```
sudo apt-get install ppa-purge
```

then run:

```
sudo ppa-purge ppa:videolan/stable-daily
```

then try installing vlc again:

```
sudo apt-get install vlc
```

---

### Post by czgirb on 2012-10-08
[I]Yup!
sudo apt-get install ppa-purge [/I]
[I]sudo ppa-purge ppa:videolan/stable-daily
[/I]

and log-out => log-in and re-install vlc
It works ... Thank you very much
So the thread is closed

---

### Post by ForEveryman on 2012-10-09
I had the very same problem yesterday and the fix described in this thread solved the problem. Thanks!
 
=D>

---

### Post by jakkups on 2012-11-13
I have the same problem as well. It happened today, but none of the advice in this thread has helped solve it, can anyone help me out? It would be very much appreciated.

---

### Post by jakkups on 2012-11-13
This is what it said is Ubuntu Software center

```
Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.1-4) but 2.0.1-4 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.1ubuntu1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.4ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.3 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.3 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.3 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed
```

Terminal

```
sudo apt-get install vlc 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 vlc : Depends: vlc-nox (= 2.0.1-4) but it is not going to be installed
       Depends: libavcodec53 (>= 4:0.8-1~) but it is not going to be installed or
                libavcodec-extra-53 (>= 4:0.8-1~) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.0.1-4) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.1-4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I don't know what happened. I clicked on update and it removed some stuff including VLC player. I'm running Ubuntu 12.04 if that helps out at all.

---

