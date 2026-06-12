---
title: "How to get Wikiquote's Quote of the Day in a window or other program"
date: 2007-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by lapsey on 2007-12-06
I wrote this script to parse Wikiquote's Quote of the Day (QOTD) and display it on a line in a dialog window. It is very simple and requires **lynx** and **zenity** (ubuntu main repository). I have used this on both Feisty and Gutsy. I am posting this tip because I have not found this done anywhere else, yet.

```
#!/bin/bash

# en wikiquote page format correct at time of writing.

lynx -source http://en.wikiquote.org/wiki/Special:Export/Wikiquote:Quote_of_the_day/`date +%B_%-d,_%Y` | tac | grep "~" -m 1 | sed 's/&lt;/</g; s/&gt;/>/g; s/<br>/\n/g; s/<[^>]*>//g; s/|[^|]*|//g; s/{{[^}}]*}}//g; s/\[//g; s/\]//g' | sed 's/^ *//; s/  */ /g; s/&#8212;/-/g; s/\&#8217;/'\''/g; s/&quot\;/"/g; s/'\'\''/"/g; s/&#8230;/.../g' | zenity --text-info --title "Quote of the day" --width=400 --height=300

exit
```

Save the code with any filename you like. You can run it in any desktop environment using "bash PATH_TO_FILE".

If you would like to try it out now, run it in a plain terminal, command line, or other program without the dialog, just copy and paste the following line:
```
lynx -source http://en.wikiquote.org/wiki/Special:Export/Wikiquote:Quote_of_the_day/`date +%B_%-d,_%Y` | tac | grep "~" -m 1 | sed 's/&lt;/</g; s/&gt;/>/g; s/<br>/\n/g; s/<[^>]*>//g; s/|[^|]*|//g; s/{{[^}}]*}}//g; s/\[//g; s/\]//g' | sed 's/^ *//; s/  */ /g; s/&#8212;/-/g; s/\&#8217;/'\''/g; s/&quot\;/"/g; s/'\'\''/"/g; s/&#8230;/.../g'
```

**How it works:**

What it does is grab the page [http://en.wikiquote.org/wiki/Special:Export/Wikiquote:Quote_of_the_day/](http://en.wikiquote.org/wiki/Special:Export/Wikiquote:Quote_of_the_day/) Month_Day,_Year for the date your computer is set to. So if this script returns a blank line then the quote of the day for your time has not yet been created.

Using tac and grep it finds the last quote (the final version of the QOTD) with a tilde in it. (the tilde is how the english language wikiquote emphasizes the quoted person).  

Using sed it cleans up the wiki-style source code (first sed command), then converts strange characters and does a bit of formatting too (second sed command). 

Finally it sends this to a zenity dialog.

[img]http://img147.imageshack.us/img147/464/screenshotqu8.png[/img]

I have been using this for a few months now and have had no problems so far (other than the quote of the day being late in getting written)

**To get this to run on start in:** 

**Gnome**: System > Preferences > Sessions > Startup Programs > Add 
Name "wikiqotd"
Command "PATH_TO_FILE"

**IceWM**: nano ~/.icewm/startup
```
#!/bin/sh

# ...

bash PATH_TO_FILE

```

---

### Post by ciroberts on 2009-08-27
Pretty neat! Will try as soon as I get home. Thanks!

---

