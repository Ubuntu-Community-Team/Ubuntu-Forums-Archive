---
title: "Git delete from local and remote repositories"
date: 2015-06-30
forum: Programming Talk
---

### Post by Drenriza on 2015-06-30
I have installed git-core on a raspberry pi behind a hardware firewall ment as a git repositori for different projects and files i work on.

My question is, what is the proper way of removing files from the git repositori and than from the disk local and remote.

I have searched on the web but cant find a good example with a explonation on the subject.
I have also looked in the Pro Git (free) pdf book, but didnt quite find what i looked for.

Hoping someone can help me / point me in the right direction.
Thanks on advance.

---

### Post by trent.josephsen on 2015-06-30
```
$ git rm SOME_FILE
$ git commit
$ git push
```

---

### Post by Drenriza on 2015-06-30
> **trent.josephsen said:**
> ```
$ git rm SOME_FILE
$ git commit
$ git push
```

Hey Trent

Thanks for the reply!

But isint this only for local repo? What about the remote one?

---

### Post by spjackson on 2015-06-30
> **Drenriza said:**
> 
But isint this only for local repo? What about the remote one?
"git push" sends your local commits to remote, so your "git rm" gets applied there.

---

