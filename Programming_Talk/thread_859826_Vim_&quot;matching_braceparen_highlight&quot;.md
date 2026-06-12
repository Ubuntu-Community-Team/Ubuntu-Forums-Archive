---
title: "Vim &quot;matching brace/paren highlight&quot;"
date: 2008-07-14
forum: Programming Talk
---

### Post by glitch13 on 2008-07-14
When writing php (in Vim of course), it has this awesome feature.  When your cursor is over a brace, bracket, or paren it will highlight the matching close or open one.

Like I said, this is totally awesome.

Anywho, I have ubuntu installed on an ancient machine at home that I use as a webdevelopment/subversion server.  I'm talking Pentium1.  Ubunutu runs fine, boot time notwithstanding, but when my cursor in vim hits a paren/brace/bracket the machine pretty much hard locks for about .5 seconds.  This is super-frustrating when trying to scroll through a medium sized php file.

Is there anyway to turn just the feature off (and keep syntax highlighting)?

---

### Post by LaRoza on 2008-07-14
> **glitch13 said:**
> 
Is there anyway to turn just the feature off (and keep syntax highlighting)?

Comment out the "showmatch" line in your .vimrc.

I think that will do it.

---

### Post by zgoda on 2008-11-10
> **glitch13 said:**
> When writing php (in Vim of course), it has this awesome feature.  When your cursor is over a brace, bracket, or paren it will highlight the matching close or open one.

Is there anyway to turn just the feature off (and keep syntax highlighting)?

Put this in your vimrc:
```
let loaded_matchparen=1
```

---

