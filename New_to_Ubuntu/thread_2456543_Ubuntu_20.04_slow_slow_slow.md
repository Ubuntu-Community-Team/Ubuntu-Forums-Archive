---
title: "Ubuntu 20.04 slow slow slow"
date: 2021-01-13
forum: New to Ubuntu
---

### Post by paullangdon678 on 2021-01-13
Hi
I have just installed Ubuntu 20.04 and have not changed anything in terms of drivers. I have updated software.
Self built PC working ok with windows 10. I am dual booting.
I have been trying to run hard info from the terminal to give spec of PC but I cannot get this to run. I am getting messages which ask to to wait or continue after a long delay. Up to now I have done little more than open browser and install and use Thunderbird, and install Chromium.
I see delays with all three. And when I say delays they are significant (can be minutes).
Really could do with some help here - any ideas?
I will post spec up shortly.

---

### Post by TheFu on 2021-01-13
My first 20.04 install ended wiih terrible performance.  I selected to use zfs and my gpu drivers were not installed. That lasted only a few hours before i reinstalled using lvm - I need advanced storage management which is why either lvm or zfs were chosen. Regular people should just use a normal install.

[LIST]
[*]**inxi -Fz** is a quick summary of the hardware. Post that.
[*]Bleeding edge hardware is almost always a problem for any non-microsft OS. Best hope of support is running 20.10.
[*]**sudo ubuntu-drivers autoinstall** will install GPU drivers; reboot when that is done, if it does anything GPU related.
[*]Ensure the swap is at least 4.1G size.  **swapon -s**
[*]Check if X11 or Wayland is being used - pre-login there is a "gear" to switch between those.
[/LIST]

Those are my best guesses for things to check and show.

---

### Post by paullangdon678 on 2021-01-13
OK thanks TheFu. Things are so bad that I cannot progress any of your advice sorry. I have waited about five minutes for terminal to open comes message that is not responding and gives my choice to force quit or continue. When it does and I try to install inXi-Fz it asks me to install it - when I try to install that does not work and I get a message about cache being locked. Also typing this post has taken about ten minutes as Firefox keeps freezing. I will update to the latest Ubuntu (assuming I can...) and see what happens after that.

---

### Post by TheFu on 2021-01-13
Boot from the installation media and choose "Try Ubuntu" - is that slow?

---

### Post by paullangdon678 on 2021-01-13
Thanks Try Ubuntu seems fine.

---

### Post by TheFu on 2021-01-13
> **paullangdon678 said:**
> Thanks Try Ubuntu seems fine.

So you know it is something about your install choices.  Try something different in the installation.
but in the meantime, you can install **inxi** and run that to provide data back here.  The install in a Try Ubuntu environment is lost at reboot, but it is just a few seconds for most people.

---

### Post by paullangdon678 on 2021-01-13
I have now upgraded to 20.10 - let us see how that goes. Looks promising at the moment. On my first instal I made no choices I just went with letting Ubuntu decide. 

Perhaps the LTS version did not like something. Results of **inxi -Fz **below:


```
  Kernel: 5.8.0-36-generic x86_64 bits: 64 Desktop: N/A 
  Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:
  Type: Desktop System: ASUS product: N/A v: N/A serial: <filter> 
  Mobo: ASUSTeK model: PRIME Z490-P v: Rev 1.xx serial: <filter> 
  UEFI: American Megatrends v: 1208 date: 07/21/2020 
CPU:
  Info: 8-Core model: Intel Core i7-10700T bits: 64 type: MT MCP 
  L2 cache: 16.0 MiB 
  Speed: 800 MHz min/max: 800/4500 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 5: 800 6: 800 7: 800 8: 800 9: 800 10: 800 11: 800 12: 800 
  13: 800 14: 800 15: 800 16: 800 
Graphics:
  Device-1: NVIDIA TU117 [GeForce GTX 1650] driver: nouveau v: kernel 
  Display: x11 server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: NV167 v: 4.3 Mesa 20.2.6 
Audio:
  Device-1: Intel Comet Lake PCH cAVS driver: snd_hda_intel 
  Device-2: NVIDIA driver: snd_hda_intel 
  Sound Server: ALSA v: k5.8.0-36-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 1.84 TiB used: 9.86 GiB (0.5%) 
  ID-1: /dev/nvme0n1 vendor: A-Data model: SX8200PNP size: 953.87 GiB 
  ID-2: /dev/sda vendor: Seagate model: ST500DM002-1BD142 size: 465.76 GiB 
  ID-3: /dev/sdb vendor: Seagate model: ST500DM002-1BD142 size: 465.76 GiB 
Partition:
  ID-1: / size: 47.06 GiB used: 9.83 GiB (20.9%) fs: ext4 
  dev: /dev/nvme0n1p5 
Swap:
  ID-1: swap-1 type: file size: 2.00 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:
  System Temperatures: cpu: 27.8 C mobo: N/A gpu: nouveau temp: 27.0 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 326 Uptime: 9m Memory: 7.67 GiB used: 1.93 GiB (25.1%) 
  Shell: Bash inxi: 3.1.07
```

---

### Post by mastablasta on 2021-01-14
> **paullangdon678 said:**
> 
Perhaps the LTS version did not like something. 

yes, it looks like that older kernel had issues wit nvidia gtx 1650

you now have new kernel (in linux opensoruce drivers are in kernel - so new kernel = usually new drivers). but your chip:

```

Graphics:
  Device-1: NVIDIA TU117 [GeForce GTX 1650] driver: nouveau v: kernel 
  Display: x11 server: X.Org 1.20.9 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: NV167 v: 4.3 Mesa 20.2.6 

```

has proprietary drivers available. so install those and hopefully the issue will be resolved. since you are using nvidia, check and make sure that old xorg session rather than (more experimental) wayland is used.

my kid has Ryzen 7 and nvidia GTX1650. he is on 18.04 but HWE (hardware enablement) kernel, so he should be on same kernel now. anyway we installed nvidia proprietary drivers and and so far it has beer running great. he also just bought some newish windows games (doom 2016, Subnautica...) on steam sale and they work fine. but we do use Kubuntu which still uses the old Xorg.

---

### Post by paullangdon678 on 2021-01-14
Thanks for all the help.  I am hoping to play a  couple of games on here but not through windows. Everything  is flying along atm so I think I will stay as I am for a short while and then move to installing propriety drivers. I am assuming I choose from the drivers available through the software and updates in Ubuntu so that will be '460'. I am celebrating being able to screenshot - that was impossible yesterday :):
[http://gofile.me/5zaWR/5Y7SDXTqq](http://gofile.me/5zaWR/5Y7SDXTqq)

---

### Post by TheFu on 2021-01-14
> **paullangdon678 said:**
> Thanks for all the help.  I am hoping to play a  couple of games on here but not through windows. Everything  is flying along atm so I think I will stay as I am for a short while and then move to installing propriety drivers. I am assuming I choose from the drivers available through the software and updates in Ubuntu so that will be '460'. I am celebrating being able to screenshot - that was impossible yesterday :):
[http://gofile.me/5zaWR/5Y7SDXTqq](http://gofile.me/5zaWR/5Y7SDXTqq)

see #2 post above.

---

### Post by mastablasta on 2021-01-14
you can forget about "gaming" with nouveau on this card. maybe some old games, but everything else needs the closed source driver.

---

### Post by TheFu on 2021-01-14
> **mastablasta said:**
> you can forget about "gaming" with nouveau on this card. maybe some old games, but everything else needs the closed source driver.

People have fun gaming on all sorts of hardware.  I game using virtual machines without any special setup besides SPICE/QXL while using cheap or virtual GPUs.  Just depends on the game.  SimCity works great.  So do Mindcraft, Real War, C&C, and Starflight.  My favorite game is "evil administrator", which works on any computer with more than 1 person. ;)

---

### Post by paullangdon678 on 2021-01-18
Yes got it thanks

---

### Post by paullangdon678 on 2021-01-18
Thanks got it now.

---

