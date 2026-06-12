---
title: "Unable to install Dr Racket using apt-get-install"
date: 2016-07-01
forum: New to Ubuntu
---

### Post by lesthafari on 2016-07-01
Hello,

I typed at the terminal ```
 sudo apt-get-install software-properties-common ppa:plt/racket
``` and the terminal returned:

"impossible to find ppa : plt packet"

Any help?

---

### Post by grahammechanical on 2016-07-01
You are using the wrong command to start with. The command is

```
sudo add-apt-repository ppa: <ppa name>
```

As I do not know the version of Ubuntu that you are using I cannot give the full command.

```
sudo add-apt-repository ppa:plt/racket 
```

That might work but here is the launchpad page for that PPA. Click on Read about installing and Choose your Ubuntu version.

[https://launchpad.net/~plt/+archive/ubuntu/racket](https://launchpad.net/~plt/+archive/ubuntu/racket)

You will need to update and then try installing Racket. It is a three stage process. First, add the URL of the PPA to the software sources list. Second, Update, Third, install the software.

Regards

---

