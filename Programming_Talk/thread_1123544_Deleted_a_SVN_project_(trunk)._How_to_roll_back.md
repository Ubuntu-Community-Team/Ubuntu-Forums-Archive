---
title: "Deleted a SVN project (trunk). How to roll back?"
date: 2009-04-12
forum: Programming Talk
---

### Post by moma on 2009-04-12
Hello all,

:oops: I accidentally deleted the entire source code of my [Gscreendump application]("http://code.google.com/p/gscreendump/"). The source code is managed by SVN on the Google-code's site, so it should be easy task to roll back to the previous state.

The accident happened here:
[http://code.google.com/p/gscreendump/source/detail?r=101](http://code.google.com/p/gscreendump/source/detail?r=101)

I ran this command
$ svn delete [https://gscreendump.googlecode.com/svn/trunk](https://gscreendump.googlecode.com/svn/trunk) --username osmoma 

What I ment to say, was this 
svn delete [https://gscreendump.googlecode.com/svn/version-0.2](https://gscreendump.googlecode.com/svn/version-0.2) --username osmoma 
But I deleted both ../svn/trunk and ../svn/version-0.2

I want the [https://gscreendump.googlecode.com/svn/trunk](https://gscreendump.googlecode.com/svn/trunk) back?
How? Any suggestions.

---

### Post by Reiger on 2009-04-12
Oh, oh; loosing some hard gained result is so much easier than building it, isn't it?
Anyways it appears you would not be the first person to try deleting a trunk to discover that is most undesirable; so for a re-assuring read (and apparently a useful howto get-things-back-from-the-delete)

[http://svn.haxx.se/users/archive-2005-07/0479.shtml](http://svn.haxx.se/users/archive-2005-07/0479.shtml)

Uh forgot a link: [http://m0j0.wordpress.com/2007/10/25/recovering-deleted-files-from-an-svn-repository/](http://m0j0.wordpress.com/2007/10/25/recovering-deleted-files-from-an-svn-repository/)

Good luck getting your app back!

---

### Post by slavik on 2009-04-12
you should be able to revert to a previous revision ...

---

### Post by SuperSonic4 on 2009-04-12
```
cd /path/to/directory
svn commit
```

should roll back your svn

---

### Post by moma on 2009-04-12
Hello and thank you all for a prompt reply. 

I could also do a new import because the local copy is intact.
$ [COLOR="SeaGreen"]cd /media/sdb4/development/gscreendump[/COLOR]

$ [COLOR="SeaGreen"]svn import -m "New import after accidental delete" .   [https://gscreendump.googlecode.com/svn/trunk](https://gscreendump.googlecode.com/svn/trunk)[/COLOR]
(the . denotes the current dir)

The trunk/ directory is now restored and project can move on.
The version 0.3 of Gscreendump will have some drawing capabilities, add talk-bubbles ([callouts]("http://cdnimg.piczo.com/images/callouts/clouds/roundCalloutRight.gif")), arrows etc. to your screenshots/images.

You all saved my sunday afternoon;-)

ps. do not forget to watch the [demo-videos...]("http://code.google.com/p/gscreendump/downloads/list") (screencast-[1-3].avi).

---

### Post by davebridges on 2009-10-18
I had this exact problem today and after banging my head against a wall (and sending unresponded questions to #svn) your solution saved my butt.  Thanks!

---

### Post by MadCow108 on 2009-10-18
here's an excellent documentation for svn
[http://svnbook.red-bean.com/en/1.5/](http://svnbook.red-bean.com/en/1.5/)

including how to undelete stuff:
[http://svnbook.red-bean.com/en/1.5/svn.branchmerge.basicmerging.html#svn.branchmerge.basicmerging.resurrect](http://svnbook.red-bean.com/en/1.5/svn.branchmerge.basicmerging.html#svn.branchmerge.basicmerging.resurrect)

---

