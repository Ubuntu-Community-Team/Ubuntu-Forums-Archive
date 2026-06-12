---
title: "echo: not found"
date: 2011-05-04
forum: Programming Talk
---

### Post by lowrider2025 on 2011-05-04
I have a problem with a bash script:

it looks like:
```
#!/bin/sh
set -x

today=`date '+%w'`
echo $today


```

gives the following error:
./script.sh: 1: echo: not found

Trying with /bin/echo gives the same error.

---

### Post by lowrider2025 on 2011-05-04
Must have inserted some unknown character whilest trying to enter the backtick symbol. I'm having problems using the backtick character in nano (it opens the replace function instead).Now I enter a ´ and then Alt Gr + ` to start a replace and then I can enter the backtick for good. Does anyone know if there is an easier way of getting the backtick character ? Or changing the shortcut to replace a character to something else ?

---

### Post by r-senior on 2011-05-04
In Bash, you can use $(...) rather than `...`. But you need to change #!/bin/sh to #!/bin/bash to get Bash. I'm not sure if Dash (which is what /bin/sh links to) supports the $(...).

---

### Post by Arndt on 2011-05-04
> **lowrider2025 said:**
> Must have inserted some unknown character whilest trying to enter the backtick symbol. I'm having problems using the backtick character in nano (it opens the replace function instead).Now I enter a ´ and then Alt Gr + ` to start a replace and then I can enter the backtick for good. Does anyone know if there is an easier way of getting the backtick character ? Or changing the shortcut to replace a character to something else ?

You could use xmodmap to map some otherwise unused character to what you want.

---

### Post by lowrider2025 on 2011-05-05
> **r-senior said:**
> In Bash, you can use $(...) rather than `...`. But you need to change #!/bin/sh to #!/bin/bash to get Bash. I'm not sure if Dash (which is what /bin/sh links to) supports the $(...).

So this should work perfectly when using bash:
today="$(date '+%w')"

Which scripting shell is lighter/faster for the system: bash or dash ?

---

