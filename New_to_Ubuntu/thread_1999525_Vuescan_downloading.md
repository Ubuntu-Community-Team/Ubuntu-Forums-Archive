---
title: "Vuescan downloading"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by photogenius_uk on 2012-06-08
I am an absolute Ubuntu beginner having downloaded the latest version through Windows Vista.  I am now trying to download Vuescan as I use it all the time with Vista. I can download it (apparently Ok) but cannot open it to use. I will want to use it with my scanners (probably I'll be back asking for help with that operation as well!) but I've got to cross this initial bridge first!  Please explain in simple language if it's possible and how!  Thanks.


Alan

---

### Post by steeldriver on 2012-06-08
You need to extract the binary file from the downloaded tar archive (*.tgz) - if you're familiar with Windows it's just like using WinZip

You can either click on it and open it with the graphical Archive Manager and then select Extract or you can open a terminal, navigate to the directory containing the downloaded .tgz file, and type

```
tar xfz vuex3291.tgz

```where 'vuex3291.tgz' is the file you downloaded. Then you can just double click the vuescan executable file, or change (cd) to the VueScan directory and type

```
./vuescan
```Once it all works you may want to move the extracted files to somewhere on the system path so that you can execute it from anywhere (or even add it as a menu item)

---

### Post by photogenius_uk on 2012-06-11
Thank you for replying - it was good of you. Please don't think I am ungrateful but I am so computer illerate (especially re Ubuntu) that i didn't understand a word of what you told me.  Could you repeat your message and give me a "dummies" step by step please??

Alan

---

### Post by steeldriver on 2012-06-11
Hi Alan

[B]I use the Xubuntu desktop so if these instructions don't work for you then you will need to wait for someone else to chime in
[/B]
1. in your file manager, right-click on the vuex3291.tgz file that you downloaded (if you used Firefox to download it, it should be in the Downloads folder of your home folder)

2. select "Open with Archive Manager"

3. in the Archive Manager window, select the VueScan folder and right-click again and select 'Extract...' (or go to the 'Archive' main menu and select 'Extract...' from there) - just like using WinZip

4. use the file browser that pops up to choose where you want the extracted program files to go - I suggest right in your home folder for now - and press the 'Extract' button at the bottom

5. Quit the Archive Manager

6. go back to your file manager and navigate to the extracted VueScan directory - you should see 3 files: vuescan  vuescan.8ba  vuescan.ds - the first one of these is the executable file

7. right-click on the vuescan file and select 'Execute'

---

