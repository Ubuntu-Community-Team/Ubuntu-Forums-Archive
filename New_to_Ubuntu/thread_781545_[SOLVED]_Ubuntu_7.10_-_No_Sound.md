---
title: "[SOLVED] Ubuntu 7.10 - No Sound?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by UnknownFear on 2008-05-04
Hello all. I installed Ubuntu 7.10, but I have no sound. I searched online for my sound card and I found a linux-compatible sound card. Now, I have it on my desktop and I am ready to install it... but I don't know how to install it. The instructions on installing it are as follows:

[I]Installation
------------
1. As root type:

	make install

2. Add a new reference to the driver in /etc/modules.conf:

	alias sound emu10k1

3. Play some sound. The module should be auto-loaded.

Note for Debians' users: use /etc/modutils directory,
   create file emu10k1 here with the same content as is suggested in
   the paragraph (5.) and run update-modules afterwards - this
   will create the correct /etc/modules.conf file)
[/I]

Can someone help me out? I am aware that I need to be in the Terminal to install it, but some  help would be greatly appreciated. Thank you for your time.

---

### Post by Kosimo on 2008-05-04
You're running 7.10 instead of newer 8.04 for some particular reason?

---

### Post by dicecca112 on 2008-05-04
> **UnknownFear said:**
> Hello all. I installed Ubuntu 7.10, but I have no sound. I searched online for my sound card and I found a linux-compatible sound card. Now, I have it on my desktop and I am ready to install it... but I don't know how to install it. The instructions on installing it are as follows:

[I]Installation
------------
1. As root type:

    make install

2. Add a new reference to the driver in /etc/modules.conf:

    alias sound emu10k1

3. Play some sound. The module should be auto-loaded.

Note for Debians' users: use /etc/modutils directory,
   create file emu10k1 here with the same content as is suggested in
   the paragraph (5.) and run update-modules afterwards - this
   will create the correct /etc/modules.conf file)
[/I]

Can someone help me out? I am aware that I need to be in the Terminal to install it, but some  help would be greatly appreciated. Thank you for your time.

in terminal type sudo make install.  You'll have to be the folder the directions specify before that step.  it'll prompt for your password, enter it, and it'll display some output.  When its done type sudo gedit /etc/modules.conf.  Add that line to the bottom of the file.  I would then reboot.  Then if you have no sound, check to make sure nothing is muted in volume manager

---

### Post by mkrahmeh on 2008-05-04
hi
if the downloaded package is a compressed file, make sure to extract it first, and inside the newly created directory check if there is a configure file, which has to be executed by
```
./configure
```
and is supposed to generate a file named *makefile*
dont worry about the msgs rolling about your terminal, its normal, afterwards do the following to compile then install the driver respectively
note: u need to become a root to complete the following 

```
make
make install
```

if this ddnt work, go with adding that line to the /etc/modules.conf..
if u faced any troubles or got stuck at the middle of the process for any reason, plz post here.. 

good luck

---

### Post by UnknownFear on 2008-05-04
OK. I am stuck :( I'll be honest, I honestly do not know how to do this. Can someone please help me out?

---

### Post by Enlitend on 2008-05-04
you need to provide more info.
What's the name of the file you just downloaded?

---

### Post by UnknownFear on 2008-05-04
> **Enlitend said:**
> you need to provide more info.
What's the name of the file you just downloaded?

The name of the file I downloaded is emu10k1-v0.20a

---

### Post by mkrahmeh on 2008-05-05
> The name of the file I downloaded is emu10k1-v0.20a 

is this file an executable or a directory ??
post the output of
```
file emu10k1-v0.20a
```

also post the output of
```
ls -l emu10k1-v0.20a
```

---

### Post by keylime on 2008-05-05
I had a similar issue - upgrading to the newest flavor resolved my sound issue.

---

### Post by UnknownFear on 2008-05-05
Nevermind. I got my sound to work. I messed around with the settings. Thanks for everyones concern.

---

