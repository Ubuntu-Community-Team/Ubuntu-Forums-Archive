---
title: "Is there code folding in Gedit?"
date: 2007-08-02
forum: Programming Talk
---

### Post by tc101 on 2007-08-02
I read somewhere that gedit had code folding, but I can't find any documentation on it.  Does it do code folding?

---

### Post by kknd on 2007-08-02
No =(

---

### Post by AlexThomson_NZ on 2007-08-03
If you are looking for a code editor somewhere between gedit and anjuta check out geany (it's got code folding btw)

---

### Post by Geekkit on 2007-08-03
> **tc101 said:**
> I read somewhere that gedit had code folding, but I can't find any documentation on it.  Does it do code folding?

You know it's funny you bring this up. Although that wasn't a feature I was missing in Gedit, two features I was missing in Gedit were:

[LIST]
[*]selection of words where the word contains underscores (like in many C programs)
[*]Save All
[/LIST]

I just, and I mean just, installed Anjuta tonight and got both those plus the code folding. I even set the font colors to what Gedit shows for familiarity reasons. If I were you I would definitely check out this Anjuta program. I'm finding it infinitely helpful.

---

### Post by Geekkit on 2007-08-03
> **AlexThomson_NZ said:**
> If you are looking for a code editor somewhere between gedit and anjuta check out geany (it's got code folding btw)

Thanks for this Alex, I'm going to check this one out too.

---

### Post by tc101 on 2007-08-03
I am going to check out geany.  I am programming in python.  Anjuta says it is for C++, which I don't know.

---

### Post by Geekkit on 2007-08-03
> **tc101 said:**
> I am going to check out geany.  I am programming in python.  Anjuta says it is for C++, which I don't know.

I've actually settled on Geany ... for now. I tried Anjuta but it's a little bit more than what I need. That and I didn't figure out the search-and-replace feature. Geany seems to be the most like what I remember EditPlus in the Win32 world to be.

The only feature Geany doesn't seem to have (correct me I'm wrong here), is that it doesn't allow you to change the colors of comments, quotes and things. Other than that it's quite to my liking.

However this is truly one of the best parts of Linux though isn't it? Don't like the editor you're using? Switch. There are like a gazillion options to choose from. And it's not like you're having to pick through the crap bin either. Most of the editors I've seen for Linux are heavy hitting professional quality grade tools.

---

### Post by jay019 on 2007-08-03
> **Geekkit said:**
> ...
The only feature Geany doesn't seem to have (correct me I'm wrong here), is that it doesn't allow you to change the colors of comments, quotes and things. Other than that it's quite to my liking..


Open /usr/share/geany/filetypes.xml and edit away. :)
You can adjust foreground / background colors and switch on/off bold and italic. You could even ad your own keywords if you so desired.

---

### Post by po0f on 2007-08-03
Color config dialog plz!!

That was my only gripe with Geany and a serious enough oversight on the author's part to go back to Gedit.  :)

---

### Post by jay019 on 2007-08-03
Whats wrong with editing a file by hand. :-P

You could write a GUI front end for editing those files I guess. 
Would be a nice little project for someone with some time to spare.

---

### Post by Geekkit on 2007-08-03
> **jay019 said:**
> Open /usr/share/geany/filetypes.xml and edit away. :)
You can adjust foreground / background colors and switch on/off bold and italic. You could even ad your own keywords if you so desired.

Thanks for that .. now I'm happy.  :)

---

### Post by erollin on 2008-07-23
Hey!  geany is great!!  

I tried Anjuta, Eclipse, Kdevelop and some extensions of gEdit.  Geany is very simple and yet does everything I want.

Thanks for the tip!

---

### Post by ORiONx9 on 2008-07-23
> **Geekkit said:**
> You know it's funny you bring this up. Although that wasn't a feature I was missing in Gedit, two features I was missing in Gedit were:

[LIST]

[*]Save All
[/LIST]

 Ctrl + Shift + L Save all tabs. 

Is that what you're looking for?

---

### Post by dksmiffs on 2009-07-12
+1 for Geany.  My first impressions are very good.

I, too, started looking elsewhere when I found that Gedit had no code folding.  Geany is also MUCH more self contained than Gedit for KDE users.  Install is lightning fast, 1 package via aptitude for Geany versus 62 for Gedit.  Geany also launches very fast.

---

### Post by rgbpe on 2009-08-24
test is 

[http://code.google.com/p/gedit-folding/downloads/list](http://code.google.com/p/gedit-folding/downloads/list)

unzip and copy them to /home/[USER]/.gnome2/gedit/plugins

restart gedit

alt+z for folding

---

### Post by xlyz on 2009-09-28
> **rgbpe said:**
> 
[http://code.google.com/p/gedit-folding/downloads/list](http://code.google.com/p/gedit-folding/downloads/list)


thanks for the link. now i'm set :)

---

### Post by doas777 on 2009-09-28
> **jay019 said:**
> Whats wrong with editing a file by hand. :-P


by that, do you mean by inscribing each bit on the platter surface with a stylus, or by butterflies?

---

### Post by delfick on 2009-09-29
eventually we'll have code folding for gtksourceview 
[http://mail.gnome.org/archives/gedit-list/2009-September/msg00019.html](http://mail.gnome.org/archives/gedit-list/2009-September/msg00019.html)
(that was posted yesturday)

(gedit uses gtksourceview)

:)

---

### Post by Schvarcz on 2009-10-21
Hi guys!

   I found it right now, but i couldn't test this yet, i'm at work now... But i will  let it here for who wish.

    This tip was found [HERE]("http://brainstorm.ubuntu.com/idea/8728/") and the supposed code folding plugin is [HERE]("http://code.google.com/p/gedit-folding/downloads/list").

Good luck for us!


OBS: the links are in black because of the css code
:guitar:

---

### Post by sonicb00m on 2009-11-12
> **rgbpe said:**
> test is 

[http://code.google.com/p/gedit-folding/downloads/list](http://code.google.com/p/gedit-folding/downloads/list)

unzip and copy them to /home/[USER]/.gnome2/gedit/plugins

restart gedit

alt+z for folding

unfortunately, this doesn't work for me. I created that directory but it didn't show up so i copied them to usr/share/gedit-2/plugins/ instead and the "simple folding" plugin shows up but does nothing. alt-z doesn't have any effect either.

im running 2.28.0

---

### Post by SilverWave on 2010-02-24
> **erollin said:**
> Hey!  geany is great!!  

I tried Anjuta, Eclipse, Kdevelop and some extensions of gEdit.  Geany is very simple and yet does everything I want.

Thanks for the tip!

Geany is very simple and yet does everything I want.

Yep I was looking for low resource editor with lightning fast opening times... for editing a _big_ html file.

Not quite as low usage as gvim but close and a great find/replace and folding as well :)

---

### Post by d3v1150m471c on 2010-02-24
You could use kate.

[http://ubuntuforums.org/showthread.php?t=967123](http://ubuntuforums.org/showthread.php?t=967123)

---

### Post by astahov on 2010-07-18
If Gedit had code folding it be the best editor.
I love it very much basicly the only tool I use, and manuals.

If I knew how to write code for it to add the feature to it I would defenitely do it but I am only on PHP and ROR right now :(.

Going to give Geany a try, code folding is a huge feature for me.

---

### Post by Sockerdrickan on 2010-07-18
> **astahov said:**
> If Gedit had code folding it be the best editor.
It's on the road map at least [http://live.gnome.org/Gedit/RoadMap](http://live.gnome.org/Gedit/RoadMap)

---

### Post by mocca007 on 2010-11-28
I found this, works like a charm :)

[http://code.google.com/p/gedit-folding/](http://code.google.com/p/gedit-folding/)

Install the plugin (download the 2 file and place them in gedit's plugin directory), activate it in gedit, and use ALT Z to fold the code.

---

