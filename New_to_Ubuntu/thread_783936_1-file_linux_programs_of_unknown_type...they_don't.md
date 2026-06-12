---
title: "1-file linux programs of unknown type...they don't launch"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by savethewabbit on 2008-05-06
i downloaded today two very small programs that are supposed to run on linux... problem is that in each .zip file i find one single file of unknown type, about 6kb big, executable but won't work if i try to click it or if try to launch it via wine.
i've downloaded these programs off a forum, and i saw people thanking for them, so i suppose i'm doing something wrong, as everybody else was able to make the programs work!
since these are a linux version of windows programs, perhaps i should overwrite the .exe file in the windows program folder with this one? it seems too weird.

so what should i do with this kind of files? how do i make them run?

---

### Post by mlentink on 2008-05-06
Overwriting windows executables with linux ones is not going to help you, just make the windows ones unuseable.

Have you tried
```
chmod +x nameoffile
```


Edit: It might help us if yuo gave the name of those files...

---

### Post by Joeb454 on 2008-05-06
Well what filetype is it (i.e. the file extension) This way we will be able to give a little more detailed help :)

---

### Post by didac on 2008-05-06
Unzip your files to the Desktop. Fire a terminal and type:

```
cd Desktop
ls -l
```

Your file should be listed with permissions like rwxrwxrwx, at least the first x should be present. If not, do as mlentink says:

```
chmod +x nameoffile
```

Then type:

```
./nameoffile
```

and watch the messages. Post them here.

---

