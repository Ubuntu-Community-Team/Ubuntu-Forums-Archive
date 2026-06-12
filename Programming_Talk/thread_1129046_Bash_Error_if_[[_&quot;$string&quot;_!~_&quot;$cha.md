---
title: "Bash Error: if [[ &quot;$string&quot; !~ &quot;$char&quot; ]]; then"
date: 2009-04-18
forum: Programming Talk
---

### Post by Penguin Guy on 2009-04-18
This is the code to find if $string contains $char:
```
[COLOR="Green"]if [[ "$string" =~ "$char" ]]; then[/COLOR]
```

This code, however, does not work:
```
[COLOR="Red"]if [[ "$string" **!**~ "$char" ]]; then[/COLOR]
```


What I am trying to do is execute commands if $string does NOT contain $char:
Can somebody explain what I may be doing wrong or how I can fix this?


The correct code is:
```
if [[ ! "$string" =~ "$char" ]]; then
```
-as posted by [amingv]("http://ubuntuforums.org/member.php?u=420496").

---

### Post by amingv on 2009-04-18
Is what you're trying to do by any chance

[PHP]if [[ ! "$string" =~ "$char" ]]; then[/PHP]
?

---

### Post by Penguin Guy on 2009-04-18
> **amingv said:**
> Is what you're trying to do by any chance

[PHP]if [[ ! "$string" =~ "$char" ]]; then[/PHP]
?
Yes, thanks! That works great!

---

