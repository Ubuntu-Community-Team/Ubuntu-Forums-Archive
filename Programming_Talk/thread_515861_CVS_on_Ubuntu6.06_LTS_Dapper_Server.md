---
title: "CVS on Ubuntu6.06 LTS Dapper Server"
date: 2007-08-02
forum: Programming Talk
---

### Post by sfcg on 2007-08-02
I'm new to CVS and Ubuntu, but found myself in a position to support both in my workplace. I've searched high and low for a decent doc on backing up CVS and I cannot for the life of me find anything conclusive. Hence I was recommended to these forums by someone who frequents them. There once was an O'Reilly book here on it, but has since dissapeared. If I do not find anything through this channel I will likely just go buy the book again. 

I know the nature of CVS, and hence understand it locks files for editing to ensure the integrity of the source, therefore when backing up the repository you have to somehow get those locked files/directories/tree's or whatever checked in before you back it up.

Can anyone point me to a doc/script that explains the best practices for this?

Thanks,

Chris

---

### Post by ptillemans on 2007-08-04
Hi,

we have been using CVS for a long time now and have 100's of gigabytes in our repositories. We never ever had an issue with locks after a restore.

The CVS repositories are just directories with files in them. CVS creates 'lock' directories when people are accessing these, however these can also (seldom) remain there for other reasons.

In general : just backup the repository directory starting from the root and you will be fine.

For more general info : 

[http://tldp.org/REF/CVS-BestPractices/html/CVS-BestPractices.html](http://tldp.org/REF/CVS-BestPractices/html/CVS-BestPractices.html)


Peter

---

