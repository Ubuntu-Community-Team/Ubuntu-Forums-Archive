---
title: "Packaging on Xubuntu"
date: 2012-03-20
forum: Packaging and Compiling Programs
---

### Post by bOgNeR17 on 2012-03-20
I have started to do some reading on packaging and I am currently attempting to get set up for it. I have run into a slight problem when I try to run the following command all I get is **"Command not Found"**

```
$ sudo apt-get install gnupg pbuilder ubuntu-dev-tools bzr-builddeb apt-file
```

Anyone know what is causing this and a way that I can correct it? Also I am running the latest stable version of Xubuntu just incase.

Thanks in advance all help appreciated :)

---

### Post by MG&amp;TL on 2012-03-20
Are you including the $ sign in your command? That's just to show you're a normal user, not root (#) or running a different shell (usually %)

The command should literally be:

```
sudo apt-get install gnupg pbuilder ubuntu-dev-tools bzr-builddeb apt-file
```

---

### Post by bOgNeR17 on 2012-03-20
Oh I feel really stupid can't believe I didn't notice that I had the $. Yeah its working fine now after remove it. Thanks for the help.

---

### Post by MG&amp;TL on 2012-03-20
No problem at all, good luck with the packaging. I never quite got it. :)

---

### Post by bOgNeR17 on 2012-03-20
Another problem folks, trying to run this line but not sure what to put between the <release>?

```
pbuilder-dist <release> create
```

---

### Post by Bucky Ball on 2012-03-20
What release are you using? Put that, without the <> signs. Eg:

```
pbuilder-dist Lucid create
```

---

### Post by bOgNeR17 on 2012-03-20
I'm using Xubuntu 11.10 (Oneiric Ocelot) so would it be:
```
pbuilder-dist Oneiric Ocelot create

```

---

### Post by Bucky Ball on 2012-03-20
> **bOgNeR17 said:**
> I'm using Xubuntu 11.10 (Oneiric Ocelot) so would it be:
```
pbuilder-dist Oneiric Ocelot create

```

Didn't think you'd need 'Ocelot'. Is this how you solved your issue? Please share to help others. ;)

---

### Post by bOgNeR17 on 2012-03-20
Don't think it workd :/ 

```
diarmuid@diarmuid17:~$ pbuilder-dist Oneiric create
Warning: Unknown distribution "Oneiric". Do you want to continue [y/N]? y
[sudo] password for diarmuid: 
W: /home/diarmuid/.pbuilderrc does not exist
I: Logging to /home/diarmuid/pbuilder/Oneiric_result/last_operation.log
I: Distribution is Oneiric.
I: Building the build environment
I: running debootstrap
/usr/sbin/debootstrap
E: No such script: /usr/share/debootstrap/scripts/Oneiric
E: debootstrap failed
W: Aborting with an error
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//28019 and its subdirectories
```

---

### Post by Bucky Ball on 2012-03-20
You need to use 'sudo' before the command I would imagine and it is 'oneric' I think ... ;)

Maybe try with a lower-case 'o' also. But looking at your errors I suspect there is something else going on.

---

### Post by bOgNeR17 on 2012-03-20
```
pbuilder-dist oneiric create
```

Above code worked fine, just had to change Oneiric to oneiric :) Cheers

---

### Post by Bucky Ball on 2012-03-20
Great news! Enjoy ... ;)

---

