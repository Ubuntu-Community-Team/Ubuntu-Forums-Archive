---
title: "[Python] questions about gettext"
date: 2010-05-17
forum: Programming Talk
---

### Post by BackwardsDown on 2010-05-17
Hi!

I'm creating an application where you can create projects and append todo-lists, files, agenda's, etc to manage your workflow. In the end it should sync with UbuntuOne. Project [HERE]("https://launchpad.net/project-manager").


Now I'm translating my program with gettext. I've got in most of the files:
```
t = gettext.translation('project_manager', 'locale', fallback=True)
_ = t.gettext

```
Is there a way to make this global and do this only in the main file? It seems ugly now.


Also I want to translate sentences with variables in it like:
> Are you sure you want to delete $project_name from the list?
How do I do that with gettext?

---

### Post by smartbei on 2010-05-18
For the first question, you probably have a file that is included in all the rest of your files - some sore of common definitions file. If so, you could have the gettext code in that file, and do:
```
from common import _
```
And that would be it.
You might have several things that you may want to put in the file, in which case you could import *.
As for processing $variables - I suggest you do this in a method of your own, after retrieving from gettext. Since I have not been able to find a relevant example online, you can either google some more for it (I bet you've already done this), or implement your own. One solution is to use either $varname or {varname}, etc. and parse the string, recognize the varname and extract it with gettext.

---

### Post by BackwardsDown on 2010-05-18
Thanks for replying!

> **smartbei said:**
> For the first question, you probably have a file that is included in all the rest of your files - some sore of common definitions file. If so, you could have the gettext code in that file, and do:
```
from common import _
```
And that would be it.
I think I'm going to do that. I think I would need such file eventually anyway.

> **smartbei said:**
> As for processing $variables - I suggest you do this in a method of your own, after retrieving from gettext. Since I have not been able to find a relevant example online, you can either google some more for it (I bet you've already done this), or implement your own. One solution is to use either $varname or {varname}, etc. and parse the string, recognize the varname and extract it with gettext.
Yeah I found some PHP-examples that do this but I thought it was such a common practice I could not imagine that it's not supported by gettext itself. I'll overload the _ myself to get the features I need :).

Thanks!

---

