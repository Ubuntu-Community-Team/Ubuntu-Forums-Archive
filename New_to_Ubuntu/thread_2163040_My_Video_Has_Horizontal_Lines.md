---
title: "My Video Has Horizontal Lines"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by Smallwheels on 2013-07-16
My video has lines in it as if the player is only reading half of the movie. I attached a thumbnail to this post. Please look at it and let me know how to correct this. Observe the edges of the white sections. It is easiest to see there. 

I have downloaded the restricted extras. I have downloaded the special codecs that allow commercial DVDs to be played. I have played this movie in the VLC player and using XBMC. The images is the same. On my other computer using the same monitor these lines are not present. It shows the whole video. 

There are no special markings on the DVD or its package that indicate technical specifications of the disc. It just has several formats listed, NTSC being one of them. It also says Digitally Mastered. I purchased this DVD. It is not a copy or something downloaded and then put onto a DVD disc. 


Smallwheels

---

### Post by dannyboy79 on 2013-07-17
looks like a deinterlace issue but i am not sure what to tell you to solve the issue. there's progressive scan and interlaced. what player are you using to play the dvd?

---

### Post by MirrorUniverse on 2013-07-17
In VLC, you can go to the Video menu and mess with the Deinterlace and Deinterlace Mode options.  Hopefully one of those settings will help resolve this.

---

### Post by Smallwheels on 2013-07-18
I found this problem in the VLC and XBMC programs. I played with the VLC de-interlace buttons and the lines disappeared. Thank you for your knowledge. 

What exactly does deinterlace mean in the VLC video player?

Next I went to XBMC and couldn't find any ways to adjust the video. Then started paying attention to what XBMC was doing. It was tracking my location and sending me weather information for my area. I have no desire for programs to automatically make such contacts. Doing so tells me it is gathering data from my machine and sending it out on the web. That means it could be reporting about my usage of DVDs and other videos Thus I removed it. So even though I couldn't get it to work it doesn't matter now. 

Thanks again.

---

### Post by MirrorUniverse on 2013-07-31
Before I can explain deinterlacing, I have to explain two other things first.  First is progressive (aka noninterlaced) scanning, which draws all the lines in a frame of video to be displayed in sequence.  The other main method of drawing a frame of video on a monitor is interlaced scanning, where on one pass the even lines are drawn, then a second pass draws the odd lines.  The following I got from wikipedia...
 Deinterlacing is the process of converting interlaced video, such as common analog television signals or 1080i format HDTV signals, into a non-interlaced form.  Most modern displays, such as LCD, DLP and plasma displays,  are not able to work in interlaced mode, because they are  fixed-resolution displays and only support progressive scanning. In  order to display interlaced signal on such displays, the two interlaced  fields must be converted to one progressive frame with a process known as *de-interlacing*.  However, when the two fields taken at different points in time are  re-combined to a full frame displayed at once, visual defects called *interlace artifacts* or *combing* occur with moving objects in the image.
> On my other computer using the same monitor these lines are not present. It shows the whole video. 

That strikes me as strange.  I wonder why one computer would do that and the other would not.  Different software?  As in maybe you used Windows Media Player for one computer and VLC / XMBC on the other?
Edit: By the way, do you remember what setting you changed to get it to work?  Just curious.

---

