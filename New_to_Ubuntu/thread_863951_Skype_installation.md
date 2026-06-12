---
title: "Skype installation"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by simonlugi on 2008-07-19
I have Ubuntu 8.04 and want to install Skype. I downloaded the file on the Skype website and get an error "Wrong architecture I386". My computer has AMD64
Can you tell me what I should install.
Simon

---

### Post by iaculallad on 2008-07-19
> **simonlugi said:**
> I have Ubuntu 8.04 and want to install Skype. I downloaded the file on the Skype website and get an error "Wrong architecture I386". My computer has AMD64
Can you tell me what I should install.
Simon

Open your terminal and issue the commands below, one-at-a-time.

```
cd ~/Desktop
sudo apt-get install ia32-libs ia32-libs-sdl ia32-libs-gtk ia32-libs-kde libstdc++5
sudo apt-get install ia32-libs-openoffice.org
sudo wget http://www.skype.com/go/getskype-linux-beta-deb
sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb
```

---

### Post by hyper_ch on 2008-07-19
add the medibuntu repositories and then you can install skype through synaptic

---

### Post by simonlugi on 2008-07-19
Thanks I got Skype to open but the microphone is not transmitting. I am receiving sound OK though.

---

### Post by eHobayyeb on 2008-07-23
Me too, the microphone is not transmitting. I am receiving sound OK though.
Please help.

---

### Post by gordon3913 on 2008-07-23
When I use Skype I can hear but the microphone volume is very low.

I have boosted the volume control level to the maximum.

Is there anything else that I can do?

---

### Post by simonlugi on 2008-07-25
Thanks I did finally get the mic to work by going to Volume Control and enabling everything there is and setting most things to max volume. Not sure this the best as the mic is live all the time now and even if I am not logged into Skype sound gets picked up by the mic and comes through the speakers.

The other thing I have noticed with the Linux version of Skype is that it does not automatically load and log in when I boot up. In the Windows version as soon as Windows is fully booted Skype is active. There is a tick box on the front that I have ticked but does not seem to store this setting.

---

### Post by gordon3913 on 2008-07-25
Try the Skype Menu, Options, General, check the box "Start Skype minimised in the system tray"

---

