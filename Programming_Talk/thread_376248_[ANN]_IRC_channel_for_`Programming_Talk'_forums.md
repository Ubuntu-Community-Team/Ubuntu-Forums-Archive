---
title: "[ANN]: IRC channel for `Programming Talk' forums"
date: 2007-03-04
forum: Programming Talk
---

### Post by lnostdal on 2007-03-04
Hey,
Sometimes it's easier and faster to communicate via IM.  But instead of using closed or "isolated" 1-1 stuff like MSN or Jabber I thought it would be nice if we had a channel we could use.

While I know #ubuntuforums already exists, it isn't really dedicated to programming-related things. #ubuntu-programming seems like a reasonable name, so I've registered that on Freenode. Complete details:

[list]
[*]server: chat.freenode.net
[*]channel: #ubuntu-programming
[/list]

Examples of IRC-clients you can use are XChat and Gaim.

Freenode also has many other channels related to software projects and programming in general. It actually hosts the official channels for projects in many cases, so you can get directly in touch with the developers of your favorite Linux-software. It is worth visiting for anyone interested in Open Source and/or programming.

Hope to see some of you hackers or future-hackers there. :)

edit:
The channel is currently logged here: [http://nostdal.org/~lars/irc-logs/](http://nostdal.org/~lars/irc-logs/) (the "#ubuntu-programming*"-files)

---

### Post by ZylGadis on 2007-03-04
Good idea, coming.

---

### Post by indylarry on 2007-03-04
Thanks for setting that up!  I agree.  It is nice to have real time help from a group.

---

### Post by daniel of sarnia on 2007-03-04
this should be made a sticky so more people that are interested can join it.

---

### Post by studiesrule on 2007-03-05
Another vote for sticky-ing it, and a great many thanks. This would really help the guys with small problems (like me)

---

### Post by hod139 on 2007-03-05
Before stickying it, you might want to consider a name change.  It looks like channels ubuntuforums and ubuntuforums-beginners already exist.  Perhaps this should be called ubuntuforums-programming instead of ubuntu-programming?  Just a thought.

---

### Post by pmasiar on 2007-03-05
IRC is nice and immediate - but do we have archives? Sometimes good solutions worth linking to and becoming FAQ can be posted in forums and be archived and found by Google. Sometimes good suggestion can come couple hours later after question was asked - asynchronously. IRC is synchronized. Will be all good suggestions posted to IRC promptly forgotten? Will be some good gnomes creating a wiki from them?

Just asking, having IRC will be great for simple questions.

---

### Post by lnostdal on 2007-03-06
pmasiar: 
good suggestion .. i was thinking about getting a bot in there and have it log conversations .. like this: [http://www.ircbrowse.com/index.html](http://www.ircbrowse.com/index.html) .. 

i believe the bot is open source (yes, it is: [http://www.cliki.net/irc-logger](http://www.cliki.net/irc-logger) ) .. so if we want we can set up a separate bot + log-site .. 

i'll be sure to look into this later


hod139:
i'm aware of this, but #ubuntu-programming sounds more "general" to me .. 

there are users who develop for ubuntu but does not use the forums .. they use things like mailing-lists etc .. so well, i was thinking everyone should be included

---

### Post by WW on 2007-03-09
* bump *


(Just a reminder.)

---

### Post by po0f on 2007-03-09
How did I not see this until just now?  I think it's a good idea.

So has someone set up a logging bot?  And where are the logs to be hosted?  Maybe a wiki-ish site?

---

### Post by lnostdal on 2007-03-09
i'll look into the logging-bot thing right away .. i can host them and the bot on my server, but i don't really have a suitable domain for this at the moment (can add that later though - if needed)

---

### Post by Wybiral on 2007-03-09
I vote sticky too! It's a really cool idea.

---

### Post by lnostdal on 2007-03-11
ok, logging is up now at: [http://nostdal.org/~lars/irc-logs/](http://nostdal.org/~lars/irc-logs/) (the files named "#ubuntu-programming-*.lml" represent the channel of this announcement)

it's a very simple format meant for parsing by computers .. gonna add a html-frontend to it later .. or maybe put up an xml-rpc service so others can add frontends to it

(source code is here btw: [http://nostdal.org/~lars/programming/lisp/swirc/](http://nostdal.org/~lars/programming/lisp/swirc/) )

---

### Post by lnostdal on 2007-03-15
i've been thinking about something .. does ubuntuforums have some sort of API?

maybe it would be cool to have a bot hooked up to the programming-forums .. when a new thread is posted it could be mentioned in the chat-channel (people could just put an ignore on the bot if/when it becomes annoying)

i was first thinking of doing this by hooking it up via email-subscription, but it seems i can only subscribe to daily batches/summaries of new threads and not get mail instantly when a new thread is posted

---

### Post by Wybiral on 2007-03-15
> **lnostdal said:**
> i've been thinking about something .. does ubuntuforums have some sort of API?

maybe it would be cool to have a bot hooked up to the programming-forums .. when a new thread is posted it could be mentioned in the chat-channel (people could just put an ignore on the bot if/when it becomes annoying)

i was first thinking of doing this by hooking it up via email-subscription, but it seems i can only subscribe to daily batches/summaries of new threads and not get mail instantly when a new thread is posted

That's a pretty cool idea.

---

### Post by lnostdal on 2007-03-15
maybe this is what i'm after: [http://ubuntuforums.org/external.php?type=rss2&forumids=39](http://ubuntuforums.org/external.php?type=rss2&forumids=39) .. :)

---

### Post by hod139 on 2007-03-15
I was going to suggest an RSS reader bot, but it looks like you beat me :)  Hopefully you can design the bot to not put too much extra load on the forums, or the mods might get upset.

---

### Post by lnostdal on 2007-03-15
yeah, the preferred method would be not to have it polling (pull) for new threads directly against the ubuntuforum servers in any way .. getting it to send an email (push) to an external server would avoid this

..or even better; having it send a regular HTTP-request to some given server with some info about the new thread in POST-variables would totally rock :)

---

