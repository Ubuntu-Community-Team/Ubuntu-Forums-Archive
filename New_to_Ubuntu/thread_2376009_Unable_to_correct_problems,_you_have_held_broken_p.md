---
title: "Unable to correct problems, you have held broken packages."
date: 2017-10-29
forum: New to Ubuntu
---

### Post by mivanova on 2017-10-29
I have been trying to install clang++ and this is what i get:
python-clang-5.0 is already the newest version (1:5.0-3).
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 python-clang-3.9 : Breaks: python-clang-3.8 but 1:3.8.1-24ubuntu7 is to be installed
 python-clang-4.0 : Conflicts: python-clang-x.y
                    Breaks: python-clang-3.8 but 1:3.8.1-24ubuntu7 is to be installed
                    Breaks: python-clang-3.9 but 1:3.9.1-17ubuntu1 is to be installed
 python-clang-5.0 : Conflicts: python-clang-x.y
                    Breaks: python-clang-3.8 but 1:3.8.1-24ubuntu7 is to be installed
                    Breaks: python-clang-3.9 but 1:3.9.1-17ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.



I tried sudo apt-get update/upgrade/autoclean/autoremove
sudo apt-get install -f. Nothing of that works.
Any help is appreciated. Thank you in advance

---

### Post by mc4man on 2017-10-29
You need to post what command you ran that produced the messages you posted.
(- the comment "trying to install clang++" isn't helpful as there is no such package..

Preferably open a terminal, run it again, copy all the text & paste into a reply. After pasting highlight all the pasted text & click on the hash-tag button in the reply toolbar to put that text in a code box.

---

