---
title: "Vim config question...."
date: 2010-12-06
forum: Programming Talk
---

### Post by Neovos on 2010-12-06
I have the following code that I found in my vim config to enable the saving of manual folds:

```
au BufWinLeave * mkview 1
au BufWinEnter * silent loadview 1
```

and every time I open a new window split or any other empty document, it comes up with ```
Error detected while processing BufWinEnter Auto commands for "*":
E32: No file name
``` which is a non issue really cause it's just saying that theres no saved folds for a nonexistent document, but I'd like to get rid of that banner if I could, it's kind of annoying. Anyone got any ideas?

---

### Post by DaithiF on 2010-12-07
```
au BufWinLeave ?* mkview 1
au BufWinEnter ?* silent loadview 1

```
to prevent matching empty filenames?

---

### Post by Neovos on 2010-12-07
> **DaithiF said:**
> ```
au BufWinLeave ?* mkview 1
au BufWinEnter ?* silent loadview 1

```
to prevent matching empty filenames?

so simple! It worked, thanks!

---

