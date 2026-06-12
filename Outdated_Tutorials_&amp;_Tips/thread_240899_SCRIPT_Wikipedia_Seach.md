---
title: "SCRIPT: Wikipedia Seach"
date: 2006-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by its_me_gb on 2006-08-21
ok, this is the first script i've written and is very simple :D

i got fed-up of having to open my browser to search for items on wikipedia, so i wrote this.

it uses zenity, so check its installed... or something.

paste into a text editor and save.

chmod +x /path/to/file

and you're sorted. i placed it in my ~/.gnome2/nautilus-scripts/ folder so that i could access it from the desktop. 

it's simple but does what i want.

enjoy  

```

#!/bin/bash
baseurl="http://en.wikipedia.org/wiki/Special:Search?search="
if foo=`zenity --entry --title="Search For..." --text="What are you searching for?"`
then fullurl=${baseurl}${foo}
     firefox ${fullurl}
else
exit
fi

```

---

### Post by marcw on 2006-08-25
Similarly, I adapted a MW Dictionary javascript to do Wikipedia.

Create a Firefox toolbar bookmark with the following properties (The location script must be all one line):

Name:```
Wikipedia
```

Location:```
javascript:Qr=document.getSelection();if(!Qr){void(Qr=prompt('Enter word to find in Wikipedia:',''))}if(Qr)location.href='http://en.wikipedia.org/wiki/'+escape(Qr)+' '
```

Now when you have a word highlighted on a web page and click the Wikipedia toolbar link, the Wikipedia entry for that word will appear on a new page.  Also, if no word is highlighted when you click the Wikipedia toolbar link, a prompt window will open in which you can type a word to look up in Wikipedia.

I have attached a screenshot of what it looks like in my browser.

---

