---
title: "Distributing your software professionally in ubuntu?"
date: 2013-08-05
forum: Packaging and Compiling Programs
---

### Post by kalar on 2013-08-05
[COLOR=#333333][FONT=UbuntuRegular]Current status : I have made a .deb package which I have hosted on an Apache server. People can do apt-get install from repository.

Now the problems:

While people does apt-get install mypackage. They get a unauthorized warning.

To solve the warning i signed the package and generated the public key.  My client then add the public key from an url after which they don't get the warning.

Now what I want is that my client should not get warning without going into trouble of downloading and then adding the public key. Like any other famous software packages.

[/FONT][/COLOR]

---

### Post by ian-weisser on 2013-08-05
Well, the recommended path is to add your software to the Ubuntu repositories (instead of using your own repo).

---

### Post by kalar on 2013-08-06
What if I would like to make the software commercial and don't feel secure with Ubuntu repository.

---

### Post by ian-weisser on 2013-08-06
The short answer to your questions is: Use the apt-add-repository command in a script (or .deb in the Ubuntu repository).

Ubuntu users expect to find your software in the Ubuntu Software Center (SC), and to pay for it there.
To be in SC, the .dev must be in one of several specific repositories.
If your software is not in (the trusted) SC, customers will wonder why not. Fewer will pay for software they are suspicious of.

---

