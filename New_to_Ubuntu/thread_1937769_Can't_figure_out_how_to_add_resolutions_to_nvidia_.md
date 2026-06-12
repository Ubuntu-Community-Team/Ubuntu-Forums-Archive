---
title: "Can't figure out how to add resolutions to nvidia x server settings program"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by Aurinko on 2012-03-08
I installed Ubuntu 11.10 on my new computer yesterday, and all day I've been reading the internet and trying everything to get a higher resolution to show up as an option in the 'NVIDIA X Server Settings' program, but no, I'm stuck.

My dual boot Win7 has no troubles using the same monitor at 1600x1200@85Hz with the same hardware, and my old computer with Ubuntu was also using the same monitor at this resolution & refresh rate.

In similar problems on this forums, people are asked this, so here it is if case it helps someone reading my message.
```
aurinko@pc:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GF114 [GeForce GTX 560] (rev a1)
```Looking at the Additional Drivers program, first I was using NVIDIA accelerated graphics driver (version current) and then I changed to NVIDIA accelerated graphics driver (post-release updates) (version current-updates) in hopes of that helping, but no. I can't even guess which driver is newer, because for some reason those don't show any version numbers there.

I tried the section "Adding undetected resolutions" from [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution).
```
aurinko@pc:~$ cvt -v 1600 1200 85
# 1600x1200 84.95 Hz (CVT 1.92M3) hsync: 107.21 kHz; pclk: 235.00 MHz
Modeline "1600x1200_85.00"  235.00  1600 1728 1896 2192  1200 1203 1207 1262 -hsync +vsync
aurinko@pc:~$ xrandr --newmode "1600x1200_85.00"  235.00  1600 1728 1896 2192  1200 1203 1207 1262 -hsync +vsync
xrandr: Failed to get size of gamma for output default
aurinko@pc:~$ xrandr --addmode default 1600x1200_85.00
xrandr: Failed to get size of gamma for output default
```Nothing happened after that, and the page doesn't say what to do next, so after searching the internet some more, I tried typing this, which didn't help either:
```
aurinko@pc:~$ xrandr --output default --mode 1600x1200_85.00
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
```So that section of that wiki page doesn't help.

Then I've surfed the net a bit more, and one page said to run nvidia-xconfig and that would fix everything. Fine, I tried:
```
aurinko@pc:~$ sudo nvidia-xconfig
[sudo] password for aurinko:

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```But no, that didn't fix everything. And that page didn't explain what to do next either. I thought I'd try restarting the computer, even though that wasn't mentioned anywhere.
Bad idea. After that I was stuck with 640x480, and when I tried to run the xrandr commands again, I got something like this (I wasn't able to copy/paste it with the screen being so tiny and all the scrollbars and such were missing, so might not be exactly the same):
```
xrandr: screen cannot be larger than 640x480 (desired size 1600x1200)
```So I went and restored xorg.conf from the backup, because nothing seemed to work right with that resolution, alt+tab didn't switch away from the terminal window at all, just asked me if I wanted to list 2217 possibilities (wtf??), so it was pretty impossible to use, because I couldn't switch between windows to google some more.

Some pages say that I should edit xorg.conf manually, but I have no idea  what to put there, it only has 3 lines at the moment, and I'm guessing I  can't just copy the file from my old Ubuntu box because that box has  different hardware.

Would anyone have any ideas on what to try next? It feels really frustrating that changing resolution is this hard.

---

### Post by pootan on 2012-03-08
The way I do it is to generate a modeline as you have done using xrandr. Then I will run nvidia-settings and save an xorg.conf file using the highest resolution available in nvidia-settings. Then I will go to the xorg.conf file and manually replace the generated nvidia-settings modeline with the one xrandr gave me. Perhaps the modeline from your old box will work as well.

 It's a good idea to read up on how to delete your xorg.conf from the command line in case your xorg.conf file doesn't work and you get dumped there.

---

### Post by Aurinko on 2012-03-08
Thanks, that helped!

I went to nvidia-settings and saved an xorg.conf file there, opened it in gedit and realized that now it looks a lot like on my old box, so I changed the HorizSync and VertRefresh lines for the monitor to match the ones on the file on my old box, and tried reboting... and that was enough, now I have lots of nice new resolutions available and they work nicely!

So if any other newbie stumbles here with the same problem, there's a nice button in tbe 'X Server Display Configuration' section of the 'NVIDIA X Server Settings' program, called "Save to X Configuration File" which creates a nice xorg.conf file.

---

