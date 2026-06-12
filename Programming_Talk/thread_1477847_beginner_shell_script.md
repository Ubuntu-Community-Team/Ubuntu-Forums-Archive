---
title: "beginner shell script"
date: 2010-05-09
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-05-09
please help with this example 

```
#!/bin/sh
VALID_PASSWORD="secret" #this is our password.
echo "Please enter the password:"
read PASSWORD
if [ "$PASSWORD" == "$VALID_PASSWORD" ]; then
        echo "You have access!"
else
        echo "ACCESS DENIED!"
fi
```
im getting this error when i type secret 

```
[: 9: secret: unexpected operator
ACCESS DENIED!
```

---

### Post by Jose Catre-Vandis on 2010-05-09
You only need one equal sign in the test:
```
#!/bin/sh
VALID_PASSWORD="secret" #this is our password.
echo "Please enter the password:"
read PASSWORD
if [ "$PASSWORD" = "$VALID_PASSWORD" ]; then
        echo "You have access!"
else
        echo "ACCESS DENIED!"
fi

```

---

### Post by cap10Ibraim on 2010-05-09
Thanks yes it works now , but is that syntax(first post) completely wrong or old or.. because I copied it from a tutorial

---

### Post by Portmanteaufu on 2010-05-09
Actually, the problem is that you're writing **B**ash code and running it with the **D**ash shell.

Ubuntu is a bit unusual in that '/bin/sh' (a system shortcut to the default shell) is pointing to Dash. In most other systems, it points to Bash. Unfortunately, most tutorials go ahead and assume it's pointing to Bash without mentioning it.

If you change your first line to 
```
#!/bin/bash
```
then '==' will work as expected.

(Btw, this is a very, very common stumbling block. I've seen it in two or three threads in the last week, so don't feel bad! :D )

---

### Post by cap10Ibraim on 2010-05-09
I was waiting for a similar reply thanks a lot

---

### Post by Jose Catre-Vandis on 2010-05-09
> **Portmanteaufu said:**
> Actually, the problem is that you're writing **B**ash code and running it with the **D**ash shell.

Ubuntu is a bit unusual in that '/bin/sh' (a system shortcut to the default shell) is pointing to Dash. In most other systems, it points to Bash. Unfortunately, most tutorials go ahead and assume it's pointing to Bash without mentioning it.

If you change your first line to 
```
#!/bin/bash
```
then '==' will work as expected.

(Btw, this is a very, very common stumbling block. I've seen it in two or three threads in the last week, so don't feel bad! :D )

I went at it so quickly I didn't spot that!

---

