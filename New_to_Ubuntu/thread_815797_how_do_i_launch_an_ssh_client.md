---
title: "how do i launch an ssh client?"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by srossnz on 2008-06-02
i need an ssh client or terminal i went to synaptic to see if i could find one, it says i have them installed already but see no menu item for one.  Synaptic really should list how to launch these apps.. it's a bit like "hey you have this app! being a noob we will not tell you how to run it lolz!!"  o_O

---

### Post by tomcheng76 on 2008-06-02
open up gnome-terminal (your console)
type
> 
ssh [email]username@yourhost.com[/email]
for example
ssh srossnz@192.168.0.18

then enter your password

---

### Post by Rocket2DMn on 2008-06-02
SSH is built into linux, you just run
```
ssh <server>
```
There are other options like
```
ssh user@server
ssh <server> -l <user>
```
See the man pages for more details
```
man ssh
```

---

### Post by sdennie on 2008-06-02
You should be able to ssh somewhere with:

```

ssh some_where

```

When installing a package doesn't give a menu item, the following should tell you what binaries you've installed:

For example:
```

dpkg -L openssh-client | grep bin/

```

---

### Post by iansane on 2008-06-02
I know how you feel. It would be nice if synaptic developers made sure all of the packages include better documentation but they are from different development branches.

I have putty ssh and remote desktop installed and they are both under Applications>internet. the command for putty is "putty" in terminal.

LOL get this. The command for remote desktop is "vinagre" ??? 

Why not "remote-desktop"? ...nah that would be crasy and make no sense ;-)

remote desktop is cool though. It looks like MS terminal server if your used to that.

Putty works great for SSH

---

### Post by iansane on 2008-06-02
nothing wrong with using one of the ones I named, with a GUI instead of all that terminal typing.

But it's good stuff to learn :-)

My mistake. The remote desktop client is called vinagre in synaptic. I just found it under remote desktop in Add/Remove programs.

still think remote-desktop would be better for a command.:-)

---

