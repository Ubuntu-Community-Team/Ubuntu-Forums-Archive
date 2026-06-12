---
title: "Reading from a file using a for loop"
date: 2013-03-12
forum: Programming Talk
---

### Post by toad3000 on 2013-03-12
When I want to read a file using a while loop all I do is just ```
while read line; echo $line done <$file
```
But I am unable to do something similar like this using a for loop. ```
for ((count=1;count<=5;count++));read line; done <$file
```

Could someone guide me in the direction for reading from a file in for loop? Thanks

---

### Post by ofnuts on 2013-03-12
Your syntax seems to work, though. However, since you will always have to check that "read" worked, the classic "while read" idiom with an explicit counter test in the loop would do the same thing.

Edit: overlooked the missing "do"... but the advice still holds.

---

### Post by schragge on 2013-03-12
```
for ((count=1;count<=5;count++)) [COLOR=red]do[/COLOR] read line; done <$file
```

---

### Post by Vaphell on 2013-03-12
> ```
for ((count=1;count<=5;count++))[COLOR="#FF0000"]; do[/COLOR] read line; done < "$file"
```

;)

---

### Post by schragge on 2013-03-12
:P If it is bash then semicolon after numeric *for* is optional. Actually, even spaces are optional, although I admit that this is bad practice:
```
for((count=1;count<=5;count++))do read line; done < "$file"
```

---

### Post by Vaphell on 2013-03-12
o.O well well, I didn't know that :)
but who thought allowing for a style different than all other flavors of *do ... done* loops is a great idea? Is there no value to consistency? o.O

---

### Post by schragge on 2013-03-12
Well, it's essentially a ksh compatibility feature. While pdksh/mksh/zsh wouldn't allow this, ksh93 and bash will. The reasoning goes like this:
Traditional generic *for* loop command (for var in [COLOR=blue]list[/COLOR]) needs to be delimited either by newline or by semicolon for shell to know where the [color=blue]list[/color] ends (or if it is present at all). OTOH, the numeric *for* loop expression is already unambigously delimited by ((...)). Convenience wins over consistency. :)
[highlight]Disclaimer.[/highlight] I don't endorse such coding style by any means. It's really confusing, and not universally supported by all shells.

---

