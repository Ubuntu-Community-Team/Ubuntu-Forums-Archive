---
title: "Broke boot sequence and privileges"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by emagar on 2012-07-22
I am a recent Linux convert also trying to learn Emacs. 

Attempting to install an online thesaurus for Emacs, I did something awfully wrong, it seems. 

I saved the tar file from [https://user.in-berlin.de/~myrkr/dictionary/download.html]("https://user.in-berlin.de/%7Emyrkr/dictionary/download.html") then followed instructions here: [https://user.in-berlin.de/~myrkr/dictionary/installation.html]("https://user.in-berlin.de/%7Emyrkr/dictionary/installation.html") . I unzipped the tar files and then saw the XEmacs 21 lines in the last link. I attempted to adapt the script to my Emacs23. 

My bash history appears below. The 
```
make EMACS=xemacs package
```failed to recognize xemacs, so I tried 
```
make EMACS=emacs package
```instead.  A message [COLOR=Red]"I hope you know what you are doing" [/COLOR]appeared without prompting me to ok what was going on... Installation failed and the dictionnary callup was not recognized in emacs. I then  deleted files and directories created in ~/.emacs.d. 

But the system behaves oddly since. Booting twice led me to BIOS (presumably the disk boot sequence is corrupt, asking for a USB instead.) A subsequent, successful boot left me without administrator privileges. 

Any advice on how to undo the damage will be highly appreciated.

This is from my .bash_history

```
mv ~/.emacs.d/dictionnaryThesaurusLookup.el ~/.emacs.d/dict.el
cd ~/Downloads/
ls
gzip -dc dictionary-1.8.7.tar.gz | tar xf -
ls
cd dictionary-1.8.7/
make
sudo checkinstall 
sudo checkinstall --fstrans=0
sudo make install
ls
gedit README
make EMACS=xemacs package
[COLOR=Red]make EMACS=emacs package[/COLOR]
cd ..
ls
rm dic*
ls
sudo rm -r dic*
ls
cd ~/.emacs.d/
ls
rm dict.el

```

---

### Post by emagar on 2012-07-22
> **emagar said:**
> A message [COLOR=Red]"I hope you know what you are doing" [/COLOR]appeared without prompting me to ok what was going on... 

I guess the above is the most puzzling of all... I didn't expect an operating system to issue such message without first seeking confirmation for what is about to happen.

Machine has been running ok, but I hesitate to reboot.

In case I have to reinstall the system, would saving a copy of my home directory be enough to recover personal configurations?

Thanks again.

---

