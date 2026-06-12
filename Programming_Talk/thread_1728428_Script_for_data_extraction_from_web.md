---
title: "Script for data extraction from web"
date: 2011-04-13
forum: Programming Talk
---

### Post by hyperAura on 2011-04-13
Hi guys, 

I need to extract information from several websites in order to analyse them further but it needs to be done fast (approximately every 30 seconds).

What do you suggest as the best language to use in order to do the download and parsing of these files?

thanks

---

### Post by Some Penguin on 2011-04-13
There's still a very, very current thread on the same basic question.

[http://ubuntuforums.org/showthread.php?t=1728258]("http://ubuntuforums.org/showthread.php?t=1728258")

---

### Post by DaithiF on 2011-04-14
whatever language you know and are comfortable with.  The use-case isn't so specific that the choice of language will matter much.

If you're starting out with programming then probably python is a good place to start.  in particular look at the beautifulsoup module when you get to the parsing bit.

---

### Post by hyperAura on 2011-04-14
@Some Penguin: I read the description of the other thread before posting mine and I though that mine was more like a general question compared to that question.

Anyway I know java and c but some people told me that scripting languages are much faster in doing these kind of work and since I am designing a new application which is completely based on the data that are going to be extracted, I want this bit to be as efficient as possible.

Thanks for the reply DaithiF, python has been recommended by other people from my work environment so it should be a good choice.

---

### Post by DaithiF on 2011-04-14
> **hyperAura said:**
> Anyway I know java and c but some people told me that scripting languages are much faster in doing these kind of work and since I am designing a new application which is completely based on the data that are going to be extracted, I want this bit to be as efficient as possible.

They don't mean execution time though (or if they do then they are wrong! :) )  They probably mean that time to **develop **the application tends to be quicker with a language like python / perl than something like java or C.  But that depends entirely on how familiar you are with the language.  If its your first time using python but you've programmed java for years then you will be much quicker writing it in java.

---

### Post by Some Penguin on 2011-04-14
With a crawl, most of the time spent would normally be on (1) network traffic, or (2) persistent storage (whether it be to a relational database, key-value store or other).   Neither is particularly language-dependent.  Some languages might have better support for building massively parallel distributed crawlers, but other than that?  You shouldn't see much difference at all.

---

### Post by hyperAura on 2011-04-14
Thanks for your answers guys. Guess the rumors are wrong then.. :)

---

