---
title: "bash script"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-10-17
Okay so I made a bash script that calls rdesktop and inputs all the typical settings I use.  Basically in the script I have a variable name $computerName.

is there any way that in the terminal when run the script like ./UCCON I can also define that variable in the same line? Such as ./UCCON $computerName=myPC

---

### Post by RATM_Owns on 2008-10-17
You could add the variable in your bashrc.

```
gedit ~/.bashrc
```
And add in 
> export computerName=(insert blah here)

---

### Post by jerome1232 on 2008-10-17
You could use $1, for example

if you call the script like this

```
./script blah
```

then the variable $1 = blah in your script. So either replace $computerName with $1 or assign $1 to $computerName.

```
computerName=$1
```

---

