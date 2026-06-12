---
title: "jEdit install problem"
date: 2006-09-26
forum: Programming Talk
---

### Post by tivolives on 2006-09-26
I've looked through the forum, and while there's plenty of discussion about jEdit, I don't see my problem addressed. I follow the directions here:
[http://www.cs.cornell.edu/~djm/ubuntu/#jedit](http://www.cs.cornell.edu/~djm/ubuntu/#jedit)

apt-get runs, then I get:
...
Err [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Packages
  506 Failure To Connect To Web Server [IP: 64.74.207.41 80]
Err [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Sources
  506 Failure To Connect To Web Server [IP: 64.74.207.41 80]
Fetched 5B in 3m17s (0B/s)
Failed to fetch [http://dl.sourceforge.net/sourceforge/jedit/./Packages.gz](http://dl.sourceforge.net/sourceforge/jedit/./Packages.gz)  506 F ailure To Connect To Web Server [IP: 64.74.207.41 80]
Failed to fetch [http://dl.sourceforge.net/sourceforge/jedit/./Sources.gz](http://dl.sourceforge.net/sourceforge/jedit/./Sources.gz)  506 Fa ilure To Connect To Web Server [IP: 64.74.207.41 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.

Two questions:

Is there a reason why there is no synaptic install for jEdit?

Is there a better editor? I particularly liked tag completion, function completion, etc. (I mostly used it for XML editing on Windows).

---

### Post by meng on 2006-09-26
Last I used it, jedit could be downloaded as a jar archive and run directly, assuming of course that you had a JRE. Why not try that?

---

### Post by tivolives on 2006-10-23
Thank you, I did that, and it works. I ask again:

Is there a reason why there is no synaptic install for jEdit?

It seems to me to be one of the best editors out there.

---

### Post by Ben Sprinkle on 2006-10-23
Kate is good, so is Gedit. Both have syntax highlighting for a shit load of languages. I use Kate. :)

---

### Post by cnu on 2006-11-03
> **meng said:**
> Last I used it, jedit could be downloaded as a jar archive and run directly, assuming of course that you had a JRE. Why not try that?

I can install JEdit using the jar file, if I choose to open using Sun Java 5 Runtime. 
But how to do a system wide install?

---

