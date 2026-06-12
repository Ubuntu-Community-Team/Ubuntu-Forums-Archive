---
title: "Launching apps from terminal"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by ViliX64 on 2013-03-13
Hi, I know names of some packages and if I want to run them, I type e.g. "leafpad" and it will start. But how can I find launching names of other programs?
I'm asking, because it is easy to write: "sudo leafpad"
Thanks.

---

### Post by TK999 on 2013-03-13
Searching the package database from the terminal should bring you hits. For example, if you wanted to find out LibreOffice Calc's name, you'd write:
```

apt-cache search LibreOffice Calc

```
The resulting list will likely contain the package's name, which you can use to start the process.

Also, you should not run graphical applications with **sudo, **as it messes up file ownsership (files you edit with it will be owned by root) and has security implications. Use **gksudo **instead (or **kdesudo **if you are using Kubuntu).

---

### Post by ViliX64 on 2013-03-13
Thanks, but when I do the code as you said, there is too many commands and I don't know which one of them works..
```

vilem@vilix-X201EP:~$ apt-cache search LibreOffice Writer
libreoffice-base-core - office productivity suite -- shared library
libreoffice-filter-binfilter - office productivity suite -- legacy filters (e.g. StarOffice 5.2)
libreoffice-writer - office productivity suite -- word processor
accessodf - Libreoffice extension to check accessibility of ODF documents
bibus - bibliographic database
bibus-doc-en - Bibus bibliographic database documentation
libreoffice - office productivity suite (metapackage)
libreoffice-templates - Additional set of templates for LibreOffice
libreoffice-writer2latex - Writer/Calc to LaTeX converter extension for LibreOffice
libreoffice-writer2xhtml - Writer/Calc to XHTML converter extension for LibreOffice
libwriter2latex-java - OpenOffice.org Writer/Calc to LaTeX/XHTML converter -- library
libwriter2latex-java-doc - OpenOffice.org Writer/Calc to LaTeX/XHTML converter -- javadoc
writer2latex - OpenOffice.org Writer/Calc to LaTeX/XHTML converter
writer2latex-manual - OpenOffice.org Writer/Calc to LaTeX/XHTML converter -- manual
libobasis4.0-en-us-writer - Writer language module for LibreOffice 4.0, language en_US .1.2
libreoffice4.0-writer - Writer brand module for LibreOffice 4.0 .1.2
libobasis4.0-writer - Writer module for LibreOffice 4.0 .1.2
libobasis4.0-librelogo - LibreLogo toolbar for LibreOffice 4.0 Writer .1.2

```

---

### Post by TK999 on 2013-03-13
If there are many results, discard the ones that start with "lib" first, as they are programming libraries. Then, check the descriptions on the right&mdash;in this case, you should go for **libreoffice-writer**, whose description is "office productivity suite -- word processor". Similarly, if you wanted to run an imaginary program "Foobar", you'd select an entry like "foobar-program - florbish for grommicking".

---

### Post by ViliX64 on 2013-03-13
Thank you very much TK999 :)

---

### Post by TK999 on 2013-03-13
No probs :)

---

### Post by ViliX64 on 2013-03-13
Anyway, I can't still run it.
```

vilem@vilix-X201EP:~$ apt-cache search LibreOffice Writer
libreoffice-base-core - office productivity suite -- shared library
libreoffice-filter-binfilter - office productivity suite -- legacy filters (e.g. StarOffice 5.2)
libreoffice-writer - office productivity suite -- word processor
accessodf - Libreoffice extension to check accessibility of ODF documents
bibus - bibliographic database
bibus-doc-en - Bibus bibliographic database documentation
libreoffice - office productivity suite (metapackage)
libreoffice-templates - Additional set of templates for LibreOffice
libreoffice-writer2latex - Writer/Calc to LaTeX converter extension for LibreOffice
libreoffice-writer2xhtml - Writer/Calc to XHTML converter extension for LibreOffice
libwriter2latex-java - OpenOffice.org Writer/Calc to LaTeX/XHTML converter -- library
libwriter2latex-java-doc - OpenOffice.org Writer/Calc to LaTeX/XHTML converter -- javadoc
writer2latex - OpenOffice.org Writer/Calc to LaTeX/XHTML converter
writer2latex-manual - OpenOffice.org Writer/Calc to LaTeX/XHTML converter -- manual
libobasis4.0-en-us-writer - Writer language module for LibreOffice 4.0, language en_US .1.2
libreoffice4.0-writer - Writer brand module for LibreOffice 4.0 .1.2
libobasis4.0-writer - Writer module for LibreOffice 4.0 .1.2
libobasis4.0-librelogo - LibreLogo toolbar for LibreOffice 4.0 Writer .1.2
vilem@vilix-X201EP:~$ libreoffice-writer
libreoffice-writer: command not found
vilem@vilix-X201EP:~$ libreoffice4.0-writer
libreoffice4.0-writer: command not found

```

Yes, I have libreoffice 4.0 installed and it normaly works while launching from menu.

---

### Post by deadflowr on 2013-03-13
If you want to run graphical apps like leafpad, or gedit, or what have you, don't use sudo.
Use gksudo, or in kde kdesudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by stinkeye on 2013-03-13
> **ViliX64 said:**
> Hi, I know names of some packages and if I want to run them, I type e.g. "leafpad" and it will start. But how can I find launching names of other programs?
I'm asking, because it is easy to write: "sudo leafpad"
Thanks.
Drag the application launcher from the dash or menu into a gedit/leafpad window and look at the
**Exec=** line.

---

### Post by ViliX64 on 2013-03-13
stinkeye.. nice tip! I thought about that, but I could not find any menu editor, with whole commands..

---

### Post by stinkeye on 2013-03-13
> **ViliX64 said:**
> stinkeye.. nice tip! I thought about that, but I could not find any menu editor, with whole commands..
I don't understand what you mean here. :confused:

Do you mean the exec line doesn't always show the full path?
If so then, use the exec line with the "which" command.
eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] which thunderbird
**/usr/bin/thunderbird**
```

There's also this command I came across in an earlier thread to list all the exec commands from the .desktop files in /usr/share/applications...
```
sed -nrs '/^(Name|Exec)=/p;${g;p}' /usr/share/applications/*.desktop
```

---

### Post by montgomeryj on 2013-03-14
There is also a way to add applications that don't come with Ubuntu (or any other Linux distro for that matter) so that you can start them with sudo or gksudo.  You would follow instructions similar to those found on [https://gist.github.com/olivierlacan/1195304](https://gist.github.com/olivierlacan/1195304) depending on the exact file structure of the distro that you are running.  I hope that that helps.

---

