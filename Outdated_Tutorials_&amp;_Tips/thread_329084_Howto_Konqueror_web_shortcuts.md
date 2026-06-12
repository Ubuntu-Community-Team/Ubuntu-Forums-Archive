---
title: "Howto: Konqueror web shortcuts"
date: 2006-12-31
forum: Outdated Tutorials &amp; Tips
---

### Post by njee on 2006-12-31
This is a topic I haven't been able to find much info here on the forums, and something I find quite a few people using Kubuntu don't know about.

Konqueror is the Swiss-Army knife of web browsers, you can do almost anything Firefox can do as long as you know how to do it and you're not afraid to MacGyver it yourself. 

You can create your own web shortcuts, similar to those adopted by Firefox, that allow you to search a web site just by typing in the search terms into the search bar at the top right corner of the Konqueror web browser interface. 

I believe this was introduced on any version of Kubuntu that has KDE 3.5 or higher, so it will work on Edgy, Dapper and Breezy (with updates).


Open Konqueror and click on the **Settings** menu. 

Click on **Configure Konqueror** .

On the next screen select the options for **Web Shortcuts**. 

Click on the **New** button.


We'll use _Amazon.com_ as an example to show you how to it's done.

Under **Search Prover Name** you type the name of the search service pr website, so in this case *Amazon*

The Search URL is where we type in the generic search string for the webpage with a placeholder that will make Konqueror search for whatever we type in.

To figure this out on Amazon we'll run a search through the web browser the obtain the search format URL.

So if we fire up Amazon in a new tab and run a search for any term (though one word is best) we can see what we're supposed to emulate.

A search for *monkey* yields the search URL;


[http://www.amazon.com/s/ref=nb_ss_gw/105-3964155-7674828?url=search-alias%3Daps&field-keywords=](http://www.amazon.com/s/ref=nb_ss_gw/105-3964155-7674828?url=search-alias%3Daps&field-keywords=)**monkey**&Go.x=0&Go.y=0&Go=Go"


So now we have the generic string we just replace our search word with the Konqueror placeholder which is always;

```
\{@}
```

So the new search URL looks like;


[http://www.amazon.com/s/ref=nb_ss_gw/105-3964155-7674828?url=search-alias%3Daps&field-keywords=](http://www.amazon.com/s/ref=nb_ss_gw/105-3964155-7674828?url=search-alias%3Daps&field-keywords=)**\{@}**&Go.x=0&Go.y=0&Go=Go"


So cut and paste that into the **Search URL** field on the **New** search window.

The last field to fill is the **URL Shortcut** in which you can assign a shortcut to the new web shortcut. In the case of Amazon I use *amz*.

To add the new search engine to your Search Plugin you simply _tick the box next to the web shortcut_ under the main **Web Shortcut** options.

On the main screen simply select your web shortcut from the menu (by clicking on the icon of the current web shortcut) next to the search field, type in your query and you're away!

To remove your web plugin simply select it from the list and select **Delete**

Another trick is is if you don't like using a separate search bar there you can search simply by using the **URL Shortcut** in the main address bar.

So the alternative way to use our web shortcut is to type,

*amz: QUERY*

where QUERY is whatever you'd like to search for. This way you can do away with the search bar altogether (remove it by clicking **Settings**, **Confgure Extensions** and then unticking **Search Bar Plugin**) and simply use the address bar for all your searches.

Lastly, to save you having to do them all over again if you reinstall Kubuntu I believe you can backup the files. Just copy them out of the directory;

**/home/nick/.kde/share/services/searchproviders**

and then copy them back into the same directory under your new install.



I've had difficulty using this method for all web pages (such as Ubuntuforums for instance, any help?) but have managed a few I use often and have copied the URL search strings below so that you can easily add them to your system without having to figure out the strings for yourself. Please feel free to add any other you use and think other people would need!


Amazon
```
http://www.amazon.com/s/ref=nb_ss_gw/102-7710298-6403369?url=search-alias%3Daps&field-keywords=\{@}&Go.x=0&Go.y=0&Go=Go
```

Ebay
```
http://search.ebay.com/search/search.dll?fsop=1&fsoo=1&from=R3&strKw=+&siteid=0&satitle=\{@}
```

UltimateGuitar.com Songs
```
http://www.ultimate-guitar.com/search.php?s=\{@}&w=songs
```

UltimateGuitar.com Bands
```
http://www.ultimate-guitar.com/search.php?s=\{@}&w=bands
```

Youtube
```
http://www.youtube.com/results?search_query=\{@}&search=Search
```

---

