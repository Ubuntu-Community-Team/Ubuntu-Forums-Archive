---
title: "[SOLVED] Problem with Subversion"
date: 2008-10-23
forum: Programming Talk
---

### Post by zigmund on 2008-10-23
Hello,

I'm trying to use Subversion so to learn it I have downloaded the code of a project on which I have just started working. Then I have followed some manual about subversion and in the console I have written:
```
svnadmin create /home/svn/projectname
sudo svn import /tmp/projectname file:///home/svn/projectname -m "Initial Version" 
```

In order to obtain a repository. Where /tmp/projectname is the folder where I put the project (with the subfolder trunk, branches and tags).

Before this operation Have I to set up a layout (with trunk, branches and tags)? Where and How do I can do this? 

The import command ending with 
```
svn: File '/tmp/projectname/trunk/nomefile.java' has inconsistent newlines
svn: Inconsistent line ending style
```


Somebody can help me?


tanks and regards

ciao

---

### Post by snova on 2008-10-23
Subversion can do automatic line ending conversions so that things work better when checked out on different platforms. Probably the only thing that happened is that the file in question had two different kinds, and it got confused as to which one to use internally.

Run "file" on the file and see what it outputs, it should confirm my theory. Then find a way to convert them, and that should fix it.

Oh, and why are you using sudo? It shouldn't be necessary.

---

### Post by geirha on 2008-10-23
I agree with snova. Has it perhaps been edited both in windows (which uses \r\n for new lines) and linux (which uses just \n for new lines)? If that's the case, try removing any '\r's from the end of each line with a simple sed.
```
sed -i 's/\r$//' file.java
```

---

### Post by zigmund on 2008-10-24
I have solved my problem,Tanks

regards

---

