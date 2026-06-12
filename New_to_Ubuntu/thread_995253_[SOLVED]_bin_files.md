---
title: "[SOLVED] bin files"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by linbeans on 2008-11-27
Hi, it seems that I've finally found a driver for my wireless on my Compal JHL90 Laptop.

However, the file is a bin file which when I run:
```
chmod +x rt2860.bin
```

```
./rt2860.bin
```

I get:
> bash: ./rt2860.bin: cannot execute binary file

What could I do to install this bin driver on my system?

Thanks

---

### Post by Michael.Godawski on 2008-11-27
Go into a terminal and issue the following command in the directory where the bin file is:

     Code:
     ```
chmod a+x name_of_file.bin 
```
Then run it by writing:

     Code:
     ```
sudo ./name_of_file.bin
```

---

### Post by kevstar31 on 2008-11-27
See this thread
[http://ubuntuforums.org/showthread.php?t=844599]("http://ubuntuforums.org/showthread.php?t=844599")

---

