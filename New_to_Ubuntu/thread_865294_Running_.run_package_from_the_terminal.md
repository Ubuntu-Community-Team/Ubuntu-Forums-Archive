---
title: "Running .run package from the terminal"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Les Oeufs on 2008-07-20
I'm installing Doom 3 with the patch.
I'm following the instructions I got from here [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)
So I got the .pk4 files in the right place, and I got the latest patch, but I cant figure out how to run it. If I double click it, nothing happens because wine is set as the default application for whichever reason. I went into the terminal, and I went to the directory where I put the file, but I dont know what the command is to run it. I tried "sudo <filname>" but thats not working.
Any help?
The file is called doom3-linux-1.3.1.1304.x86.run

---

### Post by cmileto on 2008-07-20
sh doom3-linux-1.3.1.1304.x86.run
or
sudo sh doom3-linux-1.3.1.1304.x86.run

---

### Post by RATM_Owns on 2008-07-20
```
chmod +x doom3-linux-1.3.1.1304.x86.run
./doom3-linux-1.3.1.1304.x86.run
```

Or

```
sh doom3-linux-1.3.1.1304.x86.run
```

---

### Post by Les Oeufs on 2008-07-20
Worked like a charm. Thanks!

---

