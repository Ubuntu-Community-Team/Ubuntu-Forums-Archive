---
title: "I need English Talknig Dictionary (pronounciation)"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by medya on 2008-09-18
Hi Guys , I am an English teacher I need a program in ubuntu which pronounces English words for me .


there are several dictionaries for Ubuntu but they are not Talking (pronouncing words)

can you help me to find one?

---

### Post by Titan8990 on 2008-09-18
I believe that dictionary.com has this functionality if you are using a computer with internet access.

---

### Post by medya on 2008-09-18
I need something without internet need .

---

### Post by prshah on 2008-09-18
> **medya said:**
> Hi Guys , I am an English teacher I need a program in ubuntu which pronounces English words for me .


espeak is a ubuntu text-to-speech program, but it's not 100% correct (odd accent, but fine phonetic wise.) You can use it without need for Internet (except for the installation). Try it: Open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo apt-get install espeak espeak-data
``` Then to use espeak, (continuing in the terminal) give the command ```
espeak -s 100 "This is a test"
``` (The "-s" adjusts speed)

---

### Post by medya on 2008-09-18
intresting is there any gui front end for it ?

---

### Post by medya on 2008-09-18
but still I need a reall talking dictionary, it is such a shame that we dont have it in linux world.

---

### Post by lian1238 on 2008-09-18
What did you use in Windows before? Maybe you can use wine to install it?

(By the way, it's not pronounciation.. it's pronunciation. I used to make that mistake too.) ;)

---

### Post by C.S.Cameron on 2008-09-18
Could you not download something like dict-gcide and have espeak read it?

and have you checked out:

stardict-plugin-espeak?

International dictionary - eSpeak TTS plugin
StarDict is a cross-platform and international written in GTK+ 2.x.
It has powerful features such as "Glob-style pattern matching",
"Scan selection word", "Fuzzy search", etc.

This package contains eSpeak TTS plugin for StarDict which can
pronounce words.

You can find this with synaptic.

---

### Post by medya on 2008-09-18
yeah I already know about starDict, the bad thing about espeak is, u need to close any music player. or it wont pronounce

---

### Post by C.S.Cameron on 2008-09-18
I understand opendict uses festival TTS,
and it has a Turkish-English dictionary

---

### Post by Grimhound on 2008-09-18
I'm currently just looking for a good expansive dictionary that holds info on the computer rather than needing to parley with a web server. @.@

---

### Post by medya on 2008-09-18
I cant speak turkish ;) I just need english word pronounciations :D

---

### Post by Rany . on 2009-06-08
Hello, I am using stardict. When I push the pronounce button, nothing happens, only when I choose Espeak TTS, there are sound coming out. The other 2, Festival TTS & Command TTS, nothing comes out. As for Espeak, only partial sound. Example if I type "Going", the sound came out as "Go", or "ding". Oce in 5 tries or so, it pronounces the whole word "Going".
Anyone knows what is causing this, or how to ix this?

Thanks.

---

### Post by LowSky on 2009-06-08
> **medya said:**
> intresting is there any gui front end for it ?

sort of, screenlets (in the repos), which is a desktop widget program does offer a desktop entry box, basically a type a word and hear it, very basic.

---

### Post by durand on 2009-06-08
If you upgrade to a newer version of ubuntu, the sound problem will go away.

---

### Post by kwacka on 2009-06-08
Medya, try 'Festival' - its in the repositories.

You can see the manual here:[link to Festival manual]("http://www.cstr.ed.ac.uk/projects/festival/manual/")

---

### Post by Rany . on 2009-06-08
It worked after I added a couple of dictionaries. :)

---

