---
title: "Awk/Bash scripting newbie needs help"
date: 2010-03-10
forum: Programming Talk
---

### Post by connect404 on 2010-03-10
Hi all, Im attempting to use awk for the first time in a very long time and any help you can give would be gold... either point me in the right direction, or anything you can :)

Im looking to combine the functionality of [rsstail]("http://www.vanheusden.com/rsstail/") and [blogpingr]("http://sourceforge.net/projects/blogpingr") (one written in php and the other in python) to automate watching an rss feed and then pinging it out to a select group of ping services. rsstail is in ubuntu repo and blogpingr is via sourceforge.

Running rsstail as follows
```
rsstail -i 2  -n1 -l -u http://www.engadget..com/rss.xml
```
will output: 
```
Title: Lenovo IdeaPad S10-3t review
Link: http://www.engadget.com/2010/03/10/lenovo-ideapad-s10-3t-review/
```
The -n1 means it only shows the latest entry.. but all new posts will then continue to tail the screen.

I then managed to mash together the following awk code to find "Title:" .. strip it out, and then grab the url only from the next line...
```
| awk  '/Title:/{$1=""; printf "%s ",$0}{getline;$1=""; print}'
```
```
Lenovo IdeaPad S10-3t review http://www.engadget.com/2010/03/10/lenovo-ideapad-s10-3t-review/
```
Unfortunately it doesn't work when I pipe them together, thats the first issue... :)

Then I'm trying to output this to blogpingr which wants it in a format of:

```
blogpingr http://www.engadget.com/2010/03/10/lenovo-ideapad-s10-3t-review/ "Lenovo IdeaPad S10-3t review"
```

Im very stuck, I cant make any of it work together.. what should I do? :)

Thanks all!

---

### Post by DaithiF on 2010-03-10
Hi, I would probably use sed for this rather than awk, but thats just personal preference:

```
cat testfile | sed -n '/Title:/{N;s/Title: \(.*\)\nLink: \(.*\)/\2 "\1"/;p}' | while read url title; do 
   echo blogpingr $url $title
done
```
where obviously your rsstail command would replace the cat testfile piece, and remove the echo before blogpingr command once your happy with the results.

---

### Post by geirha on 2010-03-10
If there's exactly two lines for each feed, then you could simply use a while loop that reads two and two lines
```
#!/bin/bash
while read -r _ title && read -r _ url; do
  echo blogpingr "$url" "$title"
done < <(rsstail -i 2  -n1 -l -u http://www.engadget..com/rss.xml)

```

---

### Post by connect404 on 2010-03-11
> **geirha said:**
> If there's exactly two lines for each feed, then you could simply use a while loop that reads two and two lines


WoW! that works very well... I just had to add
```
"\"$title\""
```
to wrap the title in "'s

This runs now, but Im not convinced its working... when I run blogrping from the command line I get this:
```
brian:/home/tools# blogpingr http://www.xxxxxxxxxxx.com/Sony-Ericsson-W995 "Sony Ericsson W995"
* Pinging Sony Ericsson W995 http://www.xxxxxxxxxxx.com/Sony-Ericsson-W995
* Ping OK: http://api.moreover.com/RPC2
    Thanks for the ping! The update to Sony Ericsson W995 has been updated in our database.  We used parameters - weblogname = Sony Ericsson W995, weblogurl = http://www.xxxxxxxxxxx.com/Sony-Ericsson-W995, changesurl = http://www.xxxxxxxxxxx.com/Sony-Ericsson-W995, categoryname = none

```

But from the bash script you wrote it outputs this.. but nothing follows.. when the next entry is added to the feed I get another blogpinr line, but thats it, not responses.. any ideas?
```
tools@brian:~$ ./autoping
blogpingr http://www.xxxxxxxxxxx.com/Sony-Ericsson-W995 "Sony Ericsson W995"
```


Thanks again for your help!!;)

---

### Post by connect404 on 2010-03-11
/me smacks head!!

Its too early, I didnt even notice the echo :)

---

### Post by geirha on 2010-03-11
> **racerx-dan said:**
> /me smacks head!!

Its too early, I didnt even notice the echo :)

Yes, for "safety". :)

Don't add the extra quotes. Those will become literal and part of the title. You probably don't want that.

---

### Post by connect404 on 2010-03-11
> **geirha said:**
> Yes, for "safety". :)

Don't add the extra quotes. Those will become literal and part of the title. You probably don't want that.

I need them to be literal, as blogrping needs them to wrap the post name, if there are spaces it thinks they are treated as extra args.

Cheers again!

---

### Post by geirha on 2010-03-11
The one set of quotes should take care of that. If not, blogpingr is badly written.

---

### Post by connect404 on 2010-03-11
> **geirha said:**
> The one set of quotes should take care of that. If not, blogpingr is badly written.

Just had a bit of a play and your right, it is working without the quotes... It was when I was testing it with the echo still in place!

---

