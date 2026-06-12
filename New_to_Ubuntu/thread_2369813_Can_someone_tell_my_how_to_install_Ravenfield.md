---
title: "Can someone tell my how to install Ravenfield"
date: 2017-08-27
forum: New to Ubuntu
---

### Post by iblueflash on 2017-08-27
Hi,I download Ravenfield from [https://steelraven7.itch.io/ravenfield](https://steelraven7.itch.io/ravenfield)
I can run it and I don't know why.

---

### Post by arochester on 2017-08-27
[https://www.youtube.com/watch?v=R8EM4SURfbM](https://www.youtube.com/watch?v=R8EM4SURfbM) ?

---

### Post by iblueflash on 2017-08-27
Can you tell my the commands pls because the video isi in 360p and I can"t see

---

### Post by Perfect Storm on 2017-08-27
this should do it, shown for 64-bit:
```
cd <path>
chmod +x Ravenfield.x86_64
./Ravenfield.x86_64
```

You only need to run chmod +x once.

---

### Post by iamdantheneedhelp on 2018-07-13
I have the same problem too, but when I run 
cd <path>
chmod +x Ravenfield.x86_64
./Ravenfield.x86_64

it says chmod: cannot access 'Ravenfield.x86_64': No such file or directory

---

### Post by ajgreeny on 2018-07-13
You need to use the full path in the first line of that series of commands.  I do not know where the file will be sitting after installing so you will need to look for it

Typing the command **cd <path>** will do nothing as <path> is meaningless in a command, so find where the Ravenfield.x86_64 file is then use that full pathway in the command.

---

### Post by iamdantheneedhelp on 2018-07-13
Thanks

---

