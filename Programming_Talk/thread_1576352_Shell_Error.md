---
title: "Shell Error"
date: 2010-09-17
forum: Programming Talk
---

### Post by huangyingw on 2010-09-17
Hello all,
    I want to write such a shell file dof.sh as bellow:
    ```
#!/bin/bash
for ss in `$1`; do $2 $ss; done

```
    And I add an alias entry as dof in $HOME/.bashrc file.
    So, I would like to use it in the following way:
    ```
dof "git status|grep samples.* -o" "git rm --cached"
```
    But I got the following error:
    ```
yinghuang@yinghuang-desktop0:~/myproject/git/c_c++/gtest-1.5.0$ dof "git status|grep samples.* -o" "git rm --cached"
git: 'status|grep' is not a git command. See 'git --help'.
```
    I guess that it might be the "|" character is misunderstand in `$1`.
    How could I help `$1` to correctly understand this "|" character?

---

