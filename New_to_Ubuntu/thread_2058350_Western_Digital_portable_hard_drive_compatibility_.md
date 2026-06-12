---
title: "Western Digital portable hard drive compatibility with Ubuntu"
date: 2012-09-15
forum: New to Ubuntu
---

### Post by joeqesi on 2012-09-15
I'm looking to buy a portable hard drive to back up my laptop from but apparently the hard drive I'm currently looking at is formatted NTFS to be compatible with Windows.
I was just wondering whether it would still work with my laptop that's using Ubuntu.

Here's the link for the hard drive: [http://store.westerndigital.com/store/wdeu/en_GB/pd/ThemeID.22586100/productID.234267000/parid.13831800/catid.13832400/categoryID.42026800](http://store.westerndigital.com/store/wdeu/en_GB/pd/ThemeID.22586100/productID.234267000/parid.13831800/catid.13832400/categoryID.42026800)

---

### Post by critin on 2012-09-15
Can't it be reformatted to ext4?

---

### Post by Bartender on 2012-09-15
You can leave it NTFS.

The biggest problem with these packaged externals (and in my limited experience WD is the worst) is the software that gets in between you and just using the danged drive.

WD externals (maybe this has changed) have a little circuit board between the external port and the drive.  There's firmware loaded onto that board.  When you plug it in, the board tries to install itself as a virtual drive, etc. etc. 

I had a WD external that was unusable on my Ubuntu PC.  The WD firmware got in the way, Ubuntu couldn't recognize it, etc.  I broke the thing open, freed the HDD from its confinement, dropped it into a generic dock, and Ubuntu immediately identified the HDD.

That's why I'd suggest buying a dock and a bare drive.  Sometimes you can get a killer deal on these externals, so buying one and busting it open might even be an option for the brave soul who has a dock or is willing to buy one.

---

### Post by oboedad55 on 2012-09-15
> **joeqesi said:**
> I'm looking to buy a portable hard drive to back up my laptop from but apparently the hard drive I'm currently looking at is formatted NTFS to be compatible with Windows.
I was just wondering whether it would still work with my laptop that's using Ubuntu.

Here's the link for the hard drive: [http://store.westerndigital.com/store/wdeu/en_GB/pd/ThemeID.22586100/productID.234267000/parid.13831800/catid.13832400/categoryID.42026800](http://store.westerndigital.com/store/wdeu/en_GB/pd/ThemeID.22586100/productID.234267000/parid.13831800/catid.13832400/categoryID.42026800)

Linux can read/write NTFS, so no problem there. You can also format the drive to whatever file system you choose. If it is exclusively for Linux I would use EXT4. Otherwise, if you need to read data from it in Windows you can leave it NTFS. Or split it.

---

### Post by joeqesi on 2012-09-15
On the Western Digital forums an Ubuntu 10.10 user said he reformatted a "My Passport Essential SE" to ext4.

I understand that this isn't the same product but it's all I can find on their website.

I'm going to email them to clarify but it'll probably take a few days before they get back to me.

---

### Post by joeqesi on 2012-09-15
Fair enough, thanks for the help guys.

---

