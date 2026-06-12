---
title: "setting global path"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by Spgt on 2013-02-24
So I installed ModelSim recently and I find it annoying to go to the linux folder and execute the VSIM file every time

I heard that I can set the path globally and run ./vsim from any directory and execute the program.

First, does it have to be in ~/.bashrc?

another problem is that I cannot execute the program using this line
export PATH=$PATH:"/altera/12.1/modelsim_ase/linux/"

And finally what is ./ in front of the vsim file name that i have to use?! what does it do? and where should I use it?

---

### Post by matt_symes on 2013-02-24
Hi

Set the global path in /etc/environment

```
matthew-S206:/home/matthew/storage/my_isos % cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
matthew-S206:/home/matthew/storage/my_isos % 
```

> And finally what is ./ in front of the vsim file name that i have to use?! what does it do? and where should I use it?

It is a path to the current directory and allows you to execute files when you are in the same directory as the file.

Kind regards

---

### Post by Spgt on 2013-02-24
I added 
export PATH=$PATH:"/altera/12.1/modelsim_ase/linux/"
to /etc/environment

after I logged out and executed sudo ./vsim from home directory it complained that it did't find the commend

---

### Post by matt_symes on 2013-02-24
Hi

Post the out of your /etc/envrionment.

After that reboot to reread the file.

Kind regards

---

### Post by Vaphell on 2013-02-24
> **Spgt said:**
> I added 
export PATH=$PATH:"/altera/12.1/modelsim_ase/linux/"
to /etc/environment

after I logged out and executed sudo ./vsim from home directory it complained that it did't find the commend

when you use ./ you explicitly say 'run from current directory'
you have to drop ./ entirely to take advantage of the global $PATH. No directory given = scan $PATH locations, if not found throw error.

---

