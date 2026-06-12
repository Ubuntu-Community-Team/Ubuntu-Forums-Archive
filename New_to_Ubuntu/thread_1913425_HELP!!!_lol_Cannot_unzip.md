---
title: "HELP!!! lol Cannot unzip"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by CrimsonDove on 2012-01-22
I installed P7zip-full using the software center, I got Mirc to run (BIG  thanksto the nice guy who posted instructions for THAT!) so I now have a lovely seekbot zipped file that I cannot open. I located the file (right clicked on it in IRC and hit open folder), right click and NOWHERE does it say 'extract' double clicking does not work. I have been reading pages for over an hour and MOST of what I find applies to a different version of Ubuntu or something because what they point you to does not seem to exist! I have the newest version (just installed last night)
I really need some help please!!
And please use beginner ex-windows, only had Ubuntu for 1 day dummy talk!!! LMAO

---

### Post by Cheesemill on 2012-01-22
I think you need to install unzip.

```
sudo apt-get install unzip
```

p7zip is only for .7z files.

---

### Post by CrimsonDove on 2012-01-22
> **Cheesemill said:**
> I think you need to install unzip.

```
sudo apt-get install unzip
```p7zip is only for .7z files.


I tried that I got this:
$: command not found

My Software Center says I already have unizp :(

---

### Post by dFlyer on 2012-01-22
If your running 11.10 unzip should have been installed by default. Have you just tried right clicking on the file and selecting extract here?

---

### Post by CrimsonDove on 2012-01-22
> **dFlyer said:**
> If your running 11.10 unzip should have been installed by default. Have you just tried right clicking on the file and selecting extract here?


Yup right click only brings up:
Select
Open (No windows program configured to open this type of file)
Explore
Cut 
Copy
Create Link
Delete
Rename
Properties (which does nothing when I click it)

---

### Post by Cheesemill on 2012-01-22
Is it definately a zip file?
What is the output of:
```
file /path/to/zipfile
```

---

### Post by CrimsonDove on 2012-01-22
> **Cheesemill said:**
> Is it definately a zip file?
What is the output of:
```
file /path/to/zipfile
```

Yeeeaaah dunno what that means lol

It is the same text zip file I have always received from Mirc.

Oh does it matter that I am running ubuntu from USB??

---

### Post by CrimsonDove on 2012-01-22
I got it!! I moved the file where I could find it easier and the Archive Manager found it and opened it!! Thank for you help! Im sure Ill be back for more! I got "Linux for Dummies" so hopefully my next bid for help wont be something so simple!! lol

RESOLVED!!!

---

