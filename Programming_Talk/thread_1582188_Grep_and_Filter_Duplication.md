---
title: "Grep and Filter Duplication"
date: 2010-09-26
forum: Programming Talk
---

### Post by huangyingw on 2010-09-26
Hello, 
    I am intending to write such a script:
```
for ss in `git remote -v|grep -o ^[a-zA-Z]*`; do git push --all $ss && git push --tag $ss; done
```
    The fault of my solution is that it will produce duplicate result, the root is that:
```
git remote -v|grep ^[a-zA-Z]* -o
```, the result is that:
```
gh
gh
origin
origin

```.
     The original result of ```
git remote -v
``` is ```
gh	git@github.com:huangyingw/bashrc.git (fetch)
gh	git@github.com:huangyingw/bashrc.git (push)
origin	/media/smb/myproject/git/linux/bashrc (fetch)
origin	/media/smb/myproject/git/linux/bashrc (push)
```
What I want is just filter out two word: "gh" and "original"
     How could I filter out the duplicated ones, and, I think my regular ```
^[a-zA-Z]*
```, is not so exact to filter out the first word in one line, could someone provide me with a more exact one for "the first word in one line"?

---

### Post by Trumpen on 2010-09-26
You can pipe the output of grep to uniq:

```
git -v remote | grep -o '^[[:alpha:]]*' | uniq
gh
origin
```

Otherwise, you could substitute grep with awk:

```
git -v remove | awk '/\(fetch\)$/{print $1}'
gh
origin
```

The above comand prints the first word of those lines that end with '(fetch)'.

---

### Post by huangyingw on 2010-09-26
> **Trumpen said:**
> You can pipe the output of grep to uniq:

```
git -v remote | grep -o '^[[:alpha:]]*' | uniq
gh
origin
```

Otherwise, you could substitute grep with awk:

```
git -v remove | awk '/\(fetch\)$/{print $1}'
gh
origin
```

The above comand prints the first word of those lines that end with '(fetch)'.
Yes, thank you. I appreciate the first solution.

---

