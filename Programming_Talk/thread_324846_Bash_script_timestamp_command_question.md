---
title: "Bash script timestamp command question"
date: 2006-12-24
forum: Programming Talk
---

### Post by Bobtheknight on 2006-12-24
Hey all,

Merry Christmas, first of all.  I want to write a script that backs up my data in a directory.  Here's my idea.

if (there are more untraversed folder){
     go into first untraversed folder;
     call this script again recursively;

    while (there are more files left){
        Compare timestamp of files from source to destination;
            if (source->timestamp > dest->timestamp){
                cp (source, dest);
            }
    }
}

This project turns out to have a deeper scope thank I imagined.  Can anyone help me by telling me 1.  Is this implementable in bash scripting.  2.  How do I get the timestamp of a file (when it's last modified).  I'll look up the recursion by myself if there's a solution.

Thanks :D

---

### Post by po0f on 2006-12-24
Bobtheknight,

You're doing *waaayy* too much work.  Use `rsync`.  ;)

---

