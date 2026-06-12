---
title: "Odd cli behavior after feisty upgrade"
date: 2007-06-21
forum: Programming Talk
---

### Post by jro on 2007-06-21
This problem only started after I upgraded to Feisty. I have a custom PS1 ENV var:

```

\n\e[1;32m\u@\h\e[0m:[\e[1;36m\w\e[0m]\n[\e[0;32m\@\e[0m]:

```

Which makes my prompt look roughly like (sans the colors) this:

```

jeffrey@arnor:[~]
[09:39 PM]: 

```

The problem I have is that when enter a command longer than 24 characters long I can't ctrl+a back to the beginning of the line. For example, if I enter (no thats not an ACTUAL command, but it works for the illustration):

```

jeffrey@arnor:[~]
[09:39 PM]:xxxxxxxxxxXxxxxxxxxxxxxx

```

If I hit ctrl+a to go to the beginning of the line, the cursor only goes to the capitalized X. I have no idea whats going on. Although I do know its directly related to my PS1 var, since I tried removing it and the behavior stopped. Oddly enough this behavior is present in every environment Gnome Terminal, Xterm, and a straight text environment.  I am open to any suggestions. I can change my PS1 var, thats easy, but I would really like to figure out why this is happening.

---

### Post by po0f on 2007-06-21
jro,

Change your PS1 to the following (I tested it and it works for me):

```
\n\e[1;32m\u@\h\e[0m:[\e[1;36m\w\e[0m]\n[\e[0;32m\@\e[00m]:
```

I honestly don't know why this works; maybe you aren't fully resetting (proper term?) the terminal with `\e[0m`.

---

### Post by Mr. C. on 2007-06-21
When your prompt (PS1) contains non-moving character sequences (eg. those that give attributes to the text, but don't move the cursor), you must surround those sequences with the \[ and \] sequences pairs.  This tells bash to not count those characters when it computes the length of its prompt.

Here's a code segment  I use to set my prompts that shows use of these bracketed pairs (in each of the tc* vars).  The code allows you to compute the title sequences instead of having to embed them:

```
PS1='[\h:\W]'

#ESC [ Pm m     Character Attributes (SGR)
#    Pm = 0 -> Normal (default)
#    Pm = 1 -> Blink (appears as Bold)
#    Pm = 4 -> Underscore
#    Pm = 5 -> Bold
#    Pm = 7 -> Inverse
tcStandoutOn="\\[`tput smso`\\]"
tcStandoutOff="\\[`tput rmso`\\]"
tcBoldOn="\\[`tput bold`\\]"
tcAttrOff="\\[`tput sgr0`\\]"
tcSetBg="\\[`tput setab`\\]"
tcFgGreen="\\[`tput setaf 2`\\]"
tcFgBlack="\\[`tput setaf 0`\\]"
tcFgYellow="\\[`tput setaf 3`\\]"
tcTitleStart='\e]2;'
tcTitleEnd='\007'

# \[ and \] bracket non-printing chars in prompt

if [ $UID -eq 0 ] ; then
    PS1="$tcStandoutOn$PS1$tcStandoutOff # "
else
    PS1="$PS1 \$ "
fi

PS1="$tcFgYellow$tcBoldOn\]$PS1\[$tcFgBlack$tcAttrOff\]"

```

MrC

---

### Post by po0f on 2007-06-21
jro,

I was also going to add (as demonstrated in Mr. C.'s code snippet) that it's more readable IMO to have escape sequences set to variables.  I go as far as to add braces around variable names to separate them from surrounding variables, ie:

```
PS1="${tcFgYellow}${tcBoldOn}\]${PS1}\[${tcFgBlack}${tcAttrOff}\]"

## as opposed to just

PS1="$tcFgYellow$tcBoldOn\]$PS1\[$tcFgBlack$tcAttrOff\]"
```

But, of course, do what works best for you.  :)

---

### Post by jro on 2007-06-22
Thank you both of you. I am impressed with the speed and accuracy of your responses. Mr. C hit the nail directly on the head. I was trying to figure this problem out by reading through [this great article]("http://www.pantz.org/scripting/shell/colorterm.shtml") by Daniel Robbins. Near the end he talks about surrounding non-printing charactes with "\[" and "\]", just like Mr. C suggested. I tried it and it worked! I was just going back to post my solution when lo and behold the two of you beat me to the punch.

For those picking up the thread, here is a change log. Oh and po0f, your final suggestion is very valid indeed. My initial posting was simply an echo of my PS1 var. So you caught me being lazy, my PS1 assignment does look much like what you outlined. 

Initial code, with the printing problem outlined in my first post
```

red='\e[0;31m'
RED='\e[1;31m'
green='\e[0;32m'
GREEN='\e[1;32m'
yellow='\e[0;33m'
YELLOW='[1;33m'
blue='\e[0;34m'
BLUE='\e[1;34m'
violet='\e[0;35m'
VIOLET='\e[1;35m'
cyan='\e[0;36m'
CYAN='\e[1;36m'
white='\e[0;37m'
WHITE='\e[1;37m'
NC='\e[0m'

export PS1="\n$GREEN\u@\h$WHITE:[$CYAN\w$WHITE]\n[$green\@$WHITE]:$NC"

```

Then after taking the advice of Mr. C and the article I linked to above. I changed the NC variable assignment to be:

```

NC='\[\e[0m\]'

```

Well, cheers friends, thank you very much for your help. One final question, I wonder why this problem didn't manifest itself in Bash 3.1.17?

---

