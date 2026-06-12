---
title: "Monitor Screen Space"
date: 2009-02-23
forum: Programming Talk
---

### Post by mastermindg on 2009-02-23
I have a program that's running in VMWare that monitors web services and alerts red or green in the app. Would it be possible to create an application that would monitor that section of the screen and when the color changes to red or green it would kick off a script on the Ubuntu side?

---

### Post by jespdj on 2009-02-23
Probably that would be possible, but such a solution is really very brittle. What if the red or green indicator is in a slightly different position because the windows are not exactly in the same place? What if the screensaver kicks in and the indicator is not visible on screen anymore?

I'd suggest looking for a more robust solution.

---

### Post by mastermindg on 2009-02-23
1) The program will always be in the same place as will the red/green indicators. 


2) I Don't Have the screensaver active, and even if I did, I'm working on the system while this application is running, so no chance of a screensaver activating.

---

### Post by mastermindg on 2009-02-23
How about using a screen capture program to periodically capture a section of the screen and then save the images to a folder.

I know fdupes will find duplicates within a folder, but is there a way to find a duplicate of 1 file (i.e. I could capture a section that shows red or green and then use a program to check for duplicates of this)?

So, I drop two images in a folder called image_orig, 1 image all red, 1 image all green. And then have the screen capture program drop images in a folder called image_cap. Both folders are in the same folder, so essentially I would need an application to find duplicates of images in image_orig but to check strictly in image_cap.

---

### Post by mastermindg on 2009-02-23
So I've almost got it down:

I'm using import to take my screenshot and crop it to just what I'm looking for:

```
import -window 0x2000008 -crop 16X28+1207+96 cropped.jpg
```

I used xwininfo to get the window id.

Then I found a python script that matches similar images:

```
python ./SnapMatcher.py --finddups caps .75
```

Now I can wrap all this is a shell script with a conditional statement and pipe some output, probably a system beep or something.

Just wanted to add that I wasn't really looking for an answer here, just some suggestions. I know I'll find a solution, but I like to tap the community every now and again and see if anyone has got something that I haven't seen.

Thanks.

---

### Post by Tomosaur on 2009-02-23
It really depends on what kind of access you have to the program you're trying to monitor. If it gives output or logs when the colour changes, you could write a little program which checks for that on the VMWare OS, then sends a quick message to a program running on the Ubuntu side via the net. Probably more reliable than screen-grabbing, but tis up to you.

---

### Post by tom66 on 2009-02-23
A possible, less fragile way of doing it I could think of would be to have a web server running on your computer (I suggest XAMPP) and said VMWare app should be able to access localhost on that server, because it would be networking with your (physical) computer. Then it's simply a matter of modifying your program to connect to a PHP script which does the logging or whatever necessary.

---

### Post by mastermindg on 2009-02-24
If this was my own application or if it had a known API then I wouldn't be looking at the screen grab. Unfornately this application uses proprietary backend scripting that I don't have access to, so I am forced to go with this method. However, it still works.

Thanks for the suggestions though.

---

