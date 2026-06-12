---
title: "cant reduce my brightness in ubuntu"
date: 2017-08-08
forum: New to Ubuntu
---

### Post by loke3006 on 2017-08-08
hello,i just installed ubuntu newly alongside with my windows 10(which is in SSD) in HDD,but i can't reduce the brigtness in 'brightness and lock' is there a problem in my drivers or something els.... i dont for sure and one more thing my windows seems to be faster than ubuntu and when i play a video in ubuntu it just scrambles like hell and it says some error and closes and my processor is also running heavily for playing a simple video is there something i could do to solve this.....!any suggestions welcomed and thanks in advance.

---

### Post by again? on 2017-08-08
You can give more detailed info about your system.
The sysinfo script inxi can do this.
```
sudo apt install inxi
```

Then copy and paste the output of 
```
inxi -b
```
eg
```
glen@GU17:~$ inxi -b
System:    Host: GU17 Kernel: 4.10.0-30-generic x86_64 (64 bit) Desktop: Gnome 3.24.2 Distro: Ubuntu 17.04
Machine:   Device: desktop Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x BIOS: Award v: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) speed/max: 1400/3800 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: X.Org 1.19.3 drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1680x1050@59.88hz
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 384.47
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
Drives:    HDD Total Size: 870.2GB (13.4% used)
Info:      Processes: 312 Uptime: 18:58 Memory: 2261.8/3931.5MB Client: Shell (bash) inxi: 2.3.8
```
[How To Use CODE tags ]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by loke3006 on 2017-08-08
```
System:    Host: loke-ROG Kernel: 4.10.0-28-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: ASUSTeK (portable) product: GL502VMK v: 1.0
           Mobo: ASUSTeK model: GL502VMK v: 1.0
           Bios: American Megatrends v: GL502VMK.300 date: 12/27/2016
CPU:       Quad core Intel Core i7-7700HQ (-HT-MCP-) speed/max: 898/3800 MHz
Graphics:  Card: NVIDIA Device 1c60
           Display Server: X.Org 1.19.3 drivers: (unloaded: fbdev,vesa) FAILED: nouveau
           Resolution: 1920x1080@60.02hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 4.0, 256 bits)
           GLX Version: 3.0 Mesa 17.0.7
Network:   Card-1: Intel Wireless 8260 driver: iwlwifi
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 1128.2GB (1.9% used)
Info:      Processes: 245 Uptime: 5 min Memory: 1135.0/15997.9MB
           Client: Shell (bash) inxi: 2.2.35
```

---

### Post by again? on 2017-08-08
Did you see the [How To Use CODE tags ]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") link?
Appears you are using software rendering instead of your GPU(hardware)... hence the sluggishness of your system.

Not familiar with "Graphics: Card: NVIDIA Device 1c60" or available drivers.
Would have to google fixes or wait for someone to answer with more knowledge with nvidia chips.

---

### Post by loke3006 on 2017-08-08
ok my graphics card is nvidia gtx 1060 6gig ddr5.....!this could help you

---

### Post by again? on 2017-08-08
You may just need to install the proprietary nvidia drivers, although why the nouveau drivers(open source)
show "Failed" in your inxi output I don't know.
My nvidia card(GeForce GTX 550 Ti) is older than yours and on first boot it uses the default nouveau drivers which work well.
I then install the nvidia drivers to play games.
Possibly your card is too new for the nouveau drivers.

To install nvidia driver, search "drivers" in the dash and open additional drivers.
Install the latest nvidia driver and reboot once finished.

If your machine is the same as [this]("https://forum.peppermintos.com/index.php?topic=5873.0") it appears to
work with nvidia drivers.

---

### Post by loke3006 on 2017-08-08
i've done that and installed 384.59 but after rebooting i cant login it just keeps on logging out and i found some solutions and came back where i started....!

---

### Post by loke3006 on 2017-08-09
any ideas on how to install my drivers......!

---

### Post by ClickXT on 2017-08-09
Did you try looking at the NVIDIA drivers page?

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
Select Linux (64) and read the text in 'Additional Information'

---

### Post by again? on 2017-08-09
> **loke3006 said:**
> i've done that and installed 384.59 but after rebooting i cant login it just keeps on logging out and i found some solutions and came back where i started....!
According to [this page]("http://www.nvidia.com/Download/driverResults.aspx/120917/en-us") your gpu is supported by the 384.59 driver.
It's advisable to purge nvidia drivers before using the graphics ppa.
Try this.
Completely remove old drivers.
```
sudo apt purge nvidia*
```

Check if graphics ppa is already enabled.
```
egrep -v '^#|^ *$' /etc/apt/sources.list.d/*.list | nl
```
**If** you don't see  the following line in your output
> /etc/apt/sources.list.d/graphics-drivers-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial main 
**then** add the drivers ppa
```
sudo add-apt-repository ppa:graphics-drivers/ppa
```

Update packages.
```
sudo apt update
```

Install the latest driver.
```
sudo apt install nvidia-384
```

Cross fingers and reboot.

Also....
I haven't used Windows for ten years and use older hardware, so don't know how dual booting works these days, which could be a factor.
May be you need to disable secure boot in the Bios to unlock hardware.
[Disable ASUS Motherboard's UEFI secure boot]("https://www.all4os.com/windows/disable-asus-motherboards-uefi-secure-boot.html")

---

### Post by loke3006 on 2017-08-12
sorry bro no luck.........!cant get into login screen after installing the graphics driver it never logs in..everytime i log in it just keeps logging out.........!and one more thing my resolution is just 800x600 and cant change it because there is no other resolutions in the list except this 800x600 so any ideas to solve this one .....!?

---

### Post by loke3006 on 2017-08-13
sorry bro no luck......!i can't login after my drivers are installed and it juzz keeps logging out as soon as i login.............and moreover my resolution became 800x600 and i cant change it by any means.....so any other plans i just uninstalled the nvidia drivers and i can login now but still my laptop scorches like hell!

---

### Post by again? on 2017-08-13
Did you disable secure boot before trying to install gfx drivers?

---

### Post by again? on 2017-08-14
Does your machine have dual graphics?
[Ubuntugnome 16.04 on Asus ROG GL552V]("https://jeremymdyson.wordpress.com/2016/04/27/ubuntugnome-16-04-on-asus-rog-gl552v/")

---

### Post by loke3006 on 2017-08-16
got it ....it seems the secure boot was the one troubling i disabled it and got my drivers working but still if i change my brightness it again comes to 100 after every restart....any ideas on how to solve this?

---

### Post by again? on 2017-08-16
Don't use a laptop so just googling.
One to try...
[http://ubuntuhandbook.org/index.php/2015/04/fix-screen-brightness-issue-in-ubuntu-laptop/](http://ubuntuhandbook.org/index.php/2015/04/fix-screen-brightness-issue-in-ubuntu-laptop/)

The outcome with this sort of stuff varies due to different hardware but if doesn't work the article explains how to remove.

---

