---
title: "sh/bash alternatives for (auto)expect to automate installation?"
date: 2007-08-04
forum: Programming Talk
---

### Post by Krijk on 2007-08-04
I'm trying to automate my software/computer installs. 

Some software have an interactive dialogue. For example:
[LIST]
[*]Which directory to install in? [/usr/local]
[*]What type of install [ full, server, client]
[*]Are you sure you want to install [yes/no]
[/LIST]

I would like to have an input file to put the required install options in it and also the ability to insert CR/LF as responses. The inputfile is then read by the script to insert the options when installing.

I've read that expect will be able to do this, but isn't there an alternative way that I can use in sh/bash script without having to install extra software?

---

### Post by pmasiar on 2007-08-04
Python? is installed everywhere, and more flexible than bash

---

### Post by Krijk on 2007-08-04
Python is not an option. Some don't have it installed and it's difficult to get permission to install aditional software.

---

### Post by pmasiar on 2007-08-04
Just curious, which Linux distro does not have Python by default? Or any other free software system? 

What are your target platforms?

---

### Post by Krijk on 2007-08-05
How about linux firewalls.

---

### Post by cwaldbieser on 2007-08-06
> **Krijk said:**
> I'm trying to automate my software/computer installs. 

Some software have an interactive dialogue. For example:
[LIST]
[*]Which directory to install in? [/usr/local]
[*]What type of install [ full, server, client]
[*]Are you sure you want to install [yes/no]
[/LIST]

I would like to have an input file to put the required install options in it and also the ability to insert CR/LF as responses. The inputfile is then read by the script to insert the options when installing.

I've read that expect will be able to do this, but isn't there an alternative way that I can use in sh/bash script without having to install extra software?

Will it not work to simply redirect a file with the responses to the input of the program?  e.g.
```

$ install-program < responses.txt

```

---

