---
title: "Software Center won't Open!!!! hELP!!!"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by MaxxABillion on 2012-03-28
I recently installed Ubuntu in a VM and after trying some commands, my software store will not open and after entering the      

sudo apt-get update

 this is the error I received:

E:  Type '<!DOCTYPE' is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list
E:  The list of sources could not be read.

Any help will be greatly appreciated.  I am an ubuntu newbie and all this is new to me

---

### Post by uRock on 2012-03-28
> **MaxxABillion said:**
> I recently installed Ubuntu in a VM and after trying some commands, my software store will not open and after entering the      

sudo apt-get update

 this is the error I received:

E:  Type '<!DOCTYPE' is not known on line 2 in source list /etc/apt/sources.list.d/medibuntu.list
E:  The list of sources could not be read.

Any help will be greatly appreciated.  I am an ubuntu newbie and all this is new to me
What version of ubuntu are you using?

---

### Post by MaxxABillion on 2012-03-28
> **urock said:**
> what version of ubuntu are you using?


11.10

---

### Post by JC Cheloven on 2012-03-28
May you please post back the output of this comand at a terminal? ```
cat /etc/apt/sources.list.d/medibuntu.list
``` Thanks

---

### Post by MaxxABillion on 2012-03-28
> **JC Cheloven said:**
> May you please post back the output of this comand at a terminal? ```
cat /etc/apt/sources.list.d/medibuntu.list
``` Thanks

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" >
<head><title>
    default.secureserver.net
</title>
    <style type="text/css">
    body{margin:0;padding:0;}
    img{border-style:none;}
    #container {background-color:#FFF;}
    </style>
</head>
<body>
<div id="container">
<img src="/unavailable.jpg" width="800" height="400" alt="Sorry! This site is not currently available." />
</div>

<!-- Copyright -->
</body>
</html>
```

---

### Post by MaxxABillion on 2012-03-28
> **MaxxABillion said:**
> ```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" >
<head><title>
    default.secureserver.net
</title>
    <style type="text/css">
    body{margin:0;padding:0;}
    img{border-style:none;}
    #container {background-color:#FFF;}
    </style>
</head>
<body>
<div id="container">
<img src="/unavailable.jpg" width="800" height="400" alt="Sorry! This site is not currently available." />
</div>

<!-- Copyright -->
</body>
</html>
```


Any help anyone can provide will be greatly appreciated.  I'm a newbie and I want to give Ubuntu a try, but this is really annoying.

---

### Post by Krytarik on 2012-03-28
> **MaxxABillion said:**
> ```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" >
<head><title>
    default.secureserver.net
</title>
    <style type="text/css">
    body{margin:0;padding:0;}
    img{border-style:none;}
    #container {background-color:#FFF;}
    </style>
</head>
<body>
<div id="container">
<img src="/unavailable.jpg" width="800" height="400" alt="Sorry! This site is not currently available." />
</div>

<!-- Copyright -->
</body>
</html>
```
Try again to add the Medibuntu repos to your Software Sources:
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```Source: [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

Regards.

---

### Post by cortman on 2012-03-28
What is an html file doing in /etc/apt/lists/sources.list.d? Shouldn't it be removed?
Also, is OP actually running Medibuntu?

---

### Post by JC Cheloven on 2012-03-29
@MaxxABillion: hey, that's weird! As cortman said, this is not the expected syntax for the file, and the contents have nothing to do with medibuntu, as far as I understand. For example, see mine (for oneiric, should have a similar syntax for any version):

```
$ cat /etc/apt/sources.list.d/medibuntu.list
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ oneiric free non-free #Medibuntu - Ubuntu 11.10 "oneiric ocelot"
#deb-src http://packages.medibuntu.org/ oneiric free non-free #Medibuntu (source) - Ubuntu 11.10 "oneiric ocelot"
```

So please, delete this file (or move it elsewhere just in case), for example with
```
sudo mv /etc/apt/sources.list.d/medibuntu.list ~/oddfile

```
then run ```
sudo apt-get update
```, and try a fresh connetion to medibuntu. [Instructions here]("https://help.ubuntu.com/community/Medibuntu").

---

