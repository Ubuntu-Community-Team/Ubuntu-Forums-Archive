---
title: "Creating a launcher"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by owenll on 2012-04-30
I am trying to create a launcher for a programme (shredder Chess). If I use a terminal to cd into > /home/owen/Rhaglenni/Gwyddbwyll/DeepShredder11/ then run the command > java -jar LinShredder.jar the programme starts. However when I use alacarte to try and create a launcher using > /home/owen/Rhaglenni/Gwyddbwyll/DeepShredder11/java -jar LinShredder.jar i get an error saying that > /home/owen/Rhaglenni/Gwyddbwyll/DeepShredder11/java cannot be found. I know this is basic, but is it possible to create a launcher?

---

### Post by owenll on 2012-04-30
I've read this [https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher) -> "The Hard Way" but do not understand  :oops:

---

### Post by Cheesemill on 2012-04-30
Instead of:
```
/home/owen/Rhaglenni/Gwyddbwyll/DeepShredder11/java -jar LinShredder.jar 			 		
```

You need:
```
java -jar /home/owen/Rhaglenni/Gwyddbwyll/DeepShredder11/LinShredder.jar 			 		
```

---

### Post by slavssn on 2012-04-30
Try this out as a command in your launcher:

```
sh -c "cd /home/owen/Rhaglenni/Gwyddbwyll/DeepShredder11 && ./java -jar LinShredder.jar"
```

I think it should work.

---

### Post by owenll on 2012-04-30
Thanks both for your replies. I was led in the right direction. I finally got it to work with> sh -c "cd /home/owen/Rhaglenni/Gwyddbwyll/DeepShredder11 && java -jar LinShredder.jar"

---

