---
title: "php string detect if just a crlf?"
date: 2011-02-11
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-11
in VB6 you can say this
```
If $Fileline1 = vbCrLf Then exit sub
```

What I need is a PHP equivalent test to see if the string read off the file is just a
crlf.
something like this? I know this wont likely work

If ($Fileline == /r/n){return;}

any help? thanks

this might be the same thing for what I need to do.
If (trim($Fileline1) == ""){return;};//vbCrLf

---

