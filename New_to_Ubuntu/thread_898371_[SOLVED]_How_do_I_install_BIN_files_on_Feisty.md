---
title: "[SOLVED] How do I install BIN files on Feisty?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Udibuntu on 2008-08-23
Hi Guys,

I want to update Google Earth from version 4 that's in Medibuntu to version 4.3 that's available via Google.

I've downloaded the BIN file but don't know how to make it work.

I've tried ```
sudo sh ./Google_Earth_CZXD.bin
``` but I apperantly botched something as it doesn't work.

Please help.

Cheers,

Udi

---

### Post by iaculallad on 2008-08-23
Try:

Change location to your bin's directory:

```
cd BIN_Location
```

Still, on the BIN's directory, give it an executable attribute:

```
sudo chmod +x Google_Earth_CZXD.bin
```

Finally, execute it:

```
./Google_Earth_CZXD.bin
```

or if it requires privilege:

```
sudo ./Google_Earth_CZXD.bin
```

---

### Post by philinux on 2008-08-23
How to install anything

[http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

Link busted dang

---

### Post by Udibuntu on 2008-08-23
> **iaculallad said:**
> Try:

Change location to your bin's directory:

```
cd BIN_Location
```

Still, on the BIN's directory, give it an executable attribute:

```
sudo chmod +x Google_Earth_CZXD.bin
```

Finally, execute it:

```
./Google_Earth_CZXD.bin
```

or if it requires privilege:

```
sudo ./Google_Earth_CZXD.bin
```

Thank man.

First command yields
```
udi@udi-laptop:~$ cd BIN_Location
bash: cd: BIN_Location: No such file or directory
udi@udi-laptop:~$ 
```

The BIN file was downloaded to my desktop (I don't have a home partition, only a home folder, if that means anything).

Please give me a step by step for dummies, since I am one as far as it comes to terminal use...

Thanks again,

Udi

---

### Post by PilotJLR on 2008-08-23
Hi - I think iaculliad meant that directory name as a variable for you to fill in.  :-)

So if the file is on your desktop, then:
```

cd ~/Desktop
sudo chmod +x Google_Earth_CZXD.bin
sudo ./Google_Earth_CZXD.bin

```

---

### Post by PilotJLR on 2008-08-23
FYI, the tilde (~) means "home". So if your username is "bob" and your home directory is "/home/bob", then the "~/Desktop" means "/home/bob/Desktop"

---

### Post by Udibuntu on 2008-08-23
> **PilotJLR said:**
> Hi - I think iaculliad meant that directory name as a variable for you to fill in.  :-)

So if the file is on your desktop, then:
```

cd ~/Desktop
sudo chmod +x Google_Earth_CZXD.bin
sudo ./Google_Earth_CZXD.bin

```

Thanks PilotJLR, it was installed, but it doesnt initialize after I click the icon.

GE 4 works just fine.

Can you help here or is this an GE issue I should address Google?

---

### Post by philinux on 2008-08-23
snip.

Your're running Feisty doh!

---

### Post by Udibuntu on 2008-08-23
> **philinux said:**
> snip.

Your're running Feisty doh!

Alas yes, I am...

---

### Post by philinux on 2008-08-23
Any reason you didn't upgrade?

---

### Post by Udibuntu on 2008-08-23
> **philinux said:**
> Any reason you didn't upgrade?

Some:

Waited for an LTS version like Hardy to come out, waited to make a home partition since I don't habe one, waiting to have enough time to read more on Hardy, etc.

I plan on installing a fresh Hardy in October.

Any help on the GE 4.3 issue?

---

### Post by philinux on 2008-08-23
Run the app from the terminal and it will hopefully show some errors as to why it's not starting.

---

### Post by dizee on 2008-08-23
> **Udibuntu said:**
> 
I've tried ```
sudo sh ./Google_Earth_CZXD.bin
``` but I apperantly botched something as it doesn't work.

for future reference, you can either run
```
sudo sh Google_Earth_CZXD.bin
```
or
```
sudo ./Google_Earth_CZXD.bin
```
not both at the same time ;)

---

### Post by Udibuntu on 2008-08-23
> **dizee said:**
> for future reference, you can either run
```
sudo sh Google_Earth_CZXD.bin
```
or
```
sudo ./Google_Earth_CZXD.bin
```
not both at the same time ;)

Dizee thanks, I think the problem with GE 4.3 (earth is missing) is a bug with GE itself.

Udi

---

