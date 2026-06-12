---
title: "who are willing to write a firefox plugin for this forum?"
date: 2006-03-16
forum: Programming Talk
---

### Post by say2sky on 2006-03-16
I have found a firefox search plugin for ubuntu forums at
[http://mycroft.mozdev.org](http://mycroft.mozdev.org)

but this search plugin has not been approved and it doesn't work correctly. Hope sb can help to rewrite it. I post the code below for your reference

============================================================
# Search Plug-in for Ubuntuforums ([http://www.ubuntuforums.org](http://www.ubuntuforums.org))

# by Luca Gasperini <gas@tranza.it> created: 27 Jan 2006



<search

 version="7.1"

 name="UbuntuForums"

 description="UbuntuForums Forum Search"

 action="http://www.ubuntuforums.org/search.php"

 searchForm="http://www.ubuntuforums.org/search.php"

 method="get"

 queryCharset='UTF-8'

>



<input name="do=process&query" user >



<interpret

 browserResultType='result'

 resultListStart='Key Word(s):'

 resultListEnd='Showing results'

 resultItemStart='<a href="showthread.php?t'

 resultItemEnd='</a>'

 charset='UTF-8'

 >



<browser

	update="http://mycroft.mozdev.org/update.php/id0/ubuntuforums.src"

	updateIcon="http://mycroft.mozdev.org/update.php/id0/ubuntuforums.png"

	updateCheckDays="7"

>



</search>

---

### Post by timas on 2006-03-16
so, how do you envision this, like the google search box in your firefox? 

I've never really grasped the idea behind having site controls baked into your firefox.. doesn't the site itself offer the required functions? :)

I might give it a try just for the heck of it though, haven't written a firefox extension before and this sounds like the kind of thing that shouldn't be too difficult

---

### Post by adamkane on 2006-03-21
Go here and click the link to install the plugin:
 [http://gas.tranza.it/2006-ubuntu-search/]("http://gas.tranza.it/2006-ubuntu-search/")

---

### Post by ubuntu27 on 2006-03-21
Create your own: [http://www.rollyo.com/firefox_search.html](http://www.rollyo.com/firefox_search.html)


I've added the following sites into my search engine Rollyo:

[http://ubuntustudio.com/](http://ubuntustudio.com/)
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
[http://fridge.ubuntu.com/](http://fridge.ubuntu.com/)
[http://os.newsforge.com](http://os.newsforge.com)
[http://www.ubuntulinux.nl/](http://www.ubuntulinux.nl/)
[http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)
[http://placelibre.ath.cx/keyes/index.php/](http://placelibre.ath.cx/keyes/index.php/)
[http://distrowatch.com/](http://distrowatch.com/)
[http://doc.gwos.org/](http://doc.gwos.org/)
[http://www.ubuntu-ie.org/Wiki](http://www.ubuntu-ie.org/Wiki)
[http://www.canonical.com/](http://www.canonical.com/)
[http://www.ubuntu-es.org/](http://www.ubuntu-es.org/)
[http://www.ubuntux.org/](http://www.ubuntux.org/)
[http://ubunteros.blogsome.com/](http://ubunteros.blogsome.com/)
[http://www.ubuntulinux.jp/](http://www.ubuntulinux.jp/)
[http://shots.osdir.com/](http://shots.osdir.com/)
[http://help.ubuntu.com/](http://help.ubuntu.com/)
[http://www.ubuntupeople.com/file/forums/](http://www.ubuntupeople.com/file/forums/)


You should do it also. It's really useful ;)

---

### Post by shadwstalkr on 2006-03-21
I use quicksearch bookmarks instead of the search toolbar, because I can open a new tab and make a search without taking my hands off the keyboard.  Basically you bookmark the search URL, but replace the query with '%s' and give it a keyword.  Then you can type the keyword followed by search terms in the location, and you'll get your search page.  There should be a few examples that came with Firefox to get you started.  For this site, [http://www.ubuntuforums.org/search.php?do=process&showposts=0&quicksearch=1&s=&query=%s](http://www.ubuntuforums.org/search.php?do=process&showposts=0&quicksearch=1&s=&query=%s) works for me.

---

### Post by adamkane on 2006-03-23
Rollyo is based on Google Search, which means it is not up-to-date. A custom UbuntuForums SearchPlugIn is preferable to Rollyo.

---

### Post by ubuntu27 on 2006-03-23
[QUOTE=adamkane]Rollyo is based on Google Search, which means it is not up-to-date. A custom UbuntuForums SearchPlugIn is preferable to Rollyo.[/QUOTE]

Yeah, I agree that a custom UbuntuForums search is what we need... want.

A! PS:  [Rollyo](http://www.rollyo.com) is NOT based on [Google](http://www.google.com/), instead it is based on [YAHOO!](http://search.yahoo.com/) ;)

---

### Post by adamkane on 2006-03-23
Go here and click the link to install a custom UbuntuForums search plugin:
[http://gas.tranza.it/2006-ubuntu-search/]("http://gas.tranza.it/2006-ubuntu-search/")

Or here:
[http://www.ubuntuforums.org/showthread.php?t=140397](http://www.ubuntuforums.org/showthread.php?t=140397)

---

### Post by say2sky on 2006-03-29
[QUOTE=adamkane]Go here and click the link to install a custom UbuntuForums search plugin:
[http://gas.tranza.it/2006-ubuntu-search/]("http://gas.tranza.it/2006-ubuntu-search/")

Or here:
[http://www.ubuntuforums.org/showthread.php?t=140397](http://www.ubuntuforums.org/showthread.php?t=140397)[/QUOTE]

:confused: thanks for your info. But this plugin does not work with Conquery by highlight keyword and select search plugin from context menu. 

I have spent some time try to find out why this plugin work when it is put in firefox's search bar but not work in context menu. But I cann't find the problem.

---

