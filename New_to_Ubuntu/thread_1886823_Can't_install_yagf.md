---
title: "Can't install yagf"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by MFoxx on 2011-11-25
Hello, everybody,
I can't install YAGF. I did the following: 
1) I unzipped the folder (clicking on "Extract here")
2) then I moved into the folder: "cd /home/r/Desktop" and "cd yagf-0.8.5-Source"
3) after that i typed : "./configure"
 But it read :"No such file or directory".

Here you can see all my actions:
r@r-P4M800-M7 ~ $ cd /home/r/Desktop
r@r-P4M800-M7 ~/Desktop $ cd yagf-0.8.5-Source
r@r-P4M800-M7 ~/Desktop/yagf-0.8.5-Source $ ./configure
bash: ./configure: No such file or directory
r@r-P4M800-M7 ~/Desktop/yagf-0.8.5-Source $ 

What did I do wrong?
Thanks in advance

---

### Post by Sealbhach on 2011-11-25
Just run

```

cmake
```

then 

```
make

```
and

```
sudo make install
```

---

### Post by MFoxx on 2011-11-26
Thank you for reply, Sealbhach. 
But in spite of this assistance I couldn't install "yagf." 
Can anyone help me?

---

### Post by Sealbhach on 2011-11-26
You need to help us to help you. What kind of error messages did you get? Did you make sure you have the right Qt version, see bottom of [this]("http://symmetrica.net/cuneiform-linux/yagf-en.html") page?

.

---

