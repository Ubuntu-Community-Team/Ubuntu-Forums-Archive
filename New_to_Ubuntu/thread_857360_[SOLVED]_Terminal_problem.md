---
title: "[SOLVED] Terminal problem"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Toliot on 2008-07-12
hey,
whenever terminal asks for pass:
i cant type...but i can press enter and it says incorrect password
and terminal doesnt let me creat folders...mkdir...
is there a way to fix this?:confused:
thx in advance

---

### Post by drs305 on 2008-07-12
> **Toliot said:**
> hey,
whenever terminal asks for pass:
i cant type...but i can press enter and it says incorrect password
and terminal doesnt let me creat folders...mkdir...
is there a way to fix this?:confused:
thx in advance

Ubuntu won't show your password as you type but it is being registered. Just type your login password and hit enter. It will 'take' assuming you have administrator access.

---

### Post by scragar on 2008-07-12
the terminal just doesn't show what your typing when it asks for your password, it's an extra layer of security to stop people seeing how long your password is.

mkdir has the syntax:
```
mkdir **DIR name**
```
adding a left slash(**\**) before any spaces to avoid problems with them.

---

### Post by tibellus on 2008-07-12
> and terminal doesnt let me creat folders...mkdir...
is there a way to fix this

Where are you trying to create a directory? If you're trying to create one in a folder where you don't have write permission as a normal user (like /usr/share), this won't work. As drs305 said, just type your password when you're asked and press Enter. This is a way to hide the password from some bad guy who's looking over your shoulder :)

---

### Post by Toliot on 2008-07-12
Thx guys!!
i got it to work
im the only user on the computer so that makes me admin right ?:confused:

---

### Post by Toliot on 2008-07-12
> **tibellus said:**
> Where are you trying to create a directory? If you're trying to create one in a folder where you don't have write permission as a normal user (like /usr/share), this won't work. As drs305 said, just type your password when you're asked and press Enter. This is a way to hide the password from some bad guy who's looking over your shoulder :)

i was trying to create it in a hidden file but i forgot to ls -a is that why it didnt let me ?

---

### Post by drs305 on 2008-07-12
> **Toliot said:**
> Thx guys!!
i got it to work
im the only user on the computer so that makes me admin right ?:confused:

Yes. The first user is automatically placed in the 'admin' group.

> 
i was trying to create it in a hidden file but i forgot to ls -a is that why it didnt let me ?

"ls -a" is only a command to show you a list of files, including hidden ones. Normally the only place you can create a file or folder without administrator privileges (sudo) is in your own home folder.

When you have your questions regarding this subject answered, please mark the thread solved using the "Thread Tools" link at the top right of the first post.

---

### Post by Toliot on 2008-07-12
> **drs305 said:**
> Yes. The first user is automatically placed in the 'admin' group.



"ls -a" is only a command to show you a list of files, including hidden ones. Normally the only place you can create a file or folder without administrator privileges (sudo) is in your own home folder.

When you have your questions regarding this subject answered, please mark the thread solved using the "Thread Tools" link at the top right of the first post.
ok thx for all the help :)

---

