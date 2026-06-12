---
title: "[SOLVED] encryption techniques"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by jmd9qs on 2008-09-24
hey,

can't find a good way (google is great, but google'ing for linux questions often leaves me w/ other questions...), to encrypt DIRECTORIES...


i can, and have, encrypted/decrypted many a file w/ ccrypt and mcrypt, however, i am a linux newbie, and i would like to encrypt directories (and subsequently all the files in them) using one command. all this without the risk of "ruining" or "overwriting" or whatever. seriously. i need this. please, please help me. oh jesus

---

### Post by Primefalcon on 2008-09-24
hit alt + f2 and type in

```
seahorse
```

create a set of gnugp code keys, then you can right click on any folder, file and select encrypt

just so you know, thats governmental level encryption btw ;-)

---

### Post by jmd9qs on 2008-09-25
the seahorse thing works well and is customizable enough for me... however, when i encrypt using it, it just creates encrypted COPIES of whatever i encrypted... i was hoping that it would encrypt and keep the original file so i don't have to delete the original everytime i encrypt/decrypt. any way to do this?

---

### Post by _sAm_ on 2008-09-25
You could try encfs(witch upcoming Ubuntu will have by default). It is an encrypted filesystem. 

You could encrypt one folder and have all your private stuff inside, the size is not fixed - it will grow as you move/save files in it(so it will not be bigger then whats inside). 

I googled for a guide for you and found this one;
[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

---

### Post by jmd9qs on 2008-09-25
thanks! this works beautifully and is EXACTLY what i wanted... appreciate it

---

### Post by Primefalcon on 2008-09-25
that is good for general use however if there is something that you want to keep completely secure I'd still try the gnugp since that is governmental level secure as I said.

to get rid of the original file securely(unrecoverable)

in your terminal

```
shred -vzu /path/to/file
```

you can add or remove the v since that just adds verbose output so you can see exactly what's going on

---

### Post by jmd9qs on 2008-09-25
primefalcon

is there any risk that when i decrypt the files, i will not have what i encrypted? i don't want to shred the originals if such a risk exists...

---

### Post by Primefalcon on 2008-09-25
I've never had that happen, just back up your keys froM within seahorse, in case you have to format for whatever reason but keep them secure. as I said if you need 100% security that not even the us government can crack, then use this, there's been a couple of trials lately where they haven't been able to gain access to access to their files using this method of encryption

btw you can give your public key to give friends and they can send you mails that only you can read ;-) just don't give out your secret key

---

### Post by jmd9qs on 2008-09-25
how would i do that? (sorry, still a noob!)

---

### Post by Primefalcon on 2008-09-25
will if your using evolution its as simple as opening it up going to 

edit => preferences

click on your profile and click edit

security

and paste in the id your key set which you can get from seahorse in the keyid column

and to set it up to send from other operating systems here's a how to for thunderbird
[http://enigmail.mozdev.org/documentation/quickstart.php](http://enigmail.mozdev.org/documentation/quickstart.php)

I know it might seem like a lot but it's quite quick to set up really, and once it is its just a matter of ticking the encrypted box to send an encrypted email that only the person your sending to can decrypt

---

