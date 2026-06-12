---
title: "Firefox search plugin for Ubuntuforums"
date: 2005-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by gasparov on 2005-05-02
Firefox search plugin

```

$ wget [http://www.tranza.it/ubuntusearch.tar.gz](http://www.tranza.it/ubuntusearch.tar.gz)
$ tar -zxvf firefoxsearch.tar.gz
$ sudo mv ubuntuforums.*  /usr/lib/mozilla-firefox/searchplugins/
$ rm firefoxsearch.tar.gz

```

N.B. Make sure there is no other ubuntuforums.xxx in the directory you are working

---

### Post by JonahRowley on 2005-05-02
Great tip!  But I use Opera, so here's how to do it in Opera.  Opera is not so cool when it comes to extending it, so it's a little more kludgy.

Open up **~/.opera/search.ini** in a text editor, gedit seems to be popular, but I'm a vim user.  You'll see lots of entries like this:
```
[Search Engine 1]
Name=&Google
URL=http://www.google.com/search?q=%s&sourceid=opera&num=%i&ie=utf-8&oe=utf-8
Query=
Key=g
Is post=0
Has endseparator=0
Encoding=utf-8
Search Type=0
Verbtext=17063
Position=-1
Nameid=0
```

There are a few limitations here.  First, the entries are numbered, and they must remain in order, or it doesn't seem to work.  I usually take entries I don't use out of this file, since there is a lot of "junk" in there.  Just make sure you don't mess up the order.

Name is what apprears in the search box, the & is to assign an *accelerator*, or keyboard shortcut.  URL is the URL to submit to, %s gets replaced with the search string.  There is also %i, which is replaced with the prefered number of search results per page, but I don't use that.  Key is also useful, if I set my Key to "u", I can enter **u firefox** into the address bar to search, as well as using the search box.  IsPost should be 0, it defines the HTTP request method for the search.  As for the others, I just don't touch them, and everything stays fine.  Also, it picks up the icon automatically.

Here is my section for Ubuntu forum searched.  Don't forget about the order!  You might have to change the number of yours.

```
[Search Engine 7]
Name=&Ubuntuforums
URL=http://www.ubuntuforums.org/search.php?q=%s
Query=
Key=u
Is post=0
Has endseparator=0
Encoding=utf-8
Search Type=0
Verbtext=17063
Position=-1
Nameid=0
```

A tip about the mozilla tip, you don't have to use sudo, you can also copy this to your personal profile directory.  Look in **~/.mozilla/firefox/profiles.ini** for your profiles directory, and copy the files to **~/.mozilla/firefox/<insert profile directory here>/search/**.

---

### Post by WildTangent on 2005-05-02
what does it do?

-Wild

---

### Post by ow50 on 2005-05-02
This should work on any Mozilla browser. Tested on Epiphany.

```
javascript:q = '' + (window.getSelection ? window.getSelection() : document.getSelection ? document.getSelection() : document.selection.createRange().text); if (!q) q = prompt('Search Ubuntu Forums for:', ''); if (q!=null) location='http://www.ubuntuforums.org/search.php?q=' + escape(q).replace(/ /g, '+'); void 0
```

Use that as the address for a bookmark. It will pick up any text you have selected or if nothing is selected it will show a dialog where you can enter keywords to search for.

---

### Post by JonahRowley on 2005-05-02
WildTangent:  These add an "Ubuntu Forums" search option to the search box next to the address bar.

ow50:  Even better, and this works in Opera as well ;)

---

### Post by poofyhairguy on 2005-05-02
Thanks..

---

### Post by Josh M on 2005-05-03
Worked for me, thanks!

---

### Post by Heliode on 2005-05-03
Excellent! Just what I needed actually!

---

### Post by WildTangent on 2005-05-03
nifty...me like

-Wild

---

### Post by 23meg on 2005-05-03
the url is dead..

---

### Post by 23meg on 2005-05-03
i was thinking of making one myself; thankfully i remembered to do a search first! :)

this is so good it should be made sticky. i'm sure it will encourage searching. you should also [submit it to the mycroft db.](http://mycroft.mozdev.org/contribute.html)

---

### Post by Majlo on 2005-07-05
Great tip !!
Thanks :-)

---

### Post by UbuWu on 2005-07-05
Can be done even easier: click on search on the forums, right-click the textfield, and click add keyword for this search (or something similair, only know the dutch text). enter some keyword like ubfor or whaterver you like. Then you can enter 'ubfor searchstring' where you normally type an url.

---

### Post by Majlo on 2005-07-05
[QUOTE=UbuWu]Can be done even easier: click on search on the forums, right-click the textfield, and click add keyword for this search (or something similair, only know the dutch text). enter some keyword like ubfor or whaterver you like. Then you can enter 'ubfor searchstring' where you normally type an url.[/QUOTE]


Thanks for tip.
Work great..
;-)

---

### Post by frodon on 2005-07-06
really cool !

thanks qasparov and UbuWu for the tips, both work.

---

### Post by Albaraha on 2005-07-06
URL of firefoxsearch.tar.gz isn't working.

---

### Post by Albaraha on 2005-07-08
Could we get another mirror of the files, pls.?

---

### Post by Wandering Wombat on 2005-07-08
Cheers...... Thanx for this tip!

---

### Post by gasparov on 2005-07-09
[QUOTE=Albaraha]URL of firefoxsearch.tar.gz isn't working.[/QUOTE]

Fixed,sorry but free pages are so unreliable,expecially if you use them as ftp space :), now it's on property domain

---

### Post by Albaraha on 2005-07-09
[QUOTE=gasparov]Fixed,sorry but free pages are so unreliable,expecially if you use them as ftp space :), now it's on property domain[/QUOTE]
 Thanks very much.
How do I change the search bar order to get this plugin in position 2?

---

### Post by Ptero-4 on 2005-07-09
[QUOTE=Albaraha]Thanks very much.
How do I change the search bar order to get this plugin in position 2?[/QUOTE]
 Hi. how do I add this to the Apple's Safari browser. I look for stuff here from my eMac and having the ubuntuforums search box in the safari search box (the one at the right of the address bar) would be useful.

Thanks

---

### Post by ProNoblem on 2005-07-11
Because i didn't see the difference between the google and ubuntuforums search, i added this small icon as an attachment which you can place in /usr/lib/mozilla-firefox/searchplugins. 

Now the canonical logo shows up when you've selected the ubuntu-forums search (in stead of the magnifying glass) so that you won't accidentally enter searches for google into the ubuntuforums search.

(or you can do)
```

cd /usr/lib/mozilla-firefox/searchplugins/
sudo wget http://www.ubuntuforums.org/attachment.php?attachmentid=1627&stc=1 

```

---

### Post by moment on 2005-07-11
I know this might be very dull but if you just want to search the tips and tricks section add this line before </search> tag in the src file:

```
<input name="forumchoice" value="58">
```

---

### Post by majinwu on 2005-07-16
URL of firefoxsearch.tar.gz isn't working again  ](*,)

---

### Post by benplaut on 2005-07-16
[QUOTE=majinwu]URL of firefoxsearch.tar.gz isn't working again  ](*,)[/QUOTE]

 :mad:

---

### Post by rejser on 2005-07-17
[QUOTE=benplaut]:mad:[/QUOTE]

](*,) 
](*,) 
](*,) 
](*,)

---

### Post by sal on 2005-07-23
anyone know when the url will be working again?
or anyone know how i could hack firefox search to add this myself?
TIA!

---

### Post by manicka on 2005-07-23
[QUOTE=sal]anyone know when the url will be working again?
or anyone know how i could hack firefox search to add this myself?
TIA![/QUOTE]
 I've tar.gz'd the two files needed from my plugins folder and attached them 

You'll need to untar then  manually copy them into /usr/lib/mozilla-firefox/searchplugins/

HTH

---

### Post by sal on 2005-07-23
thanks for that.
i set up a new system the other day and this was killing me that it was not up.

---

### Post by adamkane on 2006-03-05
Go here and click the link to install the plugin:
[http://gas.tranza.it/2006-ubuntu-search/](http://gas.tranza.it/2006-ubuntu-search/)

Google.com searches are **not** the same as Firefox searches. Google searches are **not current**. Search plugins allow you to search for posts from today and yesterday, not just from two weeks ago.

---

### Post by Jaymac on 2006-12-06
Just came across this search today, and as of Opera 9.02, the solution posted by JonahRowley will not work...

Here is how I do it:
Tools > Preferences > Search > Add

Name: Ub&untu Forums
Keyword: u
Address: [http://www.ubuntuforums.org/search.php?q=%s&do=process](http://www.ubuntuforums.org/search.php?q=%s&do=process)

---

### Post by Meson on 2007-10-22
The plugin isn't working for me.  When I do a search it opens up the advanced search form with my search text already in the field, but it does not actually perform the search.

BTW - This should be a default feature for firefox when ubuntu is installed!

---

