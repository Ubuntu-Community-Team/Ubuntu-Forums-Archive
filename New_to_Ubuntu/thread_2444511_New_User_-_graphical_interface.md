---
title: "New User - graphical interface"
date: 2020-05-31
forum: New to Ubuntu
---

### Post by sumatra1340 on 2020-05-31
Hello.

v16.04 in TRY Ubuntu mode.
Primary use -  move files from Win8 to USB.
Lenovo G50 / 128 GB HDD / RAM @ 16

After starting a move, the graphical interface was replaced by a full screen black terminal window.  I've attempted a few commands but my linux-speak is at the Pre-K level. I'm leary of trying something that I don't have a stronger grasp on.

As recommended in another post I tried NOMODEST (not sure about the spelling) but there's been no change.

The initial move has been completed but there's a few more files (profiles) to move.

Note > I spent the better part of yesterday reviewing the ins/out of Ubuntu & TRY UBUNTU was working fine.

---

### Post by Autodave on 2020-05-31
Are we to assume that Win8 and Ubuntu are on the same machine?

As far as nomodeset, what are the specs on your machine: especially the graphics card?

Have you installed and drivers for the GPU?  If so, what one and where did you get it from?

---

### Post by Impavidus on 2020-05-31
nomodeset is used if the graphics are otehrwise not properly iniialised. In your case, you had graphics until they suddenly crashed during a file copy. That could still be a graphics driver bug though.

If the only purpose is to copy some files to backup storage, we may be able to help you through doing that by command line.

---

### Post by mastablasta on 2020-06-01
> **sumatra1340 said:**
> 
After starting a move, the graphical interface was replaced by a full screen black terminal window.

that is not a normal behaviour. how did the terminal window look like? did it have a user name and PC name? for example this would be the terminal line in live session where you would then add your commands to the right of$ sign:
 ```
ubuntu@ubuntu:~$
```

has the screen looked like so?

the G50 has intel celeron with intel HD. the graphics drivers are part of kernel and would load on boot. so everything regarding GPU drivers should work just fine. unless the GPU chip is overheating, otherwise damaged, or if something is wrong with the image used to boot the OS. have you checked the md5 sum of the image on download?: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
after moving the image or DVD or USB you should also check for any errors.

there are a few other distros you could try for backup. they take up much less space than ubuntu. 

finally if PC works in terminal mode only you could install mc (midnight commander) to give you some sort of GUI for an easier way to copy the files.

---

