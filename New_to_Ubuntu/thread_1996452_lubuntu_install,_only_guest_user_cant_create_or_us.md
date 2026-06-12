---
title: "lubuntu install, only guest user cant create or use anything."
date: 2012-06-04
forum: New to Ubuntu
---

### Post by jewlez on 2012-06-04
Fresh install of Lubuntu from their website. I used the non graphical install and it went well. I have the opening login but only guest and other show up.  This is the latest release of 12.04 of lubuntu from the website.  Not sure why I only get Guest and other and it never asked me to create a user at the time of the install.  As guest I cannot sudo or su, which is expected.  Nor can I create another user.  I know root password is set with a hash and I dont expect to login as root either.  I researched this in google quite a bit and didnt find my answer.

What user do I login as or did I miss something on the Lubuntu install.  I can't imagine I could get so stuck as to not even get in as a user and have built a box with only guest access.  Seems a little useless.

Any help is appreciated.

Jewlez

---

### Post by cortman on 2012-06-04
This sounds like a faulty installation. I would recommend reinstalling Lubuntu, and making sure you enter the username/password info.
You might also check the md5sum of the ISO image you downloaded- info on that [here]("https://help.ubuntu.com/community/HowToMD5SUM"). If they don't match up, it may be a corrupted image (it's happened to me already) and you should download a new one.

---

### Post by ajgreeny on 2012-06-04
Something has obviously gone very wrong!

I assume from your post that you used the Alternate Install CD to install the OS, and that will ask you to make a user (username) and the type the password twice.  If that didn't happen you may have a corrupt burn of your CD or perhaps the iso file you downloaded was bad; did you check the md5sum

 
[COLOR=Red]a1685837ad50845b6685086fc4743c83[/COLOR]   for the 32 bit


 [COLOR=Red]a277a7d3b8a6fc1dd98e65adb5262493[/COLOR]   for the 64 bit


If you still have the iso file you can check the md5sum now, either in linux with command ```
md5sum /path/to/iso
```or in windows.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)



It must be identical to the appropriate one above and if it is even slightly different, it is no good.  You then get a chance to check the CD when you boot, which is always worth doing if you burn it yourself.


Finally, if you need to download again or burn again, do so at as slow a speed as possible on your hardware.

---

