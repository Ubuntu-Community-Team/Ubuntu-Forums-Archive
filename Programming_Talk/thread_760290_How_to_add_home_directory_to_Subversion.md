---
title: "How to add home directory to Subversion"
date: 2008-04-20
forum: Programming Talk
---

### Post by linfidel on 2008-04-20
I'm trying to learn Subversion, and also do something useful by putting my home directory under source control.  I've read documentation on various setups, but nothing will work, other than adding each file one by one.

It seems like the only way to add a directory "in-place" is to create an empty repository directory, then add the files.  This almost worked for me, but I can't get it to add the hidden files starting with a dot.  It seems to add other files, so I guess I'm doing the commands correctly.

I also tried doing import, and then checkout to make it a working directory, but it refuses to overwrite existing files.

Anyone have any experience with this?  I could use a pointer or two.

Thanks,

---

### Post by aks44 on 2008-04-20
You could checkout in an empty directory.

In that checkout directory, recursively delete all *files* (not dirs) that are not inside a .svn directory (so that you won't overwrite your files in /home that have changed in the meantime).

Then just move the .svn directories that are left into your actual /home.

That should do the trick.

**OF COURSE, BACKUP EVERYTHING BEFORE DOING THAT...** ;)


EDIT:
Problem with versioning your whole /home dir is that some apps will delete directories without any care for SVN. This may lead to strange errors (as far as SVN goes)... IMHO this is a bad idea to do that.

---

### Post by linfidel on 2008-04-20
> **aks44 said:**
> You could checkout in an empty directory.

In that checkout directory, recursively delete all *files* (not dirs) that are not inside a .svn directory (so that you won't overwrite your files in /home that have changed in the meantime).

Then just move the .svn directories that are left into your actual /home.

That should do the trick.
I was wondering if that would work.  I was afraid that some files in .svn would have the path.  Are you sure it doesn't?  I guess I could just try it... to steal a phrase from a local newsgroup poster - Learn by Destroying.

> **aks44 said:**
>  
**OF COURSE, BACKUP EVERYTHING BEFORE DOING THAT...** ;) That goes without saying. :)

> **aks44 said:**
> EDIT:
Problem with versioning your whole /home dir is that some apps will delete directories without any care for SVN. This may lead to strange errors (as far as SVN goes)... IMHO this is a bad idea to do that.
Maybe I don't understand how it works yet (very possible, I just started learning).  I thought one of the features of SVN was that it handled directory changes without problems.  My guess was that I would just do a commit every now and then, and it would mirror the current state.

But if I can't get it to handle the hidden files, then it's not going to work, since that's mostly what I want to save.  I'm planning to skip big directories with documents, etc.  Those I should back up with rsync or something similar.

Thanks for your input so far.  I'd like to hear more, especially about the directory deletion issue.

---

### Post by linfidel on 2008-06-25
I've abandoned Subversion in favor of git, written by our friend Linus.  It's much better suited to the way I want to do things.  Also, it's very fast - almost as if the authors had inside knowledge about the kernel.  ;)

---

