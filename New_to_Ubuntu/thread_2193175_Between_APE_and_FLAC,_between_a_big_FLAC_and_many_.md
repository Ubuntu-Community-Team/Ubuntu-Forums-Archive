---
title: "Between APE and FLAC, between a big FLAC and many small ones... falls the shadow"
date: 2013-12-11
forum: New to Ubuntu
---

### Post by IterViator on 2013-12-11
Hi guys, I'm new to Ubuntu. 

Hi happily converted APE to Flac with dbpoweramp and xrecode on windows for years, and I happily split many FLAC albums by using CUESPLITTER.

Now that I'm on Ubuntu (Lubuntu 13.04) all this seem impossible. I've tried soundconverter but it didn't work. And I've tried a few command line procedures, but those didn't work too.

Can you help a poor audiophile? Note that I'm a total newbie, so I need you to explain to me even the simplest and most obvious passages.

Thanks in advance! Rock on.

---

### Post by neural_adapter on 2013-12-11
I am only familiar with command line tools. 

I have used [shntool]("http://www.etree.org/shnutils/shntool/") to split files and convert.

---

### Post by IterViator on 2013-12-12
> **neural_adapter said:**
> I am only familiar with command line tools. 

I have used [shntool]("http://www.etree.org/shnutils/shntool/") to split files and convert.

I downloaded shntool from Synaptic, and I successfully splitted and converted a large FLAC file with the help of this guide [https://wiki.archlinux.org/index.php/APE%2BCUE_Splitting](https://wiki.archlinux.org/index.php/APE%2BCUE_Splitting)
But I couldn't get cuetools to tag my flacs.

The terminal tells me: cuetag.sh: command not found

---

### Post by coffeecat on 2013-12-12
For splitting up flac files, have a look at Audacity - it's in the repository. It's a fairly comprehensive audio editor, with possibly much more than you want, but at least it's a gui app and it can both split and convert.

Another two gui apps you might find useful are soundconverter (fairly obvious what that does!) and sound-juicer, a CD ripper. Both in the repositories and installable via Synaptic or Software Centre.

I thought ape was a type of metadata tag, so I'm not quite sure what you mean by converting ape to flac. If you need audio file tag editors there are several in the repos.

---

### Post by Bucky Ball on 2013-12-12
Audacity is your friend. The swiss army knife of audio. Cross platform, used by both general users and professionals. ;)

---

### Post by IterViator on 2013-12-12
I always used Audacity just to record things. Can it tag my music by using cuesheets?

---

