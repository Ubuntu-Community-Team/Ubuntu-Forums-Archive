---
title: "installing a program not in 'Ubuntu Software' ?"
date: 2019-11-09
forum: New to Ubuntu
---

### Post by grahaml2 on 2019-11-09
How do install a program/app that is not in ‘Ubuntu Software’ shop/store.
 I've downloaded Amok EXIF Sorter (64x Linux version), its unpacked in ‘Downloads’

 I’m running Ubuntu 19.10 desktop.
 Amok renames and moves photos to a file structure, I’ve used Amok to upload photos from a windows comp to my NAS for a number of years if theres a ubuntu alternative I’d like to know
 I am quite new to Linux/Ubuntu so just assume I know nothing – which isn’t far from the truth

---

### Post by howefield on 2019-11-09
Right click on the file named exifsorter.jar and from the permissions tab, check the box to allow executing as program, then right click the same file and select open with Java Runtime...

---

### Post by oldrocker99 on 2019-11-09
To find any Ubuntu program, do this:
```
sudo apt install synaptic
```

Synaptic shows all the software available. It categorizes types of software, and has a search function which looks at the description as well as the filename.

---

### Post by grahaml2 on 2019-11-09
unfortunately i'm still stuck 

> **howefield said:**
> Right click on the file named exifsorter.jar and from the permissions tab, check the box to allow executing as program, then right click the same file and select open with Java Runtime...

have done the first part ok, the second part, I cant find the java runtime, it does not seem to exist ?



when i run  'sudo apt install synaptic' it goes so far through the process then a grey window appears within/over the terminal headed by 'Configuring oracle-java13-installer' with some text and a 'OK' clicking the ok or hitting enter does nothing the grey window stays and appears to block the process ??


:) if it was simple then they'd get monkeys to do it ?? ook ook

---

### Post by mc4man on 2019-11-09
> **grahaml2 said:**
> unfortunately i'm still stuck 



have done the first part ok, the second part, I cant find the java runtime, it does not seem to exist ?


Run
```
sudo apt install default-jre
```

---

### Post by grahaml2 on 2019-11-10
> **mc4man said:**
> Run
```
sudo apt install default-jre
```

did that, went through a in terminal routine which was successful until this (image) popped up, clicking ok does nothing, scrolling to the bottom of the text reveals/does nothing,  there seems to be no way to accept the agreement 
[ATTACH=CONFIG]284376[/ATTACH]

---

### Post by echotech2 on 2019-11-10
Did you try TABbing til OK is highlighted?

---

### Post by grahaml2 on 2019-11-10
[**[COLOR=#000000]echotech2[/COLOR]**]("https://ubuntuforums.org/member.php?u=1842545") 	 
 						
echotech2, your a hero, that worked, Jarva now works and Amok EXIF Sorter runs.

I think I've only once had to use the keyboard tab key to get a Terminal to continue and that was ages ago

---

