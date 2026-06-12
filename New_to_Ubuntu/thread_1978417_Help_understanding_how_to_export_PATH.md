---
title: "Help understanding how to export PATH?"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by jps2012 on 2012-05-11
I'm trying to understand how to export a PATH. Most of the FAQs I've read deal with how to set a path for a new script, but I want to do this for an entire folder full of scripts. 

So, three questions: 

1. How do you edit a path in bash that will include all the files in a given folder? 

2. When you edit (or set) a path using the command below (copied from a FAQ), are you overwriting the existing path, or are you appending it? 

3. When you issue the following command, does it force a change in a text file/shell script, or do you also have to follow the command with an edit of the text file/shell script (in .bash_profile, for example)? 

Here's the command in question: 

PATH=$PATH:$HOME/bin:/opt/mpich-1.2.4/bin
export PATH

Thanks, folks.

---

### Post by MG&amp;TL on 2012-05-11
To set an environment variable such as $PATH temporarily, you can just use the export command. The command adds ~/bin and a place in /opt to PATH-you can tell as it adds them to the existing PATH:

```
export PATH=$PATH:/blah
```

-this references the old path in the command for setting the new one. Path now has an extra location-/blah on the end of it.

To set it permamently, put the command in your ~/.bashrc. Bash loads this at startup, so it will always be set.

As for your first question-if you mean recursively, I don't think that can be done-but bash will automatically read all files one level under the directories in $PATH

---

### Post by jps2012 on 2012-05-13
Thanks, MG&H. It wasn't clear to me (from the FAQs) if the existing PATH would be overwritten by "Export." I appreciate the straightforward explanation.

---

### Post by MG&amp;TL on 2012-05-14
> **jps2012 said:**
> Thanks, MG&H. It wasn't clear to me (from the FAQs) if the existing PATH would be overwritten by "Export." I appreciate the straightforward explanation.


No problem, sometimes it might be worth reading the manpage though. :)

---

