---
title: "need grep regular expression for link grabbing"
date: 2006-09-19
forum: Programming Talk
---

### Post by pedrotuga on 2006-09-19
i am looking for a shell regular expression to use with grep and the -o parameter so i can match all [http://..........mp3](http://..........mp3) ocorrences.

basicaly i want to perform some bach downloads...

i think the easyest way is:
1.dload the page with curl
2.get all the links pointing to mp3 files into a text file using grep
3.dload all those files using wget

this gives me more control over the dload than simple wget usage... besides some wget full site dload dont get al the files for some reaon i dunno.

so.. my problem... i need a regex to use with grep that maches all the mp3 urls.

does anybody has something?

---

### Post by ghostdog74 on 2006-09-20
> **pedrotuga said:**
> i am looking for a shell regular expression to use with grep and the -o parameter so i can match all [http://..........mp3](http://..........mp3) ocorrences.

basicaly i want to perform some bach downloads...

i think the easyest way is:
1.dload the page with curl
2.get all the links pointing to mp3 files into a text file using grep
3.dload all those files using wget

this gives me more control over the dload than simple wget usage... besides some wget full site dload dont get al the files for some reaon i dunno.

so.. my problem... i need a regex to use with grep that maches all the mp3 urls.

does anybody has something?

I don't have a grep,curl,wget solution. here's an example all in Python:

```

#!/usr/bin/python
import re,urllib2,urllib
htmlpage = urllib2.urlopen("http://www.google.com").read()
alllinks = re.findall('<a href=(.*?)>.*?</a>',htmlpage)
count=1
for links in alllinks:
    if "mp3" in links:
        urllib.urlretrieve(links,"file-%d.html"%count)
        count += 1
       

```

---

### Post by pedrotuga on 2006-09-20
> **ghostdog74 said:**
> I don't have a grep,curl,wget solution. here's an example all in Python:

```

#!/usr/bin/python
import re,urllib2,urllib
htmlpage = urllib2.urlopen("http://www.google.com").read()
alllinks = re.findall('<a href=(.*?)>.*?</a>',htmlpage)
count=1
for links in alllinks:
    if "mp3" in links:
        urllib.urlretrieve(links,"file-%d.html"%count)
        count += 1
       

```

i don know so much about python... is there a way to pass the url as a parameter in the CLI?

like... 
```
python myscrip.py http://mysite.com
```

---

### Post by cwaldbieser on 2006-09-20
> **pedrotuga said:**
> i don know so much about python... is there a way to pass the url as a parameter in the CLI?

like... 
```
python myscrip.py http://mysite.com
```

```

import sys
url = sys.argv[1] #url is now the first argument after the program name.

```

---

### Post by pedrotuga on 2006-09-20
> **cwaldbieser said:**
> ```

import sys
url = sys.argv[1] #url is now the first argument after the program name.

```


thats cool.

can i use something like this to pass the filetype as well?

```

import sys
url = sys.argv[1] #url is now the first argument after the program name.
filetype = sys.argv[2];

```


btw, how are the arguments separated? by spaces?


ps: if anybody still has a shell regular expressionj for links that would be apreciated

---

### Post by ghostdog74 on 2006-09-20
yes, they are separated by spaces.

---

### Post by skymt on 2006-09-20
You can actually do it all in wget, something like this:```
wget -r -l 1 -A mp3 http://www.example.com/mp3.html
```"-r" means recursive download, "-l 1" means one level, "-A mp3" means only download mp3 files.

There. One step.

---

### Post by pedrotuga on 2006-09-20
> **skymt said:**
> You can actually do it all in wget, something like this:```
wget -r -l 1 -A mp3 http://www.example.com/mp3.html
```"-r" means recursive download, "-l 1" means one level, "-A mp3" means only download mp3 files.

There. One step.

yep.. that works for most of the sites... but i tryed it on a myltiply.com page and it didnt work....

i tryed already fetching the links from the page manualy and paste them in a text file that i use later as source for wget... it worked cool.
thats basically why i wanted that regex.

also, it can be very practical for several purposes.. for example if one wants to make a script to create a sitemap, or something like that.

---

### Post by skymt on 2006-09-20
```
http://[^[:space:]]*.mp3
```See if that works. You can use the -o option in the latest GNU Grep to only output the text that matches, rather than the whole line, which is the default.

EDIT: Fix Perlism.

---

### Post by pedrotuga on 2006-09-20
> **skymt said:**
> ```
http://[^[:space:]]*.mp3
```See if that works. You can use the -o option in the latest GNU Grep to only output the text that matches, rather than the whole line, which is the default.

EDIT: Fix Perlism.


OMG! it works like a charm!
thanks a billion skymt!
thanks a million everybody!

```
curl -U Mozilla http://yourpage.com/bla.html > page
grep -o http://[^[:space:]]*.mp3 page > links
wget -i link
```dont ask me why... but this works beter than wget alone.
for some reason wget doesnt get all files...

i think this can be very practical to schedulle downloads.

i think i will use >> instead of > then keep an archive of all the files i want to dload, then launch wget when i am not using my computer.
this can also ve practical for those with download limits. A cronjob pointing to the beggining of the happy-hour (no traffic limits) would save a lot of bandwidth.

BTW, is this correct shell regex sintax
http://[^[:space:]]*.(mp3|wma|ogg)
?

---

### Post by skymt on 2006-09-20
> **pedrotuga said:**
> OMG! it works like a charm!
thanks a billion skymt!
thanks a million everybody!You're welcome! Glad it worked! :D > **pedrotuga said:**
> BTW, is this correct shell regex sintax
http://[^[:space:]]*.(mp3|wma|ogg)
?Sorry, no. Shells (at least, not any of the usual suspects like bash, tcsh, or zsh) don't support regexs. What they support is globbing, which is like regex for dummies. In a shell, the easy, cross-shell way would be "*.mp3 *.wma *.ogg".

Unless you mean proper syntax for the grep command, in which case the answer is yes, with two problems. Basic regular expressions (the default for GNU grep) don't understand "(" "|" or ")" as meaning anything special (they just match themselves). Your expression (with the change I'm about to explain) would work with egrep or grep -E (the two commands are equivalent).

The problem with your expression as a regular expression is that "." means "any character". So, you have to use "\.":```
http://[^[:space:]]*\.(mp3|wma|ogg)
```For information on regular expressions, look up the grep [documentation](http://www.gnu.org/software/grep/doc/).

---

### Post by pedrotuga on 2006-09-21
I am trying to use a regular expression to match any http link.
I tryed this but it doesnt work

```
grep -o http://[^[:space:]]*.[^\"[:space:]] file > youroutputfile.txt
```

it output stuff like this

```

http://tek.sapo.pt/"><img s
http://tek.sapo.pt/comp/><img s
http://tek.sapo.pt/perif/"><img s
http://tek.sapo.pt/soft/"><img s
http://tek.sapo.pt/net/"><img s
http://tek.sapo.pt/tlm/"><img s
http://tek.sapo.pt/tele/"><img s
http://tek.sapo.pt/bus/"><img s
http://tek.sapo.pt/stat/"><img s
http://tek.sapo.pt/4R/454251.html"><area s
http://tek.sapo.pt/pessoas/"><area s
http://tek.sapo.pt/4E6/110688.html"><area s
http://tek.sapo.pt/4U/275011.html"><area s
http://newsletters.sapo.pt/tek/"></map></td>

```

i dont get what's wrong... didnt i specified NOT to match " ???
why does it match?

---

### Post by pedrotuga on 2006-09-21
ok, i didnt read you answer with enough atention... i had in mind that you said that "." would mach only itself instead of the oposite.

i got to the solution

```
 grep -o -e http://[^[:space:]\"]* srcfile > destfile

```

\\:D/\\:D/\\:D/

thanks guys

---

### Post by HeavyMetaler on 2008-08-08
Why not go crazy and just do it all without writing to a file.   Meet xargs.

```

#!/bin/sh
url=$1
curl $url | grep -o <regex here> | xargs wget

```

---

### Post by slavik on 2008-08-08
give -n 1 to xargs, or shell might complain (if all the parameters won't fit on the cmdlin).

---

### Post by mssever on 2008-08-08
Why resurrect a two-year-old thread?

---

### Post by ghostdog74 on 2008-08-08
because that's his post number 2.

---

### Post by Sockerdrickan on 2008-08-08
And people using Google will find this very useful.

---

### Post by Joeb454 on 2008-08-08
> **mssever said:**
> Why resurrect a two-year-old thread?

Agreed - Thread Closed

---

