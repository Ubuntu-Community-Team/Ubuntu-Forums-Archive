---
title: "Bash script to check string length"
date: 2014-01-21
forum: Programming Talk
---

### Post by jimmyh1972 on 2014-01-21
Hi - i wrote a script 

#!/bin/bash


PASS=$(zenity --entry --text "enter text")
if [ ${PASS} -lt 4 ]; then
`zenity --error`
else
`zenity --entry --text "OK"`
fi

i want to check if the sting length is more than 4 digits/chars/sepcial signs

its not working...

what am i doing wrong?

thanks' Jimmi

---

### Post by steeldriver on 2014-01-21
To get the length of the variable you need to use {#var} not {var} I think

```
${[COLOR=#0000ff]#[/COLOR]PASS}
```

---

