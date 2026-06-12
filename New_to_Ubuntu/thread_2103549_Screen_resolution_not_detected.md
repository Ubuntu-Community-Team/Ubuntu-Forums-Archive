---
title: "Screen resolution not detected"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by ydylan77 on 2013-01-10
I know that this is a redundant post, but I haven't found a proper and permanent solution that works yet so I am asking the community for some help.  I have only been on Linux for about a day so I know very little...so get your spoons out LoL I need help.


PC is [Pavilion a1213w 2GB RAM]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00497087&cc=ad&dlc=en&lc=en&jumpid=reg_r1002_usen_c-001_title_r0003") <link to specs>

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 960 x 600, maximum 960 x 600
default connected 960x600+0+0 0mm x 0mm
   960x600        60.0* 
   960x540        60.0  
   800x600        60.0     56.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0  
   800x480        60.0  
   720x480        61.0  
   640x480        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        61.0

---

### Post by fantab on 2013-01-10
The Graphics Processor **SiS Mirage 2 Shared video memory (UMA) **is the issue on the said machine. I don't know if there are is any  Proprietory (Linux) Drivers available of this. You probably won't get any Hardware acceleration on the default basic Open Source Linux Drivers which are running on your machine ATM.

What is the native resolution of your 'screen'?

Try the [**FIX HERE**]("http://ubuntuforums.org/showpost.php?p=11503588&postcount=4") and see if it helps.

---

### Post by ydylan77 on 2013-01-10
Screen Resolution for SyncMaster B2030 wants 1600x900 @60Hz. 
Thanks for the response I will check out the link you have posted and let you know where it gets me.

---

