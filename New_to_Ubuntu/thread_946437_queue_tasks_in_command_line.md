---
title: "queue tasks in command line"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by rob1984 on 2008-10-13
hello,  i need a bit of help with command line (bash) syntax. here's what i want to do:

i'm using tovid to create dvds from avi files. i have a lot of them to do, which is taking me forever so i'd like to leave it running while i'm at work.

how can i ask tovid to go through the files one by one and execute:
```
tovid -pal -ffmpeg -in 'avifile' -out 'compliantmpeg' -quality 10
```

any help will be great

thanks

---

### Post by Orange_and_Green on 2008-10-13
Try a shell script... open gedit and type:

```
#!/bin/bash
for i in $( ls *.avi); do
tovid -pal -ffmpeg -in $i -out $i.mpeg -quality 10
done

```

Save this as "script.sh" in the same directory where the avis are. Right click->Properties->Permissions-> make sure it is allowed to be executed as a program.

Then run it and have fun :)

P.S. You obviously might need to change a few bits to suit your specific needs, but this is the basic idea.

---

### Post by kpkeerthi on 2008-10-13
You might want to use -noask switch to stop tovid from prompting for input.

---

### Post by rob1984 on 2008-10-14
cheers. i'll give it a go

---

