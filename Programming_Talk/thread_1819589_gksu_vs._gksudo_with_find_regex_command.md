---
title: "gksu vs. gksudo with find regex command"
date: 2011-08-06
forum: Programming Talk
---

### Post by Paddy Landau on 2011-08-06
I have something I'm finding very odd.

Create a couple of files as follows:
```
[COLOR=DarkSlateGray]$[/COLOR] [COLOR=DarkRed]touch abc.tmp abctmp[/COLOR]
```Now run the following three find commands. Notice how the first three return the correct answer (abc.tmp), but the last one returns both files.
```
[COLOR=DarkSlateGray]$[/COLOR] [COLOR=DarkRed]find . -regextype posix-egrep -regex '.*\.tmp' -print[/COLOR]
./abc.tmp
[COLOR=DarkSlateGray]$[/COLOR] [COLOR=DarkRed]sudo find . -regextype posix-egrep -regex '.*\.tmp' -print[/COLOR]
./abc.tmp
[COLOR=DarkSlateGray]$[/COLOR] [COLOR=DarkRed]gksudo -- find . -regextype posix-egrep -regex '.*\.tmp' -print[/COLOR]
./abc.tmp
[COLOR=DarkSlateGray]$[/COLOR] [COLOR=DarkRed]gksu -- find . -regextype posix-egrep -regex '.*\.tmp' -print[/COLOR]
./abc.tmp
./abctmp
```(Note: gksudo is the same as gksu --sudo-mode.)

This is not exactly a problem for me, but I'd dearly love to understand why gksu does not perform as I expect.

Can you tell me why gksu gives a different answer?

---

### Post by AlphaLexman on 2011-08-06
I honestly don't know the answer, but I can confirm identical results. However, double backslashes in the 'gksu' line gives your expected results...
```
gksu -- find . -regextype posix-egrep -regex '.*\[COLOR="Red"]\[/COLOR].tmp' -print
```

---

### Post by slavik on 2011-08-07
type gksudo
type gksu
gksu which find
gksudo which find
gksu type find
gksudo type find

I think that maybe gksu is an alias or something and the parameters are being interpreted twice.

---

### Post by Paddy Landau on 2011-08-07
> **AlphaLexman said:**
> double backslashes in the 'gksu' line gives your expected results...
I confirm that I get the same result as you.

Weird! I wonder why? But that may give a hint for the answer.

> **slavik said:**
> I think that maybe gksu is an alias or something and the parameters are being interpreted twice.
According to the manual ([FONT=Courier New]man gksu[/FONT] or [FONT=Courier New]man gksudo[/FONT]), [FONT=Courier New]gksudo[/FONT] is equivalent to [FONT=Courier New]gksu --sudo-mode[/FONT].

I've just realised that gksu uses the su backend, and gksudo the sudo backend (unless using --su-mode or --sudo-mode). Read the manual for a better explanation. Therefore, it must be something to do with the difference between su and sudo.

Taking into account AlphaLexman's discovery about the double-backslash, somehow the command must be passed to something that interprets the backslash when using su.

However, both of the following commands give the correct result:
```
sudo su -c "find . -regextype posix-egrep -regex '.*\.tmp' -print"
sudo su -c "find . -regextype posix-egrep -regex '.*\\.tmp' -print"
```Meanwhile, notice the following apparent contradiction. Line 4 supposedly should be the same as line 3.
```
gksu   --sudo-mode -- find . -regextype posix-egrep -regex '.*\.tmp' -print  # Does work
gksudo             -- find . -regextype posix-egrep -regex '.*\.tmp' -print  # Does work
gksu               -- find . -regextype posix-egrep -regex '.*\.tmp' -print  # Does not work
gksudo --su-mode   -- find . -regextype posix-egrep -regex '.*\.tmp' -print  # Does work
```I remain nicely in the dark! :confused:

---

