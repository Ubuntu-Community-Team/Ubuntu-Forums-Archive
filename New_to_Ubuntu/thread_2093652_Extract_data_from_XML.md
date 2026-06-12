---
title: "Extract data from XML"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by mrblonde1369 on 2012-12-11
Hi everyone, I hope I've chosen the right section to post my question.

I am trying to work with some XML data, and being completely ignorant in XML, PHP, and programming in general, I'd like to ask you fellows some help.

I have hundreds of XML file, all with the same structure, which looks like this - I can't find a way to keep the format of XML in this post...:

> <wordsketch corpname="preloaded/itwac"><keyword pos="-n" freq="35080">dente</keyword><gramrel><grname hits="339" score="1.3">n_modifier</grname><collo hits="76" score="11.1" query="w16558204">duola</collo><collo hits="9" score="8.8" query="w16558242">mascellaro</collo><collo hits="2" score="7.5" query="w16558244">bickla</collo><collo hits="3" score="6.81" query="w16558210">asintomatico</collo>

there are different "gramrel" for each file, I've just copied here the first one.

What I need to do is to automatically go through all the XML files, and when the script/program find a specific word in the <collo> tag, then it adds it to an output file which contains the following:

keyword (in the <keyword> tag),the word (in the <collo> tag), hits (in the <collo> tag) and score (in the collo <tag>).

Can anyone suggest an easy way to do this? maybe with a bash script?

thanks a lot in advance

---

### Post by NM5TF on 2012-12-11
there is an article that might get you started using xmlstarlet
to do what you want.....go here:

[http://aggregator.foolab.org/node/53327](http://aggregator.foolab.org/node/53327)

or possibly by using awk....go here for more info:

[http://ubuntuforums.org/showthread.php?t=1913589](http://ubuntuforums.org/showthread.php?t=1913589)

Tommy

---

