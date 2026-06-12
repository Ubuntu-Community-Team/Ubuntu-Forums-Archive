---
title: "bash script with expect"
date: 2009-03-21
forum: Programming Talk
---

### Post by martien on 2009-03-21
Hello everyone. I had to change some users' passwords and the default passwd <user> needs to write the password twice.. I couldn't find password changing script with parameters instead of writing them like passwd, so i decided to write one. But here comes the hard part. The easiest way will be to use bash script, but i am not a quite good at bash scripting. So i need to know how exactly i must set parameters in the bash script and how to repeat user's new password twice (i already know that will be bash's expect). Any idea?

---

### Post by men28 on 2009-03-21
Paste this to a file named 'password.sh':

```
echo "Enter password:"
read pass1
echo "Re-Enter password:"
read pass2

if [ $pass1 != $pass2 ] ; then
echo "Passwords are different."
else
echo "OK"
fi

```

Don't forget:
```
chmod u+x password.sh
./password.sh
```

---

### Post by ghostdog74 on 2009-03-21
except that when entering password , you should mask out what you are type. use stty -echo to mask. stty echo to unmask.

---

### Post by men28 on 2009-03-24
Thank you ghostdog74. I studied something new and interesting from your post.

This is an improved version of the script:

```
stty -echo
echo -n "Enter password:"
read pass1
echo -ne "\nRe-Enter password:"
read pass2
stty echo

if [ $pass1 != $pass2 ] ; then
echo -e "\nPasswords are different."
else
echo -e "\nOK"
fi

```

echo -n - echo vithout new lines
echo -e - echo vith escape sequences like \n
\n - new line

For more information see: man echo

---

### Post by ghostdog74 on 2009-03-24
actually, echo is less portable than printf. wherever possible, use printf instead.

---

### Post by men28 on 2009-03-24
I looked at man printf documentation.
Printf looks more powerful than echo. It supports a lot of C format specifications.
For example to convert a decimal number to hexadecimal one I have typed:

```
$ printf "%d=%X\n" 10 10
10=A
```

---

