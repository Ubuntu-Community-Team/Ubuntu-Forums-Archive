---
title: "HOWTO: Customize terminal header"
date: 2008-01-21
forum: Outdated Tutorials &amp; Tips
---

### Post by PurposeOfReason on 2008-01-21
By default, the terminal header is a bit boring and unattractive. This format is determined by your ~/.bashrc file. By default there will be many lines, most of which don't matter. We want the PS1 line (which determines what to show) looks like the following:
```
PS1='[\u@\h \W]\$ '
```
The PS1 line will show anything between the opening and closing ' , including spaces. You have many option of what to put, all listed here:
```
\a     an ASCII bell character (07)
            \d     the date in "Weekday Month Date" format (e.g., "Tue May 26")
            \D{format}
                   the format is passed to strftime(3) and the result is inserted into the  prompt  string;  an  empty  format
                   results in a locale-specific time representation.  The braces are required
            \e     an ASCII escape character (033)
            \h     the hostname up to the first `.'
            \H     the hostname
            \j     the number of jobs currently managed by the shell
            \l     the basename of the shell's terminal device name
            \n     newline
            \r     carriage return
            \s     the name of the shell, the basename of $0 (the portion following the final slash)
            \t     the current time in 24-hour HH:MM:SS format
            \T     the current time in 12-hour HH:MM:SS format
            \@     the current time in 12-hour am/pm format
            \A     the current time in 24-hour HH:MM format
            \u     the username of the current user
            \v     the version of bash (e.g., 2.00)
            \V     the release of bash, version + patch level (e.g., 2.00.0)
            \w     the current working directory, with $HOME abbreviated with a tilde
            \W     the basename of the current working directory, with $HOME abbreviated with a tilde
            \!     the history number of this command
            \#     the command number of this command
            \$     if the effective UID is 0, a #, otherwise a $
            \nnn   the character corresponding to the octal number nnn
            \\     a backslash
            \[     begin  a sequence of non-printing characters, which could be used to embed a terminal control sequence into
                   the prompt
            \]     end a sequence of non-printing characters

```

You may put them in any order that you wish, as long as that they are within you're ' s.  You may also use colors if you so wish, a full list of colors is below:
```
Black       0;30     Dark Gray     1;30
Blue        0;34     Light Blue    1;34
Green       0;32     Light Green   1;32
Cyan        0;36     Light Cyan    1;36
Red         0;31     Light Red     1;31
Purple      0;35     Light Purple  1;35
Brown       0;33     Yellow        1;33
Light Gray  0;37     White         1;37
```

My PS1 line looks as follows:
```
PS1='\[\e[0;34m\][\W]\[\e[m\] '
```
which, based on the above tables means to use blue to show the current directory, and then switch pack to the default color ([\e[m\] for the rest of the output. There are no limits to how short or long you make this line, a good example line is as follows:
```
PS1='\[\e[0;32m\]\u\[\e[m\] \[\e[1;34m\]\w\[\e[m\] \[\e[1;32m\]\$ \[\e[m\]\[\e[1;37m\] '
```

Of course these aren't the only functions of the ~/.bashrc file, but as far as the header goes, those are your options to what will show.



**If any of this makes no sense, please let me know and I'll try to expand it.

---

### Post by m.musashi on 2008-01-24
> **PurposeOfReason said:**
> By default, the terminal header is a bit boring and unattractive. This format is determined by your ~/.bashrc file. By default there will be many lines, most of which don't matter. We want the PS1 line (which determines what to show) looks like the following:
```
PS1='[\u@\h \W]\$ '
```
Very cool. But I don't see a section like that. I'm guessing it's in this mess
```
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac
```
But I don't know where to start commenting and what to change. Any pointers?

Thanks.

---

### Post by PurposeOfReason on 2008-01-24
Remember you posted this here so you can revert it if I'm wrong. However, notice the two PS1 lines at the beginning? They are essentially the same thing, one is just in color. So I'm just going to comment them out, then put your own PS1 line somewhere, preferably at the beginning, and see if that works.

```
# set a fancy prompt (non-color, unless we know we "want" color)
#case "$TERM" in
#xterm-color)
#   PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#    ;;
#*)
#    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
#    ;;
#esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac
```

---

### Post by patrock on 2008-01-24
Just append it to the bottom of the file.  It will just override any previously set ones.

Here's mine:
```
PS1='\n[\[\e[36;40m\]\u\[\e[0m\]] \[\e[32;40m\]\W \[\e[0m\]\$ '
```

---

### Post by m.musashi on 2008-01-24
@PurposeOfReason: Hey, that worked. Thanks. I thought maybe the bit about ${USER}@${HOSTNAME} had to change as that's what I normally have as part of the prompt. Guess not. That's one confusing file though.

---

### Post by D-EJ915 on 2008-01-28
If you want to try it out first to see what it does, simply type "export " then your PS1=... part so it would look like

> export PS1='\n[\[\e[36;40m\]\u\[\e[0m\]] \[\e[32;40m\]\W \[\e[0m\]\$ ' for the one patrock posted.

This doesn't do anything to any files, it just changes it for that one window.

---

### Post by kaiju on 2008-02-16
hey, this is a very fine little thread.

how about making a collection of terminal headers people are using?

---

### Post by thyultimate on 2008-03-03
wow!! i didn't even know that something like ~/.bashrc existed, thanks a lot guys

---

### Post by Lostincyberspace on 2008-03-12
Hey I have a question I was playing with my colors and I got a color I really like but cant get it again.
Could some one tell what to put in to get the color
I have include a picture of it.

---

### Post by PurposeOfReason on 2008-03-12
> **Lostincyberspace said:**
> Hey I have a question I was playing with my colors and I got a color I really like but cant get it again.
Could some one tell what to put in to get the color
I have include a picture of it.

That is either 1;31 or 0;31.

---

### Post by Lostincyberspace on 2008-03-12
Actually the color was 1;36 the light cyan Sorry I was very misleading I didn't even make a reference to the color.

---

### Post by LeoSolaris on 2008-03-13
Hey! I was just playing with this yesterday from the terminal. If you change the PS1 line from terminal directly, it will change, but it changes back when ya restart the terminal. I figured there would be a file in the back somewhere, and I noticed POR's sig, and rejoiced!

Thanks, I like having the current time and date at the beginning. It makes things much more convenient.

I'm using PS1='\T on \d - \u:\w\$' It shows the time in 12 hour with seconds, on the date - my user name:current dir$

In the Terminal's edit, I changed the profile so it shows up 25% translucent, as well as displaying a better name for it that the PS1 line. In my case, 'Leo's Terminal'

Leo S.

---

### Post by ChaoticVengeance on 2008-03-16
My PS1 lines are preceded by this:

${debian_chroot:+($debian_chroot)}
So my line looks like:
PS1='${debian_chroot:+($debian_chroot)}\[\e[0;31m\](\t)\[\e[m\]\[\e[0;32m\]\u\[\e[m\]@\[\e[0;34m\]\w\[\e[m\]\$ '

What does this do, and is it required to run the terminal properly?

---

### Post by PurposeOfReason on 2008-03-16
> **ChaoticVengeance said:**
> My PS1 lines are preceded by this:

${debian_chroot:+($debian_chroot)}
So my line looks like:
PS1='${debian_chroot:+($debian_chroot)}\[\e[0;31m\](\t)\[\e[m\]\[\e[0;32m\]\u\[\e[m\]@\[\e[0;34m\]\w\[\e[m\]\$ '

What does this do, and is it required to run the terminal properly?
Since I don't use a Debian based system, I don't know what it does but I do know you probably don't need it. However, if it's there it's probably doing something and it's not hurting anything, so don't touch it. ;)

You can just make a new PS1 line and put it at the end. The last PS1 line in the file is what is used.

---

### Post by blacksm1th on 2008-03-22
Thank you PurposeOfReason. Here is my terminal:
[[IMG]http://img329.imageshack.us/img329/1498/screenshotue8.th.png[/IMG]](http://img329.imageshack.us/my.php?image=screenshotue8.png)

```
PS1='${debian_chroot:+($debian_chroot)}|\[\033[00;34m\]\u\[\033[00m\]\[^\]\[\033[00;34m\]\h\[\033[00m\]\[\033[00m\]:\[\033[00;33m\]\W\[\033[00m\]|\[\033[00;36m\]\$\[\033[00m\] '
```

---

### Post by bruno666 on 2008-03-24
Here's another example of prompt customisation :
```

# Some colors
#grey='\[\033[1;30m\]'
#red='\[\033[0;31m\]'
#green='\[\033[0;32m\]'
GREEN='\[\033[1;32m\]'
#blue='\[\033[0;34m\]'
#BLUE='\[\033[1;34m\]'
cyan='\[\033[0;36m\]'
#CYAN='\[\033[1;36m\]'
GREEN='\[\033[1;32m\]'
#white='\[\033[1;37m\]'
#yellow='\[\033[1;33m\]'
RED='\[\033[1;31m\]'
#violet='\[\033[1;35m\]'
NC='\[\033[0;m\]'

# if you are root (uid=0) brackets and @ in red, else in green for normal user
if [ "`id -u`" -eq 0 ]; then
  b=$RED
  e="$NC# "
else
  b=$GREEN
  e="$NC$ "
fi
 PS1="${debian_chroot:+($debian_chroot)}$b[$NC\u$b@$NC\h:$cyan\w$b]$e"


```

This could be either in $HOME/.bashrc for a single user, or in /etc/bash.bashrc for a system-wide setting

[[IMG]http://img181.imageshack.us/img181/9532/promptmv4.th.png[/IMG]](http://img181.imageshack.us/my.php?image=promptmv4.png)

---

### Post by Gen2ly on 2008-04-13
Good howto.   ASCII sequences can go beyond the predefined eight colors.  The process isnt' all too difficult but I learned that Freexx has a converter that converts hexidecimal code to the corresponding bash ASCII sequence.  

[http://frexx.de/xterm-256-notes/](http://frexx.de/xterm-256-notes/)

Install and:

```
echo d3d7cf | conv-rgb2xterm
```

Alternatively instead of using ASCII, tput can be used:

 ```
export TXT_GR=$(tput setaf 2)
 export TXT_BL=$(tput setaf 4)
 export TXT_BLD=$(tput bold)
 export TXT_RESET=$(tput sgr0)
 export PS1='\[${TXT_GR}${TXT_BLD}\]@${TXT_BL} \w \$${TXT_RESET} '
```

Just thought I'd throw that in.

:D

---

### Post by SkonesMickLoud on 2008-04-22
Is there any way to apply different PS1 lines to different terminal windows?

I have a dark background, and want a light font color for my Devilspie induced Desktop Terminal.  My regular terminal windows are the default Ubuntu Human theme, so a light font is difficult to read.

Can I do this, or do I have to find a happy medium?

---

### Post by conundrumx on 2008-06-26
[img]http://img117.imageshack.us/img117/5122/termcf7.png[/img]
PS1='\[\033[01;32m\]\u@\h \[\033[01;34m\]\W \$ \[\033[00m\]'

The user@host part is a different color for each of the servers so I can quickly differentiate which machine I'm connected to.  Green is my laptop.  :)

@Skones: If your desktop terminal is run from a different program you can put an export PS1 in the launcher.  You can set a PS1 in bashrc which will persist across terminals, put an export line in gnome-terminal's launcher, and another in whichever program you use for the desktop terminal.

---

### Post by trappy on 2008-07-01
Thanks for the tip, works like a charm. Here's mine;

[img]http://data.fuskbugg.se/skalman01/--temp.png[/img]

---

### Post by NickPresta on 2008-09-29
Here is mine (Kind of long):
\[\e]0;\u@\h: \w\a\]\[\e[33;1m\]\u\[\e[37;1m\]@\[\e[32;1m\]\h\[\e[20;1m\]\[\e[34;1m\](\[\e[31;1m\]\w\[\e[34;1m\])\[\e[0m\]$\[\e[0m\]

---

### Post by SentientFluid on 2009-03-01
If I use the default then anything I type wraps to the next line when it reaches the end of the Terminal window.  If I alter it then it simply wraps o the beginning of the same line I started typing on.

Default:```
${debian_chroot:+($debian_chroot)}\u@\h:\w\$
```

Mine:```
\[\e[0;33m\] [\W] \$\e[m\]
```

And when in my home folder that gives me the nice simple prompt of ```
[~]
```

Sample of problem: ```
geoff@Podfather:~$ sample text sample text sample text sample text sample text sample text
bash: sample: command not found
geoff@Podfather:~$ export PS1='\[\e[0;33m\] [\W] \$\e[m\]'
**t[~] $ sample text sample text sample text sample text sample text sample tex**
```

Note in the bold line how the last 't' in the final 'text' wraps to the beginning of the line I am typing on instead of wrapping to the next line? If I were to continue typing it would overwrite the rest of the line I started on.

It also messes with using the up and down arrow keys to scroll through the command history, but that's much harder to describe. :P

How do I fix this?

---

### Post by kaiju on 2009-03-02
> **SentientFluid said:**
> If I use the default then anything I type wraps to the next line when it reaches the end of the Terminal window.  If I alter it then it simply wraps o the beginning of the same line I started typing on.

Whatever makes the same line being used over again, it has to do with the strange escape sequences you are using.
From what you posted, the basic pattern you want for your prompt is '[\W] \$ '. The rest is coloring it by adding escape sequences, e.g. '\[\e[0;33m\]'. The M;3N (0;33 in my example) is the part where you specify the color - N is a number between 0 (black) and 7 (white), and M is either 0 (dark) or 1 (bright).
The escape sequence is '\[\e[0m\]' - you need to use this after the parts you intend to color, so that the following text will have the default color.
As an example, try this:
```

PS1='\[\e[0;33m\][\W] \[\e[0m\]\$ '

```

---

### Post by SentientFluid on 2009-03-02
> **kaiju said:**
> Whatever makes the same line being used over again, it has to do with the strange escape sequences you are using.
From what you posted, the basic pattern you want for your prompt is '[\W] \$ '. The rest is coloring it by adding escape sequences, e.g. '\[\e[0;33m\]'. The M;3N (0;33 in my example) is the part where you specify the color - N is a number between 0 (black) and 7 (white), and M is either 0 (dark) or 1 (bright).
The escape sequence is '\[\e[0m\]' - you need to use this after the parts you intend to color, so that the following text will have the default color.
As an example, try this:
```

PS1='\[\e[0;33m\][\W] \[\e[0m\]\$ '

```

That helped, thanks!  I wasn't escaping the closing sequence correctly. This is working fine now:

```
export PS1='\[\e[0;33m\][\W]\$\[\e[0m\] '
```

Teach me to try and do this when I'm tired. :P

---

### Post by D1ZZ4ZZT3R on 2009-04-21
i don't even know how to find or access a ~/.bashrc file. do i get to it from the terminal? how do i edit it? the tutorial isn't in depth enough, at least, not for me.

---

### Post by Jpardue on 2009-04-25
> **D1ZZ4ZZT3R said:**
> i don't even know how to find or access a ~/.bashrc file. do i get to it from the terminal? how do i edit it? the tutorial isn't in depth enough, at least, not for me.

To access your ~/.bashrc file type into the terminal:

sudo gedit ~/.bashrc

to add and save changes to your ~/.bashrc file via the gedit text editor.

---

### Post by kevinguillorytraining on 2009-10-09
This is one of the nice how-to

---

### Post by Nepherte on 2009-10-09
> **Jpardue said:**
> To access your ~/.bashrc file type into the terminal:

sudo gedit ~/.bashrc

to add and save changes to your ~/.bashrc file via the gedit text editor.
There's no need in opening the user owned .bashrc as root. Besides, *if* you want to open a file as root in a graphical program, one should use gksudo.

---

### Post by Evilhugbear on 2010-02-20
Hi, I have mine set up with the colors I want and it looks like [jake-ubuntu|05:47 PM|jake] ~ $ 
(but has colors)

I want to know if I make the | signs green, and keep everything else there same colors.

Is this possible?

If it is can you show me the code and where to put it in the ps1 line?

Thanks!

Edit : Never mind, I figured it out :). I just had to add a "\" after "|"

---

### Post by mtecknology on 2010-07-08
> **NickPresta said:**
> Here is mine (Kind of long):
\[\e]0;\u@\h: \w\a\]\[\e[33;1m\]\u\[\e[37;1m\]@\[\e[32;1m\]\h\[\e[20;1m\]\[\e[34;1m\](\[\e[31;1m\]\w\[\e[34;1m\])\[\e[0m\]$\[\e[0m\]

Ya.... that's impressive. A lot of colors.
I go for this one:
export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

---

