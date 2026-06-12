---
title: "Tip: xprop alias to give the Class Info you need"
date: 2009-02-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Jose Catre-Vandis on 2009-02-01
Just popping this in here so I don't lose it again, but this is a useful line to put in your .bashrc file, especially if you are using devilspie, compiz windows placement, or openbox configs.

it simplifies the output of the command xprop, by simply returning the Class information only

1. open up a terminal and open $HOME/.bashrc
```
sudo nano $HOME/.bashrc
```

2. Scroll down to alias section and add
```
alias xp='xprop | grep "WM_WINDOW_ROLE\|WM_CLASS" && echo "WM_CLASS(STRING) = \"NAME\", \"CLASS\""'
```
and save out and close your shell.

3. To test reopen a terminal and type "xp" at the prompt (no quotes)
Your cursor turns into an "X". Click on the window you need info about and it should return something like this in your terminal (for a Firefox window)
```
WM_WINDOW_ROLE(STRING) = "browser"
WM_CLASS(STRING) = "Navigator", "Firefox"
WM_CLASS(STRING) = "NAME", "CLASS"
```

of course you can modify alias name and string to your own liking :)

---

