---
title: "emacs and C/C++ auto code completion problem"
date: 2009-06-19
forum: Programming Talk
---

### Post by colau on 2009-06-19
Hi,
dpkg -l | grep emacs
```

ii  cxref-emacs                                1.6a-1.2                                  Generates latex and HTML documentation for C programs
ii  emacs                                      22.2-0ubuntu2                             The GNU Emacs editor (metapackage)
ii  emacs22-bin-common                         22.2-0ubuntu2                             The GNU Emacs editor's shared, architecture dependent f
ii  emacs22-common                             22.2-0ubuntu2                             The GNU Emacs editor's common infrastructure
ii  emacs22-gtk                                22.2-0ubuntu2                             The GNU Emacs editor (with GTK+ 2.x support)
ii  emacsen-common                             1.4.17                                    Common facilities for all emacsen
ii  html-helper-mode                           3.0.4kilo-2                               A popular HTML editing mode for emacs

```

dpkg -l | grep cedet
```

ii  cedet-common                               1:1.0pre4-3                               Collection of Emacs Development Environment Tools - com
ii  cedet-contrib                              1:1.0pre4-3                               Collection of Emacs Development Environment Tools - con

```

```

#include<stdio.h>
#include<iostream>
using namespace std;
struct st{
 int i;
 int j;
};
class cl{
public:
 int i;
 int j;
};
int main(){
 st obj;
 st *p;
 obj.
 p->
 cl obj2;
 cl *p2;
 obj2.
 p2->
 return 0;
}

```
How can I configure emacs so that it supports C/C++ auto code completion?
I followed [http://cedet.sourceforge.net/setup.shtml](http://cedet.sourceforge.net/setup.shtml) but could not find any clue to configure it in ubuntu.
To install cedet i did
```

sudo aptitude install ceded-common

```

---

### Post by colau on 2009-06-23
Bump.

---

### Post by monkeyking on 2009-06-23
Hi,
I'm not really an emacs expert,
but how do you expect autocompletion to work?

What Im really asking is how do you invoke it.

---

### Post by colau on 2009-06-24
> **monkeyking said:**
> Hi,
I'm not really an emacs expert,
but how do you expect autocompletion to work?

What Im really asking is how do you invoke it.
Autocompletion option is supposed to come after typing dot "." or arrow "->" sign.

---

### Post by PandaGoat on 2009-06-24
I am in the process of setting up the same thing.  I have it working but not to what I desire.  After I work out some things I might write a how-to.

My main reference is [http://xtalk.msk.su/~ott/en/writings/emacs-devenv/EmacsCedet.html](http://xtalk.msk.su/~ott/en/writings/emacs-devenv/EmacsCedet.html).

I would suggest first you download the newest version of cedet and use it.

---

### Post by colau on 2009-06-24
> **PandaGoat said:**
> I am in the process of setting up the same thing.  I have it working but not to what I desire.  After I work out some things I might write a how-to.

My main reference is [http://xtalk.msk.su/~ott/en/writings/emacs-devenv/EmacsCedet.html](http://xtalk.msk.su/~ott/en/writings/emacs-devenv/EmacsCedet.html).

I would suggest first you download the newest version of cedet and use it.
Is the link broken?

---

### Post by monkeyking on 2009-07-09
I've been using emacs for years, and never tried setting up this autocompletion stuff.

So I tried, but I get this error on emacs startup

```

An error has occurred while loading `/home/thorfinn/.emacs':

Symbol's function definition is void: global-srecode-minor-mode

To ensure normal operation, you should investigate and remove the
cause of the error in your initialization file.  Start Emacs with
the `--debug-init' option to view a complete error backtrace.

Loading semantic-el...done

```

I don't have varname completion,
but I do get a prototype defintion in the statusbar.
According to the  guide I should load something called

```

require semantic-ia

```

How do I do this?

---

### Post by hateregistering on 2010-11-13
Have you tried ESC+/ ?

---

