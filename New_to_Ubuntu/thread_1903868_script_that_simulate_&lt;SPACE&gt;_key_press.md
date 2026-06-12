---
title: "script that simulate &lt;SPACE&gt; key press?"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by honeybear on 2012-01-03
Hello,

For my openbox, I would like to pause mplayer with a sh script. 

I have tried : 

```
  echo KeyStr Space | xmacroplay $DISPLAY

```

It is however working. would thou eventually know whether the command correct? 

THanks

---

### Post by Flimm on 2012-06-19
How about this?

```


printf 'Delay 1\nString  \n' | xmacroplay "$DISPLAY"


```

This statement (without the quotes):

```
"Delay 1"
```

waits a second before executing the next statement, and this statement:

```
"String  "
```

(note the two spaces) types a single space.

---

### Post by Jose Catre-Vandis on 2012-06-19
You could try xdotool for this:
```
xdotool key space
```
or as long as mplayer has focus
```
xdotool key p
```

---

