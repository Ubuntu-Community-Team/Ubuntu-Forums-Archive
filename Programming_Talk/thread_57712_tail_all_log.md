---
title: "tail all log"
date: 2005-08-17
forum: Programming Talk
---

### Post by student on 2005-08-17
I'm trying to make a tailer for all logfiles, but I cant seem to find a way to test if a file is a textfile.

```
FILES=$( ls /var/log/* )
while true ; do
  for file in $FILES
  do
     if [ -N $file ] && [ -f $file ] && [ -r $file ] ; then
	tailer=$( tail -n 1 $file )
	if [ "$tmp" != "$tailer" ] ; then
	   echo $tailer
	   tmp=$tailer
	fi
     fi
   done
done
exit 0
```

---

### Post by LordHunter317 on 2005-08-17
I'm confused by what you want to do in the first place: why?

And why bother checking?  If the user is dumb enough to tail a file that might be binary, they deserve to get gibberish spewed on their screen.

---

### Post by student on 2005-08-17
[QUOTE=LordHunter317]I'm confused by what you want to do in the first place: why?

And why bother checking?  If the user is dumb enough to tail a file that might be binary, they deserve to get gibberish spewed on their screen.[/QUOTE]

and the checking is done how ?

---

### Post by LordHunter317 on 2005-08-17
It isn't, that was my point.  You should code in the names of the logfiles, or look them up from some source like /etc/syslog.conf (which will be hell to do in bash).

Otherwise, you let the user provide the names, and if the file is binary, you just tail it.  You assume the user knwos best.

I still don't understand why you're doing this.  If you want an agrregate log to tail, set one up in /etc/syslog.conf.

What you're trying to do is bad, for a bunch of reasons.

---

### Post by student on 2005-08-17
just because I want to tail all the logs in /var/log/ even when suddonly one is added for some reason, and without checking files each loop.

---

### Post by LordHunter317 on 2005-08-17
But you don't want to do that.  Logs won't show up often, and it's not a burden on the administrator to change the script when they have to change syslog.conf anyway.

**Why** are you writing this application in the first place?  What purpose does it serve?  Moreover, what does it do beyond what syslogd already provides?

You need to answer those questions first.

---

### Post by student on 2005-08-17
because this provides me with a little eterm at the bottom of my desktop,
with all the logged events showing up. And I want it this way.
[screenshot](http://users.pandora.be/kenoste/screen.jpg)

---

### Post by LordHunter317 on 2005-08-17
[QUOTE=student]because this provides me with a little eterm at the bottom of my desktop,
with all the logged events showing up. And I want it this way.
[screenshot](http://users.pandora.be/kenoste/screen.jpg)[/QUOTE]
 Then either setup a single log file to tail that has all the information you want loaded in, or setup a pipe to /dev/xconsole and tail that.  The latter is probably preferrable.

Doing what you want won't work: for starters, the odds of missing a message are quite high.  Not to mention the terribly nasty system load.

---

### Post by student on 2005-08-17
```

FILES=$( ls /var/log/*log  /var/log/messages /var/log/debug /var/log/aptitude )
while true ; do
for file in $FILES
do
	if [ -N $file ] && [ -f $file ] && [ -r $file ] ; then
	  	tailer=$( tail -q -n 1 $file | tr &#8722;d "\"'" )
	  	if [ "$tmp" != "$tailer" ] ; then
			echo "$tailer"
			echo
			tmp=$tailer
		fi
	fi
done
sleep 1
done
exit 0
 
```

I can live with my script here, this give's me a total system load at this moment of 2%

---

### Post by LordHunter317 on 2005-08-17
Too bad it's going to miss messages, on a fairly regular basis to boot if your system has regular load.  And it's going to duplicate messages.

Why are you so hellbent on using a script.  Look up the documentation on syslog.conf.  You can configure a custom log to give you exactly what you want, in a manner that's easy to provide to X.

Hell, I'd even tell you how to do it if you'd tell me what you wanted.   But I can't help you if you won't help me.

---

### Post by super on 2005-08-17
i would like to do something similar, but i have don't know how to write scripts.

what i would like is for all my system logs printed onscreen thru osd-cat. (or osd-tail, or whatever it's called) bu i would like it to show all messages from the system. for example if i used the 'run' command from the menu and typed [FONT=Courier New]updatedb -v[/FONT] i want the output to be printed on the screen. (as if i was using a terminal)

is this possible? could you tell me how?

---

### Post by student on 2005-08-17
ok   :smile: 
I just want my little bottom eterm to list all events.
But why would I miss messages ? could there be more than 1 line change in every log, within 1 second ? dunno really...

and oh, I like programming, kinda learning bash right now   :razz:

this is my command:
```
Eterm -O --no-cursor --icon-name tailer --font-fx bottom_right black --shade 0 -x --buttonbar 0 --scrollbar 0 -g 140x10+230+860 -e /home/vuurtje/tailer
```

---

### Post by LordHunter317 on 2005-08-17
[QUOTE=student]But why would I miss messages ? could there be more than 1 line change in every log, within 1 second ? dunno really...[/quote]Yes.  Mailservers are good at that, especially in the face of bounced mail.  Certain daemons on startup, as well.

Samba, all the time really, because of it's rather broken logging.


> and oh, I like programming, kinda learning bash right now   :razz:That's fine, but a good system administrator uses the best tool for the job.  This isn't the best tool.

---

