---
title: "Bash: Incremental searching with Up and Down :)"
date: 2005-07-15
forum: Outdated Tutorials &amp; Tips
---

### Post by ghostintheshell on 2005-07-15
Yo, I found what I was searching for a long time  \\:D/ 

What? 

Incremental searching with Up and Down in a terminal

How? 

- Open (or create) the *.inputrc* file in your home directory (*~/.inputrc*)
- Add these lines:

[color=Navy]"\e[A": history-search-backward
"\e[B": history-search-forward[/color]

If that prevents Left and Right from working, fix them like this:

[color=Navy]"\e[C": forward-char
"\e[D": backward-char[/color]

Close your terminal, re-open it and give it a try:
type *ls foo*
type *foo*
and now type *ls* followed by the up key --> it's magic  \\:D/ 

And now enjoy your terminal :grin:

---

### Post by doclivingston on 2005-07-15
You gotta love it when someone tell you something like this, and you say "why haven't I known about this for the past few years?".

Cheers.

---

### Post by ghostintheshell on 2005-07-15
He he ... you should love this too:

Add these lines in your *~/.bashrc* file:

[color=Navy]#Make Bash correct small typos when moving to another directory
shopt -s cdspell[/color]

then restart your terminal and try:
*cd /ec* or *cd /ur/locl*

:-\"

Another one:

Add this line in your *~/.inputrc* file:

[color=Navy]set show-all-if-ambiguous on[/color]

now, restart your terminal and enjoy the real power of the <TAB> key ;)

---

### Post by professor_chaos on 2005-07-15
why haven't I known about this for the past few years?

Thats very useful, thxs for posting.

---

### Post by doclivingston on 2005-07-15
I already knew about "shopt -s cdspell", but it doesn't seem to do anything for me.

```
export HISTIGNORE="&:[bf]g:exit"
``` is handy, it ignores bg, fg and exit when using the command history.

---

### Post by ghostintheshell on 2005-07-16
Yo, another useful tip for the terminal killers we are :D

open *~/.bashrc*
uncomment these lines:

```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
#if [ -f /etc/bash_completion ]; then
#	. /etc/bash_completion
#fi
``` 

=>

```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
	. /etc/bash_completion
fi
``` 

save, close. restart your terminal and try:
[color=Purple]*ls --c*[/color] followeb by the [color=Purple]<TAB>[/color] key
or
[color=Purple]* rm --*[/color] followeb by the[color=Purple] <TAB>[/color] key

\\:D/

---

### Post by jaac on 2005-07-16
Very nice tips :)

Anyone know how to have tab complete in a sftp session? that would be a great tip ;)

---

### Post by Caboto on 2005-07-16
Some very cool tipps. Big thanks! I specially love the incremental searching thingie.  :grin:

---

### Post by geearf on 2005-07-16
Hello,

thanks for this how to, i can become very usefull.

But i still believe i won"t stay long with the first tweak, cause then if i wanna do somethink like nano .inputrc, then i realise i aint in the right directory, i need to go to the beginning of the line to get my old "cd".

Anyway, thanks

---

### Post by ghostintheshell on 2005-07-16
[QUOTE=geearf]Hello,

thanks for this how to, i can become very usefull.

But i still believe i won"t stay long with the first tweak, cause then if i wanna do somethink like nano .inputrc, then i realise i aint in the right directory, i need to go to the beginning of the line to get my old "cd".

Anyway, thanks[/QUOTE]

*** I don't understand the problem but if it is a 'key' problem you can configure it like you want!
[color=Navy]
"\e[A" [color=black]= the up key[/color]
[/color][color=Navy]"\e[B" [color=black]= the down key[/color]

[color=black]but you can use, for example:[/color]
[/color]
 [color=Navy]"\e[/color][color=Navy][5~" [color=black]= the page up key[/color]
[/color][color=Navy]"\C-n[/color][color=Navy]" [color=black]= CTRL + 'n' key

[/color][/color][color=Navy][color=black]more help on the web ([google]("http://www.justfuckinggoogleit.com/")) or simply[/color][/color][color=Navy][color=black] [here]("http://www.linuxgazette.com/issue55/henderson.html") 
[/color] 
[color=black]*** You can also make different sections in your *~/.inputrc* file for different applications:[/color]
[/color]
for example:

 ```
$if mode=emacs
(...)
$endif

$if Bash
(...)
$endif

$if Ftp
(...)
$endif
``` 
[color=Navy]
[color=black]more help on the web ([google]("http://www.justfuckinggoogleit.com/")) or simply [here]("http://www.linuxselfhelp.com/gnu/bash/html_chapter/bashref_8.html")[/color]
[/color]
I don't test it but it is the idea ... Try it before give up ;)

Enjoy.

---

### Post by geearf on 2005-07-16
Hello,

yes it was only a key problem, cause i like the way up and down work 
you are right, i will try with other keys and it will be perfect thanks.

---

### Post by pgmario on 2005-07-18
Thanks a lot! I was looking for this kind of completion ever since owning a Linux box and only using my ibook when I'm on the road. OS X has this behaviour enabled by default. Much more convenient than CTRL+R.

---

### Post by frodon on 2005-07-19
Don't work at all for me !
It do absolutly nothing, why ? It doesn't work with tcsh terminal ?

EDIT : after some tests it seems that hotkey doesn't work with tcsh or the syntax should be different.

---

