---
title: "Unable to boot into Ubuntu anymore (14.04 LTS)"
date: 2015-11-25
forum: New to Ubuntu
---

### Post by baba3 on 2015-11-25
I am having some issues and was hoping someone could please offer some advice.  First issues are that when I boot I get 3 error messages in the startup sequence.  ```
[    14.127609 genirq: Flags mismatch irq 0.  00000080 (ips) vs. (00015a20 (timer)
[14.127663] intel ips 0000:00:1f.6: request irq failed, aborting
[    15.557319] i915 0000:00:02.0: Invalid ROM Contents
```

I have tried updating NVIDIA 310 per some advice I saw and that helped but it moved the ROM contents error to the bottom (different error code I guess).  With all of these issues it hasn't been terrible since I could still boot up until now.  

I tried getting fancy schmancy with it by setting up a custom.sh file in my profile folder which would lower the volume to 0, keyboard backlight to 0 and screen backlight to 50% upon startup but I screwed it all up and now can't boot.  All of the commands worked individually in terminal and I think i just did something bad on the script file that hosed me.  After navigating around in root on the recovery mode I found the file.

File is stored in my directory 

```
 /etc/profile.d/custom.sh
```

```
#!/bin/sh
echo 38035 | sudo tee /sys/class/backlight/gmux_backlight/backlight
echo 0 | sudo tee /sys/class/leds/smc::kbd_backlight/backlight
sudo /usr/bin/amixer -c 0 sset Master,0 0% > /dev/null
exit

```

I wasn't sure if me putting the exit is what screws it all up or if I am doing something terribly wrong/noobish.  I tried all of the commands except for the #!/bin/sh in terminal and all worked independently so I wasn't sure if I did something crazy.

I can get into the file to edit via nano but when I try to remove the exit line (which I think is what screws up my boot process) I get a save error saying it is a read only directory.

---

### Post by Melnik_Hoogland on 2015-11-25
I can't help you with your "Invalid ROM Contents" issue; that's not my area of expertise. I think I know what's causing you to be unable to boot though.

You use sudo to run all your tee commands. Of course, you need this since you need root permessions to write to those files. **However, as scripts in profile.d do not run as root, sudo asks you for your password, and blocks until you type it in.** This stops the booting process until you type your password in, and I don't think you can even type it in since you aren't doing this on a normal terminal.
I would move your script to a place where nothing will try to execute it automatically (like your home directory) until you can find somewhere it'll get executed with root permissions (init.d would probably work, but I'm tired right now and can't guarantee it. If you try it, make sure you have a live CD/USB or another OS to boot from that can get your script out of init.d in case it messes up your system again.).

As for your read-only directory error, [s]make sure you're running nano as root. I see no reason why it would complain about a read-only directory if it has root permissions.[/s] EDIT: It looks like the file system is mounted read-only from the recovery shell. Because of this, you'll need a live CD/USB to fix your system, but since you had a working computer to post this on, you should be able to make a live CD/USB if you lost your original one.

---

