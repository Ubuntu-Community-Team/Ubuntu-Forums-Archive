---
title: "repository command line permission denied"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by Nadarasan on 2012-05-23
when i use repository command line  'etc/apt/sources.;list"   I get the response as permission denied,suggest solution.

---

### Post by MG&amp;TL on 2012-05-23
...you mean you type:

```
/etc/apt/sources.list
```

?

In which case, that won't do anything. What are you trying to acheive?

---

### Post by wojox on 2012-05-23
What are you trying to do?
```
cat /etc/apt/sources.list
```

---

### Post by Nadarasan on 2012-05-25
> **Nadarasan said:**
> when i use repository command line  'etc/apt/sources.;list"   I get the response as permission denied,suggest solution.
to  see a list of software repositories and add or delete them

---

### Post by Nadarasan on 2012-05-25
> **MG&TL said:**
> ...you mean you type:

```
/etc/apt/sources.list
```

?

In which case, that won't do anything. What are you trying to acheive?
to  see a list of software repositories and add or delete them

---

### Post by JOHNNYG713 on 2012-05-25
1. Open update manager, click settings button
2. open "main menu" find "preferences", tick "software sources", then open software sources in preferences. 
this will give you a GUI window.

---

### Post by MG&amp;TL on 2012-05-25
Just for your information, the /etc/apt/sources.list file is just a list of software sources the computer will use.

---

### Post by cortman on 2012-05-25
To edit it with a graphical text editor you need to use gksu:

```
gksu gedit /etc/apt/sources.list
```

Or sudo for a console editor

```
sudo emacs /etc/apt/sources.list
```

---

### Post by ashhab2010 on 2012-05-25
you could even open up nautilus in that folder and edit manually
  
Type  
gksu nautilus /etc/apt/  
  
Then edit the file manually.

---

