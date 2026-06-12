---
title: "[SOLVED] Anyone familiar with bashish?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by m_ad on 2008-09-23
I just installed bashish and thought I configured everything correctly. Is it normal to get this EVERY time I start gnome-terminal?

```
bashish: please select the profile [New Bashish Tab]
bashish: and press [RETURN]

```

as soon as I press return it gets right to the bash prompt (modified to the theme I selected with 'bashishtheme,' but this is quite annoying every time I lauch gnome-terminal.

---

### Post by unutbu on 2008-09-23
Type
```

grep $USER /etc/passwd

```
This will show you a line from your /etc/passwd file. It might look something like

```

m_ad:x:1000:1000:M_Ad,,,:/home/m_ad:[COLOR="Red"]/bin/bashish[/COLOR]

```

The last colon-separated field is your default shell.
Check if bashish has changed this to bashish instead of the usual /bin/bash.

If it has, you can restore bash as your default shell by typing
```

sudo usermod --shell /bin/bash $USER
```

---

### Post by m_ad on 2008-09-23
This isn't the case, the shell is still set to /bin/bash.


I'm thinking that it's something that bashish modified in ~/.bashrc.. here are the lines in .bashrc that were added by bashish:

```
BASHISHDIR=`bashish --bashishdir`                             ## line added by bashish
test "$BASHISH_OLDPATH"||BASHISH_OLDPATH=$PATH                ## line added by bashish
TTY=`tty`                                                     ## line added by bashish
PATH=$HOME/.bashish/launcher:$BASHISHDIR/lib:$BASHISH_OLDPATH ## line added by bashish
BASHSIH_CP=437                                                ## line added by bashish
. _bashish_utfcheck && BASHISH_CP=utf8                          ## line added by bashish
ENV=$HOME/.profile                                            ## line added by bashish
export BASHISH_OLDPATH TTY ENV                                ## line added by bashish
bashish                                                       ## line added by bashish
. $BASHISHDIR/main/prompt/sh/init                             ## line added by bashish
```

I think it has something to do with the line 'ENV=$HOME/.profile'?

---

### Post by m_ad on 2008-09-23
Any other ideas unutbu? :)

---

### Post by unutbu on 2008-09-23
The message 
> 
please select the profile [New Bashish Tab]

comes from these lines in the "termhandler" file:
```

			printf "bashish: please select the profile [New Bashish Tab]\nbashish: and press [RETURN]"
			read -n1
			printf "\033[H\033[2J"
	
```

If you edit this file you can comment out these three lines to get rid of the message and the need to press return.

If you installed bashish from a deb package, then you can find where termhandler is installed by typing ```

dpkg --listfiles bashish | grep termhandler
```
(assuming the package is called bashish).
If that doesn't work, then try ```

sudo find / -name "termhandler" -print
```
It may take a few minutes, but it will find it.

Then type 
```

gksu gedit /path/to/termhandler
```

You will find the three lines that need commenting-out around line 105 (about 3/4 of the way down the file).

---

### Post by m_ad on 2008-09-23
This is set to where it should be.. /bin/bash. I executed the command to be sure, and the problem persists.

I screwed up gnome-terminal even more now. I decided to do what it said and select the profile as [New Bashish Tab]. This didn't only make my gnome-terminal settings worse (no toolbars, or scrolling), but it didn't fix the problem either.

---

### Post by m_ad on 2008-09-23
heres a screenshot, I cant access the toolbar or anything else..

---

### Post by unutbu on 2008-09-23
I edited my last post before seeing your latest posts. Sorry for the confusion.

If you right-click in the gnome-terminal window, can you enable the "Show Menubar" option? This may give you your menu bar back.

Then perhaps try uninstalling bashish, delete the ~/.bashish directory, and then re-installing. Then try what I posted in my previous post.

---

### Post by m_ad on 2008-09-23
LOL, thanks for the help on getting my toolbar back. I didn't realize I could right click my terminal.

I'm going to try this when I get home, I have class until 9:00pm so I'll respond as soon as I can. I hope you're still around, unutbu. I appreciate all your help so far.

---

### Post by unutbu on 2008-09-23
After studying the termhandler script some more, I think I know what it saying :)
> 
"please select the profile [New Bashish Tab]"

means "Please click on Edit>Profiles in the gnome-terminal window and select the profile
called '[New Bashish Tab]'".

I would try this before editing termhandler.

---

### Post by m_ad on 2008-09-23
Yeah, this is actually what I did and all it does is change the appearance of the terminal. It doesn't get rid of the annoying prompt everytime I start gnome-terminal..

---

### Post by m_ad on 2008-09-24
Anyone have any other ideas?

---

### Post by unutbu on 2008-09-24
Did you try commenting out the three lines as described in [post #5]("http://ubuntuforums.org/showpost.php?p=5841763&postcount=5")? It might not be the proper way (if there is a proper way) but it should be effective.

---

### Post by m_ad on 2008-09-24
Wow, unutbu, that worked. I wonder why they would add that in the program if it can't be fixed without editing their source? Seems like that statement would be followed by some sort of condition..

I can't thank you enough for sticking with me in this thread to help me solve this issue, it's not a big one but theres nothing more I appreciate than someone to help throughout a problem. Thanks again!

---

### Post by unutbu on 2008-09-24
You are most welcome. I am happy (and surprised) that I could help.

---

### Post by oarion7 on 2010-05-07
FYI the newest versions of bashish has resolved this issue:
[http://freshmeat.net/projects/bashish](http://freshmeat.net/projects/bashish)

:popcorn::guitar:

---

