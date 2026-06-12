---
title: "ok this one might be a little more than what i can bight off"
date: 2024-09-02
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2024-09-02
first i was impressed with myself for finally getting a crypto miner to work on ubuntu.  i was running on the default settings while it load tested until i noticed that it was using my cpu to mine and not my gpu's.  deactivated cpu, activated gpu, and that was the only change i had made to cudo-miner.  well i had to have the window in the net open while entering wallet addresses and creating communication between my miner and their pools.  well it started an was running through load tests, i minimized firefox, went to shoot pool, have a beer or two and came back.  now the old problem returned and it's not going away.  i can't reopen firefox, and i cant open the cudo miner window to see the results of the load test.  i'm back to having two desktop windows at the top of the show applications window, and neither one will give me access to either program.  ok turn off every running program right.  firefox closed easy enough, but cudo miner not so much.  ok lets remove and reinstall cudo miner, all the settings are in the website version right?

yep thi sucks:
                        @a-MS-7C35:~$ apt-get --auto-remove purge cudo-miner-core cudo-miner-service cudo-miner-cli
 E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
 E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?
  
ok ya wanna be tricky, takes 23 minutes to wipe hard drive and reinstall linux.

yep that didn't work, i changed my boot order AGAIN, then inserted installation media, and i get an error blue screen

error
verification failed: (0x1a) security violation
ok in the center of screen

next screen:
press any key to perform mdk management

3rd blue screen
perform mdk management

choices:
continue boot
enroll key from disk
enroll hash from disk

chose continue boot and it went back to first blue screen error.

gonna try something ill advised i think, gonna go with windows 7 to wipe the drives then try and reinstall everything from that, extra 10 minutes since windows sucks. hoping that computer doesn't get to pinicky before i wipe, it wouldn't let me install 7 because it shuts down keyboard and mouse at a certain point during installation.  will let you know how badly i fail in about half and hour 45 mins.

inxi-bz info

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

ill edit this post so i'm not spamming

UPDATE
ok update, well that plan didn't work. it hangs up at the microsoft logo and doesn't go any further.  so no fresh install it looks like.

tryed to use shift key to open grub menu to try and create a root, didn't work

---

### Post by Holger_Gehrke on 2024-09-02
Well, this isn't going to help you much since you already wiped the drive, but that error from 'apt' was due to the fact that you didn't use 'sudo'. Removing and installing software is a job for a system administrator not for a normal user. So what you should have done is:
```

sudo apt remove --purge cudo-miner-core cudo-miner-service cudo-miner-cli
sudo apt autoremove

```
sudo would have asked for your password (and not given you any indication while typing it in; security against shoulder-surfers ...) and then executed the rest of the command as root; after entering the password once a 'ticket' is stored for a certain time which allows you to run additional commands with sudo without having to enter your password every time.

Holger

---

### Post by cryofreeze666 on 2024-09-02
couldn't wipe the drive, windows 7 kept freezing at the logo frame so i couldn't get to the hard drives to wipe them.  i used that command already which was why i copied and pasted the results of it telling me i had to create a root user.  and following the instructions to hold shift at start up to create a root shell didn't work, so i'm thinking that there is more to creating a root shell than what that person typed.  which has me looking for a more detailed description, since some folks think that only experienced users read their posts and will know the rest on their own.

---

### Post by cryofreeze666 on 2024-09-05
UPDATE:

windows7 froze at logo screen when i tried to use it to wipe the hard drive after ubuntu 22.04 would not bot from any medium.  wild hair, had me try ubuntu 20.04, that allowed me to reinstall, went through the entire input sequences and removed the disk (which just installed this computers o.s. last week when i started having problems with creating new work spaces by accident.

the problem i am having now with 20.04 is that it says this after i start computer:

/dev/nvme0n1p2: recovering journal
/dev/nvme0n1p2: clean, 201272/15237120 files, 3910707/60918272 blocks

starting to think i might need to unplug, remove battery, and manually reset bios.  to find out if that will work.  

if resetting my bios doesn't work so i can fresh install an o.s. what might i try?

here is system info with one change it has 20.04 loaded into it.  i just can't inxi -bz because i can't get into the o.s. it stops at a black window with the above info on it.

System:
  Kernel: 6.8.0-40-generic x86_64 bits: 64 Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: Micro-Star model: MEG X570 UNIFY (MS-7C35) v: 2.0
    serial: <superuser required> UEFI: American Megatrends LLC. v: A.E2
    date: 08/01/2022
CPU:
  Info: 12-core AMD Ryzen 9 5900X [MT MCP] speed (MHz): avg: 2532
    min/max: 2200/4950
Graphics:
  Device-1: AMD Navi 21 [Radeon RX 6800/6800 XT / 6900 XT] driver: amdgpu
    v: kernel
  Device-2: NVIDIA GP107 [GeForce GTX 1050 Ti] driver: nvidia v: 535.183.01
  Device-3: NVIDIA GP107 [GeForce GTX 1050 Ti] driver: nvidia v: 535.183.01
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: X:
    loaded: amdgpu,ati,modesetting,nouveau,nvidia,radeon unloaded: fbdev,vesa
    gpu: amdgpu,nvidia,nvidia resolution: 1: 1920x1080~75Hz 2: 1920x1080~60Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.2.1-1ubuntu3.1~22.04.2
Network:
  Device-1: Realtek RTL8125 2.5GbE driver: r8169
  Device-2: Intel Wi-Fi 6 AX210/AX211/AX411 160MHz driver: iwlwifi
Drives:
  Local Storage: total: 2.05 TiB used: 17.06 GiB (0.8%)
Info:
  Processes: 459 Uptime: 3h 42m Memory: 62.71 GiB used: 4.01 GiB (6.4%)
  Shell: Bash inxi: 3.3.13

---

### Post by cryofreeze666 on 2024-09-30
this was solved, by using [[COLOR=#000000]Holger_Gehrke's[/COLOR]]("https://ubuntuforums.org/member.php?u=1961578")[COLOR=#000000] advice[/COLOR]

---

