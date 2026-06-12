---
title: "amixer get 'Master' | grep [on]?"
date: 2007-07-21
forum: Programming Talk
---

### Post by jmc1024 on 2007-07-21
I'm trying to write a script to toggle sound on and off.   How do I escape the braces in the grep command so that they are part of the search pattern?

amixer get 'Master' | grep [on]       
if [ 0 -e $? ];
then
    amixer set 'Master',0 mute
else
    amixer set 'Master',0 unmute
fi

I guess I could send amixer's output to /tmp/trash and then grep that, but I hate generating trash if I don't have to.

Thanks,
Mark

---

### Post by scxtt on 2007-07-21
this seems to work:

:> cat test.txt
this is a [test].
this is a {test}.

:> cat test.txt | grep "\[test\]"
this is a [test].

---

### Post by aanderse on 2007-07-21
hey

to [toggle] mute amixer you could do something like this

amixer -q set Master toggle
amixer -q set PCM toggle
etc ...

-q stands for quiet so no text output is spewed

---

### Post by jmc1024 on 2007-07-21
Okay double quotes _and_ escape characters.  
Thanks, Mark

---

### Post by jmc1024 on 2007-07-21
Hmmm....  Didn't see than in the amixer man page but it does in fact work.  Oh well, I learned two things today.
Thanks, Mark

---

