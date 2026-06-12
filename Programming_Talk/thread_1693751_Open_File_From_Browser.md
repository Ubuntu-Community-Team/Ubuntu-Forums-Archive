---
title: "Open File From Browser"
date: 2011-02-23
forum: Programming Talk
---

### Post by ubuntewb on 2011-02-23
Hey all, new to ubuntu and all things linux, so any help would be appreciated.

I am currently working on a touchscreen kiosk machine that will play videos when selected. I have the video open in VLC and this works fine. the problem I'm having is that when i open the link in firefox it wants to download the file every time.

All of the files are local in /var/www/KioskVideos/

A read somewhere on here that when opening a file from a browser you should use file:// not [http://.](http://.) However when I use "file:///var/www/KioskVideos/video.avi" it doesn't open. 

Is there some apache add on I need to download to allow it to open local files?

Like I said, I'm new to this, so please help if you can!

Thanks

---

### Post by ubuntewb on 2011-02-23
Update: 
I'm using firefox 3.6.13

if you copy file:///var/www/KioskVideos/Videos/test.avi into the address bar the video pops up without downloading and plays fine. 

if that same url file:///var/www/KioskVideos/Videos/test.avi is embeded in a link it does not work at all. Not even a log error. you can try to right click save link as. open in new tab/window. Nothing, no errors, no apache log errors. it's like you clicked on nothing...

very confused by all this.

---

### Post by SeijiSensei on 2011-02-23
If you open the URL file:///var/www/KioskVideos/Videos/, can you click on the listed files and play them?

---

### Post by ubuntewb on 2011-02-23
yes, and it does not download the file it just pops up and plays.

---

### Post by ubuntewb on 2011-02-23
Nevermind, this is an issue with firefox opening a local file is disabled by default with no way to enable it. There is an addon that will allow you to right click on a link to save it, but since my kiosk is touch screen there is no right click. So my project is screwed.

---

### Post by SeijiSensei on 2011-02-24
You could write a little PHP application that uses the passthru() function to play the file.

---

### Post by ubuntewb on 2011-02-25
Fixed! Thank you SeijiSensei for your help the passthru() looked like it would have worked but wasn't exactly what I wanted. I found another way though. 

After looking into it further the solution for me was editing the user profile firefox loads. I added 3 lines of code to user.js to allow access to the local files of a trusted domain. here is the link to the fix I found [http://forums.mozillazine.org/viewtopic.php?f=38&t=1503305](http://forums.mozillazine.org/viewtopic.php?f=38&t=1503305) the lockPrefs worked for me since I'm using firefox 3.6

I hope this helps others out.

---

