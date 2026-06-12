---
title: "prety much the same error message no matter which wine i use"
date: 2024-08-30
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2024-08-30
error message:

_winetricks:_
sha256sum mismatch! Rename /home/a/.cache/winetricks/steam/SteamSetup.exe and try again.

_play on linux:_

enters wizard gets to installing microsoft fonts then hangs up on "downloading andale32.exe..." my patience usually wears out after an hour or so and i kill it.  tryed 3 times so far.

do i have to have everything with wine in the name installed?  i've downloaded installed and tryed to install steam starting at the top, got an error then uninstalled and moved to the next one to install.  is there a way to install to a specific folder using the wine program instead of the default folder?  i've even tried play on linux

it seems reading, the reviews, that ubuntu doesn't like wine, or any of the other variants.  wonder if debian will work with it?  

doesn't matter to me which format of linux i use, well it does if it isn't usable.  direct download of steam, wouldn't let me play any games formatted to windows.  guess what, that's my entire library.  i don't want to use windows garbage any more, help a fella out?  which linux is best for being able to run programs for windows?

ystem:
  Kernel: 5.15.0-119-generic x86_64 bits: 64 Desktop: Gnome 3.36.9 
  Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: Gigabyte model: GA-78LMT-USB3 6.0 v: SEx 
  serial: <filter> BIOS: Award v: F2 date: 11/25/2014 
CPU:
  6-Core: AMD FX-6300 type: MCP speed: 1406 MHz min/max: 1400/3500 MHz 
Graphics:
  Device-1: NVIDIA driver: nvidia v: 470.256.02 
  Display: x11 server: X.Org 1.20.11 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa tty: N/A 
  OpenGL: renderer: NVIDIA GeForce RTX 3060/PCIe/SSE2 
  v: 4.6.0 NVIDIA 470.256.02 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
Drives:
  Local Storage: total: 232.89 GiB used: 15.18 GiB (6.5%) 
Info:
  Processes: 278 Uptime: 1h 48m Memory: 23.45 GiB used: 2.00 GiB (8.5%) 
  Shell: bash inxi: 3.0.38

---

### Post by Perfect Storm on 2024-08-30
Hello,

You don't need running Steam via wine. Steam comes with its own "layer" called proton which allows you tio play most Windows game on Linux.

1) Download Steam for Ubuntu/Linux
2) Double click it
3 When logged in go to settings ---> Compatiblity 
4) Click the "Enable Steam to Play all titles"
5) Restart Steam

I play Baldur's Gate 3 to Hogwarts Legacy on my Linux installation :)

---

### Post by nicolasdentremont on 2024-08-31
The Linux version of Steam works great and with Proton you can play most games.

I would like to recommend installing Steam using the .deb installer downloaded right from their website. The snap version in the Ubuntu Software/Snap store doesn't work quite as well.

However if you have issues running games with the Linux version of Steam using Proton you can try installing the Windows version of Steam using Lutris. I had a couple games that wouldn't work at all with Proton and Lutris had them up and running in no time. Lutris combines Wine with a few other things specifically for running games that would otherwise require a lot of tweaking with just Wine.

---

### Post by cryofreeze666 on 2024-09-03
thanks for the info, didn't do the settings thing you mentioned when i first installed it, didn't know about it.  to bad steam doesn't supply literature about installing their product, i was using 3rd party sites all over the place trying to find a way to reliably install the program. but for the sake of clarification, are you using the snap stoe steam, or the download from the site for those instructions to work?

---

### Post by cryofreeze666 on 2024-09-06
> **Perfect Storm said:**
> Hello,

You don't need running Steam via wine. Steam comes with its own "layer" called proton which allows you tio play most Windows game on Linux.

1) Download Steam for Ubuntu/Linux
2) Double click it
3 When logged in go to settings ---> Compatiblity 
4) Click the "Enable Steam to Play all titles"
5) Restart Steam

I play Baldur's Gate 3 to Hogwarts Legacy on my Linux installation :)

well i installed it from steam first, set the system compatibility, was even able to install games, playing them though it tells me i need directx.  so i uninstalled and deleted everything and installed steam from the snap store, again reset compatibility and closed steam,  after restart i installed and tried to play but keeps telling me i need directx.  tried linux runtime and steam proton after resetting compatibility for mor of the same.  don't tell me let me guess i need 22.04 installed?  was there something basic i'm missing?  

this computers vital statistics
System:
  Kernel: 5.15.0-119-generic x86_64 bits: 64 Desktop: Gnome 3.36.9 
  Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: Gigabyte model: GA-78LMT-USB3 6.0 v: SEx 
  serial: <filter> BIOS: Award v: F2 date: 11/25/2014 
CPU:
  6-Core: AMD FX-6300 type: MCP speed: 1406 MHz min/max: 1400/3500 MHz 
Graphics:
  Device-1: NVIDIA driver: nvidia v: 470.256.02 
  Display: x11 server: X.Org 1.20.13 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa tty: N/A 
  OpenGL: renderer: NVIDIA GeForce RTX 3060/PCIe/SSE2 
  v: 4.6.0 NVIDIA 470.256.02 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
Drives:
  Local Storage: total: 1.14 TiB used: 42.42 GiB (3.6%) 
Info:
  Processes: 282 Uptime: 7h 49m Memory: 23.45 GiB used: 2.56 GiB (10.9%) 
  Shell: bash inxi: 3.0.38

---

### Post by nicolasdentremont on 2024-09-07
Sometimes trying different versions of Proton in the game settings helps.

Trying different Nvidia drivers sometimes helps too.

There is also a ProtonDB website that lists many Steam games and whether or not they work and what people had to do to make them work

---

### Post by Perfect Storm on 2024-09-07
Which games are you trying to play?

---

### Post by cryofreeze666 on 2024-09-08
nicolas, am i to be lead to believe that the drivers i downloaded from nvidia are garbage, i'm so shocked, why would nvidia do such a thing beside the fact that their dicks whose customer support absolutely sucks if your not using windows.

but now that i'm done being an ass.  

which settings, the one under under steam at top left corner, or the settings at right side of screen when you click on game in library and open the [play] window?

---

### Post by cryofreeze666 on 2024-09-08
perfect storm
Games purchased through amazon that i almost returned when i found out i could not download to a storage device so i could use them on my terms not someone elses.

all the final fantasy games, well except the free ones, i'm a fan. they are asking for direct x versions 3 thru 11
two tomb raider titles underworld and tomb raider (not the original playstation graphics though
action taimanin (free)
angel legion (free)

---

### Post by nicolasdentremont on 2024-09-09
> **cryofreeze666 said:**
> nicolas, am i to be lead to believe that the drivers i downloaded from nvidia are garbage, i'm so shocked, why would nvidia do such a thing beside the fact that their dicks whose customer support absolutely sucks if your not using windows.

but now that i'm done being an ass.

Nvidia support for Linux definitely leaves some to be desired.

>  which settings, the one under under steam at top left corner, or the settings at right side of screen when you click on game in library and open the [play] window?

In Steam way at the top left. Steam > Settings > Compatibility, then you would check "Enable Steam play for all other titles"

To access the different versions of proton you would right click on a game in your library and go to Properties > Compatibility and check the box for "Force the use of a specific Steam play compatibility tool". That will show you a dropdown menu with a bunch of different versions of Proton to choose from. Sometimes you have to try them one by one.

Also in the game properties, in the General tab you will see "Launch Options" where you can input commands that the game will run as it launches. Sometimes specifying launch options will help but you need to know what you're putting in there.

If you search your games on [https://www.protondb.com/]("http://www.protondb.com/") you will see what steps others had to take to get them running.

You say you got your games from Amazon. I'm not sure how that works. Do they sell Steam games?

---

