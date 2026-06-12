---
title: "[SOLVED] zenity &amp;quot;eating&amp;quot; clipboard contents?"
date: 2008-01-17
forum: Programming Talk
---

### Post by Phrawm48 on 2008-01-17
I'm just beginning to write some small BASH scripts.

I recently put together this little script that uses *xclip* and *zenity* to display a Gnome (GUI) info box with the number of words and characters contained in the primary clipboard.

```
1 #!/bin/bash
2 
3 words=$(xclip -out primary | wc --words)
4 chars=$(xclip -out primary | wc --chars)
5 
6 zenity --info --title='Words (Characters)' --text="Words=$words (Chars=$chars)"
7 
8 # echo "echo words=$words chars=$chars"

```The script works fine -- once -- but the problem I'm having is that the script doesn't produce the same output if it's run twice.  More specifically, it appears that *zenity* is clobbering (or if you prefer, "eating") the contents of the clipboard.

If I comment out line 6, ("*zenity*...") and un-comment line 8 (*echo*...") I can run the script again and again and the script will repeatedly redisplay the number of words and characters in the clipboard.  No problem.

But if I reverse the commenting so as to use *zenity* to display the results of the *xclip* command, only the first iteration works properly -- the second iteration displays 0 and 0 (zero and zero).  I then have to reselect text to make the script display a non-zero value.

Everything troubleshooting method I've tried (such as *unset*'ing the variables in the script) produces the same result -- *zenity* appears to be "eating" the contents of the clipboard.

Can anyone please suggest some alternative troubleshooting methods or perhaps tell me how my script is deficient?

Cheers & thanks,
Ric

---

### Post by Phrawm48 on 2008-01-17
Okay, I found a fix for my *zenity* problem, or at least a circumvention.

I rewrote the script as follows:
```

1 #!/bin/bash
2 # Script to count words and characters of primary clipboard selection.
3
4 # Create a working copy of primary clipboard in cselection.
5 cselection=$(echo $(xclip -selection primary -out))
6
7 # Create variables for the number of words and characters.
8 words=$(echo $cselection | wc --words)
9 chars=$(echo $cselection | wc --chars)
10
11 # Use zenity to display a GUI information message.
12 zenity --info --title='Words (Characters)' --text="Words=$words (Chars=$chars)"
13
14 # Because zenity appears to empty clipboard, copy selection back into
15 # clipboard after running zenity.
16 echo $cselection | xclip -selection primary 

```The "fix" is in line 16, which "resets" the contents of the clipboard after running *zenity*.

Probably I'll cringe at this script after I've acquired a bit more experience, but for now it enables multiple iterations...

Cheers & hope this helps,
Ric
SFO

---

