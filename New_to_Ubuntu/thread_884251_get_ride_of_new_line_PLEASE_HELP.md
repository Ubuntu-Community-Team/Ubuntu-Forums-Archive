---
title: "get ride of new line PLEASE HELP"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by just_linux on 2008-08-08
ok here:
I have a list of addresses I want to download. and I wrote a code to download them all. 
 
But for some reason, when the program reads the ta=ext from the fil, it will include "\n" new line too. 
So how should I get ride of the new line thing 
here is the code: I print it too so you see it :popcorn:
```

	
		# Now read to download:
		while [ $i -gt 0 ]
		do
		let i-=1
		echo -n "Here is what I have in the URL  : "
		echo ${ready[$i]}
		axel ${ready[$i]}
		done
	


```
:guitar:
here is the respond (I run it and then I copy there address myself and run it ):
[HTML]
[COLOR="Red"]Here is what I have in the URL  : http://61.152.95.185/Sarzaminmusic/Persian/128KB/Mehrshad%20-%20Cheshmak/02_%20Ashegho%20Mashoogh.mp3
Initializing download: http://61.152.95.185/Sarzaminmusic/Persian/128KB/Mehrshad%20-%20Cheshmak/02_%20Ashegho%20Mashoogh.mp3
HTTP/1.1 400 Bad Request[/COLOR]
joseph@joseph-desktop:~/Desktop$ [COLOR="DarkOliveGreen"]axel  http://61.152.95.185/Sarzaminmusic/Persian/128KB/Mehrshad%20-%20Cheshmak/02_%20Ashegho%20Mashoogh.mp3
Initializing download: [/COLOR]http://61.152.95.185/Sarzaminmusic/Persian/128KB/Mehrshad%20-%20Cheshmak/02_%20Ashegho%20Mashoogh.mp3
File size: 3214568 bytes
Opening output file 02_ Ashegho Mashoogh.mp3
Starting download

[  0%]  .......... .......... .......... .......... ..........  [  52.3KB/s]
[  1%]  .......... .......... .......... .......... ..........  [  74.0KB/s]
[  3%]  .......... .......... .......... .......... ..........  [  70.4KB/s]
[  4%]  .......... .......... .......... .......... ..........  [  72.2KB/s]
[  6%]  .......... .......... .......... .......... ..........  [  74.7KB/s]
[  7%]  .......... .......... .......... .......... ..........  [  81.2KB/s]
[  9%]  .......... .......... .......... .......... ..........  [  40.2KB/s]



[/HTML]:lolflag:

here is the respond (I run it and then I copy there address myself and run it ):

[COLOR="Red"]Here is what I have in the URL  : [http://61.152.95.185/Sarzaminmusic/Persian/128KB/Mehrshad%20-%20Cheshmak/02_%20Ashegho%20Mashoogh.mp3](http://61.152.95.185/Sarzaminmusic/Persian/128KB/Mehrshad%20-%20Cheshmak/02_%20Ashegho%20Mashoogh.mp3)
Initializing download: [http://61.152.95.185/Sarzaminmusic/Persian/128KB/Mehrshad%20-%20Cheshmak/02_%20Ashegho%20Mashoogh.mp3](http://61.152.95.185/Sarzaminmusic/Persian/128KB/Mehrshad%20-%20Cheshmak/02_%20Ashegho%20Mashoogh.mp3)
HTTP/1.1 400 Bad Request[/COLOR]
joseph@joseph-desktop:~/Desktop$ [COLOR="DarkOliveGreen"]axel  [http://61.152.95.185/Sarzaminmusic/Persian/128KB/Mehrshad%20-%20Cheshmak/02_%20Ashegho%20Mashoogh.mp3](http://61.152.95.185/Sarzaminmusic/Persian/128KB/Mehrshad%20-%20Cheshmak/02_%20Ashegho%20Mashoogh.mp3)
Initializing download: [/COLOR]http://61.152.95.185/Sarzaminmusic/Persian/128KB/Mehrshad%20-%20Cheshmak/02_%20Ashegho%20Mashoogh.mp3
File size: 3214568 bytes
Opening output file 02_ Ashegho Mashoogh.mp3
Starting download

[  0%]  .......... .......... .......... .......... ..........  [  52.3KB/s]
[  1%]  .......... .......... .......... .......... ..........  [  74.0KB/s]
[  3%]  .......... .......... .......... .......... ..........  [  70.4KB/s]
[  4%]  .......... .......... .......... .......... ..........  [  72.2KB/s]
[  6%]  .......... .......... .......... .......... ..........  [  74.7KB/s]
[  7%]  .......... .......... .......... .......... ..........  [  81.2KB/s]
[  9%]  .......... .......... .......... .......... ..........  [  40.2KB/s]



:lolflag:

---

