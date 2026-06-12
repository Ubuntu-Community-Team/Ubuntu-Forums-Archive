---
title: "shell bookmarks"
date: 2012-08-22
forum: Programming Talk
---

### Post by trois_1 on 2012-08-22
Hello,
I try to use shell bookmarks with DirB.

It is a script file with a list of function.

Need to be sourced in .bashrc.
But, when i sourced the file, errors rised !
can try it?
Do you have this problem?
any idea?

The file join to this post.

bash: .bashDirB: line 117: syntax error near unexpected token `elif'
'ash: .bashDirB: line 117: `    elif [ "$1" == "-" ]

---

### Post by spjackson on 2012-08-22
That script has DOS line endings, i.e. CR LF. Bash scripts are sensitive about this. If you convert it to LF line endings, your problem will be solved.

---

### Post by trois_1 on 2012-08-22
ok, thanks, it works now.

---

