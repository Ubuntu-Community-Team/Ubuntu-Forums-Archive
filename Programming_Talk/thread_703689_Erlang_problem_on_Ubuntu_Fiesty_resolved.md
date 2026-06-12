---
title: "Erlang problem on Ubuntu Fiesty resolved"
date: 2008-02-21
forum: Programming Talk
---

### Post by efittery on 2008-02-21
When typing:

erl -sname foo

I kept crashing.

I tracked it down to:

The permissions on ~/.erlang.cookie were -r--------

Which required me to use:

sudo erl -sname foo

You could also log into your ubuntu box as the administrator who has as you know priviledges to do anything.

I am not sure how normal users that do not have the pass word for sudo can get around this.

Any suggestions from anybody?

:)

---

