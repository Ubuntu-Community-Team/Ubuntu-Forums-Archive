---
title: "Auto indent in Quanta"
date: 2006-04-05
forum: Programming Talk
---

### Post by DonQuixote on 2006-04-05
I've been trying to get Quanta configured as I'd like it, but so far I'm stumped on the auto-indent settings.  For some reason when ever I enter a "{" in the editor it flings it all the way back to the first column.  This is not something that I desire.  I'd like it to drop that "{" right below the function/method I'm writing...

I'd like this:
```

function name()
{
  foreach()
  {
     stuff;
  }

}

```

Not this (as it does it now)
```

function name()
{
  foreach()
{
   stuff;
}

}

```

Any help on this would be greatly appreciated!

Thanks!

---

### Post by zami on 2006-09-06
Have you tried checking the box in
Tools > Indentation > Normal ?

I just tried that out, and it seems to be handling {}'s just fine with indentation.

Also look under
Settings > Configure Editor > Indentaion (on the left side)
My current working settings are 
-automatic indentation = none (odd, no?)
-keep ident profile
-tab key indents
-insert indent charactors
other settings are not selected.

No idea if any of that helps, but thought I'd try!

-zami

---

