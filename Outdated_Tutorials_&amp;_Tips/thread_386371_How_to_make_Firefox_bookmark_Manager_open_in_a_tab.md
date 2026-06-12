---
title: "How to make Firefox bookmark Manager open in a tab instead of new window."
date: 2007-03-16
forum: Outdated Tutorials &amp; Tips
---

### Post by adam.tropics on 2007-03-16
[COLOR=#000000]I was wandering around [Mozilla Forums]("http://forums.mozillazine.org/") today, as you do, and came across this one. It's not all that new, but if,as I do, you have a dislike to new windows opening everywhere, and choose not to use Opera, then this may be for you.[/COLOR]
 
 [COLOR=#000000]The goal is to be able to organise bookmarks from a tab, rather than opening a new window. To do this involves installing an extension, called userChrome.js which gives you more control over the javascript firefox runs. You can install it [here]("http://www.haslo.ch/zeniko/software/userchrome.js.xpi"). There is also a VERY long thread [here]("http://forums.mozillazine.org/viewtopic.php?t=397735") that goes into all sorts of other little things that can be done with it, but for the purposes of this brief guide we're really only interested in one.[/COLOR]
 
 [COLOR=#000000]Once the extension is installed, find your firefox profile folder. This is generally in a hidden folder in your home directory,called ~/.mozilla/firefox/XXXXXX.default where XXXXXX represents some ridiculously long random id.[/COLOR]
 
 [COLOR=#000000]Anyway, inside that folder, enter the chrome folder. If you do not see a file called userChrome.js then create one with your favourite text editor.[/COLOR]
 
 [COLOR=#000000]Into that file, you need to put:[/COLOR]
 
 ```
// JavaScript Document 
 
 /* Bookmark Manager open in Tab */ 
 document.getElementsByAttribute("key", "manBookmarkKb")[0].setAttribute("oncommand", '(getBrowser().selectedTab = getBrowser().addTab("chrome://browser/content/bookmarks/bookmarksManager.xul")).label = "Bookmarks Manager";');
```[COLOR=#000000]..and you're done. Restart firefox, and from your bookmarks menu, click organise bookmarks, and with a little luck...presto![/COLOR]
 
 [COLOR=#000000]You can use a similar approach with the download manager and History Show in Tabs with the code below, but personally, I don't find those two nearly as handy.[/COLOR]
   ```
/* Download Manager open in Tab */ 
 document.getElementById("Tools:Downloads").setAttribute("oncommand", '(getBrowser().selectedTab = getBrowser().addTab("chrome://mozapps/content/downloads/downloads.xul")).label = "Download Manager";'); 
  
 /* History Manager open in Tab */ 
 document.getElementById("viewHistorySidebar").setAttribute("oncommand", '(getBrowser().selectedTab = getBrowser().addTab("chrome://browser/content/history/history-panel.xul")).label = "History Manager";');

``` [COLOR=#000000]If you change your mind, simply uninstall the extension, and you may have to manually remove userChrome.js, then just restart your browser.

This will also work in Swiftfox btw. Have fun.

 
[/COLOR]

---

