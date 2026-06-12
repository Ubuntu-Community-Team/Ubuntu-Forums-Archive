---
title: "Looking For alpha testers. for flash ripper"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by josephmills on 2012-04-14
Hello there a little while back I started working on a perl script to copy cached flash from a browser. I have now just finished it. and am looking for alpha testers to let me know how it works. 
The program is under the gpl3 you can Download the program from 

[Here ](http://bazaar.launchpad.net/~josephjamesmills/ubforums-2-ubwiki/ubforums-2-ubwiki/download/josephjamesmills%40ubuntu.com-20120414092932-f4q25op6dv325hrk/ripper_01ripper1_amd-20120414092931-nc8i7210iddxzafi-1/ripper_01-ripper-1_amd64.deb)

Then just install with ubuntu software center. And it will be in your menu. 

The Ripper is Easy to use.
1) Open a Browser 
2) Go find a Video 
3) Let it Load all the Way 
4) After Loaded Press OK 
5) look in videos folder 


Thanks and I look forward to hearing from you. 

Joseph

---

### Post by Avaritia on 2012-04-14
It worked fine when I just tested it on a couple of videos, if you could make it convert the videos into a format of your choice after it downloaded it would be good.

---

### Post by Curtis6767 on 2012-04-14
After viewing video, open Dash, click on Ripper.

Terminal window and small pop-up menu appear.

Click "Ok" to save video.

New pop-up menu appears with location to save video.

Click "Ok" if selected destination is suitable. 

Go to Home/Videos to locate saved video.

Right click to produce drop down menu and select preferred Player.

P.S. Worked fine but would not open in Movie Player or Banshee. Did work with VLC.

Could just be my system.

Very neat little app. Thanks.

Edited to add the following:

The videos do not seem to store in their own file. I viewed and saved two videos but the second video stored on top of the first, replacing it.

This is the file I got for both videos:

```
/proc/2390/fd/28 -> /home/curtis/Videos/
```

Which part of this can or should be edited so each video gets its own file?

Thanks

---

### Post by josephmills on 2012-04-14
> **Curtis6767 said:**
> After viewing video, open Dash, click on Ripper.

Terminal window and small pop-up menu appear.

Click "Ok" to save video.

New pop-up menu appears with location to save video.

Click "Ok" if selected destination is suitable. 

Go to Home/Videos to locate saved video.

Right click to produce drop down menu and select preferred Player.

P.S. Worked fine but would not open in Movie Player or Banshee. Did work with VLC.

Could just be my system.

Very neat little app. Thanks.

Edited to add the following:

The videos do not seem to store in their own file. I viewed and saved two videos but the second video stored on top of the first, replacing it.

This is the file I got for both videos:

```
/proc/2390/fd/28 -> /home/curtis/Videos/
```

Which part of this can or should be edited so each video gets its own file?

Thanks



Wooooaahh that is not good ok I am going to look into that. Thanks a million glad that you like besides the 1st bug.

---

### Post by Curtis6767 on 2012-04-15
Rename the video once it's stored. 

That seems to work.

---

