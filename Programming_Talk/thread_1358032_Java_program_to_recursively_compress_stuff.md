---
title: "Java program to recursively compress stuff"
date: 2009-12-17
forum: Programming Talk
---

### Post by kennethadammiller on 2009-12-17
Hi, my name is Adam Miller. I'm currently making an application to recursively go through a specified directory and compress all the files of a certain type. Right now it works, but only with the zip algorithm, which is crap compared to 7z. I want to incorporate the 7z algorithm into the functionality of the program so that it spits out 7z files instead of zip. There are two ways I can do this:

1) add the lmza library to the eclipse/my library and do it that way
2) configure it to run through the terminal by passing commands with runtime

I'm having hell as it is, and I think that this could be done several ways, not necessarily exclusive to java. It might also be a shell script. I made it because I have a huge collection of ebooks and the pdf format is crap (chm much better). Anyway, if anyone could help, I've got the source code pasted below.

Currently, if you look at it, please tell me how to configure the program to run with subprocesses to the terminal.

a file with the main function in it  (think i messed up on an insignificant detail. It's fighting me. you might just ignore this one and write it yourself)
[http://pastebin.com/f25d470a5](http://pastebin.com/f25d470a5)        

a file with the method to compress each file recursively this is the one I need tips on
[http://pastebin.com/ff09222c](http://pastebin.com/ff09222c)

---

### Post by falconindy on 2009-12-18
Eh... This is a 1 liner in BASH. I don't know the args offhand to 7z, so you'll need to alter this to your liking...
```
find . -type f -iname *.pdf -exec 7z a {} \;
```

---

### Post by kennethadammiller on 2009-12-19
Kind of funny you say that. I had figured that out like 30 mins after I posted this. haha. hope that post didn't make me look stupid

---

