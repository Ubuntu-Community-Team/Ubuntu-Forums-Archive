---
title: "Sansa Fuze files are not detected"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by davisetdavis on 2011-12-23
I have a 3 year old sansa fuze that i previously synced with windows xp,i now run Ubuntu 11.10 and it detects the sansa and labels it properly, lists folders,ie,MUSIC,PHOTOS,AUDIO, etc.but shows zero files(there should be 695 files)-------Does anyone know what i can do to convert the windows wma files so they are compatable with Ubuntu??? Short of erasing the albums and re-downloading them with Banshee.    
 Thanks for any help you can give me.

---

### Post by hackb0y294 on 2011-12-23
Hi and welcome to the Forums.
Does your Fuze show up on the desktop as a removable drive when you plug it in? If so, Ubuntu should list the WMA files whether or not Banshee can read them (which it can, with plugins), so try opening it from the desktop or Unity sidebar and see if your files are listed. 

To enable Banshee to read the WMA files, open a terminal (press Alt - F2, type terminal) and type or copy/paste the following, and press enter:

```
sudo apt-get install gstreamer0.10-ffmpeg && sudo apt-get install gstreamer0.10-plugins-bad && sudo apt-get install gstreamer0.10-plugins-ugly
```

That should work; post if it doesn't and I'll see what I can do.

---

### Post by davisetdavis on 2011-12-23
Ubuntu does list SANSA FUZE ,and it does show files,but the files are empty when i open them.I ran the apt-get install line you gave,it was already installed and there were no updates.Everything in the system works great,except this one issue.

---

### Post by hackb0y294 on 2011-12-23
Okay. What exactly do you mean by empty? Does the file size show up as 0, or do they show as having no length in Banshee?

---

### Post by davisetdavis on 2011-12-23
In Ubuntu they show up as 0,in Banshee it shows 4 Gig of unknown.
Oh,also i agree,down with the new world order.

---

### Post by hackb0y294 on 2011-12-23
Alright, I did some sleuthing, and I found here [http://ubuntuforums.org/showthread.php?t=889306](http://ubuntuforums.org/showthread.php?t=889306)
and here [http://ubuntuforums.org/showthread.php?t=1491410](http://ubuntuforums.org/showthread.php?t=1491410)
that if you put the device in MSC mode (here's how to do it: [http://kb.sandisk.com/app/answers/detail/a_id/207/session/L2F2LzEvdGltZS8xMzI0Njk2NDkyL3NpZC9IQzVJNG1Naw%3D%3D]("http://kb.sandisk.com/app/answers/detail/a_id/207/session/L2F2LzEvdGltZS8xMzI0Njk2NDkyL3NpZC9IQzVJNG1Naw%3D%3D")), it should show up as a mass storage device in Ubuntu, which in turn enables Ubuntu and Banshee to read it correctly. However, as mentioned in the second link I gave you:
> If you installed the music in MTP mode, it will only be seen in MTP  mode.  If you want to use the Fuze on Ubuntu, the best option (maybe the  only option) is to delete everything, then put it in MSC and transfer  the music back to the Fuze.So, maybe you could delete all your music (if you don't have the music on your computer already, copy it from your Fuze first, if you can), switch to MSC mode, then transfer it all back with Windows, and then boot Ubuntu and try it. I don't have a Fuze, so I'm sort of flying by night here, but I hope it works for you, and again, if not, go ahead and post back.

Nice to meet another freedom loving Person!

---

### Post by davisetdavis on 2011-12-24
Thank you for all your help! I have changed the ubs mode a dozen times,I was hoping for a magic bullet,but in the back of my mind i kinda thought I would wind up re-installing the music files.
I really do appreciate your help.
Merry Christmas!

---

### Post by hackb0y294 on 2011-12-24
Hey, no problem, and same to you!

---

### Post by SingleSpeed10 on 2012-01-29
> **hackb0y294 said:**
> Alright, I did some sleuthing, and I found here [http://ubuntuforums.org/showthread.php?t=889306](http://ubuntuforums.org/showthread.php?t=889306)
and here [http://ubuntuforums.org/showthread.php?t=1491410](http://ubuntuforums.org/showthread.php?t=1491410)
that if you put the device in MSC mode (here's how to do it: [http://kb.sandisk.com/app/answers/detail/a_id/207/session/L2F2LzEvdGltZS8xMzI0Njk2NDkyL3NpZC9IQzVJNG1Naw%3D%3D]("http://kb.sandisk.com/app/answers/detail/a_id/207/session/L2F2LzEvdGltZS8xMzI0Njk2NDkyL3NpZC9IQzVJNG1Naw%3D%3D")), it should show up as a mass storage device in Ubuntu, which in turn enables Ubuntu and Banshee to read it correctly. However, as mentioned in the second link I gave you:
So, maybe you could delete all your music (if you don't have the music on your computer already, copy it from your Fuze first, if you can), switch to MSC mode, then transfer it all back with Windows, and then boot Ubuntu and try it. I don't have a Fuze, so I'm sort of flying by night here, but I hope it works for you, and again, if not, go ahead and post back.

Nice to meet another freedom loving Person!
This seems to explain why on my Sansa Clip I couldn't see files  in Win7 that I had copied onto it from Ubuntu and I couldn't see files in Ubuntu that I had copied onto it from Win7. I had the USB mode on the Sansa Clip set to Auto Detect. Win7 probably used MTP whereas Ubuntu probably used MSC. After I set my Sansa Clip to use only MSC both OSs can now see the files.

---

