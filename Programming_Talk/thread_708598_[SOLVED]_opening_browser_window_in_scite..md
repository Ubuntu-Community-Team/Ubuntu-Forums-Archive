---
title: "[SOLVED] opening browser window in scite."
date: 2008-02-26
forum: Programming Talk
---

### Post by chex_m8 on 2008-02-26
[SIZE="4"]I'm having trouble opening the current file I'm editing in scite in a firefox browser window. I do Tools > Go, firefox opens but instead of opening my the current file i'm working on it opens my homepage. Any suggestions would be great. here is what my user.properties looks like.


# file extensions to open with browser - Semi-colon separated list
file.patterns.html=*.html;*.php;*.htm;*.js

command.go.$(file.patterns.html)=firefox $(FileSource)

[/SIZE]

---

### Post by talowe on 2008-02-26
command.go.$(file.patterns.html)=firefox $(FilePath)

---

### Post by chex_m8 on 2008-02-27
OK thx that seems to have helped, now im getting a new error. heres the error

>firefox /media/disk/Winter Term '08/CS 133JS/Week 5/Lab7/tutorial4/abStartDone.htm
sh: Syntax error: Unterminated quoted string
>Exit code: 2



heres what my user.options looks like

# file extensions to open with browser - Semi-colon separated list
file.patterns.html=*.html;*.php;*.htm;*.js

command.go.$(file.patterns.html)=firefox $(FilePath)

---

### Post by talowe on 2008-02-27
I am not sure, but it might be the quote in > WinterTerm '08.  Bash could be looking for a matching end quote.  (Might want to avoid using quotes in file and directory names.)

Try firefox "$(FilePath)"

---

### Post by chex_m8 on 2008-02-27
Thank you, you were correct on all accounts. The single quote in the file name was causing problems as well as some spaces I had in the folder names. However instead of going through and editing all my folders I did what you said and put double quotes around   the filepath. that made it so I didnt have to edit anything, Thx again.  

firefox "$(FilePath)"

---

