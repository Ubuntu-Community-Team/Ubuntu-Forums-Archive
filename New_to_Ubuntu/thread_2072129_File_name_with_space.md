---
title: "File name with space"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by Bri4nS on 2012-10-17
Hi ya everyone!

I have a question regarding how I run a file in Bash that I created in Emacs.

The file is in the directory **home/brian** and I have called it** Example 1**

I'm following a tutorial that said to run it I type in the Bash shell:

**source myscript**

so I typed:

**source Example 1**

and it said there was no directory or file found.

I tried as an alternative:

**home/brian/Example 1**

and still nothing... :(

I would really appreciate any advice as to what i am not doing. This is my first go at programming for Linux and I've hit a snag already! :sad:

Thanks for any help!

---

### Post by nothingspecial on 2012-10-17
You need to deal with the space

```
"Example 1"
```

```
Example\ 1
```

or use the Tab key.

---

### Post by Bri4nS on 2012-10-17
Hey Nothing Special!

OMG! Thank you sooooooooo much! That worked perfectly!

Thanks heaps!! :-)

---

### Post by audiomick on 2012-10-17
From the sound of things, you are likely to be running into that again. I would suggest avoiding spaces altogether in your file names. Instead of "example 1", use "example_1", for instance. Symbols like & and < can be a problem too.

---

### Post by Bri4nS on 2012-10-18
Hey audiomick

Thanks for your reply. I appreciate it. 

Thanks for the link to openubuntu as well, I've bookmarked it and will spend quite a bit of time there!

---

