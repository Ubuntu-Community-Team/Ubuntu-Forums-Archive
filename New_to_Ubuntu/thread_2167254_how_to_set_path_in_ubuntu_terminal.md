---
title: "how to set path in ubuntu terminal"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by radha2 on 2013-08-13
Hello Friends

How to set path for the file creation?

Whenever I am using cd command with specific path its not working..


Now what i have to do ?

---

### Post by Bucky Ball on 2013-08-13
For a start be more specific about what command you are using and the output. Please give the exact command and the output, preferably copy/pasted from a terminal.

If you are using 'cd' to get to a file/directory that doesn't exist then no, it won't work. Try:

```
cd /etc
```

Do you end up at a command prompt that ends in /etc?

If you actually want to create an empty file, then:

```
sudo touch <name_of_new_file>
```

... where <name_of_new_file> equals whatever you want the file to be named.

Create a directory:

```
sudo mkdir <name_of_new_directory>
```

To get to new directory, say if you made it in /etc:

```
cd /etc/<name_of_new_directory>/
```

You CAN'T cd to a file. You can cd to the directory it's in then inspect the file with a couple of commands, for instance, presuming your file is in /etc:

```
cd /etc
nano <your_file>
```

Or:

```
nano /etc/<your_file>
```

... using one command to see the file.

---

### Post by DuckHook on 2013-08-13
> **radha2 said:**
> Now what i have to do ?I just answered a similar question from you on another thread.

You might appreciate a basic primer on Linux directory and file structure, how to navigate around the directory tree and how to use commands. Therefore, I suggest that you read the first few chapters of [this]("http://linuxcommand.org/tlcl.php") resource.

---

