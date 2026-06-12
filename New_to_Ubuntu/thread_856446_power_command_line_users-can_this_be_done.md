---
title: "power command line users-can this be done?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by rburkartjo on 2008-07-11
it would be nice to be able to do this
the below is a list of some .odt files from my computer
is there a way using the terminal to copy and paste and open from the terminal. would make things a lot simpler if could be done
/home/ray/Desktop/GROCERY LIST.odt
/home/ray/Documents/FFF.odt
/home/ray/Documents/LETTER TO INSURANCE CO TO TRY TO RESOLVE PROBLEMS.odt
/home/ray/Documents/archive home.odt
/home/ray/Documents/archive system.odt
/home/ray/Documents/backing up operating system.odt
/home/ray/Documents/backing up system2.odt
/home/ray/Documents/cheatlist.odt
/home/ray/Documents/deleting backup.tgz.odt
/home/ray/Documents/moving home.odt
/home/ray/Documents/re:archiving the system.odt
/home/ray/Documents/scripting 2.odt
/home/ray/Documents/scripting help.odt
/home/ray/Documents/what to do if you forget your password.odt
/usr/lib/openoffice/share/template/en-GB/internal/idxexample.odt
/usr/lib/openoffice/share/template/en-US/internal/idxexample.odt
/usr/lib/openoffice/share/template/en-ZA/internal/idxexample.odt
/usr/share/doc/ttf-arphic-uming/Font_Comparison_ShanHeiSun_UMing.odt.gz
/usr/share/example-content/oo-about-these-files.odt
/usr/share/example-content/oo-maxwell.odt
/usr/share/example-content/oo-welcome.odt
/usr/share/ubuntu-tweak/templates/ODT Document.odt
tks cheesemaker

---

### Post by quantumstitch on 2008-07-11
I am not exactly sure what you mean. Can you explain? Are you copying contents or just verbatim?

---

### Post by Inxsible on 2008-07-11
copying from one location to other? use the cp command

if only odt files then ```
cp /path/to/*.odt /path/to/destination
```

---

### Post by sdennie on 2008-07-11
To open them, you can also use the little known gnome command gnome-open:

```

gnome-open some_file.odt

```

That reads the document with whatever application nautilus would have opened if you'd double clicked the document.

---

### Post by rburkartjo on 2008-07-11
vor,tks that worked like a charm i can use gnome-open and then paste from the list i posted above. one more question i did notice that since some of my file names have a space in them that i must put " at the beginning of the file name and then after .odt. anyway to get around this. this is cool beans/tks cheesemaker

---

### Post by Sukarn on 2008-07-11
you can use the escape sequence for a space by putting a \ before a space.

---

### Post by rburkartjo on 2008-07-11
sukarn, could you pls give me an example you lost me/tks cheesemaker

---

### Post by aktiwers on 2008-07-11
/home/ray/Documents/LETTER\ TO\ INSURANCE\ CO\ TO\ TRY\ TO\ RESOLVE\ PROBLEMS.odt

---

### Post by youthforlinux on 2008-07-11
You can use the tab key to make it simpler, it will auto complete using what you have typed in.

---

