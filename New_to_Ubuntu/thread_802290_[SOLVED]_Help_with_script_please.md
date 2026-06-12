---
title: "[SOLVED] Help with script please"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-05-21
I need some help with this script. I don't really know scripts very well. I just want the program conky to start up later. When I just have the program open on start up it doesn't start properly, but if I start it after fully loaded it loads perfectly. ```
#!/bin/bash
sleep 1
conky
```

---

### Post by unutbu on 2008-05-21
I think your script should work. What's wrong with the script?

---

### Post by slughappy1 on 2008-05-21
Conky did not load when I started up my computer. After I wrote the script I put it in a folder that has another script that works. Then I```
sudo chmod+x conkyStart
```

---

### Post by unutbu on 2008-05-21
Make it executable if it is not executable already:

```
chmod 755 conkyStart
```

Go to System>Preferences>Sessions.
Click the Add button. Enter 

```
/path/to/scripts/conkyStart
```

for the command.

You shouldn't need to use sudo to make your script executable because you already own the script.

---

### Post by anotherdisciple on 2008-05-21
> **slughappy1 said:**
> I need some help with this script. I don't really know scripts very well. I just want the program conky to start up later. When I just have the program open on start up it doesn't start properly, but if I start it after fully loaded it loads perfectly. ```
#!/bin/bash
sleep 1
conky
```

The default units for sleep is seconds. Do you only want it to delay by one second?

---

### Post by bumanie on 2008-05-21
I think you need to change the number after 'sleep' to a longer period. Compiz etc. takes a while to start up completely. Try and change 1 to 20 or 30. Conky should come on after 20-30 seconds, depending on which time you choose. I have seen some suggest conky should not start for 60 seconds.

---

### Post by slughappy1 on 2008-05-21
Ok, I changed the command to the full path name and increased the sleep time. But now I am running into another problem. How do you get a script to do two commands? I changed mine to look like this ```
#!/bin/bash
sleep 20
emerald --replace
sleep 10
conky

``` 
I want to use emerald, but when put it into sessions it didn't load properly. I have posted a previous thread asking about it but I didn't get any good answers. So I made my script as shown, but it only executes the first command and not the second.

---

### Post by spiderbatdad on 2008-05-21
```
#!/bin/bash
sleep 20
emerald --replace &&
sleep 10
conky &
```

---

### Post by anotherdisciple on 2008-05-21
Do need the && for sure? I'm thinking it will work without it.... maybe I'm wrong

---

### Post by pdtpatrick on 2008-05-21
[http://www.r3uk.com/index.php/home/38-software/85-installing-conky-on-ubuntu-gutsy](http://www.r3uk.com/index.php/home/38-software/85-installing-conky-on-ubuntu-gutsy)

check out that link.. prety informative

---

### Post by slughappy1 on 2008-05-21
The && didn't work

---

### Post by unutbu on 2008-05-21
```
#!/bin/bash
sleep 20
emerald --replace &
sleep 10
conky &

```

---

### Post by slughappy1 on 2008-05-21
Thanks that worked!

---

