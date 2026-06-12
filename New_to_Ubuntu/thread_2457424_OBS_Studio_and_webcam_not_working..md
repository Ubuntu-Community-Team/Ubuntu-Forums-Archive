---
title: "OBS Studio and webcam not working."
date: 2021-02-01
forum: New to Ubuntu
---

### Post by oldnew1786 on 2021-02-01
Hi.

I am super new to Ubuntu, like really new. Like just installed it on Saturday night (2 days ago) new. I run a YouTube channel and I can't use my  regular things I use for making videos. OBS seems to be the best option  along with Shortcut which I plan to use.

I have no idea how to use this stuff. I have been searching all over and  can't find a fix. My problem isn't that I can't select V4L2 in the source section, but that I  have no picture at all even when I have it selected. I tried recording,  but I still get no picture and don't know where to find my video  recordings so I can't check with another program to see if my recording  works or not. I think my audio works fine, but it's a little low. So if  someone knows how I can actually view what I am recording and also how  to turn my mic up that would be awesome.

My webcam is: PC Webcam for Streaming HD 1080P, Vitade 960A USB Pro  Computer Web Camera Video Cam for Mac Windows Laptop Conferencing Gaming  with Microphone & Ring Light
My mic is: USB Microphone Kit 192KHZ/24BIT MAONO AU-A04T PC Condenser  Podcast Streaming Cardioid Mic Plug & Play for Computer, YouTube,  Gaming Recording

Thanks to anyone willing to help a complete newb out.

UPDATE: I was able to see my webcam works with cheese but I still can't see anything in OBS Studio
UPDATE: I found out there was more installing to do before it can work. I ran this "sudo apt install v4l-utils v4l2loopback-dkms v4l2loopback-utils"
But now I have to run this "v4l2loopback-utils" but it say "v4l2loopback-utils: command not found"

What should I do next?

---

### Post by oldnew1786 on 2021-02-02
UPDATE: I was trying to follow the directions here: [https://github.com/CatxFish/obs-v4l2sink/issues/54](https://github.com/CatxFish/obs-v4l2sink/issues/54)

I got to this step: sudo apt-get install libobs-dev
And I got this message: "E: Unable to correct problems, you have held broken packages."

UPDATE: I ran this command: "sudo dpkg - obs-4l2sink.deb"
And got this message: "dpkg: error: need an action option"

What should I do?

---

### Post by oldnew1786 on 2021-02-03
I ended up doing a dual boot with two drives. One for windows one for Ubuntu. That way I can still do my videos.

---

### Post by oldnew1786 on 2021-02-05
I figured out the problem but I don't know how to solve it. The problem is that v4l2 is trying to open two /dev/video0 to the applications (vlc/obs) so because there is a conflict, there is no image since the application doesn't know which one to read from so it cancels both. I tried searching for this and I found a solution somewhere in my search, but it is long gone at this point.

So if someone, anyone can tell me how to change the 4v2l to read only one "/dev/video0" that would be great. I might have to reconfigure some things because IDK what I messed up to make it do that, I was doing a lot of stuff in the process like trying to add plugins and such, but it is what is is.

Update: here is one of the videos I was watching. IDK if this helps or not with this. It was a little too complicated for me since I kept getting error messages and didn't know how to enable the deb file thing: [https://youtu.be/jIzESpHx0vg](https://youtu.be/jIzESpHx0vg)
Update: I have two separate options that are identical for OBS Studios>Tools>v4l2sink

---

