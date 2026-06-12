---
title: "xclip problem"
date: 2012-05-21
forum: Programming Talk
---

### Post by dragonbook on 2012-05-21
Hi all

If I put: **xclip -sel clip -i text.txt** in the terminal, it will copy the text from the file "text.txt" to the clipboard as I want it to.

But, if I put: **xclip -sel clip -i text.txt** in a .sh file and tell i to open in the terminal it doesn't copy the text from "text.txt" to the clipboard :(

Does anyone now why this command doesn't work from the .sh file?

---

### Post by Arndt on 2012-05-21
> **dragonbook said:**
> Hi all

If I put: **xclip -sel clip -i text.txt** in the terminal, it will copy the text from the file "text.txt" to the clipboard as I want it to.

But, if I put: **xclip -sel clip -i text.txt** in a .sh file and tell i to open in the terminal it doesn't copy the text from "text.txt" to the clipboard :(

Does anyone now why this command doesn't work from the .sh file?

How do you determine that it doesn't work? Does "xclip -sel clip -o" show what you expect?

Show the exact commands you are using, and the contents of the script file.

---

### Post by dragonbook on 2012-05-21
> **Arndt said:**
> How do you determine that it doesn't work? Does "xclip -sel clip -o" show what you expect?

Show the exact commands you are using, and the contents of the script file.

When trying to indsert text from clipboard (Ctrl+V) in gedit, nothing happens. 

The contents of the .sh file is only: 
xclip -sel clip -i text.txt


xclip -sel clip -o gives me nothing...

---

### Post by dragonbook on 2012-05-21
I am using ubuntu 12.04 and installed xclip via sudo apt-get install xclip.

---

### Post by Arndt on 2012-05-21
> **dragonbook said:**
> I am using ubuntu 12.04 and installed xclip via sudo apt-get install xclip.

If you follow the steps below, do the same things happen? How do my steps differ from yours? (I use Ubuntu 10, by the way.)

```
arndt@ubuntu:~/clip$ echo "it works" > text.txt
arndt@ubuntu:~/clip$ echo "it works2" > text2.txt
arndt@ubuntu:~/clip$ echo "xclip -sel clip -i text.txt" > clip.sh
arndt@ubuntu:~/clip$ xclip -sel clip -i text.txt
arndt@ubuntu:~/clip$ xclip -sel clip -o
it works
arndt@ubuntu:~/clip$ xclip -sel clip -i text2.txt
arndt@ubuntu:~/clip$ xclip -sel clip -o
it works2
arndt@ubuntu:~/clip$ sh clip.sh 
arndt@ubuntu:~/clip$ xclip -sel clip -o
it works
```

---

### Post by dragonbook on 2012-05-21
> **Arndt said:**
> If you follow the steps below, do the same things happen? How do my steps differ from yours? (I use Ubuntu 10, by the way.)

```
arndt@ubuntu:~/clip$ echo "it works" > text.txt
arndt@ubuntu:~/clip$ echo "it works2" > text2.txt
arndt@ubuntu:~/clip$ echo "xclip -sel clip -i text.txt" > clip.sh
arndt@ubuntu:~/clip$ xclip -sel clip -i text.txt
arndt@ubuntu:~/clip$ xclip -sel clip -o
it works
arndt@ubuntu:~/clip$ xclip -sel clip -i text2.txt
arndt@ubuntu:~/clip$ xclip -sel clip -o
it works2
arndt@ubuntu:~/clip$ sh clip.sh 
arndt@ubuntu:~/clip$ xclip -sel clip -o
it works
```

Okay now i did exactly like you did

but this strange thing happend after typing "xclip -sel clip -o":

troels@Ubuntu:~$ echo "it works" > text.txt
troels@Ubuntu:~$ echo "it works2" > text2.txt
troels@Ubuntu:~$ echo "xclip -sel clip -i text.txt" > clip.sh
troels@Ubuntu:~$ xclip -sel clip -i text.txt
troels@Ubuntu:~$ xclip -sel clip -o
**xclip -sel clip -otroels@Ubuntu:~$**

---

### Post by dragonbook on 2012-05-21
Just tested on another 12.04 machine, same problem.

---

### Post by Vaphell on 2012-05-21
check primary/secondary/clipboard
```
xsel -pi/-si/-bi < file
echo string | xsel -pi/-si/-bi
xsel -po/-bo/-so
```

---

### Post by dragonbook on 2012-05-22
> **Vaphell said:**
> check primary/secondary/clipboard
```
xsel -pi/-si/-bi < file
echo string | xsel -pi/-si/-bi
xsel -po/-bo/-so
```

Nothing in the clipboard! This is very strange. Anyone testet this on a 12.04. I will try on a ubuntu 10.10 live cd.

---

### Post by dragonbook on 2012-05-22
Installed Ubuntu 10.10 in virtual box, same problem...

Arndt: Are you using 10.04 and did you install xclip via apt-get?

---

### Post by Vaphell on 2012-05-22
apparently xclip is junk ;-)

```
$ echo "" | xsel -bi
$ xsel -bo

$ xsel -bi < examples.desktop 
$ xsel -bo
[Desktop Entry]
Version=1.0
Type=Link
Name=Examples
Comment=Example content for Ubuntu
URL=file:///usr/share/example-content/
Icon=folder
X-Ubuntu-Gettext-Domain=example-content
```

pressing ctrl+v / ctrl+shift+v pastes it anywhere, tested with 11.10 and 12.04 in VM and in fullblown 10.04

primary buffer is highlight/middleclick (-pi for input, -po for output)
secondary - ? (-si, -so)
clipboard - ctrl+c/ctrl+v (-bi, -bo)

---

### Post by dragonbook on 2012-05-23
> **Vaphell said:**
> apparently xclip is junk ;-)

```
$ echo "" | xsel -bi
$ xsel -bo

$ xsel -bi < examples.desktop 
$ xsel -bo
[Desktop Entry]
Version=1.0
Type=Link
Name=Examples
Comment=Example content for Ubuntu
URL=file:///usr/share/example-content/
Icon=folder
X-Ubuntu-Gettext-Domain=example-content
```

pressing ctrl+v / ctrl+shift+v pastes it anywhere, tested with 11.10 and 12.04 in VM and in fullblown 10.04

primary buffer is highlight/middleclick (-pi for input, -po for output)
secondary - ? (-si, -so)
clipboard - ctrl+c/ctrl+v (-bi, -bo)

But why isent this working if I put it in a *.sh file and selecting run in terminal?

---

### Post by roelforg on 2012-05-23
> **dragonbook said:**
> But why isent this working if I put it in a *.sh file and selecting run in terminal?
 
If the program (the terminal is the parent process of your sh file) that sets the clipboard exits, the clipboard empties.
 
So this happens:
Terminal opens->script runs->script sets clipboard->script exits->(clipboard contains data)->terminal exits->clipboard clear

---

### Post by Vaphell on 2012-05-23
try installing some clipboard manager tool, it should preserve data even when the parent process is no more.

---

### Post by Arndt on 2012-05-25
> **roelforg said:**
> If the program (the terminal is the parent process of your sh file) that sets the clipboard exits, the clipboard empties.
 
So this happens:
Terminal opens->script runs->script sets clipboard->script exits->(clipboard contains data)->terminal exits->clipboard clear

That would seem to explain it. I missed the part about "Run in terminal" - I thought he just meant call the script in an existing terminal emulator, which works, as I showed.

However, when I tried the things I described earlier, exited the terminal, and ran 'xclip -sel clip -o' in another terminal, the text was still there. The clipboard had not emptied.

So I'm not at all sure how it's supposed to work.

---

