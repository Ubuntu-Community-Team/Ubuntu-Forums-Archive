---
title: "How to Sync between My Private SVN and Public SVN"
date: 2009-05-02
forum: Programming Talk
---

### Post by huangyingw on 2009-05-02
Hello,
    My case is that, we share a public SVN server. So, what I could check in is only the mature, stable codes.
    But, I would like to check in every sparks I made during coding. So, I would like to create another private, personal SVN server. With that private one, I could check in as much as I like.
    But I found that it is difficult to sync between two SVN server. And it is impossible to keep one working copy,  to point to dual SVN servers.
    Maybe my solution, would be to keep two working copies, and use some command like "cp -fruv source target --exclude ".svn"" to sync between the working copies.
    Is there other better and more convinience solution?

---

### Post by geirha on 2009-05-02
The common way would be to create your own branch on the public SVN server. Once you're done coding, you merge your branch with the main branch ... Read the chapter on branching and merging in the svn-book [http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)

---

### Post by wmcbrine on 2009-05-02
This kind of thing is easy with git. Maybe it would make sense to do your work in a local git repository and update the "polished" code with git-svn? I dunno; I haven't actually worked with git-svn yet.

---

### Post by huangyingw on 2009-05-02
> **geirha said:**
> The common way would be to create your own branch on the public SVN server. Once you're done coding, you merge your branch with the main branch ... Read the chapter on branching and merging in the svn-book [http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)

I don't think it a good idea. And I think that this right must have been prohibited. If everyone create a private branch, that would be a mess.

---

### Post by huangyingw on 2009-05-03
> **wmcbrine said:**
> This kind of thing is easy with git. Maybe it would make sense to do your work in a local git repository and update the "polished" code with git-svn? I dunno; I haven't actually worked with git-svn yet.
Yes, thank you for giving me a new point. With your clues, I have googled out some DVCS candidates. And I am caring about their back-compatibility. So, I opened a new thread to discuss their differences.
Welcome you to join discussion and express your opinion at :
[http://ubuntuforums.org/showthread.php?t=1146948](http://ubuntuforums.org/showthread.php?t=1146948)

---

