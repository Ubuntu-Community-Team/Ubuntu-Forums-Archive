---
title: "[SOLVED] Newb question re: command not found"
date: 2008-06-27
forum: Programming Talk
---

### Post by Lao_Tzu on 2008-06-27
Hi everyone

I've made a very simple bash script called count.sh, located in my home folder. BUT when I'm my home folder, I get:

```

~$ sudo count.sh
sudo: count.sh: command not found
```

Copying count.sh to /usr/bin/count.sh and trying again had no effect.

It works when I do

```

~$ sudo bash count.sh
84
```

But I'd like to make it a file I can just double-click in Nautilus and make it display the number... how?

Any help for this super-newbie question would be hugely appreciated...

---

### Post by Zugzwang on 2008-06-27
Did you add the executable flag to the file? "chmod +x count.sh". Also make sure that you first line in the script contains the [shebang]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29"). And finally, if the script is located in the current directory, you need to start it with "./count.sh" instead of "count.sh".

---

### Post by Lao_Tzu on 2008-06-27
Hi Zugzwang

Thanks, that's helpful. I did ```
chmod +x count.sh
``` so now I do'nt have to prefix the command with "bash", but the original problem persists:

```

~$ chmod +x count.sh
~$ sudo count.sh
sudo: count.sh: command not found
```

P.S. the file does contain "#!/bin/bash" in the first line

---

### Post by henchman on 2008-06-27
Apparently you are in your home folder. So try using ```
./count.sh
``` or ```
sudo ./count.sh
``` as zugzwang mentioned

---

### Post by Tony Flury on 2008-06-27
As already mentioned - if count.sh is in the current directory then you need to type 
```
./count.sh
```

to get it to run - regardless of the permissions of the file.

---

### Post by Lao_Tzu on 2008-06-27
Thanks a lot, guys. Sorted.

---

### Post by nvteighen on 2008-06-27
I'm just annoyed by that "sudo"... Are you really sure you need it?

---

### Post by Lao_Tzu on 2008-06-27
Actually, no, it's not necessary:

```
~$ ./count.sh
84

```

works just fine.

---

