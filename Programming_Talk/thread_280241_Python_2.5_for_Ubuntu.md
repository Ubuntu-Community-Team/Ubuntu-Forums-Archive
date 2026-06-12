---
title: "Python 2.5 for Ubuntu ?"
date: 2006-10-19
forum: Programming Talk
---

### Post by jansenh on 2006-10-19
Hi Forum.

When will there be a Python 2.5 upgrade available for Ubuntu through the Synaptic Package Manager? 

[SIZE="1"][the Python installation seems rather complex to me and being a ubuntu newbie I want the upgrade from 2.4 to 2.5 to be as simple and straigt-forward as possible... any other ideas for this upgrade? ][/SIZE]

regards, henning

---

### Post by tseliot on 2006-10-19
It's in Edgy's repositories but it's not installed by default.

It won't be in Dapper's repos.

---

### Post by someguyouknow on 2006-10-20
> **tseliot said:**
> It's in Edgy's repositories but it's not installed by default.

It won't be in Dapper's repos.


so does that mean that it will not upgrade without you "forcing" it?
i have 38 pyton packages that will not upgrade unless i make it. Is it safe to do so?

edit: didnt mean to hijack the thread.

---

### Post by David_T on 2006-10-23
You can always install from source, which by default goes in the /usr/local/ hierarchy, and then you'd be running two different versions.

---

### Post by waffen on 2006-10-28
> **tseliot said:**
> It's in Edgy's repositories but it's not installed by default.

It won't be in Dapper's repos.

And how install Python 2.5 in Edgy? and make this the only Python version in Ubuntu?

Thanks!

---

### Post by skymt on 2006-10-28
> **waffen said:**
> And how install Python 2.5 in Edgy? and make this the only Python version in Ubuntu?

Thanks!

That's not a good idea. A lot of programs still use 2.4, and may break if you try to make them use 2.5. Also, there aren't nearly as many libraries for 2.5 yet.

You can install 2.5 through whatever package manager you prefer. It's in "python2.5". You can use it by running your programs like "python2.5 foo.py". Or, if you use a #! line, use this: "#!/usr/bin/env python2.5".

---

