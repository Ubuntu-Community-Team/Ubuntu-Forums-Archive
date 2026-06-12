---
title: "What do I miss with SUID ?"
date: 2012-04-02
forum: Programming Talk
---

### Post by j.daniel on 2012-04-02
**Hello forum,**

  I am writing a script that I want to run with root privileges (yes I know, it is dangerous etc. - still, I want to do that). Perfect use of the SUID file permission I thought!

  There is only one tiny problem; I can't make it run with root privileges!

  An illustrating example; I created the following tiny script called **iAm**:

```

#! /bin/bash
whoami
# END

```

  ...change permissions & run:

```

$ chmod +x iAm
$ ./iAm
daniel

```

  Perfect. I am daniel. Now let's change owner and set the suid bit:

```

$ sudo chown root:root iAm
$ sudo chmod u+s iAm
$ ls -lh
total 16K
-rwsr-xr-x 1 root   root     47 2012-04-02 16:10 iAm

```

  The moment of truth is approaching and...

```

$ ./iAm
daniel

```

  ???

  What is it that I miss with the SUID bit? Isn't this file supposed to run as 'root'? (btw: Ubuntu 10.10)

Cheers!
/ Daniel

---

### Post by Bachstelze on 2012-04-02
The setuid bit does not work with scripts for obvious security reasons.

---

### Post by j.daniel on 2012-04-02
Awh! That just plain sucks. So setting the SUID bit of commands like nmcli would somehow be safer?

Anyway: thank you Bachstelze!

Cheers
/ Daniel

---

