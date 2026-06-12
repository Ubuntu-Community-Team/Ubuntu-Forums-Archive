---
title: "catching a proper file from remote server please help.."
date: 2010-01-16
forum: Programming Talk
---

### Post by abhicool1 on 2010-01-16
[FONT=verdana][SIZE=2][COLOR=#000000]I am having a problem to read file from remote url. 
at this stage I have successfully grabbed a video from YouTube and link which is generated is. 
$link =  
// output [http://v14.lscache2.c.youtube.com/videoplayback?ip=0.0.0.0&sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Calgorithm%2Cburst%2Cfactor&fexp=901421%2C900033%2C903105&algor...]("http://www.webmasterworld.com/redirect.cgi?f=88&d=4062281&url=http://v14.lscache2.c.youtube.com/videoplayback?ip=0.0.0.0&sparams=id%2Cexpire%2Cip%2Cipbits%2Citag%2Calgorithm%2Cburst%2Cfactor&fexp=901421%2C900033%2C903105&algor...")

   [/COLOR][/SIZE][/FONT][FONT=verdana][SIZE=2][COLOR=#000000]which offers a file to download video.flv [/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]now my problem is i want to save this file to localhost. 
I have tried using 
[/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]$file1 = file("$link?$QUERY_STRING"); 
$file1 = @implode("", $file1); 
// echo "$file1"; 
 [/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]echo "$file1"; gives raw data of file [/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]FLV &#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533; &#65533; 8..... [/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]Now, I want to save it on my local drive so that i can convert it by using FFMPEG [/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]I have tried..  [/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]$fh = fopen("testvideo.flv", "w"); 
fwrite($fh, $file1); 
fclose($fh); [/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]but unable to write data into file. File remains blank after execuation of code. [/COLOR][/SIZE][/FONT]
[FONT=verdana][SIZE=2][COLOR=#000000]Please help me.  [/COLOR][/SIZE][/FONT]

---

### Post by matchett808 on 2010-01-17
try passing the downloading to a bash file to do a wget?

!#/bin/bash
wget $1

is all you really need (check the first line though, i cant remember wether the # or the ! comes first! lol)

---

### Post by Hellkeepa on 2010-01-17
HELLo!

First of all, "file ()" and "implode ()" is unnecessary, should have used "file_get_contents ()" instead. Even better would have been to use cURL or similar, since the file methods are often blocked from doing HTTP calls.
Similarly "file_put_contents ()" will open a (new) file, and write the data to it, before closing it again. Doing away with two lines of code. Do make sure that you have write-permissions to the folder you're trying to save the files to though, as I suspect this is the culprit. You don't do any testing on this, nor on whether or not the write was successful, after all.

Happy codin'!

---

