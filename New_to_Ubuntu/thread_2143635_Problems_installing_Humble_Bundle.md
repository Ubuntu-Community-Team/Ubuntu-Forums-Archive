---
title: "Problems installing Humble Bundle"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by ScooterBoogles on 2013-05-09
I've never bought a Humble Bundle before, but I've heard great things!

When I click the "download in Ubuntu Software Center" button I get this message on a new web page: 

> We're sorry - we're almost ready with the Humbel Double Fine Bundle in  Ubuntu Software Center. Please check back again later. Back to the [Humble Bundle]("https://www.humblebundle.com") site.

And yes, that's their typo, not mine.

So I downloaded the Mojo Installers over bittorrent but Ubuntu can't run them. 
> 
Could not display "/CostumeQuest-Linux-2013-05-07-setup.bin".

What to do?

---

### Post by ikt on 2013-05-09
If you open terminal and cd into the directory where you downloaded CostumeQuest-Linux-2013-05-07-setup.bin and do:

chmod u+x CostumeQuest-Linux-2013-05-07-setup.bin

then

./CostumeQuest-Linux-2013-05-07-setup.bin

Does it give you the same error?

---

### Post by Westonkd on 2013-05-09
The above worked for me. Also right clicking the .bin file, selecting the permissions tab, checking "Allow executing file as a program," and then double clicking the .bin did the same thing for me.

---

### Post by ScooterBoogles on 2013-05-09
Sorry, but I don't know what you mean by "cd into the directory"! That's why I'm here in Absolute Beginners. :)

I tried the "allow as executable" and it didn't work unfortunately.

---

### Post by ScooterBoogles on 2013-05-09
Okay, I figured out cd into the directory. But then it told me the file doesn't exist...so I'm going to re-download and try again tomorrow! Thanks for your help.

---

### Post by ScooterBoogles on 2013-05-09
I'm getting the same error message in the Terminal - it's telling me the file doesn't exist.

---

### Post by redfireplace on 2013-05-10
What is the exact command you are using and what is the exact output?

---

### Post by dee.dw on 2013-05-11
Same problem here. Here's the output:

```
$ chmod +x ./CostumeQuest-Linux-2013-05-07-setup.bin

$ ll Cos*
-rwx--x--x 1 dee dee 564953200 Mai 11 10:01 CostumeQuest-Linux-2013-05-07-setup.bin*

$ ./CostumeQuest-Linux-2013-05-07-setup.bin
bash: ./CostumeQuest-Linux-2013-05-07-setup.bin: File or folder not found

$ md5sum CostumeQuest-Linux-2013-05-07-setup.bin
5e1c88cac974b45646d880caf4fe6ffb  CostumeQuest-Linux-2013-05-07-setup.bin
```

One problem could be that this is a 32bit binary and I have a 64bit system ... But why this error message?

---

