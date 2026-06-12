---
title: "Cannot read files on a DVD"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2008-10-26
I recently popped a DVD in and it treats it as a normal CD-ROM and when you open the Video_TS folder it doesn't see any of the VOB files.

Any ideas?

Thanks in Advance

---

### Post by eragon100 on 2008-10-26
Install the attached .deb package, reboot the computer, and the problem should be gone :wink:

---

### Post by J0hnnyBr@v0 on 2008-10-26
Already did that and still not working....I am baffled....

Followed the instructions from Medibuntu website, installed from synaptic.....rebooted...nothing...

I have libdvdcss2 ver 1.2.9-2medibuntu4 installed

---

### Post by eragon100 on 2008-10-26
install vlc media player from add/remove and attempt to play the DVD there, vlc is a **much** better program than totem for playing dvd's.

just go to File -> Open disc.

---

### Post by SunnyRabbiera on 2008-10-26
> **J0hnnyBr@v0 said:**
> Already did that and still not working....I am baffled....

Followed the instructions from Medibuntu website, installed from synaptic.....rebooted...nothing...

hmm, and you have the packages libdvdread and libdvdnav as well?
Is this a commercial DVD or one you burned yourself?

---

### Post by J0hnnyBr@v0 on 2008-10-26
> **SunnyRabbiera said:**
> hmm, and you have the packages libdvdread and libdvdnav as well?
Is this a commercial DVD or one you burned yourself?

Its a commercial DVD.

libdvdread3 - 0.9.7-8ubuntu1
libdvdnav4 - 0.1.10-0.2

Like I said....I'm baffled.  Even when exploring the disc, it shows it to be empty, no files.

I am running Hardy.  Only thing I have changed recentky are setting to get USB working for Vbox.

---

### Post by dracayr on 2008-10-26
Is the DVD from a foreign country? I don't know if this applies for linux, but on windows, you can only read DVDs from one country. You can change this country up to three times

dracayr

---

### Post by J0hnnyBr@v0 on 2008-10-26
Ok, so I switched to another DVD and it works just fine....  So I apologize for the wild goose chase.  The original DVD is still not recognized, but the 3 others I tried work just fine...  I know the original DVD works fine in Windows, even worked ok in my Vbox version of Vista on my Hardy machine...thought I was losing my mind.

Not sure why this one DVD doesn't work, but not a huge deal...

Thanks again for all those who helped!

---

