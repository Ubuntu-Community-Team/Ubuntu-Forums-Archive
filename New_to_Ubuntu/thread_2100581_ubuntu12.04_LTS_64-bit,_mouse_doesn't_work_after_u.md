---
title: "ubuntu12.04 LTS 64-bit, mouse doesn't work after upgrading kernel to 3.4.3"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by fangqi0131 on 2013-01-02
environment: ubuntu12.04 LTS 64-bit
laptop: thinkpad x230

I have a problem after upgrade kernel to 3.4.3 and reboot, my mouse doesn't work anymore. I've tried to use command "lsusb" and it seems mouse device can  be detected. The mouse works fine in win7, so it's not the mouse problem. Any Any idea would be appreciated, thx a lot!

---

### Post by fantab on 2013-01-02
> **fangqi0131 said:**
> environment: ubuntu12.04 LTS 64-bit
laptop: thinkpad x230

I have a problem after upgrade kernel to 3.4.3 and reboot, my mouse doesn't work anymore. I've tried to use command "lsusb" and it seems mouse device can  be detected. The mouse works fine in win7, so it's not the mouse problem. Any Any idea would be appreciated, thx a lot!

Do you mean Mouse or the Touchpad?

Usually unplugging and plugging it back should solve the Mouse issue.

---

### Post by Pjotr123 on 2013-01-02
You've spoiled your system. Ubuntu 12.04 is designed for the 3.2.x kernel, not for 3.4. :shock:

---

### Post by fangqi0131 on 2013-01-02
> **fantab said:**
> Do you mean Mouse or the Touchpad?

Usually unplugging and plugging it back should solve the Mouse issue.

I mean mouse, not touchpad or trackpoint.

I've tried to plug and unplug and reboot many times, but doesn't work.

---

### Post by fangqi0131 on 2013-01-02
> **Pjotr123 said:**
> You've spoiled your system. Ubuntu 12.04 is designed for the 3.2.x kernel, not for 3.4. :shock:

thx for your info, if it's so, is there any way to revert kernel to 3.2.x?

---

### Post by Pjotr123 on 2013-01-02
> **fangqi0131 said:**
> thx for your info, if it's so, is there any way to revert kernel to 3.2.x?

Simply reinstall the latest 3.2.x kernel (if you have removed it previously) and remove 3.4. 

I advise Synaptic for this; best tool around for specialized apt tasks. So first do: ```
sudo apt-get install synaptic
```
After that, launch Synaptic, use the query "kernel" and install these 3 packages:
linux-headers-3.2.0-35
linux-headers-3.2.0-35-generic
linux-image-3.2.0-35-generic

Then remove the installed 3.4 packages (probably also 2 header packages and one image package) and reboot. You should be fine. :)

---

### Post by fangqi0131 on 2013-01-02
> **Pjotr123 said:**
> Simply reinstall the latest 3.2.x kernel (if you have removed it previously) and remove 3.4. 

I advise Synaptic for this; best tool around for specialized apt tasks. So first do: ```
sudo apt-get install synaptic
```
After that, launch Synaptic, use the query "kernel" and install these 3 packages:
linux-headers-3.2.0-35
linux-headers-3.2.0-35-generic
linux-image-3.2.0-35-generic

Then remove the installed 3.4 packages (probably also 2 header packages and one image package) and reboot. You should be fine. :)

Done, it's ok now. Thanks again for your help!;)

---

