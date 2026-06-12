---
title: "Microsoft Access"
date: 2009-03-20
forum: Programming Talk
---

### Post by gunksta on 2009-03-20
People send me Access files and I often need to send them Access files in return. That's life. But, nobody ever actually said that I need to _use_ Access. So, I'm hoping you all can help me find a way to not use Access.

I have looked high and low for a native Linux solution to reading/writing Access files. I know I can install Access 2000 under Wine, but I often need to open XP/2003 databases. Unfortunately, they changed the file type. But, all I need are the tables and queries. I don't need to look at any of the pretty front-ends or things like that. I'm just an analyst. I have two ideas and I would appreciate any feedback / suggestions the users of this forum may have.

ONE
I have a separate computer (it lives in the corner in shame) with Windows / Access installed on it. Does anyone here have any experience opening Access files via unixodbc? In theory I should be able to use odbc under Windows to do what I need to do. If I can connect Windows odbc to unixodbc, this should provide one possible work-around. But, I'm not sure what I would need on my linux box to make this work. I don't really know much about unixodbc.

TWO
Are there any WINE compatible programs, other than Access, that I can use to open / save Access files. My googling hasn't found any good solutions, but there may be something I don't know about.

Thanks.

---

### Post by squaregoldfish on 2009-03-20
Check out the mdbtools package. It contains a few bits and pieces that you might find useful. I've only ever used it for quickly scanning Access files, and it seemed to work well enough. There's an ODBC driver included as well, so you might have some luck with that.

Steve.

---

### Post by gunksta on 2009-03-20
If development on mdbtools had continued, I suspect it would now be an excellent tool for accessing mdb files under linux. As is, it does make it possible to export information out of a mdb file, which is a great first step. 

Unfortunately, mdbtools does not support creating new queries, tables or rows. Thus, I can not play with the file and produce output that I can send back to my clients/co-worers as a mdb file.

If I only need read access to the data, mdb tools is an absolute god-send. But, I do need to be able to edit/create files based on the Jet database.

---

### Post by shatterblast on 2009-03-20
A simple google search pulls up [www.kexi-project.org](www.kexi-project.org) for me.  It appears open source.  OpenOffice.org Base might also do the trick.  If the files you're wanting to import originate from Office 2003, then I would imagine you should be fine either way.  I suggest the latest version of OpenOffice if you have to deal with Office 2007 though, which is version 3.0 or higher.  I'm not aware if compatibility issues exist Ubuntu and the latest OpenOffice.  Kexi also seems to come up in Synaptic so you can install through that.

---

### Post by gunksta on 2009-03-20
OpenOffice.org is not able to manipulate .mdb files.

Kexi uses mdbtools to import from .mdb files. See my above comments for why mdbtools is a wonderful, if inadequate solution.

It would be nice if Canonical or someone else put some man-power behind mdbtools. I don't know how hard it would be to improve this set of tools, but it is a start in the right direction. If improved, this could be integrated more closely with OOo builds on Linux and Mac OS X to improve file compatibility.

---

### Post by Felix_the_Mac on 2009-03-20
You could install Windows & Access in a virtual machine, ie. VirtualBox, VMWare etc.
It would allow you to get rid of the PC in the corner.

---

### Post by HotCupOfJava on 2009-03-20
Well, I'm not sure how deep you want/are able to get into it, but you CAN use some programming languages to create/manipulate Access databases. In Java, for instance, there is the java.sql package which allows you to use SQL statements to query and create databases. You have to supply Java with the appropriate driver so it can connect to the database, but the drivers aren't hard to get a hold of. Check out [this]("http://www.planet-source-code.com/vb/scripts/ShowCode.asp?txtCodeId=2691&lngWId=2") link.

If you're really ambitious or resourceful, you could even create your own front-end for manipulating Access databases using a programming language like this. 

I know, its really easy to SAY it, isn't it..........

---

### Post by gunksta on 2009-03-21
The link provided is for Windows developers. In order for any of that to work, you would need Windows.

But, it did get me to start thinking.      And experimenting.

With a little bit of effort, it does appear to be possible to run MS Access in Wine. I'm not yet ready to publish how I succeeded, because I want to extensively test my set up before claiming that it works.

Default Wine (using Jaunty) can install Word, Excel, Access, etc. But I could only get Word and Excel to actually work. Access would start, but would crash whenever I tried to do anything useful like open a file or start a new one. It was rather useless. Right now I can open Access and open .mdb files I have on my hard drive. I appear to be able to write new queries, and do basic things, although there are some bugs.

Give me a few days and I will have more to say on the matter. I may provide a link from here to another spot, if I think my solution will be more useful elsewhere.

I'm also trying to figure out if it is possible to connect Access to my main linux system via odbc. ODBC exists in both places, but I'm not sure how to make wine's odbc connect to the linux odbc, since they are all on the same machine.

More time and effort will be needed.

I may also try to get SQL server 2005 to work.

---

### Post by rolandixor on 2009-03-30
PLEASE! post how you did it!
I need to get Access working for school work, and I'm tired of switching to vista to do it...

---

### Post by Reiger on 2009-03-30
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)
(Scroll down to the bottom of the page, it lists settings/additional stuff you need.)

---

### Post by rolandixor on 2009-03-30
> **gunksta said:**
> The link provided is for Windows developers. In order for any of that to work, you would need Windows.

But, it did get me to start thinking.      And experimenting.

With a little bit of effort, it does appear to be possible to run MS Access in Wine. I'm not yet ready to publish how I succeeded, because I want to extensively test my set up before claiming that it works.

Default Wine (using Jaunty) can install Word, Excel, Access, etc. But I could only get Word and Excel to actually work. Access would start, but would crash whenever I tried to do anything useful like open a file or start a new one. It was rather useless. Right now I can open Access and open .mdb files I have on my hard drive. I appear to be able to write new queries, and do basic things, although there are some bugs.

Give me a few days and I will have more to say on the matter. I may provide a link from here to another spot, if I think my solution will be more useful elsewhere.

I'm also trying to figure out if it is possible to connect Access to my main linux system via odbc. ODBC exists in both places, but I'm not sure how to make wine's odbc connect to the linux odbc, since they are all on the same machine.

More time and effort will be needed.

I may also try to get SQL server 2005 to work.

tell me how please :)

---

### Post by gunksta on 2009-03-30
Yeah. Sorry I've been a little busy. The link provided by Reiger is a good, but inadequate start. This is a quick write-up. I promise I will write a more coherent version when I get some time. Reiger's link recommended you install:


[LIST]
[*][SIZE=2]**riched20:**Set riched20 to 'native' in Winecfg. DO NOT INSTALL IT YOURSELF. Office 2007 comes with its own version of riched20. Without using it, Powerpoint will not launch, and other features may be lacking.  
[/SIZE]
[*][SIZE=2]**MS  Visual C++ 2005 Libraries:** Required for MS Access to launch.     [/SIZE]
[*][SIZE=2]**Windows Scripting Host (jscript):**     Needed for the Thesaurus.[/SIZE]
[*][SIZE=2]**symbol.ttf: **For versions of Wine prior to 1.1.16, this font must be installed for bullets and equations to display properly[/SIZE]
[*][SIZE=2]**usp10:** Set usp10 to 'native,builtin' in winecfg for the equation toolbar in Word. There is no need to install it; simply set the override.[/SIZE]
[/LIST]
For starters, this doesn't tell you how. I used [winetricks]("http://wiki.winehq.org/winetricks"). To do it the way I did it, you must use winetricks (or waste a bunch of time trying to get it to work some other way).

After downloading winetricks, switch to the directory where it is sitting and . . . 
```
sh ./winetricks
```This will start winetricks. I used it to install:

[LIST]
[*]richedit20
[*]richedit30
[*]MS Visual C++ Libraries (vcrun6)
[*]Jet 4.0 (jet40)
[*]All fonts (allfonts)
[*]MS VB stuff (vb6run)
[*]MDAC 28 (mdac28 )
[*]msxml3
[/LIST]
Once you let winetricks do all of it's work (this take ~5-10 minutes, depending on your connection speed). Now you will need to install Office. Remember to use the unhide option when you mount the CD or the installer fails.

Once it's done installing, use Access. There are a few problems, but 90% of it works. Warning: Automatic stuff, like the Wizard don't work. They will freeze up Access. And, Help doesn't work either. It's all blank.

For some reason, when you start a new query, you can not select the tables/queries you want to use in the standard query designer. It too is blank. But, you can switch to SQL mode and type in the FROM statement manually and then the design editor works as expected.

Cut and Paste works, with a trick. I can not use the traditional Ctrl-X, Ctrl-P. It won't work. But, if I display the office sidebar on the right and let it show my office clipboard, I can select what I want and paste from there. It's not as convenient, but it works when I need to move some output to Word or Excel.

Otherwise, this works well. Let me know how you make out. If you'd like to help me write up and maintain something to help others use Access on Wine, let me know.

---

### Post by gunksta on 2009-03-30
Good question for the community. Where should I put my directions. I could post it to my blog, but nobody reads it. I could put it here, but it's not going to be very easy for people to find (and let's face it, there aren't that many people trying to use Access on wine).

---

### Post by rolandixor on 2009-03-30
I have a website (unfortunately, not many members on it :( hosted on Ning), that you can use. It's in my sig.

Will I be able to open Access files? This is my main problem (access 2003. Haven't installed 2007 as I not too long got it).

---

### Post by gunksta on 2009-03-31
The instructions above will let you install Office 2003. You don't need to install jet40 to get Office 2000 to install because it's part of the the Office 2000 installation. Office 2007 is a very different beast. I don't have access to to a copy of Office 2007, but I do not believe these directions will work for 2007 Access.

If you really want to experiment, you could create a .wine installation with Office 2003. When it works, move it .wine-2003 or something. Then, recreate the .wine folder and let winetricks do it's thing. Then try installing Office 2007, since I could very well be wrong. (I can't prove it one way or the other.)

With Access 2003, I can open, edit and save changes. I have created/edited tables, queries and macros. I haven't created any stored procedures or VBA script yet.

I also discovered yesterday that I can not create new databases.  :-)  I don't understand why yet. My temporary solution is to place a blank database into my ~/Templates/ folder.

I would start with Office 2003. Let me know how it goes for you. Once you get it working we can talk more about where to post this to help others.

---

### Post by gunksta on 2009-03-31
I've discovered a new, annoying, bug in Access under wine. Long complex numbers like 360.476 are displayed as 3..60476. However, it looks like Access is handling the numbers correctly internally, it just barfs on the display.


I think this deserves it's own thread in the main part of the forum.

---

### Post by gunksta on 2009-04-01
I wrote a post on the General Help forum today. You can find it, [here]("http://ubuntuforums.org/showthread.php?p=6993984#post6993984"). I did a better job describing what I did and what I have found since then that I have done here. And, since the General Help forum is bigger than the programming forum, more people are likely to see it. This means more of the bugs that I have found can be fixed and more people can benefit from what we have learned.

---

