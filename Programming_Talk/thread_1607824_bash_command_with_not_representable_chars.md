---
title: "bash command with not representable chars"
date: 2010-10-28
forum: Programming Talk
---

### Post by giuspen on 2010-10-28
Hi,
I have a bash command that works great but involves a char that is not representable.
The command is the following:
[PHP]bind '"[A":history-search-backward'[/PHP]
Is it possible to change this command replacing someway the non representable chars?
Thanks.

---

### Post by gmargo on 2010-10-28
Try replacing the hard coded escape with a "\e" (backslash-e)
```

[COLOR=#000000][COLOR=Black][COLOR=#0000bb]bind [/COLOR][/COLOR][COLOR=#dd0000][COLOR=Black]'"\e[A":history-search-backward'
[/COLOR][/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#dd0000]
[/COLOR][/COLOR]

---

### Post by giuspen on 2010-10-28
> **gmargo said:**
> Try replacing the hard coded escape with a "\e" (backslash-e)
```

[COLOR=#000000][COLOR=Black][COLOR=#0000bb]bind [/COLOR][/COLOR][COLOR=#dd0000][COLOR=Black]'"\e[A":history-search-backward'
[/COLOR][/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#dd0000]
[/COLOR][/COLOR]

it works!
thanks a lot.

---

