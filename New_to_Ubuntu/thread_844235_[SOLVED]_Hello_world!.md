---
title: "[SOLVED] Hello world!"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-29
so i wrote my first shell script "hello world" and it worked, but my second one doesn't.  I did everything right but permission is denied.  where did I go wrong?  basically it's the same thing but says hello to me and not the world.  it goes: 

#!/bin/bash
#my second

echo "hello Adam"

but now when i rty the command in the terminal:

./hello_Adam

it puts out:

adamogardner@CRONUS:~$ ./hello_Adam
bash: ./hello_Adam: Permission denied

can anyone tell me whats going on?

---

### Post by Troll_the_Great on 2008-06-29
Try with "sudo".

sudo ./hello_adam

---

### Post by sisco311 on 2008-06-29
set the execute permission on the script:
```
chmod +x ./hello_Adam
./hello_Adam

```

---

### Post by NovaAesa on 2008-06-29
Or as an alternate method to what sisco311 suggested, you can right click on the file, then properties, and then make sure that the execute checkbox is checked.

---

### Post by adamogardner on 2008-06-29
ok chmod+x did the job.  I remember now doing chmod yesturday but nothing happened (like when I bought the CHEX Bold Party Blend).  I'll have to research, thanks.  just one question more:  what is the +x all about?  I don't remember doing that yesturday.

---

### Post by sisco311 on 2008-06-29
To run a script you need execute permission on the file.
You can set the permiossions in several ways.

More info [here]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by atomkarinca on 2008-06-29
chmod command alters the files permissions, +x makes the file executable. In order to execute the file you should do a chmod first.

---

### Post by Martje_001 on 2008-06-29
With the command 'chmod' you can change permissions of the file. +x means make executeable.

---

