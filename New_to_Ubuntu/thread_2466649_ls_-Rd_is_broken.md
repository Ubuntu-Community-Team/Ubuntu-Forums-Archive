---
title: "ls -Rd is broken"
date: 2021-09-01
forum: New to Ubuntu
---

### Post by psychohermit on 2021-09-01
Hi Folks,

  
Running ubuntu 20.04.2.0 LTS amd64 on a 7 year old HP ENVY TouchScreen Notebook. 

From the ls man page.

```

      -d, --directory
              list directories themselves, not their contents

     -R, --recursive
              list subdirectories recursively

glenn@Psycho:~/Desktop$ ls -Rd /
/
glenn@Psycho:~/Desktop$ ls -dR /
/

```

I believe I have stumbled on a bug in ls.

--glenn

---

### Post by yetimon_64 on 2021-09-02
I'm not so sure it is a bug. Just by reading the man file descriptions you posted the recursive switch lists subdirectories recursively. Now the "-d" switch lists only the directory and not its content. Question is; is a subdirectory considered "content" of a directory? If a subdirectory is considered as content within a directory I would expect the results you post.

**Question:** Have you ever seen that combination of options used elsewhere outside of Ubuntu with a different result?

I'm no expert and am not even entirely sure of the answer here, but from my usage of Linux/Ubuntu over the past 14 years I would not expect any other result than the one you got from my reading of those 2 option descriptions you posted. I suspect the 2 options you are combining there are not compatible with each other.

I'd suggest you wait for further replies from more experienced/qualified users and just take this post as "something to consider" in the meantime.

Cheers, yeti

---

### Post by psychohermit on 2021-09-02
It turns out that d eliminates R.  This is designed behavior.  Too bad, R would be useful in searching for a directory.

hanks,
--glenn

---

### Post by scorp123 on 2021-09-02
> **psychohermit said:**
> Too bad, R would be useful in searching for a directory. 

There are other commands you could use for that.

**"tree"**:

Could be that the "tree" package is not installed by default. To install it:
```
sudo apt install tree
```

Example of using it:
```
> cd /var/lib/apt
> tree -d

.
&#9500;&#9472;&#9472; lists
&#9474;** &#9500;&#9472;&#9472; auxfiles
&#9474;** &#9492;&#9472;&#9472; partial
&#9500;&#9472;&#9472; mirrors
&#9474;** &#9492;&#9472;&#9472; partial
&#9492;&#9472;&#9472; periodic

6 directories
```


**"find"**:

```
> cd /var/lib/apt
> find . -type d -print

.
./periodic
./lists
./lists/auxfiles
./lists/partial
./mirrors
./mirrors/partial
```

---

### Post by psychohermit on 2021-09-02
Good solutions to searching for a directory.  Thanks,
--glenn

---

