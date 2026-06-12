---
title: "Colour-blind: colours in Command Line output"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by Noor1101 on 2012-10-05
Hi, 
I'm asking this question not for myself but for a friend who is colour-blind (completely; he only sees black white and grey)

Is there a way to get rid of the colours in Command Line? I mean things like maps are blue (right?) and that sort of stuff. Can it be reset in such a way that there are no colours?

Thanks

---

### Post by mcduck on 2012-10-05
sure.

The easiest option might be just switching the settings in the terminal application you are using, for example Gnome-terminal has pretty detailed color configuration options in the terminal profile.

..and the alternative way, which would affect all terminals and TTY's, is to edit your ~/.bashrc file, it has an option to enbable/disable colors in Bash. (sadly I'm not at my Linux machine at the moment so I can't tell you the exact line, but it should be pretty clear if you read the file)

---

### Post by Noor1101 on 2012-10-05
Great, thanks! I'll look into it. This might be the final push to get him to join in with me in learning to use Linux.

:) thanks

---

### Post by iponeverything on 2012-10-05
```
alias ls='ls --color=auto'
```

is in the .bashrc file

just remove the line.

on per case basis -- bypass the alias with a "\" 

ie. 

```
\ls -l
```

---

### Post by Pletched on 2012-10-05
This will only make the background white and the foreground black.

From profile preferences click on colours and check "use colours from system theme" until it has no tick. Next, click on built-in-schemes select black on white or white on black.

---

