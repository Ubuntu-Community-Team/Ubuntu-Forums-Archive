---
title: "Open office is totally messed up!"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by hellarough on 2008-06-02
I have been looking around trying to fix the conflicts that firefox and openoffice have with my new dark theme and I was looking in here
[http://ubuntuforums.org/showthread.php?t=502953](http://ubuntuforums.org/showthread.php?t=502953)

But I couldn't rally make too much sense of what that thread was telling me to do. However,I found somewhere [in the forums] that I shoud use the following commands in the terminal to fix this problem for open office..

code:
cd /usr/lib/openoffice/program
sudo mv soffice.bin soffice2.bin
sudo mv soffice soffice2
sudo gedit soffice

(type this into the text file and save)
#!/bin/sh
env GTK2_RC_FILES=/usr/share/themes/Clearlooks/gtk-2.0/gtkrc /usr/lib/openoffice/program/soffice2 "$@"

(into terminal)
sudo chmod +x soffice

except now, open office doesnt work when I use the launchers. also, when I type ooffice into the terminal I get this...
/usr/bin/ooffice: 2: /usr/lib/openoffice/program/soffice: not found


Ideally I would love to roll back the changes that I made to openoffice so that it works again and find out how I can just configure firefox and open office to open with a different theme so they appear like they used to before I changed themes.

Thanks in advance for any help

---

### Post by shifty_powers on 2008-06-02
do me a favour

```
cd /usr/lib/openoffice/program
```

then

```
ls
```

and post the output

---

### Post by hellarough on 2008-06-02
Ha Ha...I figured it out!So, I undid the changes to the file names above and I deleted the newly created script file so that I was back at square one. Everytime i opened open office i would have a dark backround and dark fonts...


This is what I did to start open office in other themes...

In terminal use to following commands..
```
cd /usr/bin/
sudo gedit soffice
```

up pops a text file...change the file to look like this...

```

#!/bin/sh
env GTK2_RC_FILES=/usr/share/themes/Clearlooks/gtk-2.0/gtkrc /usr/lib/openoffice/program/soffice "$@"
```


or you can substitute other themes like so....


```
#!/bin/sh
env GTK2_RC_FILES=/usr/share/themes/Human/gtk-2.0/gtkrc /usr/lib/openoffice/program/soffice "$@"
```


*you might want to make a back up of the ooffice file before you make changes to it

hope it works for others

---

