---
title: "Copy.com applet missing from panel"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by suomalainen on 2014-04-06
Ubunteros,

Does anyone here use 12.04 with Copy.com v.1.43.0290 ??? All I find on Inet are answers to Ubuntu v.13 BUT I use 12.04!

Here's the issue:

I downloaded the tarball copy_agent-1.43.0290.tgz from copy.com web site. Then I extracted it and opened the folder it generated. I then open the sub folder "x86" and proceeded with double clicking the file "CopyAgent". This action places a copy.com applet in the panel.

HOWEVER, once you close the PC and reboot the entire steps above need to be done all over again as the system does not retain anything.

Has anyone defeated this problem?

Thanks

---

### Post by wn1ytw on 2014-04-06
deleted as it turns out I was wrong.

---

### Post by wn1ytw on 2014-04-06
I had to do two operations on my ubuntu devices for copy.com to work well. I may have gone a little far on the permissions but it works on 3 laptops, 2 that dualboot windows and one that started life as ubuntu 12.04LTS. And in the virtualbox I run on my iMac.

I did as the readme in the copy files suggests and in terminal I navigated to where I expanded the files to: ~/Copy and 

```


sudo ./CopyAgent -installOverlay


```

I also opened the CopyAgent program in ~/copy/x86_64 and logged in to my copy.com account. Note I have two folders in my ~/ folder: ~/copy and ~/Copy.

I also went to the ~/Copy folder and did

```


sudo chmod -R 755 ~/Copy


```

```


sudo [COLOR=#000000][FONT=verdana]chown -R scott:scott ~/Copy


```

Some may have been more than needed but copy.com works between all of my stuff. I had thought it was working untill I answered you earlier and found I needed to do the opening of CopyAgent in addition, hense the previous deleted post. Good luck!
scott[/FONT][/COLOR]

---

### Post by suomalainen on 2014-04-06
I solved the problem!

Some background first.

I have two laptops runninig Ubuntu 12.04LTS. On one laptop the "white bird" panel applet representing Copy would not install to the panel. On the other laptop it did. I attached an image so you can see what this "white bird" looks like.

Two problems:

1. Because the one laptop does not load Copy in panel it must be manually loaded each time by navigating to the Copy folder, then opening the x86 subfolder and double clicking the "CopyAgent" file.

2. The laptop containing the "white bird" in panel cannot be "Quit", else you need to follow steps in item 1 above to restart.

The solution that worked for me.

1. Once I had extracted the copy folder I then placed it into the hidden folder .copy found in the "Home Folder".

2. I opened the folder ".copy" and then the folder "copy" and finally the folder "x86".

3. Drag & drop "CopyAgent" to the panel. A "Create Launcher" will appear.

4. Give a "Name" to it and a "Comment". Associate an appropriate image to the launcher. This can be downloaded from the world wide web. I use Copy's "Blue Bird" icon. See image.

5. Reboot

6. Copy "Blue Bird" should now be in panel.


What this means.

Now that I have the copy "Blue Bird" in the panel, I can "Start" and "Quit" the Copy program according to my terms. EG: Clicking "Blue bird" starts the program which gives you the "white bird". Clicking the "White Bird" gives you the option to "Quit" the program.
 
This is how I solved my issue.

---

