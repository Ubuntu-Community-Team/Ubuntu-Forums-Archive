---
title: "sed yes"
date: 2020-12-04
forum: Programming Talk
---

### Post by maclenin on 2020-12-04
Essentially, I would like to use sed to replace the whitespaces with underscores in the "yes" lines only.

Changing this...
```
var x = [
{
"yes":"a b c",
"no":"a b c"
},
{
"yes":"d e f g h",
"no":"d e f g h"
}
];
```

...to this:
```
var x = [
{
"yes":"a_b_c",
"no":"a b c"
},
{
"yes":"d_e_f_g_h",
"no":"d e f g h"
}
];
```
Thanks for any guidance!

---

### Post by ajgreeny on 2020-12-04
The command ```
sed 's/\ /_/g' filename
``` would remove spaces from all lines of a file but it looks as if you can act only on lines matching a regex according to man sed
```
\cregexpc
              Match lines matching the regular expression regexp.  The c may be any character.
```
I've never used this but I do use the ***'s/\ /_/g'*** part of the sed command with rename command to remove spaces from any file or folder names in my home using one of the many custom-actions in my thunar file-manager.

Spaces in file/folder names are definitely bad news so I always replace them with an underscore!

EDIT:
I've just tried to figure this out but failed and my bash-foo is not good enough to sort out why; probably my lack of understanding of **regex**!
Hopefully this might give you some clues to further searching about the job you need done.

---

### Post by norobro on 2020-12-04
```
sed '/yes/ s/\ /_/g' filename
```The above uses a regex (/yes/) as an address, see the man page under 'Addresses'. If the regex matches the substitution is performed.

---

### Post by maclenin on 2020-12-04
sed yes, indeed!
```
sed '/yes/ s/\ /_/g' filename
```
This worked!

Thank you both!

Two handy sandbox references:
[https://regex101.com/](https://regex101.com/)
[https://sed.js.org/](https://sed.js.org/)

---

