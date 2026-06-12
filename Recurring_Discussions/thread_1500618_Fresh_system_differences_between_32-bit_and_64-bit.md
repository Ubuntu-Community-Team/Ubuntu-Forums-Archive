---
title: "Fresh system differences between 32-bit and 64-bit installs"
date: 2010-06-03
forum: Recurring Discussions
---

### Post by KayakJim on 2010-06-03
Interestingly enough, I have found that the resulting system after a fresh install is a bit different between the 32-bit and 64-bit versions of the Desktop platform.

A friend of mine asked me to wipe out his Windows laptop and install Ubuntu on it. Since we were having a discussion regarding why [the download page states that 64-bit is not recommended for daily use for the desktop]("http://ubuntuforums.org/showthread.php?t=1499385"), I thought I would use the opportunity to compare the two platforms.

Between each install I removed all partitions and then recreated them choosing to format as ext4.

The 64-bit version was installed first. Like my system the bluetooth and internal microphone did not work. In addition, clicking on play buttons within flash videos would intermittently work. Skype was not usable since the internal mic did not work.

Now for the 32-bit version to be installed. Bluetooth and the internal microphone both worked thus making Skype usable. The play button in the same flash video worked every time.

I'm sure there are probably a few other differences that I did not get the time to encounter. I have an old laptop sitting around and now plan to do the same to see what else I can find.

If anyone has any suggestions as to what else to try or look at I would be happy to accommodate.

Just thought I would share my findings and open this up for discussion.

---

### Post by tmette on 2010-06-03
Hmm...that's interesting.  Why would the 64bit cause the mic not to work?

---

### Post by KayakJim on 2010-06-03
> **tmette said:**
> Hmm...that's interesting.  Why would the 64bit cause the mic not to work?

Indeed. The same question applies to the Bluetooth as well.

I am hoping that we can use this "experiment" to possibly answer those questions as well as any others that may be around.

---

### Post by philinux on 2010-06-03
Moved to Recurring Discussions

---

### Post by cascade9 on 2010-06-03
> **KayakJim said:**
> The 64-bit version was installed first. Like my system the bluetooth and internal microphone did not work. In addition, clicking on play buttons within flash videos would intermittently work. 

No idea on bluetooth or the mic, but that flash issue is (AFAIK) a known problem with running 32bit flash in a wrapper. Install the 64bit version, by whatever method you like (I do it manually) and it should work....as well as flash ever does.

---

### Post by NightwishFan on 2010-06-03
I have never noticed anything different. I installed ia32-libs and even 32-bit games like wolfenstein work for me. They are the same packages only compiled to be able to take advantage of more memory and faster.

---

### Post by KayakJim on 2010-06-03
> **NightwishFan said:**
> They are the same packages only compiled to be able to take advantage of more memory and faster.

That was my initial assumption as well but there must be some differences between the two to cause hardware to work in one but not the other.

Do you think a comparison of config files or something else would possibly shed some light on this subject?

---

### Post by NightwishFan on 2010-06-03
Might be some odd bios issue. I am far from an expert and there might very well be some hidden reason. Or something unrelated at all, such as installing with a bad cd. Make sure to check for errors.

---

### Post by KayakJim on 2010-06-03
> **NightwishFan said:**
> Might be some odd bios issue. I am far from an expert and there might very well be some hidden reason. Or something unrelated at all, such as installing with a bad cd. Make sure to check for errors.

Both CDs were checked before the installs were performed.

Since the installs were performed on the same machine would that not exclude the BIOS?

---

### Post by NightwishFan on 2010-06-03
Not if something is up with addressing 64-bits, but I doubt that. I am sorry I have no answers. I do not doubt what you say though I have never encountered it. My advice? Test another distrubtion such as Debian, Fedora or OpenSUSE on 64-bit to see if they do not work either. OpenSUSE 11.2 uses a slightly older kernel than lucid though (just to be noted).

---

### Post by WinterRain on 2010-06-04
Strange indeed. 64bit ubuntu works better for me than 32bit ever did.

---

