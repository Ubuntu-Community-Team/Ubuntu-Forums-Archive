---
title: "How to update a program installed using Gdebi ?"
date: 2018-06-16
forum: New to Ubuntu
---

### Post by automate-stuff on 2018-06-16
I installed Emacs using Gdebi, the following two .deb files were installed : 

emacs25-common*.deb
emacs25*.deb

if a new version becomes available(new updated versions of the .deb files mentioned above) then should i uninstall the old .deb packages then install the new ones or should I install the new.deb files on top of the older ones ? 


Many Thanks

---

### Post by Frogs Hair on 2018-06-16
If the packages are not from the repository or seen as identical to existing packages you will have to manually update unless the option to update with the system was offered during installation. I see both packages in synaptic on 18.04, so no need to install from an outside source.

---

### Post by automate-stuff on 2018-06-16
[FONT=arial]I have these installed by manually finding the deb package for each:

[COLOR=#000000]emacs25-common*.deb[/COLOR]
[COLOR=#000000]emacs25*.deb

Now these packages become available:

[/COLOR][COLOR=#000000]emacs26-common*.deb[/COLOR]
[COLOR=#000000]emacs26*.deb[/COLOR][COLOR=#000000]

should I uninstall the 25s then install 26s or should I just install 26's on top of 25s(Without removing 25s) ?[/COLOR][/FONT]

---

### Post by Frogs Hair on 2018-06-16
The emacs26 packages are not in the repository so if you need them you'll have manually install them.

---

### Post by automate-stuff on 2018-06-16
I am not talking about repositories at all....I manually downloaded [COLOR=#000000][COLOR=#000000][FONT=arial]emacs25-common*.deb and [/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=arial]emacs25*.deb from some websites and used gdebi to install them.....

now the 26s are available so i downloaded them manually too...

my question is: Should I just install 26s on top of 25s or should I remove 25s first and then install the 26s....[/FONT][/COLOR][/COLOR]

---

### Post by again? on 2018-06-17
You would need to uninstall  emacs25 and emacs25-common first.
emacs25-common conflicts with emacs26-common.
Consider using this ppa [https://launchpad.net/~kelleyk/+archive/ubuntu/emacs](https://launchpad.net/~kelleyk/+archive/ubuntu/emacs)

Using the ppa this is the error i got when installing emacs25 then attemting to install emacs26.
```
Preparing to unpack .../emacs26-common_26.1~1.git07f8f9b-kk1+18.04_all.deb ...
Unpacking emacs26-common (26.1~1.git07f8f9b-kk1+18.04) ...
dpkg: error processing archive /var/cache/apt/archives/emacs26-common_26.1~1.git07f8f9b-kk1+18.04_all.deb (--unpack):
 trying to overwrite '/usr/share/emacs/site-lisp/subdirs.el', which is also in package emacs25-common 25.3~1.gite0284ab-kk1+18.04
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/emacs26-common_26.1~1.git07f8f9b-kk1+18.04_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Frogs Hair on 2018-06-18
> **automate-stuff said:**
> I am not talking about repositories at all....I manually downloaded [COLOR=#000000][COLOR=#000000][FONT=arial]emacs25-common*.deb and [/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=arial]emacs25*.deb from some websites and used gdebi to install them.....

now the 26s are available so i downloaded them manually too...

my question is: Should I just install 26s on top of 25s or should I remove 25s first and then install the 26s....[/FONT][/COLOR][/COLOR]

I am aware of that as I wrote you'll have to install manually . see guber2 's post above the ppa might be a better option if it has been maintained consistently. I mentioned the repository because 25 was already there.

---

