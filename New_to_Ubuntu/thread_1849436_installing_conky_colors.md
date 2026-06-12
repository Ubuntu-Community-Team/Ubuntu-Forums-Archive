---
title: "installing conky colors"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by murderd2death on 2011-09-24
i downloaded and extracted conky colors, i changed directory to the downloads folder it was extracted in, however, whenever i run the codes ```
[B]$make
$sudo make install
$conky-colors {options}[/B]


```

i get 

```

~/Downloads$ $make
~/Downloads$ $sudo make install
make: *** No rule to make target `install'.  Stop.~/Downloads$ $conky-colors {options}
No command '-colors' found, did you mean:
 Command 'xcolors' from package 'xcolors' (universe)
-colors: command not found

```

running natty, please help

regards

---

### Post by Lisiano on 2011-09-24
Don't type the dollar ($) sign. The terminal interprets anything starting with a $ as a variable```
echo $USER
``` This will show you your username, despite it saying USER.

If you ever encounter something looking like this ```
$ date
```
It means run this as a normal user.
Or if you encounter a hash (#) symbol.
```
# date
```It means run this as root or superuser (using sudo)

---

### Post by murderd2death on 2011-09-24
> **Lisiano said:**
> Don't type the dollar ($) sign. The terminal interprets anything starting with a $ as a variable```
echo $USER
``` This will show you your username, despite it saying USER.

If you ever encounter something looking like this ```
$ date
```It means run this as a normal user.
Or if you encounter a hash (#) symbol.
```
# date
```It means run this as root or superuser (using sudo)
  this is what i got```
wintermute32@wintermute32-Lenovo-B570:~$ echo USER
USER
wintermute32@wintermute32-Lenovo-B570:~$ echo$USER
echowintermute32: command not found

```

everyjthing normal?

---

### Post by Lisiano on 2011-09-24
2nd one you didn't put a space after the word "echo".

EDIT: I'll correct myself on my post above. Don't type the $ and # if there is a space between them and the word AND if they are on the very left.

---

### Post by murderd2death on 2011-09-24
> **Lisiano said:**
> 2nd one you didn't put a space after the word "echo".

EDIT: I'll correct myself on my post above. Don't type the $ and # if there is a space between them and the word AND if they are on the very left.

i dont understand, typing echo without the '$' sign is just reprinting anything i type, it doesn't serve the function of telling me the username.

---

### Post by Lisiano on 2011-09-24
Just copy paste this exactly to the terminal
```
echo $USER
```
You will see something similar to this:```
lisiano@Lisiano-Ubuntu:~$ echo $USER
lisiano
lisiano@Lisiano-Ubuntu:~$
```

Basically. If a word starts with it, type it, if a line starts with it and there is a space after it, ignore.

---

### Post by murderd2death on 2011-09-24
> **Lisiano said:**
> Just copy paste this exactly to the terminal
```
echo $USER
```You will see something similar to this:```
lisiano@Lisiano-Ubuntu:~$ echo $USER
lisiano
lisiano@Lisiano-Ubuntu:~$
```Basically. If a word starts with it, type it, if a line starts with it and there is a space after it, ignore.

so i have my username, now how am i going to use this to install conky?

---

### Post by Lisiano on 2011-09-24
*Facepalm*
> **murderd2death said:**
> ```
$make
$sudo make install
$conky-colors {options}

```

You want to type this
```
make
sudo make install
conky-colors
```
The thing with the username was to show you what you did wrong and why. Also to prevent you doing the same mistake.

---

### Post by murderd2death on 2011-09-24
> **Lisiano said:**
> *Facepalm*

You want to type this
```
make
sudo make install
conky-colors
```The thing with the username was to show you what you did wrong and why. Also to prevent you doing the same mistake.

k, now this is what i get

```
wintermute32@wintermute32-Lenovo-B570:~/Downloads$ make
make: *** No targets specified and no makefile found.  Stop.
wintermute32@wintermute32-Lenovo-B570:~/Downloads$ sudo make install
make: *** No rule to make target `install'.  Stop.
wintermute32@wintermute32-Lenovo-B570:~/Downloads$ conky-colors
conky-colors: command not found
wintermute32@wintermute32-Lenovo-B570:~/Downloads$ 

```

---

### Post by Lisiano on 2011-09-24
You have to cd to the directory you extracted the conky-colors folder. If the folder is called conky-colors then use this
```
cd conky-colors
``` then the make, sudo make install.

---

