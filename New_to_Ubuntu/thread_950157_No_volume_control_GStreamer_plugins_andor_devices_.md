---
title: "No volume control GStreamer plugins and/or devices found."
date: 2008-10-16
forum: New to Ubuntu
---

### Post by vasilios on 2008-10-16
I installed some updates, and was forced to restart my computer. After restarting, I have a muted speaker icon in the panel, and I get this message when I click on it.

"No volume control GStreamer plugins and/or devices found."

I searched Google for "volume control GStreamer plugins," and I found this solution.

[http://ubuntuforums.org/showpost.php?p=3633314&postcount=11](http://ubuntuforums.org/showpost.php?p=3633314&postcount=11)

I followed the directions, but could not get the "sudo apt-get install linux-backports-modules-generic" command to work. It says, "Couldn't find package linux-backports-modules-generic."

Can anyone help me with this? I appreciate your assistance.

---

### Post by Tamlynmac on 2008-10-16
The gstreamer plugins are available in the Synaptic Package Manager. Have you tried installing them? I believe there is a base, base apps, gnomevfs, alsa, esd and ffmpeg, etc. available.
I had a similar issue until I installed them.

---

### Post by vasilios on 2008-10-17
I've installed every GStreamer plugin in the Synaptic Package Manager. The post here ([http://ubuntuforums.org/showpost.php?p=3633314&postcount=11](http://ubuntuforums.org/showpost.php?p=3633314&postcount=11)) gives a solution, but I cannot get the "sudo apt-get install linux-backports-modules-generic" command to work. That should be the last step. Is there a way to do this other than in the terminal? Could that work with another command?

---

### Post by DraculVaDomni on 2008-10-23
hello i have the same problem the same messages i tried the same solution and i'm getting the same error message Couldn't find package linux-backports-modules-generic the problem occurred after an update of the kernel an automatic update i didn't update it all alone but when i get back to the previous kernel the sound is back u know from the grub menu the kernel version i'm using right now and in which i have the problem is the 2.6.24-21-386 under 2.6.24-21 everything is fine i wonder if my sound card isn't supported but the new kernel or sth like that :confused: i have a quite old soundcard i think it's a soundmax sth i don't remember i will check it out under my windows xp session
 
another thing i'm wondering if there was a kernel update or i'm just imagining things i will check my ubuntu session set under windows thro wubi to compare the kernel versions cuz under the other session i didn't update since i keep using this one.

i found out that my soundcard is Analog Devices AD1888 thro gnome alsa mixer i'm running under the old kernel 2.6.24-21 

i found out that u need to make the new kernel compatible with your sound card by editing some stuff but it's kinda complicated and u could end up with other problems !
thank you !

---

### Post by tld on 2008-10-28
I have the same problem.  Replacing the word "generic" with the word "hardy" got me through that step and installed the generic modules.  Unfortunately, it did not solve my sound problems.  I have the same card listed in the instructions and tried to follow the link in Step 4, but the link is dead.  I poked around on the site that contained the dead link, but I still could not find the script to compile from source.  I'm hesitant to do that anyway since I'm such a newb.  I too ran into this problem after an upgrade.

> **vasilios said:**
> 
I followed the directions, but could not get the "sudo apt-get install linux-backports-modules-generic" command to work. It says, "Couldn't find package linux-backports-modules-generic."

Can anyone help me with this? I appreciate your assistance.

---

