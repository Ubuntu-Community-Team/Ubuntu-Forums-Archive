---
title: "Bash shell option extglob"
date: 2011-04-13
forum: Programming Talk
---

### Post by kaibob on 2011-04-13
I need to set the extglob shell option in a shell script but can't get it to work. The following shell script demonstrates the issue:

```
#!/bin/bash

menu () { 

shopt -s extglob

while true ; do
  read -p "Enter a number or (e)xit: " keypress
  case "$keypress" in
    +([0-9]) ) echo "$keypress" ;; 
    "e"      ) exit ;;
    *        ) continue ;;
  esac
done
}

export -f menu

gnome-terminal -x bash -c "menu"
```

When I run this shell script, I receive the following error message:

> line 10: syntax error near unexpected token `('
line 10: `    +([0-9]) ) echo "$keypress" ;;

A few comments:

* The shell script works fine with regular pattern matching--[0-9]* in place of +([0-9])).

* The commands within the function work fine if I run them standalone in a shell script without a function. 

* I tried adding "-O extglob" to bash but that didn't help. 

The issue appears to be setting the shell option inside the function, but I don't know how to fix this, and google yielded nothing pertinent. Thanks for any help.

---

### Post by bashologist on 2011-04-14
Edit:
I was thinking of something else I think. Here's a link to the problem I had once, but I think they're different issues.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=86397](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=86397)

---

### Post by kaibob on 2011-04-15
Thanks for the response. I agree that that the issue raised in the bug report appears different from the issue I'm experiencing.

This is actually a pretty minor problem and regular pattern matching comes close to what I need. It just rankled a bit that I couldn't get this working, and I thought I might have missed something obvious. That would appear not to be the case. 

Thanks again.

---

### Post by Crusty Old Fart on 2011-04-16
It doesn't work.

From the bottom of this page: [http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

> Because the extglob option changes the way certain characters are parsed, it is necessary to have a newline (not just a semicolon) between the shopt command and any subsequent commands that use extended globs.  Likewise, **you cannot put [COLOR=Red]shopt -s extglob[/COLOR] inside a function that uses extended globs**, because the function as a whole must be parsed when it's defined; the shopt command won't take effect until the function is *called*,  at which point it's too late.  Therefore, if you use this option in a  script, it's best to put it right under the shebang line, or as close as  you can get it while still making your boss happy.Bummer, ain't it?

---

### Post by kaibob on 2011-04-16
Thanks for the information--it explains things. 

I did manage to get the script working as I want using regular pattern matching. The input from the user is one or two digits, so I used:

```
[0-9]|[0-9][0-9] ) echo "$keypress" ;;
```

Thanks again.

---

### Post by Crusty Old Fart on 2011-04-16
When I tried it with:
```

[0-9]*   ) echo "$keypress" ;;

```It worked with however many digits I threw at it.

Anyhow...glad you got it working.

All the best,

Crusty

---

### Post by kaibob on 2011-04-16
> **Crusty Old Fart said:**
> When I tried it with:
```

[0-9]*   ) echo "$keypress" ;;

```It worked with however many digits I threw at it.


The trouble with [0-9]* is that it allows a number followed by one or more characters that are not numbers, which breaks the script. This is pretty unlikely, so I guess it's not important. Thanks again.

---

### Post by Crusty Old Fart on 2011-04-17
> **kaibob said:**
> The trouble with [0-9]* is that it allows a number followed by one or more characters that are not numbers, which breaks the script. This is pretty unlikely, so I guess it's not important. Thanks again.

Oh yeah...you're exactly right. I didn't even think about that.

You're welcome again :cool:

---

