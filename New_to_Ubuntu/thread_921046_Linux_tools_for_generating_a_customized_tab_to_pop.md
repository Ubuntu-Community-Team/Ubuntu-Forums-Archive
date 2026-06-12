---
title: "Linux tools for generating a customized tab to pop up in Google"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-15
Hi, all:

Here's a search trick I found for Google for when I want to get a tv guide for the evening.  I put in: site:[www.tv.com](www.tv.com) "Airs Monday September 15, 2008".

Is there some tool I can use in Firefox or Linux or whatever that will pop up a customized tab in Firefox each time I open it with this search result--but with the current day's date?  I.e. if I bookmark a given search, can I update (no pun intended) the search when I open it, say, this next Friday to read: site:[www.tv.com](www.tv.com) "Airs Friday September 19, 2008"

??

---

### Post by mevets on 2008-09-15
Off the top off my head I know you can right click the time applet and 'Copy Date' then paste that into the search bar and add tv.com.

---

### Post by tarahmarie on 2008-09-15
What do you mean by a time applet?

---

### Post by mevets on 2008-09-15
Its in the gnome panel. And it tells time. If it has been removed then its called 'Clock' in the add to panel menu

---

### Post by advoss on 2008-09-15
I'm in KDE but I assume it functions the same in GNOME.  He means the system time display (by default) in the upper right hand corner.  It is not permanently there like it is in windows but is actually an applet (think small program) that can dock on the bar, other applets include things like eyes that watch where you move your mouse and system performance graphs.

That however is not what you are looking for.  My interpretation is that you are looking for a 'smart' bookmark that updates with the current date.  I don't know how to code it is probably possible through what is generally known as a 'bookmarklet' which I think is usually a little bit of javascript (don't quote me there) code that is set as a bookmark, and that I would guess could have the power to query the date.

I hope thats helpful.

---

### Post by tarahmarie on 2008-09-15
I get what plasmoids and widgets are; I guess I was thinking applet like Java applet.  

How would I write said bit of javascript?  If it's complicated, can you tell me where to go to get help?  Like what is the best Javascript forum?

---

### Post by Greyed on 2008-09-15
Ooohh, that's a toughy.  I don't think there is.  It almost feels like something that should be done with an rss feed.  However my rss-fu is non-existent.  :(

---

### Post by shoot2kill on 2008-09-15
[http://codingforums.com/](http://codingforums.com/) is a great forum for any sort of dev help, but webdev and JS especially...

---

### Post by mevets on 2008-09-15
In python you can do this with
```

print "site:www.tv.com \"Airs",time.strftime('%A, %B %m, %Y\"')

```

---

### Post by tarahmarie on 2008-09-15
The Python script looks the most promising; how would I integrate that into a Firefox tab?  Is it possible?

---

### Post by mevets on 2008-09-15
The easiest way to do it would be to designate a hotkey to run a python script that ran firefox and passed in the url (os.system). I know you can do this if you use compiz, but if you are not running compiz then can I ask you if there is a way to assign a key to run a cmd that could be entered as if it were into the terminal under kde?

That aside, you coud still do this in js as you thought. The approach would be much the same (using the strftime function). And it would integrate much better cause it could easily be a bookmark.

---

### Post by advoss on 2008-09-16
I don't know of a browser extension that allows it to execute python code.  If you type javascript:```
 into the address bar the browser will execute the javascript code.  I know some python and java but no javascript.  I pieced together what I could but I can't get the format to work right.

[CODE]javascript:location.href='http://www.google.com/search?hl=en&q='+'site:www.tv.com\%20'+'\"Airs\%20'+new%20Date().toLocaleString("%A,%20%B,%20%m,%20%Y")+'\"'
```


Just set a book mark to point to that and it will change the page to a google search for (example): site:[www.tv.com](www.tv.com) "Airs Mon 15 Sep 2008 11:22:31 PM CDT"
If someone could fix the date format then it will be of use to you

---

### Post by tarahmarie on 2008-09-16
> **advoss said:**
> I don't know of a browser extension that allows it to execute python code.  If you type javascript:```
 into the address bar the browser will execute the javascript code.  I know some python and java but no javascript.  I pieced together what I could but I can't get the format to work right.

[CODE]javascript:location.href='http://www.google.com/search?hl=en&q='+'site:www.tv.com\%20'+'\"Airs\%20'+new%20Date().toLocaleString("%A,%20%B,%20%m,%20%Y")+'\"'
```


Just set a book mark to point to that and it will change the page to a google search for (example): site:[www.tv.com](www.tv.com) "Airs Mon 15 Sep 2008 11:22:31 PM CDT"
If someone could fix the date format then it will be of use to you

Well, the search itself worked great, thanks!  It's just that the date format isn't quite right.  Here's the result:

Your search - site:[www.tv.com](www.tv.com) "Airs Tue 16 Sep 2008 12:28:19 AM EDT" - did not match any documents. 

How can the search string read exactly "Airs: Tuesday September 16, 2008"?

I don't write Javascript (yet), but is this possible?

---

### Post by lswb on 2008-09-16
This will get you pretty close:

Cut and paste this code into a file and save it, I'll used the file name tvguide and save it in home directory

tvguide
```

#!/bin/bash
firefox "http://www.google.com/search?hl=en&q=site:www.tv.com \"Airs: $(date +"%A %B %d, %Y")\"&btnG=Google+Search"

```

Note that this file has only 2 lines of text. The first is "#!/bin/bash" and everything else should be the second line.

Give the file execute permission. From a terminal this would be done by typing: 

chmod +x tvguide

Now create a launcher that points to this script. If you use gnome, right click on a panel, then Add to Panel/Custom Application Launcher. In the dialog box that opens, enter in the command field:

/home/your-user-name/tvguide 

(or the appropriate path & filename if you saved or named the file differently) You can use anything you like for the other fields. In gnome a launcher can be created on the desktop if preferred. The icon can be changed by right clicking on it and selecting properties, then click on the picture of the icon in the dialog box that opens. A picture of a TV would be nice I guess.

When you click on this launcher it will start firefox or open a new tab if firefox is already running and display the google search results with the current date.

I'm sure someone familiar with javascript could get this working in an html file that you could save and bookmark in firefox.

---

