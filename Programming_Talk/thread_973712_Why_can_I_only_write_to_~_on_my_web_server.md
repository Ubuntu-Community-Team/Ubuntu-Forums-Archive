---
title: "Why can I only write to ~ on my web server?"
date: 2008-11-06
forum: Programming Talk
---

### Post by pressed on 2008-11-06
For large files, I can only write to root when ssh'd into my web server. I'm trying to save face by asking this question here instead of to my host ;) Anyone have a clue why?

Some actual details:

- quota shows i'm far below quota.
- du . confirms im far below quota
- example activites include cp $1 $2 where $2 is anywhere except ~/
- example activites include tar -xzf $1 anywhere except into ~... the archive might create subdirectories, which it then extracts further files into without problem, but if i start in any subdirectory it fails.
- example activites include using an editor to change existing files, not necessarily making them much larger, and then being unable to "save". When I attempt writeout, I simply write a file of 0 bytes.

scp also fails (usually) when writing to anywhere but ~/. 

What's going on here? I feel like I'm missing something basic.

---

