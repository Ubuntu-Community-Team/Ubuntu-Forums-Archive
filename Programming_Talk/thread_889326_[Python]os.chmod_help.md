---
title: "[Python]os.chmod help"
date: 2008-08-14
forum: Programming Talk
---

### Post by GammaPoint on 2008-08-14
I'm have some difficulties understanding how to properly use os.chmod() in Python to change file system modes. What I'd like to be able to do is check to see if a file has the following permissions:

```
-rwxr--r--
```

and if not, set the permissions to this. The problem is that with os.chmod() I don't understand the correct mode identifiers that it takes as a second argument. 

I know that I can change the mode to u+r by doing the following:
```
os.chmod(filename,stat.S_IREAD)
```

for example, but I don't know to do combinations of permissions. The Python documentation [http://docs.python.org/lib/os-file-dir.html]("http://docs.python.org/lib/os-file-dir.html") says that I can do bitwise combinations but I don't really understand how to do that. Could someone please help me out?

---

### Post by ghostdog74 on 2008-08-14
> **GammaPoint said:**
> I'm have some difficulties understanding how to properly use os.chmod() in Python to change file system modes. What I'd like to be able to do is check to see if a file has the following permissions:

```
-rwxr--r--
```

you don't have to check it, since you are going to change it anyway. So just change it. the permission above is 744.
```

os.chmod("file",0744)

```
i suggest you read something on [file permissions](http://www.freeos.com/articles/3127/) to get familiarized.

---

### Post by GammaPoint on 2008-08-14
> **ghostdog74 said:**
> you don't have to check it, since you are going to change it anyway. So just change it. the permission above is 744.
```

os.chmod("file",0744)

```
i suggest you read something on [file permissions](http://www.freeos.com/articles/3127/) to get familiarized.

Ahh, thank you. I had tried '744' earlier but I guess I needed that 0 in there :)

---

### Post by NathanB on 2008-08-14
The docs mean you can use the bit-wise OR operator "|" to specify additional flags.

```

os.chmod(filename,stat.S_IREAD | stat.S_IWRITE)

```

Nathan.

---

### Post by Bachstelze on 2008-08-14
> **GammaPoint said:**
> Ahh, thank you. I had tried '744' earlier but I guess I needed that 0 in there :)

If you're wondering why that leading zero is important, it's because permissions are set as an octal integer, and Python automagically treats any integer with a leading zero as octal. So [FONT="Courier New"]os.chmod("file", 484)[/FONT] (in decimal) would give the same result.

---

### Post by GammaPoint on 2008-08-14
Thanks for those extra bits of information, I appreciate it :)

---

