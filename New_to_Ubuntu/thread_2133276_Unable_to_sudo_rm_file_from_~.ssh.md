---
title: "Unable to sudo rm file from ~/.ssh"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by Hadaka on 2013-04-07
Hi, i just installed ssh server on a couple machines and was setting up
key auth. via a tutorial, i some how included a [ " ] at the end of the file name.
I am unable to remove it...any suggestions.?
Directory:
[EMAIL="hadaka@the-beach:~/.ssh"]#hadaka@the-beach:~/.ssh[/EMAIL]$ ls
authorized_keys”  config  id_dsa  id_dsa.pub  known_hosts

this was the formatt
```
 cat ~/.ssh/id_dsa.pub | ssh **hostname** “cat >> ~/.ssh/authorized_keys”
```
result of trying to remove without the [ " ]
```
~/.ssh$ sudo rm authorized_keys
rm: cannot remove `authorized_keys': No such file or directory
 
```
when i include the quote (") it seems to start a process as it returns a 
>
```
hadaka@the-beach:~/.ssh$ sudo rm authorized_keys"
> 
 
```
only way to recover the terminal is to ctrl/c
and when i close the terminal...it says a process is running.
do i need a big hammer and a trash can or is this removable??

---

### Post by conradin on 2013-04-07
can you show me ls -l of the file and tell use the $PWD varaible to the loaction for the file you want to remove?

I just tried a similar example to your condition, I added a " at the >
and it terminated properly.  >"
rm has a -f force option, but the file does not exit is confusing.
can you try typing the firstpart of the file name then hitting tab to complete the filename?

---

### Post by Hadaka on 2013-04-07
@conradin..thanks for responding.
seems the threat of the hammer and trash can did the trick.
or..maybe it was
```
sudo service ssh stop
```
not sure..but by magic smoke and mirrors when i gave it
another rm command...it vanished....
```
hadaka@the-beach:~/.ssh$ sudo rm authorized_keys&#8221;
[sudo] password for hadaka: 
hadaka@the-beach:~/.ssh$ ls
config  id_dsa  id_dsa.pub  known_hosts
 
```
weird...
thanks again.
**thread tools seems to not be working...not able to mark SOLVED**

---

### Post by Cheesemill on 2013-04-07
You probably need to escape the quotation marks so bash ignores them...
```
rm authorized_keys\"
```

Or just use tab completion as conradin suggests...
```
rm auth<TAB>
```

---

