---
title: "wallpaper slideshow in xml using monodevelop"
date: 2010-05-16
forum: Programming Talk
---

### Post by Vysakh P on 2010-05-16
I've written a small program to create xml file for wallpaper slideshow in VB.NET (monondevelop) for Ubuntu 10.04. :(Though xml is perfectly created, when I manually add it to my Backgrounds all it shows is a "Image missing" message. I've also written one xml file by hand but this time also the same problem occurs. :-k Please help me.

---

### Post by soltanis on 2010-05-17
How about providing some context? I suggest you start by exercising some basic debugging; if you're doing any exception handling, don't, and run the program from the command line and see what it outputs.

Also, verify that the files your XML refers to actually exist, and that you're correctly parsing the XML (a great way to do this is to print out the filenames you think you've picked out from the XML file and see if they are what you expected).

---

### Post by Vysakh P on 2010-05-17
:)Thank you soltanis for your reply.

:confused:I tried to run the program from command line but it did not showed any errors. I have also printed the file names to console but found no mismatch in filenames.  The markup code below is what my program generated. I have attached the monodevelop solution. Please help me.

```

<background>
  <starttime>
    <year>2010</year>
    <month>5</month>
    <day>17</day>
    <hour>21</hour>
    <minute>51</minute>
    <second>51</second>
  </starttime>
  <static>
    <duration>60</duration>
    <file>/home/vysakh/Desktop/favs/2600.jpg</file>
  </static>
  <transition>
    <duration>5</duration>
    <from>/home/vysakh/Desktop/favs/2600.jpg</from>
    <to>/home/vysakh/Desktop/favs/50282202.jpg</to>
  </transition>
  <static>
    <duration>60</duration>
    <file>/home/vysakh/Desktop/favs/50282202.jpg</file>
  </static>
  <transition>
    <duration>5</duration>
    <from>/home/vysakh/Desktop/favs/50282202.jpg</from>
    <to>/home/vysakh/Desktop/favs/Autumn.jpg</to>
  </transition>
  <static>
    <duration>60</duration>
    <file>/home/vysakh/Desktop/favs/Autumn.jpg</file>
  </static>
  <transition>
    <duration>5</duration>
    <from>/home/vysakh/Desktop/favs/Autumn.jpg</from>
    <to>/home/vysakh/Desktop/favs/BavariaBerchtesgaden.jpg</to>
  </transition>
  <static>
    <duration>60</duration>
    <file>/home/vysakh/Desktop/favs/BavariaBerchtesgaden.jpg</file>
  </static>
  <transition>
    <duration>5</duration>
    <from>/home/vysakh/Desktop/favs/BavariaBerchtesgaden.jpg</from>
    <to>/home/vysakh/Desktop/favs/2600.jpg</to>
  </transition>
</background>
```

---

### Post by soltanis on 2010-05-18
Unfortunately, I don't know anything about Mono. But the files do exist, right? Does your program put the images on the background, or is there some other program that reads your XML file and then modifies the backgrounds?

---

### Post by Vysakh P on 2010-05-18
:)Thank you soltanis again for your quick reply and interest in my problem.

Yes soltanis files do exist. The xml file which I created by modifying 'Cosmos.xml' (replacing pictures with my own favorites) in Ubuntu 10.04 also did'nt work. My program does not change the background itself but the user has to do it manually. So I think, gnome does the job of changing the background if you select the xml file as the background.

---

### Post by soltanis on 2010-05-18
It might be that this functionality is not supported in Gnome.

Try:

[http://www.linuxjournal.com/content/create-custom-transitioning-background-your-gnome-228-desktop](http://www.linuxjournal.com/content/create-custom-transitioning-background-your-gnome-228-desktop)

I assume you already know much of the information in there. In any case, Ubuntu 10.04 runs Gnome 2.30. It is quite possible that the new Gnome has a bug which prevents slideshows from working (but if the Cosmos slideshow works, than probably not). Also, if the show has a specified start time, I would just check to make sure that it is some time in the immediate future of when you ask Gnome to run that file.

By the way, as it turns out this seems to be more of a "Desktop Environments" question than a "Programming" question (not that there was anything wrong with you posting in this section, but the only part about programming I can see you used was to generate the XML, correct?).

---

### Post by Vysakh P on 2010-05-18
:PHi soltanis 

:(Sorry for posting in wrong section. Should I post this in "Desktop Environments" section ?
 
I've visited the link you mentioned in the reply. Thanks for that. I went through the article and as you said I already know most of the things mentioned there (don't know some things too).

Another program to create the xml file is 'XML slideshow creator' available from [http://gtk-apps.org/content/show.php/XML+slideshow+creator?content=119728](http://gtk-apps.org/content/show.php/XML+slideshow+creator?content=119728). This program is very good. I copied the xml file created by this program and modified it (replaced filenames) and found that the new xml file is not working. I've also downloaded the source code for the program and found a shell script doing all the work behind (I don't know shell scripting much but do use Terminal for some small jobs). The UI is written in gambas.  

Please help me to understand things done by the shell script after the xml file is created.

---

### Post by soltanis on 2010-05-18
Have you followed the instructions on the website for making the slideshow your active desktop, i.e. gone to Change Desktop -> Add -> Filter all files -> Select your XML file?

---

### Post by Vysakh P on 2010-05-19
Yes, I have the done it the same way you mentioned, still it is not working..:(

---

### Post by Vysakh P on 2010-05-19
Yes, I have the done it the same way you mentioned, still it is not working..:(

---

### Post by Vysakh P on 2010-05-19
> **soltanis said:**
> Have you followed the instructions on the website for making the slideshow your active desktop, i.e. gone to Change Desktop -> Add -> Filter all files -> Select your XML file?

Yes, I have the done it the same way you mentioned, still it is not  working..:(

---

### Post by soltanis on 2010-05-19
Someone else just posted a gnome slideshow creation script in this forum. Try that script and see if it works. Otherwise, I don't know how else to help you.

---

### Post by Vysakh P on 2010-05-20
Thank you soltanis, thank you very much for your patience and helping me.

---

### Post by Vysakh P on 2010-05-20
Hi soltanis, to my surprise the program is working perfectly when I changed the encoding from UTF8 to ASCII.

Once again thank you soltanis.

---

