---
title: "Is there a set &quot;vocabulary&quot; for editing configuration files?"
date: 2014-10-19
forum: New to Ubuntu
---

### Post by adj3 on 2014-10-19
Hello people,

I have been recently learning more about .config files and editing them on Youtube and other sources. I've been watching tutors editing .config files with special configuration words or "keywords" if you will and honestly it seems very random. My questions are; are there standard keywords that one uses to edit .config files? Or are the keywords specific to each configuration file? How would I know which words to use?

Thanks guys :-)

---

### Post by Vladlenin5000 on 2014-10-19
Each configuration file is specific for the program/service/whatever they're meant to... configure. So, it can be anything.

---

### Post by adj3 on 2014-10-19
> **Vladlenin5000 said:**
> Each configuration file is specific for the program/service/whatever they're meant to... configure. So, it can be anything.

If they are specific to each file how would I know what keyword to use?

---

### Post by Vladlenin5000 on 2014-10-19
> **adj3 said:**
> If they are specific to each file how would I know what keyword to use?

Well, if you don't know what changes you need to do in a given configuration file then perhaps you shouldn't be messing with it.
If you give examples then maybe someone who's already using that software can give you suggestions.

---

### Post by deadflowr on 2014-10-19
> **adj3 said:**
> If they are specific to each file how would I know what keyword to use?

There is usually documentation.
Perhaps look over the manpage for the program or service, [s]or look in the directory /usr/share/doc[/s]
Or add the option --help to the programs run command in a terminal.
(They're usually the same thing)

Edit: I've edited myself, because help was what I was thinking not the doc pages.
Also, a lot config files themselves list options you can use.

---

### Post by grahammechanical on 2014-10-19
Also keep in mind that over time user interfaces change. The locations of configuration files change. A lot of configuration files are actually scripts. So, perhaps you should be looking for tutorials about BASH. Other configuration files are just text files containing a record of how the user interface is set up.

Regards.

---

### Post by vasa1 on 2014-10-19
> **adj3 said:**
> ... editing .config files with special configuration words or "keywords" if you will and honestly it seems very random. ...
Random may be a strong word but it's close to the real situation.
> **adj3 said:**
> ... are there standard keywords that one uses to edit .config files? ...
Unfortunately, no.
> **adj3 said:**
> ... Or are the keywords specific to each configuration file? ...
Pretty much.
> **adj3 said:**
> ... How would I know which words to use? ...
If you're lucky, the program would be well documented. If not, you may have to find more experienced users and ask them or contact the program's developer.

---

### Post by adj3 on 2014-10-20
> **vasa1 said:**
> Random may be a strong word but it's close to the real situation.

Unfortunately, no.

Pretty much.

If you're lucky, the program would be well documented. If not, you may have to find more experienced users and ask them or contact the program's developer.

Thank you all.
Thank you Vasa1 for your clear explanation!

---

