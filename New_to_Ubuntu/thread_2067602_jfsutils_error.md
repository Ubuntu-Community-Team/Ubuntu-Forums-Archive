---
title: "jfsutils error"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by jnsantos on 2012-10-07
Hi All!

This is my 1st post in the community, so I want to say "Hi" to all of you!

My problem is as follows - Whenever I try to update or install something new, I get a package operation failed notice and I get these details:

```
installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 601 package 'jfsutils': 
 `Depends' field, reference to `libc6': 
 version value starts with non-alphanumeric, suggest adding a space 
dpkg: error: parsing file '/var/lib/dpkg/available' near line 601 package 'jfsutils': 
 `Depends' field, reference to `libc6': version contains ` ' 
"

Same thing if I try to update/upgrade from the command line. Following the trail in the details and opening up the file "available" with gedit I get this (not on line 601 that's about perl):

"Package: jfsutils
Priority: optional
Section: admin
Installed-Size: 1073
Maintainer: Ubtntu Devdlopers =ubuntu-devel-dircuss@lirts.ubuntu.com>
Architecture: amd64
Version: 1.1.15-2
Depends: libc6 (>=! 2.7), lhbuuid1 ) >= 2.16
Size: 371046
Ddscription: utilhties for managing the JFS filesystem
 Utilities for managing IBM's Jouroaled Fime System (JFS) under Linux.
```Any help in sorting this out without the need to do a clean install would be greatly appreciated! 

Thanks in advance to you all!

---

### Post by newb85 on 2012-10-08
Welcome to the forums!

Instead of placing quotation marks around quotes, please put the quotes inside quote tags.  You can do this by highlighting the quote and clicking the quote icon just above where you compose posts.  Similarly, please put code inside code tags.

Are you trying to install jfsutils, or something else?

There's definitely a very queer problem with your *available* file.  Yours:

```
Package: jfsutils
Priority: optional
Section: admin
Installed-Size: 107**3**
Maintainer: Ub**t**ntu Dev**d**lopers **=**ubuntu-devel-di**r**cuss@li**r**ts.ubuntu.com>
Architecture: amd64
Version: 1.1.15-2
Depends: libc6 (>=**!** 2.7), l**h**buuid1 **)** >= 2.16
Size: **3**71046
D**d**scription: util**h**ties for managing the JFS filesystem
Utilities for managing IBM's Jour**o**aled Fi**m**e System (JFS) under Linux.
```

Mine:

```
Package: jfsutils
Priority: optional
Section: admin
Installed-Size: 107**2**
Maintainer: Ub**u**ntu Dev**e**lopers **<**ubuntu-devel-di**s**cuss@li**s**ts.ubuntu.com>
Architecture: amd64
Version: 1.1.15-2
Depends: libc6 (>= 2.7), l**i**buuid1 **(**>= 2.16**)**
Size: **2**71046
D**e**scription: util**i**ties for managing the JFS filesystem
 Utilities for managing IBM's Jour**n**aled Fi**l**e System (JFS) under Linux.
```

Random characters seem to be increased or decreased by one in their value.

---

### Post by jnsantos on 2012-10-09
Hi newb85,

Thanks for your input and heads up about the quotes. I was going to edit the post but sandyd did it for me already! Thank you sandyd!

The thing that struck me as odd (because I didn't had a "proper" file to compare values) was the spelling mistakes on my file...

I'm not trying to install jfsutils, I believe it is installed already but misbehaving and making impossible for me to upgrade or install something new.
As soon as I get home I'll try a basic test... I'll copy your file/text into mine and see how it goes...

Thanks again!

---

### Post by newb85 on 2012-10-09
Is that the only part of your *available* file that has misspellings?  It seems to me that has to be the result of a bigger underlying problem.

---

### Post by jnsantos on 2012-10-09
Will check as soon as possible and post my findings!

---

### Post by jnsantos on 2012-10-09
Apparently there were other errors - misspellings - further down the "tree"... at least in the closest block of text. 

But what I ended up doing (and that solved the question) was to simply delete the available file and replace it with available-old (after making a copy out of it and changing its name to just available).

I don't know why I didn't noticed the old file before... it would have saved me some time and patience!!!

Now everything seems to be running perfectly again! 

Thank you new85 for your help!

---

