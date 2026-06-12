---
title: "Great Rails Editor for Gnome"
date: 2007-05-14
forum: Programming Talk
---

### Post by daz4126 on 2007-05-14
If you have been using Ruby on Rails in Linux and looking enviously at the Mac Users as they go on and on about how great Textmate is, then Scribes is your answer. Scribes is a great little minimalist and lightweight text-editor with a brilliant template system that you can use to insert commonly used snippets of code using the tab key as a trigger. It is also in active development and very enthusiastically supported by its creator (Mystileef).

Get it from [getdeb]("http://www.getdeb.net/") then just install the templates that can be found at [bitsbam]("http://www.bitsbam.com/") (where you can also get instructions for how to get rhtml highlighting in gtk).

I've recently helped to update some of the files so that rjs files are now highlighted in the same way as rhtml files and erb tags are recognised.
 
To see how cool the templates are, try pressing ... 
 
divid [tab] 
erb [tab] 
rb [tab] 
end [tab] 
doc [tab] 
li [tab] 
h [tab] 
flash [tab] 
 
... in some rhtml files. There are lots more, have a look through the template editor once you have installed them. 

If you need any help with any of this, just ask and I'll try to help.
 
DAZ

---

### Post by michwill on 2007-06-01
Pretty cool.  The only problem I see (which seems to be the biggest in all of the packages I've tried) is the lack of a hierarchical file drawer on the side.  I mean, for all intents and purposes, some of the emacs plugins I've seen are *amazing* for editing, but when it comes to file navigation they all stink.  Textmate still wins hands down.  The only item that even comes close is bluefish ([http://bluefish.openoffice.nl/index.html](http://bluefish.openoffice.nl/index.html)).

---

### Post by justin whitaker on 2007-06-01
I'm partial to Aptana: [http://www.aptana.com/](http://www.aptana.com/)

---

### Post by michwill on 2007-06-01
Aptana, is cool, and has lots of features, but it's also bloated and waaaaaaaaay too Eclipsey.  Both Aptana and Eclipse are good ideas, but like they Java they're written in, just poorly implemented.  Glad it works for you though.  ;)

---

### Post by daz4126 on 2007-06-02
> **michwill said:**
> Pretty cool.  The only problem I see (which seems to be the biggest in all of the packages I've tried) is the lack of a hierarchical file drawer on the side.  I mean, for all intents and purposes, some of the emacs plugins I've seen are *amazing* for editing, but when it comes to file navigation they all stink.  Textmate still wins hands down.  The only item that even comes close is bluefish ([http://bluefish.openoffice.nl/index.html](http://bluefish.openoffice.nl/index.html)).


You should use your nautilus file browser for this - no point in it being implemented again in the editor when Nautilus already provides this functionality. See the attached screenshot to see how I have Scribes & Nautilus set up for running Rails projects.

DAZ

---

### Post by Samjiman on 2007-06-02
I've tried Scribes - problem is for some reason the package requires you to install Yelp, which requires Firefox. But I'm using Iceweasel (essentially Firefox, but Debian's version) and consequently I can only install it, if I uninstall Iceweasel and install Firefox. 

Also I would prefer it if it supported tabs, or had some similar file selection system to jEdit and the file syntax highlighting seems to have to be manually selected (this might just be me though).

---

### Post by michwill on 2007-06-04
> **daz4126 said:**
> You should use your nautilus file browser for this - no point in it being implemented again in the editor when Nautilus already provides this functionality. See the attached screenshot to see how I have Scribes & Nautilus set up for running Rails projects.

DAZ


Thanks, but no thanks.  I like it all integrated.  Plus, I like having multiple files open at once in a tabbed fashion.  I like navigating to a file and having it instantly display in the active window, or being able to open it in another tab.  It's all about workflow.  ;)

---

### Post by Samjiman on 2007-06-04
> **daz4126 said:**
> You should use your nautilus file browser for this - no point in it being implemented again in the editor when Nautilus already provides this functionality. See the attached screenshot to see how I have Scribes & Nautilus set up for running Rails projects.

DAZ

I managed to get Scribes installed along with Iceweasel, by installing an older Yelp DEB package, which didn't have Firefox as dependency.
Incidentally, how did you set Scribes up to attach Nautilus TextMate style? Also what dock are you using?

Thanks :)

---

### Post by orengolan on 2007-06-05
I am new to ROR and to Linux and was searching for a good and simple IDE for ROR.
I tried using Cream with the project plug-in but find it a little complicated.

I have just found out this post - [http://www.thaumatocracy.com/news/textpad-for-linux](http://www.thaumatocracy.com/news/textpad-for-linux)
It's the famos gedit with some tweaks that makes it look and feel like Textmate - 
left project view, tabs and code completion! 

If you want character completion and rhtml/rjs support get it here:
1. [http://www.garyharan.com/index.php/2006/11/16/gemini-gedit-plugin-for-all-those-textmate-fans/](http://www.garyharan.com/index.php/2006/11/16/gemini-gedit-plugin-for-all-those-textmate-fans/)
2. [http://bitsbam.com/?p=3](http://bitsbam.com/?p=3)

I will give it a shot and let you know how it worked out. it looks really promising.
Does anyone has experience with gedit or cream?

[IMG]http://ubuntuforums.org/g/images/249002/1_Screenshot-1.png[/IMG]

---

### Post by rayvinly on 2007-06-06
I followed the steps in [http://bitsbam.com/?p=3]("http://bitsbam.com/?p=3") and also got gedit-textmate from snapopen.  Now rhtml is available for selection under the syntax highlight menu.  However, I have to select it manually.  GEdit does not automatically syntax highlight rhtml files.  Am I missing something?

---

### Post by orengolan on 2007-06-08
when i unzip it (right click on the gedit-mate-1.1.tar.gz file)
i get this file - gedit-mate-1.1
I am confused. sometimes i only get a readme file!

what am i doing wrong?

---

### Post by daz4126 on 2007-06-08
> **Samjiman said:**
> I managed to get Scribes installed along with Iceweasel, by installing an older Yelp DEB package, which didn't have Firefox as dependency.
Incidentally, how did you set Scribes up to attach Nautilus TextMate style? Also what dock are you using?

Thanks :)


I didn't attach scribes to Nautilus, I just open them separately and have Nautilus in 'tree mode' and put the two windows next to each other.

By dock, do you mean the panel at the bottom? It is just a gnome panel made to look like OSX (auto-size, big icons etc)

DAZ

---

### Post by daz4126 on 2007-06-08
> **michwill said:**
> Thanks, but no thanks.  I like it all integrated.  Plus, I like having multiple files open at once in a tabbed fashion.  I like navigating to a file and having it instantly display in the active window, or being able to open it in another tab.  It's all about workflow.  ;)

I don't see why you can't have multiple windows open at once - in this way the panel at the top of your desktop acts like tabs. Scribes also has a document switcher facility.

An integrated file manager isn't DRY which is a fundamental principle of rails - why have a substandard file manager built in when you already have such a good one in Nautilus (or whatever you use for normal file browsing)?

A good setup I use when developing in rails is to use the different desktops - I have a console session open on one, scribes with Nautilus in another and firefox in another. This means there is much more room to have multiple Scirbes windows open.

DAZ

---

### Post by daz4126 on 2007-06-08
> **michwill said:**
> Aptana, is cool, and has lots of features, but it's also bloated and waaaaaaaaay too Eclipsey.  Both Aptana and Eclipse are good ideas, but like they Java they're written in, just poorly implemented.  Glad it works for you though.  ;)

I tried Aptana and Radrails and just couldn't get into them. They were also painfully slow. Scribes just seems to fit with the 'rails way' to me - it is light weight and the template system just makes development really fast. I also love the minimal interface.

DAZ

---

### Post by Samjiman on 2007-06-09
> **daz4126 said:**
> I didn't attach scribes to Nautilus, I just open them separately and have Nautilus in 'tree mode' and put the two windows next to each other.

By dock, do you mean the panel at the bottom? It is just a gnome panel made to look like OSX (auto-size, big icons etc)

DAZ

I see. I thought maybe you did that.  Your Gnome Panel made to look like Mac OS X looks pretty sweet. I thought it was a dock package.

Thanks.

---

### Post by Faire on 2007-06-09
I use jEdit for RoR developing... it's a really great editor.

---

### Post by achron on 2007-06-09
I've been looking for a good editor for RoR...  Eclipse just doesn't fit my mindset...  but the gedit with tweaks might just do...   I'm also working on converting over to Ubuntu for 99% of what I do, but the gaming (that last 1%) just isn't there yet...   I'll probably keep XP Pro around as a dual boot forever just for two games.

---

### Post by daybreaker on 2007-08-31
I've been using gEdit with the sidepanel plugin and the rhtml syntax download. It's been freaking sweet.  It's really nice, because the files arent on my machine, but thanks to the "Connect to Server" thing (which is what won me over from  Windows to Linux), I can just navigate to the ssh'd folder where all the dev files are.

Only problem is we're getting ready to move our Rails projects into subversion.  And there is no gEdit plugin for that yet.  So I may try out Aptana at first to see how the Subclipse plugin works.

---

### Post by orengolan on 2007-08-31
what is this 'connect to server'?

why do u need an SVN plugin?
is you don't like to use it from command line?

---

### Post by daybreaker on 2007-09-10
the "connect to server" thing that lets you ftp or ssh to a server, and use it like a local folder.  Makes it much easier to work on files than having to ftp files from the server, work on them, then ftp them back.

I installed rails on my computer though, so doing command line svn wont be too bad, and I can keep using gEdit.

---

### Post by polypus on 2007-10-25
i just did a little write up on using gedit for rails on gutsy, may be of interest:

[http://crepuscular-homunculus.blogspot.com/2007/10/gedit-for-ruby-and-everything-else-on.html](http://crepuscular-homunculus.blogspot.com/2007/10/gedit-for-ruby-and-everything-else-on.html)

cheers,
_c

---

### Post by orengolan on 2007-10-25
thanks!

---

### Post by daz4126 on 2007-11-20
This is brilliant. Thanks polypus,your post has persuaded me to start using Gedit for rails development instead of Scribes ... I love snapopen, makes getting to files much quicker.

DAZ

---

### Post by kknd on 2007-11-20
If you don't care to spend some RAM and aren't afraid of Java, Netbeans 6 (currently RC) is the better Ruby / JRuby IDE (in my opinion).

---

### Post by ppp0 on 2010-07-16
[_Geany_]("http://www.geany.org/")! Only Geany with [_extras_]("http://www.geany.org/Download/Extras")!

---

### Post by trivialpackets on 2010-07-16
I've used netbeans and it's pretty good, but beefy.  I do like the code completion sometimes, other times it gets in the way, so I consider that a wash.  It's slow.  I've been kind of teetering between gedit and geany myself, and using github for hosting my code and version control.  I love the way that git interacts with heroku.  It's just plain crazy.

Also ppp0, way to resurrect the thread!  :)

~ EP

---

