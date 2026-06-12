---
title: "Ubuntu Breezy Makes aspell Change"
date: 2005-11-24
forum: Programming Talk
---

### Post by SuperMike on 2005-11-24
In Ubuntu Breezy, the aspell command has changed. I used to have the following PHP code, but it breaks now:

$result = `echo "test" | aspell -l`;

Unfortunately, however, I have to change the code to this:

$result = `echo "test" | aspell list`;

So much for the makers of aspell making things backwards-compatible.

So, is there a way to do spell checks in PHP without having to shell out to code that can break all the time?

---

### Post by zootreeves on 2005-11-24
don't upgrade aspell...

---

