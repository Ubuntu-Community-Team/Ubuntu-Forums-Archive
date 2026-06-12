---
title: "move an svn repo"
date: 2007-05-19
forum: Programming Talk
---

### Post by earobinson on 2007-05-19
I had a svn repo that was located at 192.168.1.150 but Its now located at 192.168.1.99. because of this svn up or svn ci wont work on my computer. any idea how I can change the svn settings on my computer to point to the new repo?

---

### Post by WW on 2007-05-19
Try **switch**; use **svn help switch** for more information.

---

### Post by earobinson on 2007-05-19
Ya I looked at that, couldent get the syntax correct

---

### Post by Frosty Cold Drink on 2007-05-19
> **earobinson said:**
> Ya I looked at that, couldent get the syntax correct

Are you using svnserve or SSH? It should be something like

```
svn switch --relocate svn://path/to/old/repo svn://path/to/new/repo /path/to/working/copy
```

The other syntax isn't applicable to your situation.

---

### Post by WW on 2007-05-19
There is an example of using the --relocate option here: [http://svnbook.red-bean.com/en/1.2/svn-book.html#svn.ref.svn.c.switch](http://svnbook.red-bean.com/en/1.2/svn-book.html#svn.ref.svn.c.switch)

It appears that something like this should work, if you are in your working copy directory:
```

svn switch --relocate OLD_SVN_URL NEW_SVN_URL .

```
where OLD_SVN_URL is the URL that you used to check out your working copy, and NEW_SVN_URL is the new URL that you would use to check out a copy.

However, I am just reading and interpreting the document.  If you don't get a more definitive response here, you could also try the IRC channel #svn.

EDIT: What frosty said  :)

---

### Post by earobinson on 2007-05-20
thanks

---

### Post by earobinson on 2007-05-31
hum I seem to be having a problem ```
earobinson@minusone:/media/data$ svn switch --relocate /media/data/svn/data svn+ssh://earobinson@192.168.1.107/media/data/svn/data .
svn: '/media/data/svn/data' to 'svn+ssh://earobinson@192.168.1.107/media/data/svn/data' is not a valid relocation
earobinson@minusone:/media/data$ 
```

however ```
earobinson@minusone:/media/data/test$ svn co svn+ssh://earobinson@192.168.1.107/media/data/svn/data

``` will work

---

### Post by WW on 2007-06-01
The URL for a local repository should be **file:///media/data/svn/data**

---

