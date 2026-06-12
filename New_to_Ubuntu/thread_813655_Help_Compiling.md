---
title: "Help Compiling"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by FOBoi1122 on 2008-05-31
Hi,

I'm trying to get a file from [http://fjbtndrv.wiki.sourceforge.net/packages](http://fjbtndrv.wiki.sourceforge.net/packages) 

it says:


hardy
To get access to the repository, open a terminal and and run these commands

wget -O - [http://home.versanet.de/~khnz15/archive.key](http://home.versanet.de/~khnz15/archive.key) | sudo apt-key add -
sudo wget -O /etc/apt/sources.list.d/fjbtndrv.list [http://home.versanet.de/~khnz15/hardy.list](http://home.versanet.de/~khnz15/hardy.list)

it tells me to compile them myself, but i'm not really sure how to do that. Can anyone help?

---

### Post by iaculallad on 2008-05-31
> **FOBoi1122 said:**
> Hi,

I'm trying to get a file from [http://fjbtndrv.wiki.sourceforge.net/packages](http://fjbtndrv.wiki.sourceforge.net/packages) 

it says:


hardy
To get access to the repository, open a terminal and and run these commands

wget -O - [http://home.versanet.de/~khnz15/archive.key](http://home.versanet.de/~khnz15/archive.key) | sudo apt-key add -
sudo wget -O /etc/apt/sources.list.d/fjbtndrv.list [http://home.versanet.de/~khnz15/hardy.list](http://home.versanet.de/~khnz15/hardy.list)

it tells me to compile them myself, but i'm not really sure how to do that. Can anyone help?

It says that you should add the repository: Open up your terminal and input the commands you just paste.

```
wget -O - http://home.versanet.de/~khnz15/archive.key | sudo apt-key add -
```

```
sudo wget -O /etc/apt/sources.list.d/fjbtndrv.list http://home.versanet.de/~khnz15/hardy.list
```

That's one command at a time.

---

### Post by iaculallad on 2008-05-31
> **FOBoi1122 said:**
> it tells me to compile them myself, but i'm not really sure how to do that. Can anyone help?

I've did a research, You could download the alternative script [here]("http://fjbtndrv.sourceforge.net/fjbtndrv-installer.run") to save your time in compiling and manually execute it yourself.

Browse the download location using your terminal, then issue the command:

```
sudo sh fjbtndrv-installer.run
```

---

### Post by FOBoi1122 on 2008-05-31
thanks a lot, it worked out great.

---

