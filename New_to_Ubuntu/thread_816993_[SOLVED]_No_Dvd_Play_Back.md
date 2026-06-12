---
title: "[SOLVED] No Dvd Play Back"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by hufferd on 2008-06-03
So I bought a i/o magic DVD burner / cd drive / with light scribe support.  and :( I can not play back DVD's when I try o open a DVD movie with "movie player" - it says can not rear source.  But I have played CD's from this drive and all seems to be ok 

Anyone have any ideas - I check I'm for the most part sure I have all the codec's installed ??? 

:confused:

---

### Post by Kevbert on 2008-06-03
If you go to System-Preferences-Hardware Information you should see your DVD drive if it's IDE. Does it say DVD or just CD ?  If only CD it's likely to be a driver problem.
If your unsure about codecs, you could try setting up [medibuntu]("https://help.ubuntu.com/community/medibuntu") in your software sources if you haven't already.  You need to add:
```
deb http://packages.medibuntu.org/ hardy free non-free 
```
to your /etc/apt/sources.list

---

### Post by hufferd on 2008-06-03
> **Kevbert said:**
> If you go to System-Preferences-Hardware Information you should see your DVD drive if it's IDE. Does it say DVD or just CD ?  If only CD it's likely to be a driver problem.
If your unsure about codecs, you could try setting up [medibuntu]("https://help.ubuntu.com/community/medibuntu") in your software sources if you haven't already.  You need to add:
```
deb http://packages.medibuntu.org/ hardy free non-free 
```
to your /etc/apt/sources.list

Hey thanks for the little bit of info - I'm not at home right now but will try these things when I am :)

---

### Post by neurostu on 2008-06-03
So Ubuntu by default does not ship with non-free software (free as in freedom)  to play dvd's you have to enable certain non-free libraries.

Click on Applications-->Add/Remove: 
From the drop down box select: "All available applications"
Search for "Ubuntu Restricted Extras"

This will then install the dvd playback codecs.

---

### Post by krsna on 2008-06-03
Hello there,

I am facing the same issue, updated the list, downloaded updates and restricted extras, restarted computer and alas! it remains unable to read any DVD.

Any clue?

Thanks.

---

### Post by wolfen69 on 2008-06-03
if you are using Hardy:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
then:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```then:
```
sudo apt-get install libdvdcss2
```
enjoy your movies.

---

### Post by krsna on 2008-06-03
Somebody's rocking in this forum. So what was it i just did which i hadn't done with prior commands?

Thanks again :)

---

### Post by SunnyRabbiera on 2008-06-03
> **krsna said:**
> Somebody's rocking in this forum. So what was it i just did which i hadn't done with prior commands?

Thanks again :)

libdvdcss helps play protected DVD's a little better.

---

### Post by hufferd on 2008-06-03
> **wolfen69 said:**
> if you are using Hardy:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
then:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```then:
```
sudo apt-get install libdvdcss2
```
enjoy your movies.

Wanted to say thank you I now am able to watch DVD's YAY! thank you

I did have one question though -- How would I have learned to do these steps with out asking the question here? 

:confused:

---

### Post by Maestro23 on 2008-06-03
> **hufferd said:**
> Wanted to say thank you I now am able to watch DVD's YAY! thank you

I did have one question though -- How would I have learned to do these steps with out asking the question here? 

:confused:

Medibuntu Repository: [https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu](https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu))

---

