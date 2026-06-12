---
title: "git"
date: 2010-09-16
forum: Programming Talk
---

### Post by l3ecl on 2010-09-16
i thought i'd ask here since programmers are more familiar with git

how do i get git to add all hidden files? i want to add all the hidden files in my home directory (.bashrc, .vimrc ect) because i always play around with them. 

in return : best simile i heard today

"women are like bagels, i have sex with them"

---

### Post by phrostbyte on 2010-09-16
Try putting 

!.*

in the .gitignore file

I'm not 100% sure this will work, but in theory it should.

---

### Post by MadCow108 on 2010-09-17
is that what you want?

find . -name ".?*" -type f -print0 | xargs -0 git add

---

