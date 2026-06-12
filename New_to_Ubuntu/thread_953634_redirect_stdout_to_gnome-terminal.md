---
title: "redirect stdout to gnome-terminal"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-10-20
I'm trying to execute a command whereby zenity gives me a list and when I select something, the selection is executed as an argument to gnome-terminal -x $foo

My question is: how do I do this?

I have tried
```

cd /home/user/.rsync/Profiles
look=` ls | sed 's/\~//' | sort -u`
echo $look
for **** in $look; do
files=` echo $files | sed '$a'$****''`
done
profile=` zenity --list --text="Select Profile To Run" --column="Profile" $files`
cd /home/user/.rsync/Profiles
cmd=` cat $profile`
eval /usr/bin/gnome-terminal --execute=$cmd
```

and other slightly varied versions but I can't get the output to go to a terminal.

---

### Post by unutbu on 2008-10-20
```


#!/bin/sh 
profile=$(zenity --list --text="Select Profile To Run" --column="Profile" $files)
gnome-terminal -x bash -c "cat $profile; read -n1"

```

---

### Post by JohnGalt131 on 2008-10-20
> **unutbu said:**
> ```


#!/bin/sh 
profile=$(zenity --list --text="Select Profile To Run" --column="Profile" $files)
gnome-terminal -x bash -c "cat $profile; read -n1"

```


That worked. Almost. I modified it to 
```
#!/bin/sh 
profile=$(zenity --list --text="Select Profile To Run" --column="Profile" $files)
gnome-terminal -x bash $profile
```
You answered the part I was stuck on.
Thanks

---

