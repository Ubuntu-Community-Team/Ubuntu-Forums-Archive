---
title: "installed ANT. Path for BUILD.XML?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by dantastik on 2008-09-02
Hi everybody...

this is very basic but i just can't get it to work and decided to ask for help. so thank you very much in advance.

i installed ANT and i have the build.xml file ready. but what is the path for it? i just get the 

build.xml does not exist!

error message everytime...

thanks!

---

### Post by abhishek.malhotra35 on 2008-09-02
Hi dantastik,

How are you trying to run build.xml. Hopefully you have set the ant path and classpath. If you have set your paths properly, simply type ant in the command prompt where build.xml is present. If file is by some other name, type ant -buildfile <file-name>.

---

### Post by drubin on 2008-09-02
if you are in the directory where the build file is located.  provided that your ant path is part of your includes path.

You can just do a
> ant build

---

### Post by dantastik on 2008-09-03
Thanks so much you both!
I can't believe I didn't think of that :)

---

### Post by ayomi8175 on 2009-06-22
Dear All,

I have install ant in ubuntu 9.10 using sudo apt-get install ant

I got the following message 

Buildfile: build.xml does not exist!
Build failed

when i ran ant run and ant build commands.

Please help me to solve the problem.

Thanks

Ayomi

---

### Post by drubin on 2009-06-22
[QUOTE=ayomi8175;7496653]
Buildfile: build.xml does not exist!
Build failed/QUOTE]

You need to be in your current project directory.
```
cd /path/to/project/location/ 
ant build

```

---

### Post by kpkeerthi on 2009-06-22
You should run **ant** from the folder where **build.xml** exists

---

