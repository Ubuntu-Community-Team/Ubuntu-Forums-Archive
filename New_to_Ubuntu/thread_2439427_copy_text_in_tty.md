---
title: "copy text in tty"
date: 2020-03-27
forum: New to Ubuntu
---

### Post by kraynov-pavel on 2020-03-27
Hi I didn't used to terminal by this time.
I do not understand clearly how to copy text from tty
I have standalone computer with several disks and need copy uuid of them and paste to fstab.
I do not understand how to do it without GUI, btw, I just curious, does ubuntu provide this possibility, to copy some random text from text only terminal window without mouse?
in few words - I have only text terminal, and bunch of lines on it, is it possible just move cursor to some random line and copy text from it without mouse?

---

### Post by SeijiSensei on 2020-03-27
Most terminal programs support highlighting the text with a mouse, right-clicking, then using copy/paste to copy the on-screen text.

---

### Post by sudodus on 2020-03-27
[This link](https://askubuntu.com/questions/961175/copy-and-paste-doesnt-work-in-the-terminal/961226#961226) with two alternatives may help you get started.

---

### Post by TheFu on 2020-03-27
i usually send the command output both to the screen AND to a file, then edit the file to get the data needed, then scp the file to a normal Linux desktop for use as needed.   99.99999999% of the the time, i avoid using consoles for the lack in select-paste.  Always prefer using ssh connections.  it is just like being there almost always.

For example:
```
$ lsblk | tee /tmp/log
```
if you need some remedial redirection-fu tutorials, find any basic bash or CLi linux book ... or search for "the art of the command line" - there's a github gist/page about it.

BTW, that example can be modified w/ sudo to create/append to an existing system file quickly.
```
$ echo "127.0.0.1   facebook.com  google.com  twitter.com" | sudo  tee -a /etc/hosts 
```
That can drastically reduce privacy problems for a desktop.

---

### Post by Holger_Gehrke on 2020-03-28
By default there is no copy and paste in the virtual consoles. If you have a mouse connected to the machine, gpm (general purpose mouse) provides that capability. 

Otherwise you can use a terminal-multiplexer like screen or tmux. These work like a window manager for a terminal. 

In screen 'ctrl-a Esc' starts copy-mode. You can move the cursor and use space to mark the beginning and end of the text to copy. After that 'ctrl-a ]' inserts the copied text.

Holger

---

