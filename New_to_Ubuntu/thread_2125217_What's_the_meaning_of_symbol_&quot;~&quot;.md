---
title: "What's the meaning of symbol &quot;~/&quot;"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by focusdoit on 2013-03-13
Hi, I read an article about setting in .vimrc, it used the following commands:
cat > ~/.vimrc
it seems ~/ is a directory, I wonder what meaning of the above command.

---

### Post by albandy on 2013-03-13
~/ means your home folder

---

### Post by pfeiffep on 2013-03-13
cat will display the contents of a file
~/ is home for you
.vimrc is a hidden file

---

### Post by Warren Hill on 2013-03-13
```
~
```

Is your home directory you can find out what its set to by entering 

```
echo $HOME
```

Its normally set to **/home/*username*** where *username *is your user name.

Any file with a period at the beginning is an hidden file so if your user name was foo

[B]cat ~/.vimrc
cat $HOME/.vimrc
cat /home/foo/.vimrc[/B]

would all do the same thing list the contents of the hidden file** .vimrc** in your home directory.

---

### Post by evilsoup on 2013-03-13
The actual command in the OP

```

cat > ~/.vimrc

```

...would create a blank file at ~/.vimrc ...

---

### Post by Bashing-om on 2013-03-13
added info: "~/" is but one of the many "shortcuts" in linux in general and ubuntu in particular.

---

### Post by CaptainMark on 2013-03-13
> **evilsoup said:**
> The actual command in the OP

```

cat > ~/.vimrc

```

...would create a blank file at ~/.vimrc ...
Actually it would hang waiting for input and whatever you type will be saved to ~/.vimrc upon recieving an exit signal

---

