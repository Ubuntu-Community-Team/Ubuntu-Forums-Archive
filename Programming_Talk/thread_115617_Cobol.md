---
title: "Cobol"
date: 2006-01-10
forum: Programming Talk
---

### Post by otake-tux on 2006-01-10
I have to learn cobol.  I know what you are going to say.  Probably something like what Dijkstra  said "The use of COBOL cripples the mind; its teaching should, therefore, be regarded as a criminal offence."

But aparently [75% of business data is processed in COBOL]("http://www.networkworld.com/columnists/2003/1020edit.html")

So my college is teaching it.  Who knows, my first job might be as a cobol programmer (its pretty big where I live).

Anyway I'm looking for a linux COBOL compiler.  I found [open-cobol]("http://www.opencobol.org/modules/bwiki/index.php?InstallGuide")
But this aparently converts COBOL code to C code and then compiles it.  I dont know if this is very compatible with what my proffesor will be using to grade my projects so I'm asking if any of you guys know of any other COBOL compiler or know anything about this one.  I dont want to have to use windows to program in COBOL so plz help me.

---

### Post by noob_Lance on 2006-01-10
thats awsome that you posted this... im going to be switching over from web dev to software eng next week at my college... and in software... we will be learing Cobol... and i was thinking about the same this you are... any programs to compile :p

---

### Post by otake-tux on 2006-01-10
cool maybe we can help each other.  tomorrow Im going to try to compile that open-cobol.  If not ny tomorrow then definetly on thursday.  Ill post and let you know how it goes.

If you ever need anyhelp, feel free to ask.

---

### Post by noob_Lance on 2006-01-11
where the hell can i go and find tut's for cobol lol i have never even seen what the syntax or anything even looks like.... ive never even used a program that even used cobol in the least lol

---

### Post by otake-tux on 2006-01-11
COBOL is not popular in the linux world.  It still is , somehow, popular though. Click on the link I provided in the first post to see.
this is hello world in cobol:
```
IDENTIFICATION DIVISION.
         Program-Id. Hello-World.
      *
       ENVIRONMENT DIVISION.
      *
       DATA DIVISION.
      *
       PROCEDURE DIVISION.
       Para1.
           DISPLAY "Hello, world.".
      *
           Stop Run.
```
[tutorial]("http://www.csis.ul.ie/cobol/default.htm")

---

### Post by otake-tux on 2006-01-12
Okay, I finished installing a COBOL compiler.  I installed the tinycobol compilor, if any of you guys know of a better one plz let me know.

If you're interested in the compilor you can get a deb package [here]("http://rpmseek.com/rpm-dl/tinycobol_0.61-1_i386.html?hl=com&cs=tiny:PN:0:0:0:0:1612545")

then run ```
sudo dpkg -i  tinycobol_0.61-1_i386.deb 
```
there probably will be missing dependancies.  Use synaptic or apt-cache search to find them and install them.

---

### Post by fahad on 2006-02-19
i downloaded the tinycobol package and its in my sys now,
but there is no such htcobol command in my system !?

bash: htcobol: command not found

---

### Post by wmcbrine on 2006-02-19
Just because it compiles to C instead of native code, I wouldn't hold that against it. But beyond that, I'm not qualified to comment.

Here are some others:

[http://www.thefreecountry.com/compilers/cobol.shtml](http://www.thefreecountry.com/compilers/cobol.shtml)

---

### Post by Moonbuzz on 2006-04-26
I found tinyCobol to be excellent. It doesn't have some of the more advanced features, as it supports only the 85 standard, and it compiles to GCC assembly (which might be a blessing in disguise if you know your GCC-fu).

You might want to try [this repository]("http://paginas.terra.com.br/informatica/bau/debian/pacote/tinycobol/"), it's the latest version, and you can simply add it to your sources.list and install it via synaptic.

---

### Post by adssse on 2006-05-07
I used the given repository, updated and installed tinycobol without any problems. I then wrote a little hello world program to test it and saved it as hello.cob. I used the command 'htcobol hello.cob' but all I got was 'sh: as: command not found'. I was wondering if anyone who has used this could provide some help. I have verified that tinycobol installed by using 'htcobol -V' and the man pages and help all work fine, but I was unable to find an answer there. Any help would be appreciated.

---

### Post by adssse on 2006-05-09
It was my own mistake, by doing 'sudo apt-get install build-essential' it seems to have taken care of everything else I needed. Thanks to those above for bringing tinycobol to my attention.

---

### Post by stansaraczewski on 2006-07-28
It's fun to read the cobol slams here - but the first post said it all - about how many businesses still use cobol. 

There is a significant investment required in converting these programs... and if they still perform the function that they were intended to 25 years ago why would a business convert them ?

Someone please explain...

---

### Post by stansaraczewski on 2006-07-28
pls remove

---

### Post by adssse on 2006-07-30
I agree, cobol is still very usefull in todays world. I recently took a job at an insurance company that uses cobol as its backend and java as a frontend. I never had used cobol before but have found that it works very well for the needs of this industry. I was very glad to find tinycobol so that I could play around with cobol while using ubuntu.

---

### Post by stansaraczewski on 2006-07-30
It's refreshing to read your positive comments. :D

---

### Post by stansaraczewski on 2006-12-16
Oops - wrong thread... please delete...  thank you...

---

