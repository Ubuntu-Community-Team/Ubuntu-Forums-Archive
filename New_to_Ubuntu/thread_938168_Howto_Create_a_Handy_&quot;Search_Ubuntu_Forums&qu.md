---
title: "Howto: Create a Handy &quot;Search Ubuntu Forums&quot; Bookmarklet"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by PierreDeKat on 2008-10-04
Some of you have probably noticed that the Ubuntu Forums' native search function sometimes falls a little short of expectations. 

[According to the moderators]("http://ubuntuforums.org/showthread.php?t=874637"), the search function is resource intensive, so it has been relegated to a lower priority than other functions, which I can certainly appreciate. Currently there are 11,799 people surfing this site, and a goodly part of us are probably searching for something. Just imagine the load on the servers.

Well, awhile back, I made myself a "Search Ubuntu Forums" [bookmarklet]("http://en.wikipedia.org/wiki/Bookmarklet") using [this widget]("http://www.bookmarklets.com/mk.phtml"). And it's been such a huge help to me, I thought it might be good to share it with the rest of you.

Of course, you can use the widget above, just like I did. Or if you want, you can:

1. Start up your preferred internet browser.
2. Drag any old bookmark down to your "Bookmarks Toolbar" or "Personal Toolbar" or whatever you want to call it.
3. Right-click on the bookmark and select "Properties".
4. Make the Name "Search Ubuntu Forums" or "SUF" or whatever you want to call it.
5. In the "Location" box, paste this text:

```
javascript:Qr=document.getSelection();if(!Qr){void(Qr=prompt('Keywords...',''))};if(Qr)location.href='http://www.google.com/search?hl=en&suggon=0&as_q='+escape(Qr)+'&as_epq=&as_oq=&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=ubuntuforums.org&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=off'

```
There shouldn't be any spaces in this string of text, nor [http://.](http://.)..

It should start with the "j" in javascript and go to the apostrophe ( ' ) after "off"

And you will need to have your javascript turned on.

All you have to do is click the bookmarklet, enter some search terms, click "OK", and bingo, Google will scour its archive of the Ubuntu Forums and return you thousands and thousands of results that you probably wouldn't get with the native forum search function.

And those of you well-versed in Google's search function will know how to use quotation marks ( "" ) around a particular phrase if you want to search for an exact phrase. Or use the minus sign ( - ) in front of a search term, if you want to kick out results with that particular search term in them. And so on.

Or you can simply highlight some text on a webpage, click your "Search Ubuntu Forums" bookmarklet, and Google will search their Ubuntu Forums archives for the highlighted text. Either way you want to use it.

But try it out. I think you'll find it as handy as I have found it.

---

