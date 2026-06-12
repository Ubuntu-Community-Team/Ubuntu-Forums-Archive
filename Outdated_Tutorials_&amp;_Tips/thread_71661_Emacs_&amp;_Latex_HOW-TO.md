---
title: "Emacs &amp; Latex HOW-TO"
date: 2005-10-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Manny C on 2005-10-04
This is for all the lonely people, thinking that life has passed them by...
_**EMACS**_[LIST=1]
[*]Download the attached emacsconf.tar.gz archive to your home directory. Then extract the attached .emacs and .Xresources file to ~/ ```
 tar zxvf emacsconf.tar.gz 
```
[*]Install emacs and associated packages:
```
sudo apt-get install emacs21 emacs-extra emacs-goodies-el emacs-extra-goodies-el emacsauctex preview-latex xfonts-jmk
```
[*]Restart your computer (I think this is necessary)[/LIST]**_LATEX_**[LIST=1]
[*]Install LaTeX
```
sudo apt-get install tetex-base tetex-extra
```
[*]Install dvi viewers (can install only one - use kdvi if you have kubuntu, o/w use xdvi)
```
sudo apt-get install kdvi xdvi 
```
[*]Read [The Not So Short Introduction to LaTeX]("http://ctan.unsw.edu.au/info/lshort/english/lshort.pdf")[/LIST]**_FINALISE_**
Apply the .Xresources settings:
```
xrdb -merge .Xresources
``` **_LaTeX AWAY!_**
Open Emacs, and TeX away.

---

### Post by John.Michael.Kane on 2005-10-04
Can you explain this Copy the attached .emacs and .Xresources file to ~/
thanks

---

### Post by chettyk on 2005-10-04
[QUOTE=SD-Plissken]Can you explain this Copy the attached .emacs and .Xresources file to ~/
thanks[/QUOTE]

Thanks Manny C for the HOWTO. I assume that the .emacs and .Xresources files are needed if you want to carry over settings from another distribution. My .emacs file, which I have carefully preserved from a Fedora distro, has some useful macros that I'd like to use.

---

### Post by Manny C on 2005-10-17
[quote=SD-Plissken]Can you explain this Copy the attached .emacs and .Xresources file to ~/
thanks[/quote] 

Download the .tar.gz file. Use Ark to extract to the Home Directory or save the archive to ~/ and then issue the following command.
```
 tar zxvf emacsconf.tar.gz
``` 

If you are a newbie, use Ark. It is much easier.

[QUOTE=chettyk]I assume that the .emacs and .Xresources files are needed if you want to carry over settings from another distribution. [/QUOTE]

This is correct.

---

