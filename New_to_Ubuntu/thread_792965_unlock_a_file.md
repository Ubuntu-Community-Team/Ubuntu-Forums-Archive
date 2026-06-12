---
title: "unlock a file"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-13
How do I change the permissions so that a file will unlock?

I have gone to the permissions tab but when I make changes nothing happens?

How do I register the changes?

---

### Post by jamyskis on 2008-05-13
> **saskatchewan said:**
> How do I change the permissions so that a file will unlock?

I have gone to the permissions tab but when I make changes nothing happens?

How do I register the changes?

Do you mean that all the permissions options are grayed out (like in the attached picture?)

---

### Post by saskatchewan on 2008-05-13
yes, that is the one

---

### Post by cyberbill on 2008-05-13
To change permissions of a file,
in a terminal:

chmod u+w filename

(change mode add 'write' for user)

Detailed info in 'man chmod'

Is this just a random data file?
If that doesn't work, post the output of

ls -al filename

[edit]
I see you are not the owner... (was posted while I was typing)

use:

sudo chown <username> filename
[/edit]

---

