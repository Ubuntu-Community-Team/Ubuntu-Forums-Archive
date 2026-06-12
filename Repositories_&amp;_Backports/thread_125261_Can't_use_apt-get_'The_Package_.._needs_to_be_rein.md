---
title: "Can't use apt-get: 'The Package .. needs to be reinstalled..'"
date: 2006-02-03
forum: Repositories &amp; Backports
---

### Post by philxxx on 2006-02-03
Hi,

I gave Ubuntu a try a few days ago and everything worked fine, until today I tried to install TrueCrypt.
I downloaded a debian package file from the official site but got an error message while using 'sudo apt-get install truectrypt...deb' because my kernel seems to old.

I hit STRG+C and I guess that was a mistake, because now I get always:

E: The package truecrypt needs to be reinstalled, but I can't find an archive for it.

Unfortunately I don't know how to remove the package (that seems to be half installed) ... help, help.

Any hint on howto upgrade my kernel is greatly appreciated too, but I guess that I can get this browsing the forum :-)

Regards from Berlin / Germany

p hil.

PS: I forgott to mention that the Update manager in System / Administration is crashing shortly after starting.
PS-2: I'm running Ubuntu v5.10

---

### Post by MartinG on 2006-02-03
Try using Synaptic to remove broken package(s).  Otherwise```
sudo apt-get remove --purge <package_name>
```

---

### Post by philxxx on 2006-02-04
If use Synaptics Package Manager and search for the truecrypt package, it can be found.

Using Edit / Fix broken packages gives the following error-message:

E: The package truecrypt needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I tried to use the terminal, after reading your suggestions above:

Beeing in the directory, where the downloaded .deb-package (truecrypt) is I tried both:
```
 sudo apt-get remove --purge truecrypt_4.1-0_i386.deb
```
or
```
 sudo apt-get remove --purge truecrypt
```
Gives: 
Reading package lists... Done
Building dependency tree... Done
E: The package truecrypt needs to be reinstalled, but I can't find an archive for it.

Other suggestions - I hope I don't have to reinstall (reminding to much of my old windows system :evil: )

regards from berlin / germany

p hil

---

### Post by MartinG on 2006-02-04
This is getting tricky.  Did you try reinstalling truecrypt, and this time letting it take its course rather than cancelling?
sudo dpkg -i <truecrypt_package>

---

### Post by philxxx on 2006-02-04
[QUOTE=MartinG]This is getting tricky.  Did you try reinstalling truecrypt, and this time letting it take its course rather than cancelling?
sudo dpkg -i <truecrypt_package>[/QUOTE]

THANKS!!!

I don't know why 'dpkg -i' is working, but 'apt-get install' not, but it worked - that's good :-)

This worked, I got some error messages but after everything was done, I tried:
```
sudo apt-get remove --purge truecrypt
```
and everything worked fine.

Now to solve the problem, I need to update my kernel (hope to finde some info using search in this forum) and then reinstall TrueCrypt.

Thanks for the hint!

P hil

---

