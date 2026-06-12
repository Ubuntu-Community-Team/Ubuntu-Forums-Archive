---
title: "Best way to set up SVN server with users and groups?"
date: 2009-09-09
forum: Programming Talk
---

### Post by guiclaw on 2009-09-09
I hope this is the right place to post this!

Me and a few others work on web-development and we don't have any version control yet (which I'm trying to sort out!) Basically we want to use SVN, and have some form of user account system where we each just have one 'account' for SVN, and then we can specify which repositories we're allowed to access. I've tried my best to search through the SVN manuals and things, but I can't find out if what I'm trying to do is even possible.

So my main questions are, does SVN support 'users' and 'groups' globally across repositories, or is it purely repo based authentication.

Also, we would like to have some form of web-based viewer (ViewVC or WebSVN) with the similar authentication system - so only the repositories that we're allowed to access are visible.

I hope this makes sense to someone and I'd appreciate the help!

Thanks

---

### Post by johnl on 2009-09-09
Hi,

I think that you could accomplish it like so:

1. create user accounts for each member of your team on the system. ('user1', 'user2', etc.)

2. create repository1, owned by svn, group 'svn1'.  set permissions to disallow reading by others.  (note that you need to also set the permissions to g+s so that new files are created under the 'svn1' group and not the user)

2. create repository2, owned by svn, group 'svn2'. set permissions to disallow reading by others. (ditto about g+s)

3. add users who should be able to access each repo to the respective groups.

4. don't use svnserve or anything like that -- make these local repositories.  You can access them via ssh like so:

"svn co svn:ssh://user@host:path/to/repo"

each user will only be able to access repos that their group can access.

Not sure how you would setup viewvc to do this.  I don't know if it's possible.

---

### Post by Reiger on 2009-09-09
Yes. There is the concept of "realms" which IIRC can span multiple repositories and/or subsets thereof and what have you. (Probably a better idea than clobbering a system with dummy user accounts; and you can still use svn serve.) Your best starting point for SVN authentication would probably be the config files generated for a new SVN project by svnadmin. There are actually quite a few online help articles for SVN... try the subversion.tigris.org site for references. 

If you don't want to delve into realms and such elaborate approaches you can simply make a group based authentication configuration file and stick to one repository with multiple projects. (A much less complex scenario by far.)

The idea is simple: all co-developers are member of a group, say devs. But some devs are also member of another group, say, css; and yet others of the group sql. Now what you do is create more than 1 project in this repository; each project associated with a particular group. Then you use the authz config file for setting permissions per group as appropriate.


Also there is websvn, which might be the other thing you are looking for?

---

### Post by guiclaw on 2009-09-14
Thanks for your help guys. I went with the 'realms' way in the end.

I basically created a single 'users' file with all the users for the entire system, and then made an 'authz' file which specified groups and the reps that users were allowed to access, and for every new repository, the svnserve.conf file is sym-linked to the one config file that has the paths to the 'users' and 'authz' file.

This works very well, and for WebSVN, it uses the 'authz' file too, and there's a separate apache 'users' file which is updated at the same time as the users file, so apache handles authorisation - and WebSVN knows which user i'm logged in as and only displays the repositories that i'm allowed to!

Exactly what I wanted!

---

### Post by v8YKxgHe on 2009-09-14
Slightly off topic, but as you mention WebSVN - have you taken a look at [Redmine](http://www.redmine.org)? It'll provide you with great issue/feature tracking as well.

---

### Post by guiclaw on 2009-09-14
That actually looks pretty good. I've set up RT 3.8.4 to do that along with MediaWiki for wiki, but Redmine looks like a good solution - I'll have a look into it...

---

