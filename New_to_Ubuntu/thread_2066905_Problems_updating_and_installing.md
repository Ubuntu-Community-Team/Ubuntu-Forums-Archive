---
title: "Problems updating and installing"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by Azrael84 on 2012-10-05
Hi,

I seem to be having issues updating. Through update manager things just seem to hang, and if I try sudo apt-get update I get errors like Err 403 Forbidden. I tried creating a sources list then replacing the old one, but upon running the keys as the website suggested this also failed.

---

### Post by newb85 on 2012-10-05
Please post the output of 

```
sudo apt-get update
```

so we can see which sources are kicking the 403.

---

### Post by Azrael84 on 2012-10-06
Actually, today sudo apt-get update seems to work fine and no Err 403 generated, strange. Never the less if I try to update using update manager, which has a list of updates for me ready to install, I get:

> Requires installation of untrusted packages

The action would require the installation of packages from unauthenticated sources.

fonts-opensymbol gimp gimp-data gimp-plugin-registry libbabl-0.1-0 libcmis-0.2-2 libgegl-0.2-0 libgimp2.0 libreoffice libreoffice-base libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-filter-mobiledev libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-java-common libreoffice-math libreoffice-style-human libreoffice-style-tango libreoffice-writer libwps-0.2-2 python-uno spotify-client spotify-client-qt ttf-opensymbol uno-libs3 ure 

---

### Post by HunkirDowne on 2012-10-06
> **Azrael84 said:**
> Actually, today sudo apt-get update seems to work fine and no Err 403 generated, strange. Never the less if I try to update using update manager, which has a list of updates for me ready to install, I get:

Is there any functionality gained (other than ease of use) in the graphical update tool not realized by using apt from the command line?

I am admittedly a command line junkie and *still looking for that way to edit my spreadsheets from the command line *(not really).  :-/

---

### Post by Azrael84 on 2012-10-06
> Is there any functionality gained (other than ease of use) in the graphical update tool 

I'm more worried about why it's suddenly stopped working, and also why even after the command line update, the gui updater still has a big list of things it seems to want to update. Could it be a problem with the authentication keys or something?

---

### Post by Azrael84 on 2012-10-06
Actually it was apt-get upgrade that was successful, sorry. When I do apt-get update I still get the errors:

> Fetched 1,227 kB in 13s (91.8 kB/s)
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1015216E75198A89
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3BDAAC08614C4B38
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B302120208A255AF
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFF96872D340A3
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE


---

### Post by Azrael84 on 2012-10-06
I *seem* to have fixed this by manually adding keys in the manner

> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys B302120208A255AF 

for each missing key. I tried sudo apt-keys update first with no success. I then do sudo apt-get update with no errors.

Finally on update manager things seem to now install (I'm somewhat puzzled why there are items left to install at here; why did sudo apt-get update not do the installs?)

---

### Post by jrog on 2012-10-06
> **Azrael84 said:**
> I *seem* to have fixed this by manually adding keys in the manner . . . for each missing key. I tried sudo apt-keys update first with no success. I then do sudo apt-get update with no errors.
Just FYI, what you ended up doing is the standard procedure for adding repositories/PPAs. You must manually add the keys for those sources, either as you did or by installing a keyring package for the source (if it exists). This is a security feature. ('sudo apt-key update' only updates the existing local keyring with the keyring from the corresponding distribution archive.)

> **Azrael84 said:**
> Finally on update manager things seem to now install (I'm somewhat  puzzled why there are items left to install at here; why did sudo  apt-get update not do the installs?)
'sudo apt-get update' does not install anything. Did you mean 'sudo apt-get upgrade'? If so, if you don't tell apt that it can install from untrusted sources, it won't do so; that's probably why it didn't already install those packages.

---

### Post by newb85 on 2012-10-06
> **jrog said:**
> Just FYI, what you ended up doing is the standard procedure for adding repositories/PPAs. You must manually add the keys for those sources, either as you did or by installing a keyring package for the source (if it exists). 

Not necessarily.  If you add a ppa using the add-apt-repository command (or the apt-add-repository command for 12.10), the keys are added automatically.  IMO, a much simpler approach if the ppa is listed at launchpad.net.

---

### Post by jrog on 2012-10-06
> **newb85 said:**
> Not necessarily.  If you add a ppa using the add-apt-repository command (or the apt-add-repository command for 12.10), the keys are added automatically.  IMO, a much simpler approach if the ppa is listed at launchpad.net.
Good catch. You're right; I forgot that that option existed for Launchpad PPAs.

---

### Post by vkadal on 2012-10-07
I have follows all the suggestion in this thread. Used the sudo apt-get update command. There were some errors. Tried to fix individually. But still that error persists, even after reboot. Here is the copy of error message. Thank in advance for the help to come

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 531EE72F4C9D234C Launchpad webupd8
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by jrog on 2012-10-07
> **vkadal said:**
> I have follows all the suggestion in this thread. Used the sudo apt-get update command. There were some errors. Tried to fix individually. But still that error persists, even after reboot. Here is the copy of error message. Thank in advance for the help to come

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 531EE72F4C9D234C Launchpad webupd8
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
Try this and let us know the results:

```
sudo apt-get clean 
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update
```

---

### Post by vkadal on 2012-10-07
When I ran apt-get update the following was the error message

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 531EE72F4C9D234C Launchpad webupd8
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I am not able to install any package

---

### Post by Old_Grey_Wolf on 2012-10-07
> **Azrael84 said:**
> 
Finally on update manager things seem to now install (I'm somewhat puzzled why there are items left to install at here; why did sudo apt-get update not do the installs?)

Sudo apt-get upgrade does not install some things by design. Try ```
sudo apt-get dist-upgrade
```.
Here is an explanation of the differences between the two commands. [http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade](http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade)

---

### Post by jrog on 2012-10-07
> **vkadal said:**
> When I ran apt-get update the following was the error message

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 531EE72F4C9D234C Launchpad webupd8
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I am not able to install any package
I'm assuming this is after running the commands I mentioned above. If that's right, then you might try this. For each of the BADSIG errors in the output, take **the last 8 digits** of each value and put them into commands like this:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 3E5C1192
```^That's an example that should work with the last error (BADSIG 16126D3A**3E5C1192**) -- notice that only the last 8 digits of the BADSIG value are passed to --recv. I hope this makes sense. Do this for each of the BADSIG errors, then run:

```
sudo apt-get update
```and post the output here. This should at least fix *some* of the error messages, if not all of them (some of the keys you're having problems with are not Ubuntu keys, so I don't know that they'll be available on Ubuntu's keyserver). If it doesn't fix all of them, we'll take another step.

---

### Post by Old_Grey_Wolf on 2012-10-07
> **Old_Gray_Wolf said:**
> Sudo apt-get upgrade does not install some things by design. Try ```
sudo apt-get dust-upgrade
```.

Here is an explanation of the differences between the two commands. [http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade](http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade)

---

### Post by newb85 on 2012-10-07
> **Old_Gray_Wolf said:**
> Sudo apt-get upgrade does not install some things by design. Try ```
sudo apt-get dust-upgrade
```.
Here is an explanation of the differences between the two commands. [http://askubuntu.com/questions/81585...e-than-upgrade](http://askubuntu.com/questions/81585...e-than-upgrade)

Umm...I think the command is

```
sudo apt-get **dist**-upgrade
```

---

### Post by raja.genupula on 2012-10-07
open your terminal and do this 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

in the update process if you got any error then let me know .

---

### Post by Old_Grey_Wolf on 2012-10-07
> **newb85 said:**
> Umm...I think the command is

```
sudo apt-get **dist**-upgrade
```

Ooops, typo. One key off to the left. :)

I'll fix my original post. Thanks.

---

### Post by Old_Grey_Wolf on 2012-10-07
> **raja.genupula said:**
> open your terminal and do this 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

in the update process if you got any error then let me know .

I assume this is meant for vkadal. If so, that is why I wish people would start their own threads rather than confuse someone else's thread by posting their problem in it.

---

### Post by jrog on 2012-10-07
> **raja.genupula said:**
> open your terminal and do this 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```in the update process if you got any error then let me know .
EDIT: Nevermind. Missed the '*'.

---

### Post by vkadal on 2012-10-08
I tried all the suggestions in this thread. Still I am having the problem. This might have started after my last update using update manager. So I am waiting for some patch from ubuntu

---

### Post by jrog on 2012-10-08
> **vkadal said:**
> I tried all the suggestions in this thread. Still I am having the problem. This might have started after my last update using update manager. So I am waiting for some patch from ubuntu
Could you please post error messages here so that we can try to help you better? For example, what was the output of after these two commands?

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 3E5C1192
sudo apt-get update
```

---

### Post by vkadal on 2012-10-11
I solve this problem by going back to Ubuntu 10.4.4. Not a of solving the problem, but it serves my purpose. You can have it as a lost resort

---

### Post by pathmasri on 2013-07-04
Its still not working for me. Got the same error.. Any alternative ?

---

