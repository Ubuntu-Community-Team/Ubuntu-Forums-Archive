---
title: "Display choppy when playing DVDs"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by kibaruzo159 on 2012-11-03
I recently installed Ubuntu 12.10 and tried to play a standard store purchased DVD movie (Region 1).  I first tried with the default Movie Player, but the video was very choppy and sound garbled as well.  I then tried downloading some other players, such as VLC but have the same issue.  I am running ATI RS780 [Radeon HD 3200].  I believe the driver is the open source ATI driver.  I would like to use VLC and have normal playback on DVDs, so any help on troubleshooting this would be greatly appreciated.

---

### Post by squakie on 2012-11-04
Did you already install libdvdread4 (or whatever the version is up to now)?

After installing it, did you run the script in it's folder to install libdvdcss?

How much memory do you have?

If you have to dedicate system memory to video, did you max it out?

How fast is your CPU?

---

### Post by kibaruzo159 on 2012-11-04
> **squakie said:**
> Did you already install libdvdread4 (or whatever the version is up to now)?

After installing it, did you run the script in it's folder to install libdvdcss?



Hi Squakie, question about libdvdread2 got me on the right track.  I did a bit more digging in the Ubuntu help files related to that and found the following:  [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

I did the installations and all is working great now.  Thanks.

---

### Post by squakie on 2012-11-05
Just glad it helped in some small way.  Well done!

---

