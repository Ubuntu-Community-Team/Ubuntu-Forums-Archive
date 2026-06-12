---
title: "gedit hightlight like notepad++"
date: 2009-07-24
forum: Programming Talk
---

### Post by klw on 2009-07-24
Hi, 
I was wondering if there a function or plugin for gEdit which make custom marking in the code highlight all other similar code that I have marked?

Just like it is in notepad++.

To clarify what I mean e.g.
in a html-document. If I double click "br" in the markup, it will highlight all other br in the document.

---

### Post by dgoosens on 2009-07-24
... or you could just install Notepad++ with WINE...
it runs smooth

---

### Post by Tibuda on 2009-07-24
> **klw said:**
> Hi, 
I was wondering if there a function or plugin for gEdit which make custom marking in the code highlight all other similar code that I have marked?

Just like it is in notepad++.

To clarify what I mean e.g.
in a html-document. If I double click "br" in the markup, it will highlight all other br in the document.

Ctrl+F or Menu Search > Find. If you find for a word, it will highlight all ocurrences in the document.

---

### Post by Charlietje on 2009-07-24
Why not install scite?

```
sudo apt-get install scite
```

---

### Post by klw on 2009-07-24
I kinda like gEdit, and no I want to run as many software native in ubuntu without the usage of Wine.

Scite any good? maybe I should give it a try...

---

### Post by dgoosens on 2009-07-24
> **klw said:**
> I kinda like gEdit, and no I want to run as many software native in ubuntu without the usage of Wine.



I agree...
it's just that I have not found a simple light texteditor as good as notepad++.

notepad++ is the only thing I have installed in WINE... Oh and IE6... but that is just to check how badly Windows messes up a W3C-conform webdesign.

EDIT: ...and notepad++ is OpenSource... so there really is no reason not to use it.

---

### Post by mrebanza on 2009-12-01
> **dgoosens said:**
> ... or you could just install Notepad++ with WINE...
it runs smooth
beg to differ . . . . It works perfectly fine but it SLOW and LaGGGGGy with multi tabs open . . . . . I would defiantly PAY for a native Ubuntu version of notepad++

---

### Post by mrebanza on 2009-12-01
> **dgoosens said:**
> I agree...
it's just that I have not found a simple light texteditor as good as notepad++.

notepad++ is the only thing I have installed in WINE... Oh and IE6... but that is just to check how badly Windows messes up a W3C-conform webdesign.

EDIT: ...and notepad++ is OpenSource... so there really is no reason not to use it.

Same here . . .. . why isn't thier  a simple light texteditor as good as notepad++ for linux?????


I thought linux user were coders?????

notepad++ is REALLY light weight but its features and syntax highlighting MAKE SENSE and make life sooooo much easier . . . . I have downloaded every single last program from scite to bluefish and NONE of them have the somewhat simple highlighting features I took for granted with Notepad++ . . . . . Please somebody port Notepad++ into a Native Linux Program or at least continue development on one of the great text editor that are out thier for linux (thier are quite a few) to include their logical  syntax highlighting

---

### Post by TheStatsMan on 2009-12-01
> **mrebanza said:**
> Same here . . .. . why isn't thier  a simple light texteditor as good as notepad++ for linux?????


I thought linux user were coders?????

notepad++ is REALLY light weight but its features and syntax highlighting MAKE SENSE and make life sooooo much easier . . . . I have downloaded every single last program from scite to bluefish and NONE of them have the somewhat simple highlighting features I took for granted with Notepad++ . . . . . Please somebody port Notepad++ into a Native Linux Program or at least continue development on one of the great text editor that are out thier for linux (thier are quite a few) to include their logical  syntax highlighting

Gedit, Geany, Kate are all standard editors that have syntax highlighting. Perhaps give Geany a try. Most people seem to start with one of those and eventually end up using either vim or emacs. These are far more powerful, but they do involve a small learning curve.  You can find Gedit plugins here. [http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins)

---

### Post by rolandjo on 2009-12-04
Hello community,

I use Gedit but because I like the "search in files" functionalities from Notepad++ I've make an istalation of Notepad++ Portable in Wine.
This are the steps:

1. Install Wine from Ubuntu software Center, I use Wine 1.1.31;
2. Download [Notepad++Portable 5.5.1]("http://portableapps.com/apps/development/notepadpp_portable%20");
3. Go to your Notepad++ download folder, right click on the *.exe file and chose Open with Wine.....
4. Chose your language, chose your C:\Program Files\Notepad++Portable and click Install;
5 Go to Aplication Ubuntu menu, in Aplications/Wine/Browse c:/Drive or paste the following ~/.wine/dosdevices/c:/Program Files/Notepad++Portable in your File explorer 
6. Right click on Notepad++Portable.exe and chose Open with Wine.....

That's it,

Roland

---

### Post by mrebanza on 2009-12-14
> **rolandjo said:**
> Hello community,

I use Gedit but because I like the "search in files" functionalities from Notepad++ I've make an istalation of Notepad++ Portable in Wine.
This are the steps:

1. Install Wine from Ubuntu software Center, I use Wine 1.1.31;
2. Download [Notepad++Portable 5.5.1]("http://portableapps.com/apps/development/notepadpp_portable%20");
3. Go to your Notepad++ download folder, right click on the *.exe file and chose Open with Wine.....
4. Chose your language, chose your C:\Program Files\Notepad++Portable and click Install;
5 Go to Aplication Ubuntu menu, in Aplications/Wine/Browse c:/Drive or paste the following ~/.wine/dosdevices/c:/Program Files/Notepad++Portable in your File explorer 
6. Right click on Notepad++Portable.exe and chose Open with Wine.....

That's it,

Roland


wow thats great . . .  does it run any better than a native wine install????

Notepad++ runs pretty good in wine if you only have a few tabs open but I would love to just run gedit if it had the  "search in files" functionalities and highlighting that I am use too from Notepad++

I am running wine for one program and its a text editor???

maby a Notepad++ transformation package for gedit???:D

---

### Post by hnmcc on 2010-08-30
> **rolandjo said:**
> 
This are the steps:

1. Install Wine from Ubuntu software Center, I use Wine 1.1.31;
2. Download [Notepad++Portable 5.5.1]("http://portableapps.com/apps/development/notepadpp_portable%20");
3. Go to your Notepad++ download folder, right click on the *.exe file and chose Open with Wine.....
4. Chose your language, chose your C:\Program Files\Notepad++Portable and click Install;
5 Go to Aplication Ubuntu menu, in Aplications/Wine/Browse c:/Drive or paste the following ~/.wine/dosdevices/c:/Program Files/Notepad++Portable in your File explorer 
6. Right click on Notepad++Portable.exe and chose Open with Wine.....

That's it,

Roland

Thanks for this, Roland - I've now used this method twice (laptop and now desktop). :KS

But...

The "executable bit" nonsense in Lucid means that you have to change step 3 slightly.

Right click on *.exe and choose "Open with Other Application...".  In the next dialog click on "Use a Custom Command", enter "wine" (without the quotation marks) in the box, and click "Open". Then rejoin at item 4 above.

It's a matter of personal taste, but I find Notepad++ suits me better than any of the native Linux alternatives I've tried (and I've tried a few).  Being able to use the same application on Windows machines is obviously a big plus.

For me too, it's the only application I have in Wine. :D

---

