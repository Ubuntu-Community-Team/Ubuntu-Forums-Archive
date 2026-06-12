---
title: "installing mini ccnx"
date: 2014-12-11
forum: New to Ubuntu
---

### Post by samira3 on 2014-12-11
I want to install mini ccnx from the following site: [https://github.com/chesteve/mn-ccnx/wiki/Installing]("https://github.com/chesteve/mn-ccnx/wiki/Installingi") I downloaded and installed all the requirement programs and then 

sudo apt-get install git 
git clone git://github.com/carlosmscabral/mn-ccnxthey 
they worked properly but after the next command:
sudo ./mn-ccnx/util/install.sh -fnv
I got: sudo: ./mn-ccnx/util/install.sh: command not found
while, install.sh file exists in the path /mn-ccnx/util. Could u please help me what is the problem and how can it be soled?

---

### Post by bobthebaritone on 2014-12-12
Hi Samira3,
Why not just remove the period? What is you default directory when executing sudo?
Within install.sh there may be a command that is not on the path.
Cheers,
Bob

---

### Post by schragge on 2014-12-12
@Bob: No. The error message from sudo clearly states install.sh itself was not found.
@Samira: Check whether install.sh is executable, executables are shown in green and with * after them in the output of
```
ls -F --color=auto
``` If not, do
```
chmod +x ./mn-ccnx/util/install.sh
```

---

### Post by samira3 on 2014-12-13
after this command:
ls -F --color=auto
 the color of install.sh was white.
after :
chmod +x ./mn-ccnx/util/install.sh
 i got the following:

chmod: cannot access `./mn-ccnx/util/install.sh': No such file or directory

u can see that in the following image:
[IMG]http://uplod.ir/gbl5zh01powa/install.sh_prob-ubuntu_12.jpg.htm[/IMG]

---

### Post by schragge on 2014-12-13
Aha, that's because you already were in the directory *~/mn-ccnx/util*. The installation procedure assumes you were in your home directory though. Then do it like this
```

cd
chmod +x ~/mn-ccnx/util/install.sh
sudo ~/mn-ccnx/util/install.sh -fnv

```

---

### Post by CRYy0OKmKpJgc on 2014-12-13
After using chmod +x on the file (which, in case you have not caught on, makes the file executable) you can just use "sudo ./install.sh" if you are already in the "util" directory.

---

### Post by samira3 on 2014-12-13
Thanks a lot for your guide. my problem solved completely.

---

### Post by samira3 on 2014-12-16
Hello friends,

Although i thought the problem was solved, but it isn't solve yet. 
I used 
cdchmod +x ~/mn-ccnx/util/install.sh
chmod +x ~/mn-ccnx/bin/mn
sudo ~/mn-ccnx/util/install.sh -fnv

(the pic is attached):






[IMG]http://s6.uplod.ir/i/00484/rm381ftins72.jpg[/IMG]

but as it isshown in picture when i want to run the program by command: sudo miniccnx , i got: no template file given and default template file miniccnx.conf not found.exitng...
could u please help me to solve the problem?

---

### Post by schragge on 2014-12-17
It says you don't have the configuration file *miniccnx.conf* in the current directory. According to the [tutorial](https://github.com/chesteve/mn-ccnx/wiki/Tutorial), it's required to run Mini-CCNx. If it's not in the current directory you can specify it on command line when invoking miniccnx:
```
sudo miniccnx /path/to/miniccnx.conf
```

---

