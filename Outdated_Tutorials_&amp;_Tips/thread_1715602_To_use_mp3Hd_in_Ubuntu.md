---
title: "To use mp3Hd in Ubuntu"
date: 2011-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by shantiq on 2011-03-27
_**Mp3HD is a hybrid (lossy and lossless in one file) format designed by [Fraunhofer]("http://www.all4mp3.com/SoftwareHD.aspx")**_


It has no native player in Linux but can can played through Wine with the Fraunhofer player and Winamp with plugin found on their site
**It plays lossy in all players apart from the fraunhofer player and winamp with plugin where it plays lossless and is therefore unique**


**[SIZE="2"]1.[/SIZE]** To [**download**]("http://www.all4mp3.com/Download.aspx?eula=mp3hd_eula.html&file=mp3HD_Toolkit_for_Linux_2010-02-02.zip&name=Linux%20mp3HD%20Toolkit%20for%20v1.5") also zipped and attached   Make sure lame is installed on your system for the lossy part


**[SIZE="2"]2.[/SIZE]** Then open it to your home folder; then need to move it to /usr/bin and make executable this way


```
sudo mv mp3hdEncoder mp3hdDecoder /usr/bin

```

```
cd /usr/bin

```

```
sudo chmod +x mp3hdEncoder mp3hdDecoder

```

**[SIZE="2"]3.[/SIZE]**
run:

```
mp3hdEncoder

```
and accept agreement **important!**

**[SIZE="2"]4.[/SIZE]** run ```
mp3hdEncoder
``` to make sure all is fine and to see options

a good setting is this

```
mp3hdEncoder -br 320000 -if test.wav -of test.mp3
```

**and for bulk** ```
 for f in *.wav; do mp3hdEncoder -br 320000   -if "$f" -of "${f%.wav}.mp3"; done 
```



Gives you a 320kbps lossy and a lossless version (usually in the 900kbps range)


=============================================
**To decode**  ```
 for f in *.mp3; do mp3hdDecoder -if "$f" -of "${f%.mp3}.wav"; done
```


=============================================
    
**Then to the players**


the fraunhofer player is [**on the site**]("http://www.all4mp3.com/Download.aspx?eula=mp3hd_eula.html&file=MP3sPlayerV400.exe&name=Fraunhofer%20mp3HD%20player") as is the winamp plugin


=============================================

**To rip directly to mp3hd you can use Rubyripper with this line of code for the other box**



```
mp3hdEncoder  -br 320000 -if "%i" -of "%o".mp3 - -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g""]mp3hdEncoder  -br 320000 -if "%i" -of "%o".mp3 - -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"
```


More info[ **here**]("http://ubuntuforums.org/showthread.php?t=1533534")


or with **grip**

[CENTER][[IMG]http://img684.imageshack.us/img684/7421/grip1.th.png[/IMG]](http://img684.imageshack.us/img684/7421/grip1.png)  [[IMG]http://img413.imageshack.us/img413/7113/grip2.th.png[/IMG]](http://img413.imageshack.us/img413/7113/grip2.png)[/CENTER]

---

