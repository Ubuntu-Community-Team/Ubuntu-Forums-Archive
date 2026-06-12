---
title: "Watch BBC news seamlessly with mplayer (quick and easy)"
date: 2007-05-04
forum: Outdated Tutorials &amp; Tips
---

### Post by jamiethehutt on 2007-05-04
Ok I sometimes want to watch BBC news from their site, however I hate RealPlayer with a passion.

You'll need mplayer and the win32codecs package, ubuntuguide.org can tell you how to get those.

First we'll need to make a short bash script:
```
gksudo gedit /usr/bin/ramplayer
```
This script goes:
```
#!/bin/bash
if grep rtsp $1
then
	mplayer `cat $1`
else
	echo "not vaild ram file"
fi
```
Save, close gedit then run
```
 sudo chmod 755 /usr/bin/ramplayer
```
Now you should have a new ramplayer command!

Now in Firefox in the BBC News Player ([link]("http://news.bbc.co.uk/player/nol/newsid_6620000/newsid_6623300/6623383.stm?bw=bb&mp=rm")) click "Launch in standalone player". 

In the download dialog click open with, then other and go to /usr/bin/ and select your new ramplayer command, click "Do this automatically for files like this from now on" and your done!

This should work for other .ram files too but I've only watched BBC ones.

---

### Post by mrgnash on 2007-05-05
Thanks for the handy tip :) I think the first command would be **gksudo** rather than sudo, no?

---

### Post by jocko on 2007-05-05
> **mrgnash said:**
> Thanks for the handy tip :) I think the first command would be **gksudo** rather than sudo, no?

Why would that matter? Both works if you run the command in a terminal.
The only difference is where you type the password...

---

### Post by ifross on 2007-05-05
Running gksudo with graphical applications is better practice than sudo, I'm not 100% sure why, something to do with permissions. Apparently it can hose your system... Anyway here is the link that explains it:

[Click]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by jamiethehutt on 2007-05-05
> **mrgnash said:**
> I think the first command would be **gksudo** rather than sudo, no?
Yeah I suppose so, it's just the command I ran was sudo vim /usr/bin/ramplayer so I never thought.:-P 

It anyone knows any other sites that to .ram streams then it might be good to test it on that. I cant think of any though...

---

### Post by daneel6672 on 2007-06-09
Nice trick, I hate realplayer too, and cannot count the hours I've wasted in RedHat, Mandriva, and now Ubuntu  trying to get this frickin app to view film clips on the bbc news web site.

When I click on "Launch in stand alone player" I get a Download Error dialog box that says

"/tmp/blah.ram could not be opened, because the associated helper application does not exist. Change the association in your preferences."

So I opened up the mime types thing in firefox, Edit -> Preferences -> Content -> File Types, click on Manage. This lets me edit or delete existing mime types, but not to add a new one. The ubuntu wiki doesn't have a topic on adding mime types to firefox.

Suggestions?

---

