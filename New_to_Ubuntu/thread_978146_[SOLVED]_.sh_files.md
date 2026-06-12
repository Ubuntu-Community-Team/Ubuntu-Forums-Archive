---
title: "[SOLVED] .sh files"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by JacKeown on 2008-11-10
Does anyone know how to run .sh files I have tried typing sh and my file directory into bash and it didn't work I also tried enabling it as an executable and double clicking it Thanks in advance:guitar:

---

### Post by night_fox on 2008-11-10
it needs to have execute permissions, so try doing 

chmod +x foo.sh
sh foo.sh

---

### Post by tuxxy on 2008-11-10
If the file is named example.sh 

Open a terminal and type 

```
chmod +x example.sh
```

Then run the script

```
./example.sh
```

Remember to rename the command to your filename, also you may need to navigate to the directory of the file before running the commands.

---

### Post by spiderbatdad on 2008-11-10
generally...have the file in your path or be in the directory of the file, make sure it is executable, and run it from the command line...(or create a launcher,) ```
./filename.sh
```

---

### Post by night_fox on 2008-11-10
You can change this permission from nautilus.

---

### Post by OutOfReach on 2008-11-10
Or you can just run:
```

sh script.sh

```

If you don't want to set the executable permissions.

---

### Post by fooman on 2008-11-10
edit...i'm way too late.

---

### Post by JacKeown on 2008-11-10
Thanks I got every thing working. what I ended up doing is executing in in the terminal and It worked but thanks for all the usefull suggestions.

---

