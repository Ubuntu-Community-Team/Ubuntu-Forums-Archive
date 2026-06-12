---
title: "Shebangs in Python programs"
date: 2014-07-28
forum: Programming Talk
---

### Post by ofnuts on 2014-07-28
I see two forms of shebang recommend for python programs, the expected  "/usr/bin/python", and the harder to explain "/usr/bin/env python".  According to its man page, "env" is just meant to run a command in a  modified environment so using just "env command" without any environment-changing parameters doesn't make much  sense. Is there another good reason for that shebang? Or is it only for  historical reasons (for instance to set the python path in the shebang)?

---

### Post by vasa1 on 2014-07-28
I read somewhere that "#!/usr/bin/env" is preferable. If I find that advice, I'll post a link to it.

---

### Post by steeldriver on 2014-07-28
I think the idea is to provide portability - for example where python might live in /bin or /opt/bin on some platforms instead of /usr/bin

The downside is that it can break things - for example if a user's env points python to python3 when the script writer is expecting python2.7

Pretty good explanation here --> [Why is it better to use “#!/usr/bin/env NAME” instead of “#!/path/to/NAME” as my shebang?]("http://unix.stackexchange.com/a/29620/65304")

---

### Post by vasa1 on 2014-07-28
Great explanations there :)

---

### Post by ofnuts on 2014-07-28
Ah, OK. What I overlooked is that whatever intreprets the shebang is not looking at the path, so using "env" is a way to mitigate this. But this works only because env is part of the GNU coreutils so it can be assumed to be there on GNU-based systems...  But that may not work every where (OSX? BSD?). Not even mentioning Windows...

---

