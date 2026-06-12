---
title: "can't remove remastersys folder from &quot;home&quot; &lt;SOLVED&gt;"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by al.adab on 2013-03-09
hello,

I have this remastersys folder I need to remove from /home/remastersys/ and I don't know how. Deleting doesn't work. Is there a specific terminal command I need to type in? I tried sudo chown -R XXX /home/remastersys/ but it didn't work (permission denied). Can you help? thanks.

---

### Post by ibjsb4 on 2013-03-09
Who is the owner of that folder?

try

```
sudo rm ~/remastersys
```

Just understand if that works, its gone forever.

---

### Post by al.adab on 2013-03-09
I suppose I am the owner - having administrator privilege. Here's what I get: 

[I]~$ sudo rm ~/remastersys
[sudo] password for daniele: 
rm: cannot remove `/home/daniele/remastersys': No such file or directory[/I]

Should I go for *sudo rm ~ /home/daniele/remastersys* instead? I'm irrationally afraid it's quite a risky thing to do...

---

### Post by ibjsb4 on 2013-03-09
That would be

```
sudo rm [I]/home/daniele/remastersys
```

It says no such file, check the spelling of that folder.  Maybe it Remastersys?

Also.  Right click on that folder and go to properties>permissions to see the owner.
[/I]

---

### Post by al.adab on 2013-03-09
properties>permissions: owner = root (root)

...'is a directory'?

[I]~$ sudo su
[sudo] password for daniele: 
root@T42:/home/daniele# sudo rm /home/daniele/remastersys
rm: cannot remove `/home/daniele/remastersys': No such file or directory
root@T42:/home/daniele# sudo rm /home/daniele/Remastersys
rm: cannot remove `/home/daniele/Remastersys': No such file or directory
root@T42:/home/daniele# sudo rm /home/remastersys
**rm: cannot remove `/home/remastersys': Is a directory**
root@T42:/home/daniele# [/I]

---

### Post by ibjsb4 on 2013-03-09
```
sudo rm -r /home/remastersys
```

---

### Post by al.adab on 2013-03-09
excellent, it worked! thank you so much!

---

