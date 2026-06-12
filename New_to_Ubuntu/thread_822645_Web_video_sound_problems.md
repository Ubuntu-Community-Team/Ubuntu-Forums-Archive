---
title: "Web video sound problems"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by stretch77 on 2008-06-08
I have the Dell 1525n model with Ubuntu and Hardy. I don't have sound on video from the web. I can play CD's and DVD's fine. The effectual and startup sound work fine as well. I have searched and searched but couldn't find anyone else with the same problem. Thank you. I am using firefox 3.0 for browsing.
 I have tried re=installing the flash player plug in to no avail. 
 Update: Adobe flash and Gnash have also been installed; neither produced sound. After attempting to play a video from Fox News or You-tube I receive a prompt to install missing driver. I've attempted to install from this screen, but after clicking the install I am told the plug in is already installed. HELP.

---

### Post by ardvark71 on 2008-06-08
> **stretch77 said:**
> I have the Dell 1525n model with Ubuntu and Hardy. I don't have sound on video from the web. I can play CD's and DVD's fine. The effectual and startup sound work fine as well. I have searched and searched but couldn't find anyone else with the same problem. Thank you.

Hi...

Just to clarify, you've downloaded the appropriate plug-ins for the browser you're using? What is your browser?

Best Regards...

---

### Post by Happy_Man on 2008-06-08
If by "Web video" you mean "flash apps like YouTube and the like", then it is a problem with how the Flash plugin handles sound when it has to work with PulseAudio, which is the Ubuntu sound engine. There is a fix for it, which you can get by installing the package "libflashsupport" from Synaptic. Be warned, though, it makes Flash *extremely* unstable, and is not recommended for this reason. But, if you really need it, it's there.

---

### Post by markbuntu on 2008-06-08
Your best bet would be to get the ubuntu restricted extras from the repository with synaptic. libflashsupport is no good if you have firefox3.0 so you should remove it if you are not using firefox3b5.

You could also try changing System/Preferences/Sound from automatic to alsa and setting the alsa default to your sound card.

---

### Post by crashsystems on 2008-06-08
I'm the one who set up stretch77 with Ubuntu, so I'll describe the issue in a little more detail. At first it seemed to me to be the normal issue where flashplugin-nonfree grabs the sound and won't let go until the browser is closed. With that issue, I've also noticed the inverse, where is you are playing sound, lets say in Rhythmbox, then flash won't play sound until the other program is closed.

Having warned stretch77 of this, he booted his laptop, and immediately opened Firefox, and only Firefox. However, he still cannot get any sound from flash videos, though all other programs work just fine. Due to this, his symptoms seem a little different than the normal problems, but I could be wrong.

To stretch77 I'll say this: Go ahead and install the package that Happy_Man mentioned, using the first Terminal line of code below. Then browse the web as before, and see if it fixes your problem without giving you stability issues. If it does not, use the second of the two lines to remove it. Do keep us posted on how it goes.

```
sudo apt-get install libflashsupport
sudo apt-get remove libflashsupport
```

---

### Post by stretch77 on 2008-06-08
Ok. I tried the libflashsupport and still didn't have any sound on you-tube. I went ahead and uninstalled it. Thanks for the attempt. Ideas?

---

### Post by stretch77 on 2008-06-08
I also tried markubuntu's suggestion about changing the settings to alsa and didn't get any result. Thank you.

---

### Post by stretch77 on 2008-06-08
After playing with the sound settings a little I ran  "test" option on each. All of them worked except for sound conferencing/sound capture. I got silence except when I select "test sound" in the sound capture drop down instead of the test icon. Then it played very scratchy and broken.

---

### Post by crashsystems on 2008-06-08
I've got to admit, that I'm a wee bit stumped on this one, which is strange, as I've been using Ubuntu for three years and consider myself somewhat advanced in my knowledge. I'm sure the answer is probably something stupid that I'm just overlooking.

---

### Post by crashsystems on 2008-06-09
stretch77 found another post somewhere (pleas paste a link, btw) that suggests that upgrading to flash 10 might help solve the problem. Below are some lines of code that will facilitate the upgrade. Note that since Adobe doesn't provide a Debian/Ubuntu package, the following lines will fetch the Red Hat package, and convert it to something Ubuntu can use.

```
sudo apt-get install alien
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.i386.rpm
sudo alien --to-deb flashplayer10_install_linux_051508.i386.rpm
sudo apt-get remove flashplugin-nonfree
sudo dpkg -i flashplayer10_install_linux_051508.i386.deb
```

Please note that Flash 10 is still Beta, so YMMV (Your Millage May Vary).

---

