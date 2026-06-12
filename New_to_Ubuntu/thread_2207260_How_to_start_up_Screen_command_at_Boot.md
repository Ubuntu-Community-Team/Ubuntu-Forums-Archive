---
title: "How to start up Screen command at Boot"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by shimabuku2 on 2014-02-22
New to Ubuntu and currently using desktop 13.10 64-bit. I currently have a startup script called startup.sh on my desktop which contains the following.
```


#!/bin/sh
cd /home/shimabuku/Downloads/omg
sh /home/shimabuku/Downloads/omg/test.sh

```


I have added a new terminal profile called "test" and the custom command is ```
/home/shimabuku/Desktop/startup.sh
```
Lastly, I added the below code to Startup Applications.


```
bash -c "sleep 30; gnome-terminal --window-with-profile test"

```

Everything works as it should, terminal launches in 30 seconds and launches test.sh. How can I put test.sh in screen rather than in a terminal session?


I have tried the below but that doesn't work. Any help would be greatly appreciated. Thanks!


```
#!/bin/sh
screen
cd /home/shimabuku/Downloads/omg
sh /home/shimabuku/Downloads/omg/test.sh

```

---

### Post by shimabuku2 on 2014-02-22
Also tried this in the custom command in a terminal profile but did not work. I am stumped...

screen -S test ./home/shimabuku/Desktop/startup.sh

---

### Post by coldcritter64 on 2014-02-23
Try this command in a terminal and see if it is of any use,

```
gnome-terminal --window-with-profile=test -x /home/shimabuku/Downloads/omg/test.sh
``` that should fire the test.sh script directly in the specific terminal profile you made for it,  (I'd consider removing any terminal custom command you tried to add and use the -x switch and the full path to the script instead)

To launch test.sh at startup after 30 seconds one line of command in an application startup entry.

```
sleep 30 && gnome-terminal --window-with-profile=test -x /home/shimabuku/Downloads/omg/test.sh
```

Hope that works. Cheers

---

### Post by shimabuku2 on 2014-02-25
> **coldcritter64 said:**
> Try this command in a terminal and see if it is of any use,

```
gnome-terminal --window-with-profile=test -x /home/shimabuku/Downloads/omg/test.sh
``` that should fire the test.sh script directly in the specific terminal profile you made for it,  (I'd consider removing any terminal custom command you tried to add and use the -x switch and the full path to the script instead)

To launch test.sh at startup after 30 seconds one line of command in an application startup entry.

```
sleep 30 && gnome-terminal --window-with-profile=test -x /home/shimabuku/Downloads/omg/test.sh
```

Hope that works. Cheers


Thanks but this executes test.sh in a terminal session. How would I go about executing it in a screen session at startup?

---

