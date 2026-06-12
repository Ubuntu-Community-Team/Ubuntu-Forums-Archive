---
title: "How to do a backup and upgrade builds?"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by wilsonB on 2012-03-04
Now that I have Ubuntu 11.10 all configured, setup and almost all obvious problems fixed, I want to back everything up in case I break it or want to move to the next build.

I have a new SSD coming in the mail that I will reimage with this slow HD and keep it on hand as a back up...

Im trying to learn the file structure on where things are stored. 

Is there a System REstore type feature for Ubuntu?

Thanks

---

### Post by HeroOfCanton on 2012-03-04
There's a ton of good info on backing up [here]("https://help.ubuntu.com/community/BackupYourSystem").

You may want to consider doing a reinstall when you get the SSD in. I'm not sure how good ubuntu is with detecting and adjusting, but there are some features you will not want on when using a solid state due to the limited read/writes. I know on my Win7 desktop there were a lot of tweaks, like turning off hibernation and moving the VRAM to my HDD, I needed to apply to make sure the load on that drive was minimized. Hopefully someone else will chime in with more ubuntu specific info and if a reinstall may be a good idea.

---

### Post by NikTh on 2012-03-04
I think its different if you want to back everything up in case of break from "want to move to next build" . If the first then use a backup tool . I suggest "lucky backup" or "clonezilla" . 
If the second then 
a) if you have a separate home partition , do not delete it  with your new fresh install .Keep it and you will have all your personal files and configuration files of your programs at your new install. (maybe will work , maybe not) . 
b) if you don't have home partition then use a backup tool . You can restore your home when you finish your new installation.

---

