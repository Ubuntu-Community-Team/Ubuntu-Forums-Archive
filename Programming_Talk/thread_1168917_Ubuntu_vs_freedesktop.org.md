---
title: "Ubuntu vs freedesktop.org"
date: 2009-05-24
forum: Programming Talk
---

### Post by cl333r on 2009-05-24
Can anyone please comment whether Ubuntu is in a state of transition, stagnation or opposition to the specs from the freedesktop.org?

I'm examining the specs and I notice that Ubuntu doesn't seem to follow them (in many random cases) and since my app has to use lots of environment data I'm puzzled.

For example the XDG variables are gone: "echo $XDG_DATA_HOME" prints nothing or so.

Any comments please?

---

### Post by Namtabmai on 2009-05-24
Printing nothing is part of the standard.
Are you saying that the default the standard specifying doesn't match the expected value in Ubuntu?

---

### Post by cl333r on 2009-05-24
Thanks a lot! After googling more I found other users asking about this and all was needed was to read the spec till the end. Just gotta be more careful. However, if problems arise I'll ask here, thanks.

PS: this blog is interesting:  [http://ploum.frimouvy.org/?207-modify-your-application-to-use-xdg-folders](http://ploum.frimouvy.org/?207-modify-your-application-to-use-xdg-folders)

---

