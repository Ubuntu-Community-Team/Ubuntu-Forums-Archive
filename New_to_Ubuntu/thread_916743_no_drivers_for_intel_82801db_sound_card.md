---
title: "no drivers for intel 82801db sound card"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by esquivel on 2008-09-11
Hi, i have just installed the hardy ubuntu on a relatively old NEC laptop and as usual i have trouble making the sound to work. i can ''see'' the sound card using the terminal but do not know the way to activate any sound whatsoever. i have looked at the intel website for the drivers for my card but with no result. please, any help would be appreciated.

---

### Post by nothingspecial on 2008-09-11
Have you tried switching from pulse audio to alsa in your sound preferences.
Not sure exactly how to do this as I`m still on Gutsy.

---

### Post by gvartser on 2008-09-11
Hmm check this out.

[http://ubuntuforums.org/showthread.php?t=161193](http://ubuntuforums.org/showthread.php?t=161193)

/g

---

### Post by NewDisciple on 2008-09-11
If that doesn't work you will need to know who made the sound card.  I have that card on an old MPC computer and mine is a SoundMax sound card.  You will need to Google it as I don't have the URL handy at the moment.  There is a site that has a free download for the driver.  I know this because I downloaded and installed the driver yesterday.  There are numerous sites that advertise free drivers but when you follow the links they lead to a must pay link.  There is one site that claims to have it "Tech something".  It has a poor user rating for this driver and for good reason.  Trying to install this one will cause a kernel panic.  If you do decide that you need the URL I can find it a bit later.

---

### Post by Kellemora on 2008-09-11
Hi esq

That's the sound card I have in THIS computer I'm on right now and it works just fine.

Intel 82801DB/DBL/DBM (ich4/ich4-l/ich4-m) ac'97a

Under Sound Preferences in Devices TAB all of my features are set to auto-detect except for Sound Capture, that is set to ALSA - etc.
However: Under the Sound Tab, all the sounds, except log-in are set to OFF by default.  There is a test button here to check your sound.

Give that a try, because it should work.

You DO have your speakers plugged into the right port don't you?  I mess up and get it plugged into the wrong one quite often.

TTUL
Gary

---

