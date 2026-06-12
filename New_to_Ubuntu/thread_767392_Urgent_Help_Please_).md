---
title: "Urgent Help Please :)"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by mustking on 2008-04-25
Hello,

I am a big fan of windows from the ages of windows 98 but now i am tired of making format every 2 week and planned to switch to Linux. By luck i got the Kubuntu 8.04 from my local software shop and installed on my laptop (Acer 4060) and got the following issues:

1. I try to play MP3 Song and it failed to play, whereas the sound is comming out from the speaker on normal usage of PC.

2. No Window Video file working.

3. Screen Resolution 800x600 only (I have INTEL 915 VGA).

Now i am thinking to change it with the UBUNTU 8.04. Can some one confirm me that they are not expiering the same issue in UBUNTU too.

Thanks in advance.

---

### Post by Paqman on 2008-04-25
> **mustking said:**
> 
1. I try to play MP3 Song and it failed to play, whereas the sound is comming out from the speaker on normal usage of PC.

What happens when you try to play it? Does the player open and look like it's playing the file? Or do you get a message come up asking to install codecs? Is your sound working for non-mp3 files?

> 
2. No Window Video file working.

[Click here to install VLC](apt:vlc). It'll play .wmv files

> 
3. Screen Resolution 800x600 only (I have INTEL 915 VGA).

Have you enabled the driver? Go to System > Administration > Restricted Drivers Manager

---

### Post by jimv on 2008-04-25
Ubuntu doesn't come with an mp3 or WMV decoder.  You must install it.  To do this,

Click on the Applications menu, go to  Accessories, and click Terminal.

Type:

[INDENT]sudo apt-get install ubuntu-restricted-extras[/INDENT]

Once that's done, try your mp3s and videos again.

---

### Post by mustking on 2008-04-26
> **Paqman said:**
> What happens when you try to play it? Does the player open and look like it's playing the file? Or do you get a message come up asking to install codecs? Is your sound working for non-mp3 files?

When i try to play the player stop immediately whithout playing the MP3 Song.

[Click here to install VLC](apt:vlc). It'll play .wmv files

Let me install after i install the OS Again

Have you enabled the driver? Go to System > Administration > Restricted Drivers Manager

No, let me enable after installation

Do there is any version of ubuntu that comes with complete plugins installed

---

