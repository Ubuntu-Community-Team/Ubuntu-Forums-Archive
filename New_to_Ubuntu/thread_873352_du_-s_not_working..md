---
title: "du -s not working."
date: 2008-07-28
forum: New to Ubuntu
---

### Post by Suilenroc on 2008-07-28
So I'm new to Ubuntu. You've probably gathered that by my being on this particular forum, though, so I'll skip the pre information. All that I really need to say is that I've been using this guide to learn how to use the shell/terminal in Ubuntu. In the guide, I'm currently learning how to create a simple shell script that will allow me to output my system information in an HTML file. However, there's a part in it that wants to show the information in my home directory. The command that was given in the guide was 

```
 
du -s /home/* | sort -nr

```

However, anything with 

```
 
du -s 

```

in it returns this error:

```


du: cannot read directory `./.dbus': Permission denied
2706936	.


```

So, does anyone know how to solve this? Thanks!

---

### Post by iaculallad on 2008-07-28
Try:

```
sudo du -s
```

---

### Post by cheetaux on 2008-07-28
I'm guessing that you have a directory called .dbus in your home directory that you do not have read permission on (you probably created it accidently)

Type
```
ls -la
```
and see if there is a directory named .dbus listed.

---

### Post by Suilenroc on 2008-07-28
I've tried running it with sudo, when I do that, it just tells me the same thing, but, instead of it being ./.dbus that it can't access, it's ./.gvfs. 

I've tried running it as root with the 
```
 su 
``` 

command. But even that doesn't work. When listed with ls -l, both of these files come up, and the owners are root.

---

### Post by jordanmthomas on 2008-07-28
I've actually had the same problem before, and root couldn't even delete the .gvfs directory.

It was strange, and I don't remember what I did to resolve it...at least you can rest assured you're not crazy.

---

### Post by Suilenroc on 2008-07-28
Hah, well, that's good. It's not like it's crippling, but it's strange. 

(Fun fact: my first thought when this happened was "virus." Then, I remember I wasn't on windows. :P )

---

### Post by cheetaux on 2008-07-28
Using sudo, try opening up the permissions on .dbus.  For example the following command will give the user, group, and other read-write-execute permission:

sudo chmod 777 .dbus

Then when you run du -s as, you should not get a permission error.

---

### Post by knightcoder on 2008-07-28
yeah, me with the same problems.
Logged in as root, I can read the .dbus directory. But not the .gvfs

Its the gnome virtual file system. And it shows owner as "??"

What does this mean ? I've not seen this before.

---

### Post by iaculallad on 2008-07-28
For more informations related to this problem, try reading the links below:

[Superuser cannot access ~/.gvfs folder when mounted]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/225361")
[Bug 534284 – Root user can not access .gvfs]("http://bugzilla.gnome.org/show_bug.cgi?id=534284")

---

### Post by Suilenroc on 2008-07-28
thanks, cheetaux, that allowed me to access ./.dbus. After I changed permissions in that, it told me that I couldn't acces dbus_sessions, a subdirectory of ./.dbus. I changed permissions in THAT, and now I can run du -s! Thanks for that. I had previously tried changing permissiosn, but I did so in Nautilus instead of the terminal, which didn't work for some reason. 

However, and this is what I think is strange, I can du -s as a user, but when I try to sudo it, it gives me the .gvfs message! When I try to change permissions on THAT, the access is denied.

---

