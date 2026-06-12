---
title: "Installing J5EE"
date: 2009-04-01
forum: Programming Talk
---

### Post by jamesdcarroll on 2009-04-01
I downloaded JEE SDK to my machine and expected a zip or tar. Instead, its a bin file and no matter what I try it won't run. Could someone point me in the right direction on how to fire it?  I have a feeling that i have to execute chmod on it in some manner put I don't know what precisely to execute. I tried chmod 777 y.bin and it didn't work. (I changed the name because the actual file name is a mile long and I'm lazy. 

When I run ls - 1 on it

```
jim@Cheyenne:~/Desktop$ ls -l y.bin
-rwxrwxrwx 1 jim root 97103034 2009-04-01 01:03 y.bin
```

When I run sh y.bin on it

```
jim@Cheyenne:~/Desktop$ sh y.bin
y.bin: 1: Syntax error: "(" unexpected
```

When run . y.bin on it...

```
jim@Cheyenne:~/Desktop$ . y.bin
bash: ELF: command not found
```


sudo on the file doesn't change the result.

Google didn't have anything, the Sun forums had a pile of the same questions all unanswered, and nothing in the Ubuntu forums or doc (just a reference the generic JRE install.

Any ideas?

Thanks,

---

### Post by myrtle1908 on 2009-04-02
```
chmod +x y.bin
```

then to install

```
./y.bin
```

---

