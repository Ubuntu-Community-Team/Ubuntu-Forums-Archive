---
title: "Slow and Mute Youtube videos in ubuntu 11.10"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by RobikShrestha on 2012-03-12
Videos are being played without any sound. Plus, they are being played very slow.

What to do?

---

### Post by TBerk on 2012-03-12
What resolution or 'quality' are you trying to run your videos at? 

Youtube often offers a range or density from numbers like 240 and 360 up past 480 and stuff they like to call HD.

Also, is it possible to get some info on your hardware, as in what processor, video card, and perhaps amount of RAM or Memory your system and video card each has.

---

### Post by ojdon on 2012-03-12
What is your graphics card? Have you got the necessary drivers installed for your device? 

Tried flash performance in a different browser such as Google Chrome? Just to test to see if the issue is browser related.

You might get better performance by signing up to YouTube's HTML5 Video Beta instead of using flash which can be found [here.]("http://www.youtube.com/html5")

Hope that helps!

---

### Post by RobikShrestha on 2012-03-12
It seems like the problem is not only with youtube videos but videos in general. 
I tried Chromium browser. I also tried media players like VLC etc. and all of them have the same problem.

---

### Post by RobikShrestha on 2012-03-12
The hardware specification is:

RAM: 4 GB
Processor: i5
Graphics Card: Intel HD integrated with Nvidia GeForce 525M

I am sorry I did not provide much details in my original question, but the videos were being played fine till yesterday (without any lag and with sound). But now I have problems.

---

### Post by HavarN on 2012-03-12
What other applications use your computer's resources when there is a lag?

Try running```
top
```in a console while a video lags. Make a note of the top processes and cpu-usage and post back here.

---

### Post by audiomick on 2012-03-12
> **HavarN said:**
> Make a note of the top processes and cpu-usage and post back here.

top shows a running ouput which you can't copy. If you want a "snapshot" for the purposes of posting the output here do
```
top
```

Let it start and show its' output and then do crtl + c

This will stop the dynamic output from top, but leave the last stand visible in the terminal. You can then copy it by highlighting the bit you want with the mouse then do shift+ctrl+c, and paste it here. Click the # button above the post window to get code tags, then paste the output between them.

---

### Post by NikTh on 2012-03-12
Hi , 
Also , if you use Firefox  , try to install Flash Aid [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/  ]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")
and follow suggestions to install latest adobe flash , or uninstall any conflicts.  
Also you can post here the output of ```
 free -m
``` 
Good Luck
[]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/")

---

### Post by RobikShrestha on 2012-03-14
Now, all the videos are working fine i.e. including the youtube videos. I can't replicate the condition (of video lag). But the problem was there and is most probably a bug.

Should I mark this thread as solved?

---

