---
title: "Check operating  system"
date: 2009-10-11
forum: Programming Talk
---

### Post by silentrebel on 2009-10-11
What is the command in bash that returns the name of host operating system? 
Is there one that is more specific to the name of the operating system and another that returns a more general answer (Unix/Windows/...)?
If so, both would be useful to me.
Thank you,
Afsheen

---

### Post by -grubby on 2009-10-11
Well, I found this that determines if the host OS is Redhat or Debian: [http://dancingpenguinsoflight.com/2009/09/useful-bash-functions-to-determine-os-and-more/](http://dancingpenguinsoflight.com/2009/09/useful-bash-functions-to-determine-os-and-more/)

But no, I don't think Bash has anything built in to figure out the host OS. And chances are, if you need to do something so advanced as to need the name of the host OS, you might want to use something besides shell scripts.

---

### Post by silentrebel on 2009-10-11
Thanks...  I'm going to stick with shell scripts but find another programming language that has this capability...  I can then call a program written in that language and return the result...  I'm really only using the shell script for file manipulations and wrapping the rest of the program, anyway...
Thanks for your suggestions

---

### Post by NoaHall on 2009-10-11
uname

or 
uname -a 


?

---

