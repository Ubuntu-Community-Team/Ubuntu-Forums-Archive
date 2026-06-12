---
title: "View .odt files Within Terminal"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by theoreo25 on 2011-09-27
Hi guys,
I've been using linuxcommand.org to try to teach myself the command line. I like the "less" command but it isn't that useful since almost all of my text documents are saved in .odt. Is there away that i can view .odt like "less" lets you view ASCII?

Thank You

---

### Post by Tom Collier on 2011-09-27
> **theoreo25 said:**
> Hi guys,
I've been using linuxcommand.org to try to teach myself the command line. I like the "less" command but it isn't that useful since almost all of my text documents are saved in .odt. Is there away that i can view .odt like "less" lets you view ASCII?

Thank You
Um...I don't think .odt files are ASCII. It (.odt) is the file extension for OpenOffice Writer template documents.

---

### Post by haqking on 2011-09-27
> **theoreo25 said:**
> Hi guys,
I've been using linuxcommand.org to try to teach myself the command line. I like the "less" command but it isn't that useful since almost all of my text documents are saved in .odt. Is there away that i can view .odt like "less" lets you view ASCII?

Thank You

if you want to view office docs from terminal with text editors then save them as text files.

cat
less
more
vi
nano

etc.... will open them and view them, .odt is meant to and often does contain extra information which though the above commands will view them it will be a garbled mess ;-)

---

### Post by theoreo25 on 2011-09-27
> **Tom Collier said:**
> Um...I don't think .odt files are ASCII. It (.odt) is the file extension for OpenOffice Writer template documents.

i know that .odt isn't ASCII but i was hopping that maybe there was some sort of command that i could install that would allow terminal to view .odt. like if you want the command "htop" you just download it and it works within the terminal.

---

### Post by haqking on 2011-09-27
> **theoreo25 said:**
> i know that .odt isn't ASCII but i was hopping that maybe there was some sort of command that i could install that would allow terminal to view .odt. like if you want the command "htop" you just download it and it works within the terminal.

it is designed to work with open office or libreoffice and its variants.

Not everything can work in a terminal

---

### Post by Vaphell on 2011-09-27
.od* formats are just zip files with a bunch of xml files inside. You can unzip them and look into xmls in cli, but xml is not exactly easy on eyes.

---

### Post by haqking on 2011-09-27
> **Vaphell said:**
> .od* formats are just zip files with a bunch of xml files inside. You can unzip them and look into xmls in cli, but xml is not exactly easy on eyes.

ha yeah good point.

you could extract and then

```
less content.xml

```
i think thats the file, but its gonna have all the mark up in it and wont be easy to read

---

### Post by martelo on 2013-03-10
If anyone still cares about this question, the command is [FONT=courier new]odt2txt --stdout some_file.odt[/FONT]

---

### Post by overdrank on 2013-03-10
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

