---
title: "error on ubuntu recovering journal."
date: 2024-09-23
forum: New to Ubuntu
---

### Post by cryofreeze666 on 2024-09-23
ok, i'm going to try and efficiently describe this.

tryed to update the bios on my x570 unify, the safety walls designed to keep you from pushing the clear cmos and flash bios are turned the wrong way and i didn't notice.

i ended up pushing both buttons at once wiping out my bios and cmos i guess.

screen would freeze when i would turn on and it read like this:

HEADING:  gnu grub version 2.06-13+deb12u1

minimal BASH-like line editing is supported.  for the first word, TAB   lists of possible command completions.  anywhere else tab lists possible   device or file completions.

grub>

disconnected power, removed battery, because i still couldn't get to bios.  then called msi because the directions for flashing bios in the book manually and in the net had 1 slight problem only needed 1 file not all the files they showed on msi site.  bios finally reinstalled.  

well, after i managed to get bios reinstalled, i reset date/ time then  f6'd it to reset to  optimal defaults, then restarted system.   it still didn't let me into the operating system, so i  turned off the power removed the battery and i now have a new screen it  kind of freezes on.

the screen reads:
/dev/nvme0n1p2: recovering journal
/dev/nvme0n1p2: clean, 201318/ 15237120 files, 3899965/ 60918272 blocks

i  guess i should mention this, i forgot to shut the computer off and fell  asleep.  7 hours later it had a hole bunch of lines and the file number  increased to present amount from 201219/ 15237120 files.  i cant  remember the original block number so i couldn't tell you if it  changed.  

i saw a closed 7 year old fhread titled [URL="https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://askubuntu.com/questions/924170/error-on-ubuntu-boot-up-recovering-journal&ved=2ahUKEwj9hf2NudmIAxWNJDQIHdjbAqwQFnoECBkQAQ&usg=AOvVaw0iiDEIP-cdDPXl3TQMV6LI"]**Error on Ubuntu boot up - "recovering journal"**

[/URL] but that doesn't seem to be helping, because i don't get the grub window any more.

one difference in the system info, prior to this problem changed o.s. to 20.04 (focal fossa)

```
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
```

---

### Post by oldfred on 2024-09-23
Please use Code Tags with any terminal or text output.
Code Tags
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)

Recovering journal is usually from an abnormal or hard shutdown.
And clean is just a message saying system is ok.

It looks like you also upgraded to 22.04.

UEFI defaults may not be best.
That often is UEFI Secure boot on. Did you orginally install with Secure boot on? I might try with Secure Boot off.
Also drives may be set for "Intel RAID" or fakeRAID. Better to use AHCI setting in UEFI settings for drives.

If still not booting. Use 22.04 or 24.04 latest ISO installed on flash drive, and ppa from Boot-Repair.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by cryofreeze666 on 2024-09-24
1) copied and pasted that systems info from a previous post about workstation troubles.

2) ok, yes i did, screen was freezing at gru grub, now its freezing on journal page.  esc, enter, none of the f keys, and none of the ctrl options i have learned so far unfroze it.

3) copied and pasted system info from an earlier post i had about workstations opening magically when i didn't know how to open them, or have reason to since i use only 1 monitor, i went back to focal fossa, told you it was the only difference before posting system info.

4) first, when i got bios back , after so many times of having to reset bios i stopped changing factory settings.  default settings worked with original installation, hasn't worked since i accidently hit the clear cmos an flash bios buttons at the same time..  i have just reset date/ time then hit F6 for optimized defaults.  usually that would get me into o.s. straight out of bios.  but when i restart computer it goes to the journal screen.

5) seems like i'm going to have to do a master boot wipe, reset the cmos, then reflash the bios to see what that does, cause i reinstalled foacal fossa and it did nothing, i used the erase and install option.  that particular computer takes less than 20 minutes to install linux o.s. and any updates.  unless me installing with updates while computer is in this condition is a contributing factor.  i don't know, i've been using linux a little more than 2 months now.  was hoping for advice from a person who might have experienced this problem and get it fixed without starting fresh.

well lets see if a master boot wipe, clearing cmos, and reflashing the bios will take me straight to bios screen at system boot.  reset bios, for hardware added, if it does, then i'll try reinstalling operating system.  if that doesn't work, i'll let you know.

---

### Post by cryofreeze666 on 2024-09-25
UPDATE: THE PROBLEM IS MY MOTHERBOARD.  no operating system installed used motherboard to erase drives. changing 1 setting at a time to get it back to running, i found my problem. every time i engage the legacy+uefi setting so i can use my older medias for some reason it shuts everything down.  well guess i gotta call msi now, thanks for the attempts at helping me.  don't know why its having a hissy fit now, it used to work.  probably the update.

---

### Post by cryofreeze666 on 2024-09-30
actually the problem is, and is not, my motherboard.  changed motherboard slots with secondary ssd, installed an operating system and it was working slick as snot.  i am running a MSI x570 unify, in the bios section there is a heading called secure erase +.  obviously for wiping a hard drive prior to resale.  i'm supposing that since i just used it so i could reinstall the crypto o.s. i was going to use and i'm back to not being able to access the ssd because secure erase program in bios didn't do the random character generation.  i am thinking that i need to use whatever the current technology for "reassigning quadrants" to restore the drives.  like what you would do on the old magnetic drives using dos if you suspected ghost files were in there.  the old magnetic drives you reassigned the quadrants, and it wiped the drive to clean as a whistle (brand new, storage wise).  i am curious if that ability was carried over to ssd's.  waiting on a call from a "senior" tech.  i doubt they'll know how, because i haven't had to use that in so long i forgot what the 50 + lines of code were for the process.

---

### Post by oldfred on 2024-09-30
If NVMe drive, it has secure erase.
It is very quick, as I understand it, it resets the internal encryption code.
With SSD, you do not want to write 0, as that just increases wear.

Erase SSD
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
[https://wiki.archlinux.org/index.php/Solid_State_Drives/Memory_cell_clearing](https://wiki.archlinux.org/index.php/Solid_State_Drives/Memory_cell_clearing)
[https://wiki.archlinux.org/title/Solid_state_drive/Memory_cell_clearing](https://wiki.archlinux.org/title/Solid_state_drive/Memory_cell_clearing)

sudo apt install nvme-cli
nvme - the NVMe storage command line interface utility (nvme-cli)
nvme --help
sudo nvme list

erase
 sudo nvme-sanitize

---

