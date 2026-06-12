---
title: "HOW To :download videos from youtube ( new script and GUI 100% working )"
date: 2007-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by @vijay@ on 2007-08-07
**_Here is a simple script i made to download videos from youtube _**

before i used to use the script youtube-dl from [http://www.arrakis.es/~rggi3/youtube-dl/](http://www.arrakis.es/~rggi3/youtube-dl/)
but its not working for me anymore (but may be its because im behind proxy server) so i decided to make my own :lolflag:
This is similar to unplug plugin for firefox 

**IT DEPENDS ON WGET AND ELINKS** :popcorn:

:) This is how it works 
1) download the source code of the youtube webpage link using elinks
2) then searches for the link from which the video stream is coming 
3) then downloads it

usage of the script:
[B]sudo chmod +x ./download.sh
./download.sh [www.youtube.com/_____](www.youtube.com/_____)[/B]

the videos will be downloaded in the same directory
--------------------------------------------------------------------------------------------

I MADE A GUI OF THE PROGRAM ALSO ( **THIS IS MY FIRST GTK APPLICATION** )
**im learning how to program in gtk+ at present**

u can just add a list of files to the gui and keep it running overnight
U can change the download name (rename)
The files are downloaded to ~/youtube directory

**_i faced many problem while making the gui , and was unable to solve ; _****hopefully someone here will solve it**
1) unable to make the list view widget scrollable
2) unable to show the progress of the download in the application itself; so used ZENITY to indicate the progress of the download
3) when i click cancel in the ZENITY the process is not quitting

To install the application:        :guitar:
[B]1) extract the tar.gz file 
2) cd to the directory
3) sudo chmod +x install.sh
4) sudo ./install.sh[/B]

for uninstalling ........ in the same directory  
[B]1) sudo chmod +x uninstall.sh
2) sudo ./uninstall.sh[/B]
------------------------------------------------------------------------------------------
i have uploaded the source code of the gui also ;** U can  modify the source and plz post the modified one here ; and explain the probs _so that i can also learn about gtk+ and c programming_ **

SCREENSHOTS:uploaded

---

### Post by @vijay@ on 2007-08-08
just added the screenshots

---

### Post by sad_iq on 2007-08-25
The script doesn't work for me :( Haven't tried the GUI yet!!!
```
./download.sh http://youtube.com/watch?v=2BCoZiSbGtY
/home/sadiq/youtube/hello.flv: No such file or directory

```
A progress bar appears but no progress...after an hour I have to hit cancel.

---

### Post by matio on 2007-08-25
This is a fantastic program! Did you use monodevelop? I can't seem to use GTK# with monodevelop!

---

