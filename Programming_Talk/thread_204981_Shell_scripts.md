---
title: "Shell scripts"
date: 2006-06-27
forum: Programming Talk
---

### Post by rekahsoft on 2006-06-27
Ok..i have a couple questions..first how do i check dependancies and second, how do i write to files, make new files, and add to the end of an already existant file...Thanks for the help :)

---

### Post by Stromham on 2006-06-27
see : [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

---

### Post by rekahsoft on 2006-06-27
thanx :)

---

### Post by bieber on 2006-06-27
To answer your specific questions, I *think* you can check for dependencies using pkgcfg, you'll have to look that one up though, I'm not familiar with it.

You can create and write to files using the > symbol to redirect output into a file.  For instance, to write the output of the ls command to a file named out, you'd use 
```
ls > out
```
If you want to write predefined text to a file, you can use the echo command, which will just write whatever you give it as an argument to stdout or the file it's redirected to.

You can add to a file by using the cat command, which appends one file to the end of another.

---

### Post by rekahsoft on 2006-06-27
ok...how do i read files? Thanks for the help.

---

