---
title: "bash: how to have the &quot;page up&quot; functionality (search between previous commands)"
date: 2010-10-08
forum: Programming Talk
---

### Post by giuspen on 2010-10-08
Hello,
I'm used to the key "page up" when using the bash that let me pick previous commands I recently used starting with the same chars I already entered.
The problem is that I don't have that key on my laptop, is there another way to have that functionality/a way to change the shortcut?
Thanks.

---

### Post by conundrumx on 2010-10-08
Yes.

```
bind '"[A":history-search-backward'
bind '"[B":history-search-forward'
```

I use that in my .profile.  I believe those are the bindings you want.  The keys they're bound to correspond to up and down arrows (like normal history searching).  The way this ends up working is that if you haven't entered anything the history will go backwards as normal, but if you have typed something it will search history matching the already typed characters.

Please note, there are invisible characters in the snippet I posted which are necessary for the bindings to work.

---

### Post by giuspen on 2010-10-08
> **conundrumx said:**
> Yes.

```
bind '"[A":history-search-backward'
bind '"[B":history-search-forward'
```

I use that in my .profile.  I believe those are the bindings you want.  The keys they're bound to correspond to up and down arrows (like normal history searching).  The way this ends up working is that if you haven't entered anything the history will go backwards as normal, but if you have typed something it will search history matching the already typed characters.

Please note, there are invisible characters in the snippet I posted which are necessary for the bindings to work.

it works great, thank you!

---

