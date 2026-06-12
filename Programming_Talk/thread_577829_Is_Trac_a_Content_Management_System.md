---
title: "Is Trac a Content Management System?"
date: 2007-10-16
forum: Programming Talk
---

### Post by samir85 on 2007-10-16
Hey guys,

in a college course of mine, I've the task to present a Content Management System of my choice. I already know [Trac]("http://trac.edgewall.org") a little bit, but I am not so sure if it is a CMS. So can you guys tell me something about that?

I'd really appreciate any advice,

regards Samir

---

### Post by slavik on 2007-10-16
seems like trac is a wiki/bugzilla thing :)

take a look at e107. that's a CMS, has built in forums, single user authentication for everything (you can give access to users for certain sections of the site, or display different news/articles or different greeting message, etc.)

---

### Post by samir85 on 2007-10-17
Well, I know that Trac is a Bugzilla thing, but it's also much more. It's Bugzilla, Wiki, SVN repository in one. But most importantly, I still don't know if it is a CMS? ;)

---

### Post by AZzKikR on 2007-10-17
It's not really a Content Management System. Check out this link for starters:

[http://en.wikipedia.org/wiki/List_of_content_management_systems](http://en.wikipedia.org/wiki/List_of_content_management_systems)

---

### Post by pmasiar on 2007-10-17
TRAC is not CMS, but it's wiki can fake one.

TRAC is much more that just plain CMS: bug tracker and SVN repository are tightly integrated with wiki. So you can commit changeset with message "fixed #1234" and post-commit hook will close the 1234 bug. Or, wiki has special markup to link to changeset or to bug by number. And the same markup can by used in comments, and patched SVNView will make hyperlink to proper page.

---

