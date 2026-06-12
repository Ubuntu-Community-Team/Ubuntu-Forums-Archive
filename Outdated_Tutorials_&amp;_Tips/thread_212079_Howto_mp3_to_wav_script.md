---
title: "Howto: mp3 to wav script"
date: 2006-07-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Thund3rstruck on 2006-07-09
I'm sure there is something out there that does this already but I make a lot of CDs and because of this a needed a very quick method for batch converting .mp3 files to .wavs, to be burned to CDR. 

This script will loop through all the files in the folder you specify and convert them from .mp3 to .wav

copy the following code and save it in a file mp32wav.sh 

```

#!/bin/bash
#Script: mp32wav script (requires mpg123 package)
#Purpose: Loops through a path and convert all the mp3s to wavs
#
#usage: mp32wav [Path]

count=0

Convert(){
mpg123 -b 10000 -s "$x" | sox -t raw -r 44100 -s -w -c2 - "`sed s/mp3/wav/ sedEdit`"
}

syntax_error(){
clear
echo "Mp32Wav - Convert Mp3 Files To Wav Files"
echo "script syntax: mp32Wav <path>"
echo ""
exit 0
}

if [ -n "$1" ]; then
   cd "$1"
   for x in *.mp3
	do
	let "count += 1"
          echo "$x" > sedEdit
	  Convert
	done
else
	syntax_error
fi
echo "$count mp3s found and converted to wavs... [Baileysoft 2005]"
rm sedEdit
exit 0


```

1. install mpg123
```

sudo apt-get -y install mpg123

```
2. make the file executable
```

chmod +x mp32wav.sh

```
3. copy to /usr/bin
```

sudo cp mp32wav.sh /usr/bin/mp32wav

```

**Usage:**
mp32wav <path>

example: mp32wav /tmp/mp3 
Converts all the mp3s in /tmp/mp3 to wavs

example: mp32wav `pwd`
converts all mp3s in your current directory to wavs

---

### Post by gorilla_king on 2006-07-09
wow, thanks man, that's pretty cool. I usually make mp3 cd's because of my cd player in car can handle mp3's but that's great. Now i can use the normal cd writer for when i need to make real cd's. Thanks. And could i get permission to offer thie bash file on my site with your name and webaddress/email with it? Thanks. Keep up the awesome work.

---

### Post by chajuram on 2006-07-09
Hi,

There is an app called audio-convert, which I think does similar things please see [http://www.ubuntuforums.org/showthread.php?t=82806&highlight=audio-convert]("http://www.ubuntuforums.org/showthread.php?t=82806&highlight=audio-convert")

Chajuram.

---

### Post by Thund3rstruck on 2006-07-09
@gorilla_king,

 Feel free to use it however you want, and/or improve on it. I was thinking of adding a segment in it as well to call cdrecord as well so it would convert the files and burn them automatically. 

@chajuram,

 As I said in the article, I'm sure there are a ton of ways to acheive this. I just wanted something small, simple, and fast. 

 
 I find myself, making CDs all the time so for me the easiest way is to copy the mp3s into a specific folder (albumName) and run the script against the folder. In a matter of seconds I have wav files ready to be burned to traditional CDs (the ones that will play in any car).

---

### Post by gorilla_king on 2006-07-09
> **Thund3rstruck said:**
> @gorilla_king,

 Feel free to use it however you want, and/or improve on it. I was thinking of adding a segment in it as well to call cdrecord as well so it would convert the files and burn them automatically. 


Alright i'll add it later, thank you.

---

### Post by Lucho77 on 2006-08-08
Hey, thanks for this nice 'How to' I followed all the steps and everything seems to be ok, but when I executed the script said;
/usr/bin/mp32wav: line 10: sox: command not found
Could you please tell me what should I do now?

---

### Post by agc on 2006-08-09
Sox is a program that translates sound files
from one type to another.

Just type:

```
sudo apt-get install sox
```

and you will install sox.

---

### Post by Lucho77 on 2006-08-09
'agc' thank you so much, now it is working like a charm.

---

### Post by colourful-leaves on 2009-02-26
hallo @ all

I use K3b on Ubuntu 8.10
i installt

apt-get install libk3b3-extracodecs

and? 
it works

g.
richy
:guitar:
[www.colourful-leaves.de](www.colourful-leaves.de)

---

### Post by dirkjot on 2011-04-22
Ancient thread, but this is still a top google hit so therefore:

On any recent ubuntu version, there is a simple add-in for sox that does this in a completely painless way. Simply add libsox-fmt-mp3 to your installed packages via Aptitude or whatever you use. Or, in a terminal, type:

  sudo apt-get install libsox-fmt-mp3


Best,
Dirk

---

