---
title: "Estetiikka - new open source web-gallery"
date: 2007-03-01
forum: Programming Talk
---

### Post by Laterix on 2007-03-01
Hi there!

I just finished the first relase of my Estetiikka web-gallery. It's implemented with PHP and MySQL. I'm looking for people who are interested to translate it for foreign languages. Also new themes would be great! Both are easily created...

[Check out my gallery ]("http://www.taimila.com/estetiikka")and tell me what you think! Of course programming help is always appriciated too. ;)

[IMG]http://users.utu.fi/ljtaim/pics/estetiikka.png[/IMG]

---

### Post by kthakore on 2007-03-01
cool application, are there any other features you want to add to estetiikka, I would like to offer my services.

---

### Post by Laterix on 2007-03-02
> **kthakore said:**
> cool application, are there any other features you want to add to estetiikka, I would like to offer my services.

Thanks, well the layout doesn't work exactly the way it should be with IE, but since we are on the Ubuntu forums, I doubt that you are intrested in to fix that kind of thing. Because even I'm not :)

Uploading photos could support PNG and GIF files, but this is pretty trivial to add with few IFs.

Hmm... I can't think of anything big at the moment. Do you have any ideas?

---

### Post by Mirrorball on 2007-03-02
Is there a demo somewhere?

---

### Post by Laterix on 2007-03-03
> **Mirrorball said:**
> Is there a demo somewhere?
Sorry. I can't provide demo version online. :(

---

### Post by Paul41 on 2007-03-03
I am trying it now, but am getting error when I use it. I am looking to see if I can find what is causing the errors. I am also making notes of the errors so I will send them to you if you want.

---

### Post by gvoima on 2007-03-03
nice job there with the gallery :)

I'm pleased to see "kotimaisia" fellow programmers here, that makes a nice job with their release ^^

---

### Post by kthakore on 2007-03-03
which IE doesn't it work on?
also what doesn't work?
6 or 7.
also try a DTD strict to get it IE 6 and 7 to work like firefox 1.5 (for the most part), but since  you developed the design without the DTD you might have a conflict if you implement it now. 


for uplaoding png and .gif, I can do that easy. Check out the demo on my server. 

[http://74.110.2.25/www/WIP/estetiikka/index.php]("http://74.110.2.25/www/WIP/estetiikka/index.php")

---

### Post by Paul41 on 2007-03-03
> **Paul41 said:**
> I am trying it now, but am getting error when I use it. I am looking to see if I can find what is causing the errors. I am also making notes of the errors so I will send them to you if you want.

I got it all worked out now. I had to add the php5-gd package and also give full permissions to the "album_thumbs", "photos", "themes", and "thumbs" folders.

---

### Post by azazel00 on 2007-03-03
You got yourself a spanish translator if you want me. :P

I'll be downloading it later today. Do you have resource files with the text strings?

Regards,
az

Edit: Sorry, hadn't seen the 'Translate' button....

---

### Post by Laterix on 2007-03-04
> 
I'm pleased to see "kotimaisia" fellow programmers here, that makes a nice job with their release

Kiitos!

> 
which IE doesn't it work on?
also what doesn't work?
6 or 7.
also try a DTD strict to get it IE 6 and 7 to work like firefox 1.5 (for the most part), but since you developed the design without the DTD you might have a conflict if you implement it now.

I have tested it only with IE version 7. There are only small placement problems with some layout elements, but the biggest problem is that in IE there is no "Album selector" dropdown list on thumbnails view page. Also adding smileys to comments doesn't seem to work, probably because I'm not very good with JavaScript.

> 
for uplaoding png and .gif, I can do that easy. Check out the demo on my server.

How can I login? Anyway, I know that adding support for those formats is really easy. I just was lazy when I wrote that upload script. ;)

> 
I got it all worked out now. I had to add the php5-gd package and also give full permissions to the "album_thumbs", "photos", "themes", and "thumbs" folders.

Yes, this is true. I should write more complete installation instructions. At least for Ubuntu. ;)

> 
You got yourself a spanish translator if you want me. :P

Great, of course I want YOU :) I see you found the file that needs to be translated. It should be pretty easy to do translation with it.

I also received Dutch translation today and it's now available at the Translations page. I'll add all the new translations to the next release.

---

### Post by Kobalt on 2007-03-04
Very interesting soft... really beautiful.
I'll be going away to London next week but when I'm back I'll test this closely (to post my london pics by the way!). I would help for the french translation gladly if needed.

---

### Post by Laterix on 2007-03-04
> **Kobalt said:**
> Very interesting soft... really beautiful.
I'll be going away to London next week but when I'm back I'll test this closely (to post my london pics by the way!). I would help for the french translation gladly if needed.
Thanks. There is already a french translation available, but of course you can check is it 100% correct. I can't do this stuff myself. :)

---

### Post by Kobalt on 2007-03-04
I saw there was already someone (David) on the french translation... As I wrote you, I'll be back only next weekend so maybe it will be finished. Anyway, PM me if you need some extra brains for the french trad. 
And keep up the good work Lauri ! :rolleyes:

---

### Post by Laterix on 2007-03-05
I received today IE fixes and 3 translations. Thank you all for your participation! Translations are available at the website and IE fixes will be part of next release.

---

### Post by Laterix on 2007-03-07
I'm working on dark theme for Estetiikka. Here is few preview screenshots. I'm also going to change thumbnail image format from jpeg to png.

[[IMG]http://users.utu.fi/ljtaim/pics/thumb1.jpeg[/IMG]]("http://users.utu.fi/ljtaim/pics/theme1.png")

[[IMG]http://users.utu.fi/ljtaim/pics/thumb2.jpeg[/IMG]]("http://users.utu.fi/ljtaim/pics/theme2.png")

---

### Post by Ragazzo on 2007-03-08
The graphics are stunning. Did you use gimp to make them?

---

### Post by Laterix on 2007-03-09
> **Ragazzo said:**
> The graphics are stunning. Did you use gimp to make them?
Thank you and the answer would be yes, I used GIMP.

EDIT: Just to clear up that icons are not my work. I used Everaldo's Crytal Clear icons. They are published under GPL-licence.

---

### Post by Mutahir on 2007-03-26
Hi laterix,

A very nice web gallery you have developed, I am about to install and run it on my local home network for family and friends.

the dark theme you have displayed in this post, is this completed and available :)

Regards
Best of luck with your future projects.

---

### Post by Laterix on 2007-03-26
> **Mutahir said:**
> 
the dark theme you have displayed in this post, is this completed and available :)

The dark theme is almost finished and it will be in the next release 1.1. There are still some issues I have to take care of before that release.

---

### Post by Laterix on 2007-04-18
I've been busy with my master's thesis. But I have received some translations, which I have added to the website. At least swedish and chinese translations are new... maybe there are others too. I can't remember :) See the website and you'll see...

---

### Post by ibanezix on 2007-04-19
I sent the Greek translation. 

There really should be an online demo of the gallery, with all languages installed so that people can check them out.

---

### Post by DiESELMuSA on 2007-04-20
I've translated the gallery to Norwegian, and sent it to you :) Keep up the good work.
What issues do you need help with? I can program PHP a little bit

---

### Post by Laterix on 2007-04-21
Thanks for new translations! I have added them to the website.

It's true that there should be an online demo. I can't provide that at the moment, but maybe in the future... or if I find someone who is willing to provide that.

Here is few screenshots with translations... just for fun. :)

[Screen 1]("http://users.utu.fi/ljtaim/pics/greek.png")
[Screen 2]("http://users.utu.fi/ljtaim/pics/estetiikka2.png")

---

### Post by ibanezix on 2007-04-24
Here is a question: during installation I am supposed to navigate to the /config directory and execute:

```
mysql -u USER -p \DATABASE < estetiikka.sql
```

replacing USER with the database username and DATABASE with the database name.

But, how will I execute any command through FTP client? Isn't it possible to directly edit estetiikka.sql ?

BTW: 

```
 `sex` enum('male','female') NOT NULL default 'male' 
```

Hey! That's sexual descrimination!

---

### Post by Laterix on 2007-04-24
> **ibanezix said:**
> 
But, how will I execute any command through FTP client? Isn't it possible to directly edit estetiikka.sql ?

Those instructions were written in a hurry. If you set up Estetiikka somewhere else than you're own machine then phpmyadmin is maybe the easiest way to go. It supports importing databases.

> 
```
 `sex` enum('male','female') NOT NULL default 'male' 
```
Hey! That's sexual descrimination!
heh heh... sue me. :) Male was a better default value for MY gallery so I went with that.

---

### Post by ibanezix on 2007-05-04
I used a couple of screenshots of Estetiikka and an extract from the language file in a presentation in my college :)

During the making of the presentation I saw two spelling mistakes in the greek translation, which I corrected and resent.

---

### Post by Laterix on 2007-05-04
> **ibanezix said:**
> I used a couple of screenshots of Estetiikka and an extract from the language file in a presentation in my college :)

During the making of the presentation I saw two spelling mistakes in the greek translation, which I corrected and resent.

Heh heh, I got the fixed version and I'll update it as soon as I get back home. I'm interested why did you use Estetiikka in your presentation. Could you please tell me more about that? What was the presentation about?

---

### Post by ibanezix on 2007-05-04
There is an introductory course "Computer Fundamentals" for students that are not in the CS major, but CS students may participate by making presentations, something like teacher assistants. I gave a general-purpose lecture on the use and interoperability of several languages on the web, potentials of open source, trends in software etc. I doubt that anyone understood anything :)  

I used two screenshots of Estetiikka one in English and one in Greek, and an extract of the translation file, in order to illustrate various subjects, such as the separation of the content and the structure in development, the ways people cooperate in open source, the ease of adapring an open source project in another language blah blah blah ( I admit I must not be a good lecturer, sometimes I get carried away, sometimes I lose the subject completely :D ).

---

### Post by fremmus on 2007-08-18
hi, is there a more detailed installation faq? i really want to try it out, but i keep getting same error, 
> 
Parse error: syntax error, unexpected '{' in *****/header.php on line 40


help!

---

### Post by Laterix on 2007-08-19
> **fremmus said:**
> hi, is there a more detailed installation faq? i really want to try it out, but i keep getting same error, 

This probably happends because of incorrect PHP version. Estetiikka requires PHP5. Make sure that you don't have PHP4.

---

### Post by fremmus on 2007-08-19
yep, you're right!

thanks  :)

---

### Post by fremmus on 2007-08-19
[deleted]

---

### Post by KaroSHiv0n on 2007-09-06
I have read all the instructions in this thread, i can get into the gallery but thats about it, when i try to edit the gallery settings i get this:
Warning: fopen(config/config.cfg) [function.fopen]: failed to open stream: Permission denied in /var/www/gallery/classes/Configuration.php on line 95

Fatal error: Uncaught exception 'Exception' with message 'Opening file config/config.cfg failed!' in /var/www/gallery/classes/Configuration.php:100 Stack trace: #0 /var/www/gallery/save_settings.php(51): Configuration->saveCurrentConfiguration() #1 {main} thrown in /var/www/gallery/classes/Configuration.php on line 100

( have chmoded the dir as well as specifically that file in an attemt to fix this)
and when i try to upload a pic i get this:
Warning: mktime() expects parameter 5 to be long, string given in /var/www/gallery/classes/DBManager.php on line 208

Warning: Cannot modify header information - headers already sent by (output started at /var/www/gallery/classes/DBManager.php:208) in /var/www/gallery/upload_photo.php on line 111

I have php5 as well as php5-gd

any ideas? :)

---

