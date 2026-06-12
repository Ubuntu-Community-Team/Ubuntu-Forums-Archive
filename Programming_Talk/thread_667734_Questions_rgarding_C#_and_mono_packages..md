---
title: "Questions rgarding C# and mono packages."
date: 2008-01-14
forum: Programming Talk
---

### Post by BhRaviKiran on 2008-01-14
Hi Team,
              Forgive me if my question doesn't fit into this post.
               I'm already into some task of running C# applcation on platforms like SuSE Linux Enterprise desktop 10.0 and Mac os xv10.4 Tiger using the Mono-project 1.2.2.1 or higher. 

Currently, Im doing the same on Ubuntu 7.10. Could you plz help me where i can find mono packages for Ubuntu 7.10 so that i can run winforms applications. The download section of mono-project.com gives the mono for distributions like Fedora, Suse..And no mention of Ubuntu.


Thanks in advance.
Regards,
Ravi.

---

### Post by st4rdr1ft3r on 2008-01-15
They are in the repository, the mono runtime is actually installed by default. The win-forms ones are libmono-winforms1.0-cil and libmono-winforms2.0-cil.

---

### Post by BhRaviKiran on 2008-01-15
Hi,
        Thanks for the information.If mono is not installed bydefault then can i say that Ubuntu 7.10 that was downloaded from the site and burnt to the DVD has not installed the OS properly?

How can i unpack the pacakges that are already available? Does the mono installed for Ubuntu 7.10 shows the version of Mono 1.2 or higher?

Thanks in advance.

Regards,
Ravi.

---

### Post by BhRaviKiran on 2008-01-15
Hi,
        Thanks for the information.If mono is not installed by default then can i say that Ubuntu 7.10 that was downloaded from the site and burnt to the DVD has not installed the OS properly?

How can i unpack the pacakges that are already available? Does the mono installed for Ubuntu 7.10 shows the version of Mono 1.2 or higher?

Thanks in advance.

Regards,
Ravi.

---

### Post by st4rdr1ft3r on 2008-01-15
from the terminal:

```
sudo apt-get install libmono-winforms1.0-cil libmono-winforms2.0-cil mono-mcs mono-gmcs
```

will get you a basic development environment.

---

