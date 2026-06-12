---
title: "[SOLVED] $HOME/.dmrc is being ignored"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-11-12
hi, every time i insert my username and password to log in into ubuntu i have this message:

( .png attached) 

what should i do to fix this?

---

### Post by taurus on 2008-11-12
Somehow, your $HOME/.dmrc has a wrong permission.  See if you can change it back with

Applications -> Accessories -> Terminal
```
chmod 644 ~/.dmrc
ls -la ~/.dmrc
```

---

### Post by jsf_pp on 2008-11-12
```
julio@julio-laptop:~$ chmod 644 ~/.dmrc
julio@julio-laptop:~$ ls -la ~/.dmrc
-rw-r--r-- 1 julio julio 28 2008-11-10 13:21 /home/julio/.dmrc
julio@julio-laptop:~$ 
```


thanks, dunno if it worked but i'll now soon when i reboot my lappie. 
thanks again.

edit: nope. it didnt work. but thanks anyway.

---

### Post by philinux on 2008-11-12
You dont need to reboot just logout or ctrl alt backspace

---

### Post by john183 on 2008-11-12
Also make sure that no one else has write permissions to your $HOME dir. I have gotten that error message many times after playing with the permissions of of my home dir.

---

### Post by Fixman on 2008-11-12
```
 chmod 40755 $HOME 
```

---

### Post by jsf_pp on 2008-11-12
> **Fixman said:**
> ```
 chmod 40755 $HOME 
```
```

julio@julio-laptop:~$  chmod 40755 $HOME
chmod: invalid mode: `40755'
Try `chmod --help' for more information.
julio@julio-laptop:~$ 
```

it didnt work! shouldnt be 755? 
i dont wanna mess up my OS again...

BTW the first solution/post didnt work either.
bad thing, eh?

thanks anyway.

---

### Post by jsf_pp on 2008-11-12
> **john183 said:**
> Also make sure that no one else has write permissions to your $HOME dir. I have gotten that error message many times after playing with the permissions of of my home dir.

how do i do that? thanks

---

### Post by Kellemora on 2008-11-12
Hi JS

The current update seemed to has caused this AGAIN........

To FIX type in the root terminal

```
chmod 644 .dmrc
```
then type (using YOUR user name for user)
```
chmod 700 /home/user
```

That should fix it!

TTUL
Gary

---

### Post by jsf_pp on 2008-11-12
> **Kellemora said:**
> Hi JS

The current update seemed to has caused this AGAIN........

To FIX type in the root terminal

```
chmod 644 .dmrc
```
then type (using YOUR user name for user)
```
chmod 700 /home/user
```

That should fix it!

TTUL
Gary

```
julio@julio-laptop:~$ chmod 644 .dmrc
julio@julio-laptop:~$ chmod 700 /home/julio
julio@julio-laptop:~$ 
```

let me see if it works..i'll be back asap.

---

### Post by sisco311 on 2008-11-12
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?t=976610&highlight=dmrc")

---

### Post by bodhi.zazen on 2008-11-12
> **sisco311 said:**
> [Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?t=976610&highlight=dmrc")

I was just going to point out that thread :)

---

### Post by jsf_pp on 2008-11-12
thanks gary, you did it first!
thanks to all for trying anyway. and this is another thread will be marked as SOLVED!

:guitar:

---

### Post by DorianX on 2008-11-24
So this "solution" doesn't really fix my problem; changing the permission on the user's home directory to 755 makes the error message go away, but now the directory isn't writable by anyone other than that user. This just isn't acceptable for my usage model (The user account in question here's home directory is also a file repository. I really *do* need that directory to be 775, not 755. The permissions don't actually affect the operation of gdm, so where does it get off refusing to operate correctly just because I don't follow their security model?

---

