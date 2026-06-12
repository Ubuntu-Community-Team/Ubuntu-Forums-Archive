---
title: "Array defining in bash."
date: 2009-11-12
forum: Programming Talk
---

### Post by Barriehie on 2009-11-12
Pulling my hair out!  :)  I've got this line in my script and I keep getting this error:
**/home/barrie/bin/picsdaemon.sh: 24: Syntax error: "(" unexpected**

```

CHARSARRAY=( 'a' 'A' 'b' 'B' 'c' 'C' 'd' 'D' 'e' 'E' 'f' 'F' 'g' 'G' 'h' 'H' 'i' 'I' 'j' 'J' 'k' 'K' 'l' 'L' 'm' 'M' 'n' 'N' 'o' 'O' 'p' 'P' 'q' 'Q' 'r' 'R' 's' 'S' 't' 'T' 'u' 'U' 'v' 'V' 'w' 'W' 'x' 'X' 'y' 'Y' 'z' 'Z' '0' '1' '2' '3' '4' '5' '6' '7' '8' '9' )

```

What am I missing please?  I've found -many- examples that are saying this should work!

Thanks in advance!
Barrie

---

### Post by ghostdog74 on 2009-11-12
> **Barriehie said:**
> 
**/home/barrie/bin/picsdaemon.sh: 24: Syntax error: "(" unexpected**
...

What am I missing please?  
what we are missing is your whole script!. the error clearly says line 24. how are we supposed to know why it doesn't work when you only post the one line that works. you should also see if you are using bash, ie shebang #!/bin/bash

---

### Post by slakkie on 2009-11-12
works for me:

```

$ cat x.sh
#!/usr/bin/bash

CHARSARRAY=( 'a' 'A' 'b' 'B' 'c' 'C' 'd' 'D' 'e' 'E' 'f' 'F' 'g' 'G' 'h' 'H' 'i' 'I' 'j' 'J' 'k' 'K' 'l' 'L' 'm' 'M' 'n' 'N' 'o' 'O' 'p' 'P' 'q' 'Q' 'r' 'R' 's' 'S' 't' 'T' 'u' 'U' 'v' 'V' 'w' 'W' 'x' 'X' 'y' 'Y' 'z' 'Z' '0' '1' '2' '3' '4' '5' '6' '7' '8' '9' )

$ bash -x x.sh
+ CHARSARRAY=('a' 'A' 'b' 'B' 'c' 'C' 'd' 'D' 'e' 'E' 'f' 'F' 'g' 'G' 'h' 'H' 'i' 'I' 'j' 'J' 'k' 'K' 'l' 'L' 'm' 'M' 'n' 'N' 'o' 'O' 'p' 'P' 'q' 'Q' 'r' 'R' 's' 'S' 't' 'T' 'u' 'U' 'v' 'V' 'w' 'W' 'x' 'X' 'y' 'Y' 'z' 'Z' '0' '1' '2' '3' '4' '5' '6' '7' '8' '9')

```

---

### Post by Barriehie on 2009-11-12
Works for me now too AFTER I exited emacs and ran it. 

Thanks people,
Barrie

---

