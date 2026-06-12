---
title: "How to use Truecrypt"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-05-15
All the documentation I can find on truecrypt is too technical for me to understand.

Basically this is what I need:

1. IF possible encrypt my entire ubuntu partition (about 70gb, while leaving the 20gb windows partition unencrypted) - how would I go about doing this? Will it delete any files, etc.? How is this "secure"? Will I need an additional password to login?

2. Otherwise I would like to create a drive or something where I can just dump some files that I would like "extra" secure.

3. I want to encrypt a USB stick COMPLETELY. However, will I be able to use it on a windows/mac box without any trouble (WITHOUT having truecrypt installed on those computers)? Can I copy and paste files normally after encrypting.

Number 3 is the most essential, as I am VERY careful with my laptop, however, a usb stick is quite likely to get lost/stolen.

---

### Post by Sinkingships7 on 2008-05-15
> **abhiroopb said:**
> All the documentation I can find on truecrypt is too technical for me to understand.

Basically this is what I need:

1. IF possible encrypt my entire ubuntu partition (about 70gb, while leaving the 20gb windows partition unencrypted) - how would I go about doing this? Will it delete any files, etc.? How is this "secure"? Will I need an additional password to login?

2. Otherwise I would like to create a drive or something where I can just dump some files that I would like "extra" secure.

3. I want to encrypt a USB stick COMPLETELY. However, will I be able to use it on a windows/mac box without any trouble (WITHOUT having truecrypt installed on those computers)? Can I copy and paste files normally after encrypting.

Number 3 is the most essential, as I am VERY careful with my laptop, however, a usb stick is quite likely to get lost/stolen.

1. No. That's not how TrueCrypt is used. It creates a virtual volume, and everything put into that volume is encrypted as it's put in. To gain access to this volume, you have to mount it using the TrueCrypt software (and only that software will work) and provide your password. If you were to "encrypt" your entire Ubuntu partition, nothing would be accessible upon startup, and the computer would not be able to boot into the OS.

2. Yes. That's the purpose of TrueCrypt and it should make that easy and incredibly secure.

3. You can create a volume on the USB stick and put everything inside the volume. However, without the TrueCrypt software, you will not be able to access that information on other computers. With that in mind, yes, encrypting and securing your data is as easy as drag-and-drop into the mounted volume and then unmounting the volume.


If you need any help on using TrueCrypt, post back in this thread and ask. I use TrueCrypt a lot myself, and have been for almost a year now. I'll keep this thread subscribed and will do my best to answer any questions you have. TrueCrypt is a tricky piece of software to use at first, but once you get the hang of it, it's totally worth it.

Regards,
Ships

---

### Post by abhiroopb on 2008-05-15
Thanks a lot! Answers clarified things a lot.

Basically number 3 is what I needed it for the most, is there anyway to perhaps do a portable apps version of truecrypt which is directly on the usb stick? 

I tried doing number 2 and this is what happened:

1. I created a word document and followed the wizard to create the encrypted volume. I set it to 500mb, but this was not dynamic, which meant I had a 500mb empty document sitting on my drive.

Is there anyway to make it dynamic?

Also is there a easy guide on how to use the software?

---

### Post by bodhi.zazen on 2008-05-15
If you want to ecnrypt your installation, you need to use the alternate CD to install :

[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

If you want to know how to use Truecrypt, here is an awesome tutorial:

[http://www.linuxjournal.com/article/6381](http://www.linuxjournal.com/article/6381)

[http://www.truecrypt.org/docs/?s=tutorial](http://www.truecrypt.org/docs/?s=tutorial)

---

### Post by abhiroopb on 2008-05-15
Thanks for the links, but the linux journal article is very old, is it still as relevant?

---

### Post by bodhi.zazen on 2008-05-15
yes, it will certainly get you started and it is, IMO, a nice overview. For the most "up to date" information, use the second link.

---

### Post by abhiroopb on 2008-05-26
Coming back to this. Basically all I want to do now is make sure that I have a usb drive that is encrypted, so in the event I lose it no-one can access my data. Unfortunately truecrypt cannot help as it needs to be installed on any other computer I use it on. Is there anything I can use where my drive is encrypted, and when I take it to (example) an XP computer it recognises the usb stick, and asks for a password to unencrypt it...

---

### Post by hyper_ch on 2008-05-26
with regard to your usb stick:

What OSes are on the other systems? If it's windows/mac/linux you better use Truecrypt. For windows you can even set it up the way it will auto-start truecrypt from a tc-binary on the stick.

So on windows TC works quite good - just setup the traveller mode :)

On linux and mac you'll have to manually mount the tc volumes, meaning tc must be installed on those machiens first.

---

### Post by abhiroopb on 2008-05-26
Well I have a ubuntu PC at home, but if I go to my uni or a friends PC, its most likely to be XP. For example if I need to print something in the uni. It could potentailly be a mac as well.

So what exactly is traveller mode?

---

### Post by hyper_ch on 2008-05-26
[http://www.truecrypt.org/docs/traveler-mode.php](http://www.truecrypt.org/docs/traveler-mode.php)

---

### Post by nefarmboy on 2009-12-13
Ok, let's start back at the beginning.  Referencing [http://www.truecrypt.org/docs/?s=truecrypt-portable](http://www.truecrypt.org/docs/?s=truecrypt-portable) 

After I download the tar.gz, do I extract it to my hard-drive or to my USB?

Do I run the setup utility from the USB then?

I do not get the "*Traveler Disk Setup* facility" option as the reference suggests, is that Windows option?

I also do not get this option: *Tools -> Traveler Disk Setup *

I really need a step x step tutorial on this.  Anyone else get it figured out?

---

### Post by bodhi.zazen on 2009-12-14
> **nefarmboy said:**
> Ok, let's start back at the beginning.  Referencing [http://www.truecrypt.org/docs/?s=truecrypt-portable](http://www.truecrypt.org/docs/?s=truecrypt-portable) 

After I download the tar.gz, do I extract it to my hard-drive or to my USB?

Do I run the setup utility from the USB then?

I do not get the "*Traveler Disk Setup* facility" option as the reference suggests, is that Windows option?

I also do not get this option: *Tools -> Traveler Disk Setup *

I really need a step x step tutorial on this.  Anyone else get it figured out?

On this page : [http://www.truecrypt.org/downloads](http://www.truecrypt.org/downloads)

there are .deb available, from the pull down menu, under Linux.

Download the .deb

install it with dpkg

```
sudo dpkg -i truecrypt*
```

If needed you can then run 

```
sudo apt-get install -f
```

This second command will install any dependencies.

---

### Post by nefarmboy on 2009-12-15
Did that.  Now I'm trying to set up the Portable Mode on the USB.  that's where I start getting stuck.  Think I should uninstall and try again?

---

