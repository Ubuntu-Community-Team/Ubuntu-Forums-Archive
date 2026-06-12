---
title: "How do I make this guys script work?"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by hopelessone on 2012-01-04
Hi,

I have probs with vdr starting too early:

I found this:
[http://hg.openbricks.org/openbricks/file/8b50d1f48c8c/packages/vdr/scripts/runvdr](http://hg.openbricks.org/openbricks/file/8b50d1f48c8c/packages/vdr/scripts/runvdr)

What do i do?

Step by step..

Many Thanks

---

### Post by Frogs Hair on 2012-01-04
Do this from the Admin. account or be sure you have permission in the user account to make the script executable  .
 
1. copy the script as displayed to Gedit .
2. Name the script openbricks and save to a folder of your choice .
  
Line 6 allows you to adjust the start delay time if needed. 

3. right click on the script , enter Properties > Permissions . 
4. check "allow executing file as a program" .
5. Close folder  .

Set as startup Program 

6. Open Startup Applications .
7. Select add and enter the name in the dialog box .  
8. Use the browse option in the command box and move to the directory where the script is located and select open (comment is optional) 
9. Select add on the bottom of the dialog box. 
10. close all programs and restart to test the script . 

If more delay is needed change 2 to a greater number in line 6  .

---

### Post by hopelessone on 2012-01-05
Hi,

Thanks for the info,

but no go still the same...even after changing the length

Is there any way to make up a script that does this?:
1 - on shutdown
sudo edit /etc/default/vdr
ENABLED=0

2 - on start up
sudo edit /etc/default/vdr
ENABLED=1
sudo /etc/init.d/vdr start

without bothering me to ask for sudo?

Would be most grateful..!

---

