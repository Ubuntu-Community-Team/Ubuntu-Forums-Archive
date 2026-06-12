---
title: "vi customization problem"
date: 2013-03-27
forum: Programming Talk
---

### Post by shashanksingh on 2013-03-27
I have to work on a really old AIX workstation with vi version 3.10 in it.
I have done a little work in vim, but that was much more easy to use than the old vi (atleast untill I get used to the old vi).

Since I have been using the backspace key to erase my previous character for ever since I was born, I would like to have that functionality in vi as well.

I did search for a solution.

I found the following:

1 :set backspace=2 (:set all does not have a backspace option, nor nocompatible)
2. [COLOR=#000000][FONT=verdana]stty erase ^?  (Didn't work)[/FONT][/COLOR]
3. In .exrc file in my home directory, I can set up a mapping. ie, map <key> <key to be>.
    However, in the edit mode in vi, pressing backspace actually takes my cursor to one position on the left.

How do I map a supposedly arrow key to make it perform the function of a backspace?

---

### Post by schragge on 2013-03-27
[LIST=1]
[*]Check the output of stty:
```
[COLOR=green]$[/COLOR] stty -g|cut -d: -f7
[COLOR=green]7f[/COLOR]

```
or the same in human readable form: ```
[COLOR=green]$[/COLOR] stty -a|sed -n 's/.* \(erase [^;]*\).*/\1/p'
```
For stty from GNU coreutils this should give ```
[COLOR=green]erase = ^?[/COLOR]
```
For stty on Solaris (and probably on AIX, too): ```
[COLOR=green]erase = DEL[/COLOR]
``` 
[*]Check that the mapping is set up properly:
```

[COLOR=green]$[/COLOR] cat ~/.exrc|tr \\b @|sed -n '/:map.* @$/p'|od -cAn
[COLOR=green]   :   m   a   p   !     177       @  \n[/COLOR]
```
You should get similar output. 
[/LIST]

---

### Post by shashanksingh on 2013-03-27
> **schragge said:**
> Check the output of stty:
```
[COLOR=green]$[/COLOR] stty -g|cut -d: -f7

``` -> This gave me '**ff**'

> 
or the same in human readable form: ```
[COLOR=green]$[/COLOR] stty -a|sed -n 's/.* \(erase [^;]*\).*/\1/p'
```
 On AIX -> ' [COLOR=#008000]**erase = ^?** '[/COLOR]

> 
Check that the mapping is set up properly:
```

[COLOR=green]$[/COLOR] sed -n '/\ch/p' ~/.exrc|od -aAn
[COLOR=green]   :   m   a   p   !  sp del  sp  bs  nl[/COLOR]
```
You should get the same output.



I haven't really set any mappings in .exrc.
The problem is when I do 'vi .exrc'
and type 'map <backspace> ', it moves my cursor one step left to the space. It doesn't put anything after the word map.
So I was wondering since backspace is acting like an 'h' or 'left arrow', how do I represent it as text? 

In the insert mode:      backspace = move cursor one step left[INDENT=4]del = Change case of character[/INDENT]
In the command mode: backspace = function of delete or x[INDENT=4]del = Change case of character[/INDENT]

This is very weird. :confused:

---

### Post by schragge on 2013-03-27
In vi, you enter any control character by quoting it with **Ctrl**+**V** (e.g. see [this answer]("http://unix.stackexchange.com/a/23267")). This means: to enter <backspace>, press **Ctrl**+**V** **Backspace**, to enter [COLOR=blue]^H[/COLOR] press **Ctrl**+**V** **Ctrl**+**H**.

Another thought. I've compiled and installed the [traditional vi]("http://ex-vi.sourceforge.net/"). **Backspace** in it actually _deletes_ characters left of the cursor, although they remain displayed until you exit the insert mode by pressing **Esc**. This is even documented in the [tutorial]("http://ex-vi.sourceforge.net/viin/paper-3.html#section17"):
> Notice that when you backspace during an insertion the characters you backspace over are not erased; the cursor moves backwards, and the characters remain on the display.  This is often useful if you are planning to type in something similar.  In any case the characters disappear when you hit ESC; if you want to get rid of them immediately, hit an ESC and then **a** again.

I can also observe the same behaviour in [nvi]("http://manpages.ubuntu.com/manpages/precise/en/man1/nvi.1.html").

---

### Post by shashanksingh on 2013-04-02
Thanks you for the help :)

I just realized that my vi has the same behavior (it is version 5 something).

What I now know is that my delete key puts a ~ in the insert mode, and changes the case in command mode. 
My backspace key in insert mode moves my cursor one left and deletes the character on the cursor (although it will reflect AFTER a mode switch), and in my command mode, it does what Ctrl+x does, i.e., erase character under cursor.

But when I used vim, backspace and delete worked just as commands in real time at insert mode (a backspace reflected a backspace and del could do what Ctrl+x does).
Can I possible do that in traditional vi?
I would also like to map an 'Esc+\' to a 'Tab+Tab', to auto-complete the way it is done in bash.

Thanks,

---

