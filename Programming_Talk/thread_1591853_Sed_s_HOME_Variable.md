---
title: "Sed s HOME Variable"
date: 2010-10-09
forum: Programming Talk
---

### Post by huangyingw on 2010-10-09
Hello all,
     I want to replace the string "media/smb" with my environment variable "$HOME" with sed,as shown bellow:
```
	x=`echo $1 | sed -e "s/\/media\/smb/$HOME/"`
```, but it return me with such following errors:
```
sed: -e expression #1, char 17: unknown option to `s'
```
     How could I handle this?

---

### Post by PC-XT on 2010-10-10
I'm far from an expert, but here are some things I might try:

Does it work without the -e switch?

Maybe try the find command first, like
sed '/foo/ s//bar/' filename
to see if it's something other than the s command. (or just replace with other commands)

Is $1 giving a proper input to pipe?

---

### Post by Some Penguin on 2010-10-10
$HOME probably contains a / and thus needs escaping.

(In Perl, there's \Q$blah\E syntax; I don't know if sed uses the same syntax, but it presumably has an equivalent).

---

### Post by mobilediesel on 2010-10-10
> **huangyingw said:**
> Hello all,
     I want to replace the string "media/smb" with my environment variable "$HOME" with sed,as shown bellow:
```
	x=`echo $1 | sed -e "s/\/media\/smb/$HOME/"`
```, but it return me with such following errors:
```
sed: -e expression #1, char 17: unknown option to `s'
```
     How could I handle this?

Since $HOME will usually contain a slash **"/"**, use **"|"** instead of **"/"** for the sed statement:
```
x=$(echo $1 | sed -e "s|/media/smb|$HOME|")
```

Also:
[**Why is $(...) preferred over `...` (backticks)?**]("http://mywiki.wooledge.org/BashFAQ/082")

---

### Post by huangyingw on 2010-10-16
> **mobilediesel said:**
> Since $HOME will usually contain a slash **"/"**, use **"|"** instead of **"/"** for the sed statement:
```
x=$(echo $1 | sed -e "s|/media/smb|$HOME|")
```

Also:
[**Why is $(...) preferred over `...` (backticks)?**]("http://mywiki.wooledge.org/BashFAQ/082")

Sorry for a late reply for your answer. It works for me. Great thanks.

---

