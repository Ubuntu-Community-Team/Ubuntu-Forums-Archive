---
title: "The Quine Thread"
date: 2009-04-21
forum: Programming Talk
---

### Post by spupy on 2009-04-21
Ok, ladies and gentleman, let's see with what [quines]("http://en.wikipedia.org/wiki/Quine") we can come up with. Use a language of your choice and follow the rules. If possible, put your code in the second color on the last row on the color selector, as to avoid spoiling the other participants.
Python:
```
[COLOR="LemonChiffon"]
#!/usr/bin/python
prg="""#!/usr/bin/python
prg=@@
print prg.replace("@@", '"'*3+prg+'"'*3, 1)"""
print prg.replace("@@", '"'*3+prg+'"'*3, 1)[/COLOR]
```

---

### Post by unutbu on 2009-04-21
```
[COLOR="LemonChiffon"]#!/usr/bin/env python
import sys
print(open(sys.argv[0],'r').read()),
[/COLOR]
```

---

### Post by odyniec on 2009-04-21
C:
```
[COLOR="LemonChiffon"]#include <stdio.h>
#define Q "\""
#define B "\\"
#define N "\n"
#define P "int main() { printf(S, N, Q, B, Q, Q, N, Q, B, B, Q, N, Q, B, Q, N, Q, P, Q, N, Q, S, Q, N, P, N); }"
#define S "#include <stdio.h>%s#define Q %s%s%s%s%s#define B %s%s%s%s%s#define N %s%sn%s%s#define P %s%s%s%s#define S %s%s%s%s%s%s"
int main() { printf(S, N, Q, B, Q, Q, N, Q, B, B, Q, N, Q, B, Q, N, Q, P, Q, N, Q, S, Q, N, P, N); }[/COLOR]
```

unutbu, you're cheating ;)

---

### Post by Reiger on 2009-04-21
It's too easy in Haskell:
```

[COLOR="Wheat"]module Quine where
quine = (\x -> (putStrLn "module Quine where") >> (putStr (x ++ (show x)))) "quine = (\\x -> (putStrLn \"module Quine where\") >> (putStr (x ++ (show x)))) "[/COLOR]
```

---

