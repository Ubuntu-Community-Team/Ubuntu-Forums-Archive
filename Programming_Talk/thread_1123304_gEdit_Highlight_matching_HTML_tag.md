---
title: "gEdit: Highlight matching HTML tag"
date: 2009-04-12
forum: Programming Talk
---

### Post by dhruvasagar on 2009-04-12
Hey everyone!

First off I would like to say that I just adore ubuntu, I have been working on ubuntu for a year and a half and every day since has been almost magical :). Thanks to this wonderful community!!

Now coming to the point, I am enjoying coding in gEdit nowadays, its sleak, its fast, its simple, and its funky :D. With the various available plugins out there that do just about anything under the sun, it enables me to use this 'Text Editor' as a full blown IDE to do just about anything I need!

However I was wondering if there is a plugin or something I could do myself that would allow me to highlight matching HTML tags.
For example <div><div></div><div> so if I click on a particular div, it would highlight its matching div accordingly. This is not very much different from highlighting matching brackets especially if your HTML code is XHTML compliant.

---

### Post by dhruvasagar on 2009-04-12
Hey guys, can anyone please give me some input regarding this?
Highlighting matching tag is done by most other editors! It surely must not be a tough thing to achieve.
I would love to code it if I could, if anybody could give some inputs, some pointers to me on the same, perhaps I could start work on this right away.

---

### Post by shadow_code on 2009-04-12
I'm not sure this has been done yet, you could ask on the gedit mailing list.

[This page]("http://live.gnome.org/Gedit/") has some useful links

---

### Post by leupi on 2009-08-28
Just wondering what you might have found out? I am looking for something very similar. The closest that I have found is Notepad++ for Windows. It highlights exactly as you specify. I installed it under Wine in Ubuntu and it seems to work fine. I would still like to find something that runs natively under Linux without the need for Wine. Kinda interesting that the text editor that does exactly as I want is for Windows and not Linux...

---

### Post by khalifavi on 2009-12-11
as i posted this, the feature you wanted is supported in [Bluefish Editor 1.3]("http://bluefish.openoffice.nl/index.html") (still in development), if you are sure, you can just download it [here]("http://bluefish.openoffice.nl/download.html"). or if you want to see all the features, just see [here]("http://bluefish.openoffice.nl/features.html")
ah yes, i forgot to mention some "new" helping features of bluefish, here they are:
[LIST]
[*]Code block folding
[*]Highlighting matching block start and end markers (both brackets and tags)
[*]Auto-completion for many programming languages, with reference information, and even for nested languages (e.g. css inside html)
[/LIST]

---

### Post by abhilashm86 on 2009-12-11
you can[ try geany]("http://www.geany.org/"), its built for web 2.0 programming, it also shows tag matching, 
hold on, it has automatic completion of tag which you used/declared.......

---

### Post by leupi on 2009-12-11
I do like Bluefish and if that bit of functionality is going to be in the new version then I am certainly looking forward to it.

As far as Geany is concerned, that is the text editor that I use the most; however, it does not have the same functionality (that I can see) regarding tag highlighting. It does highlight tags but I would like something that will highlight the tag that my curser is on while at the same time highlighting the appropriate closing tag, making them both stand out from the others. This is what Notepad++ does.

Thanks all for the input (patiently waiting for Bluefish 1.3!)

---

### Post by edwardtilbury on 2010-06-07
The only solution I was able to find was running Notepad++ in wine! Pretty pathetic :( 

I was really surprised that I could not find a text editor for Ubuntu that had tag matching... Especially with the huge selection and all. Geany, Bluefish, Gedit, etc. I couldn't find anything with tag matching besides Notepad++ for Windows.

---

### Post by trusktr on 2010-10-21
You guys, just open up *gedit*. And start writing the plugin. ;)

---

### Post by krazyd on 2010-10-21
contrary to my original post, it looks like vim doesn't offer this feature. however it offers one which is actually more useful imho:

[http://stackoverflow.com/questions/500989/jump-to-matching-xml-tags-in-vim](http://stackoverflow.com/questions/500989/jump-to-matching-xml-tags-in-vim)

---

### Post by weedeater64 on 2011-01-23
mped

minimum profit

a programmers editor, was available in debian etch, not in lenny...

can be found on web, but will need to meet some dependencies/configuration changes...

Most excellent editor..

---

### Post by matthew.ball on 2011-01-24
> **krazyd said:**
> contrary to my original post, it looks like vim doesn't offer this feature. however it offers one which is actually more useful imho:

[http://stackoverflow.com/questions/500989/jump-to-matching-xml-tags-in-vim](http://stackoverflow.com/questions/500989/jump-to-matching-xml-tags-in-vim)
Emacs certainly offers the OP's request, and considering the whole dual Emacs and Vi share, it would really surprise me if Vi didn't have this too.

---

