---
title: "Folder permissions changed automatically"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by coolbud012 on 2013-03-04
[COLOR=#333333][FONT=Ubuntu Beta]Hey guys first of all I searched a lot on this site but didnt get any exact answer to my questions. Dont know something happened automatically and all the folders permissions changed automatically and there came a lock icon on all of my folders and files. Then I searched on this site and got the solution as this command[/FONT][/COLOR]

sudo chown 777 -R $USER:$USER $HOME[COLOR=#333333][FONT=Ubuntu Beta]It solved my problem half way, it removed the lock icon but now all folders permissions are read only so please guide me how to reset all the folder permissions as it was previously?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I'm using ubuntu 12.10[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Thanks[/FONT][/COLOR]

---

### Post by schragge on 2013-03-04
```

sudo chown 777 -R $USER:$USER $HOME

```This command looks wrong. You're mixing *chmod* and *chown* syntax here. I suppose what you've meant is

```

sudo chown -R $USER: $HOME
[COLOR=#ff0000]chmod -R 777 $HOME[/COLOR]

```Still, I advise you against running [COLOR=#ff0000]the second[/COLOR] command: although it'll give you full access to all your files, it also will make them all executable and world-writeable in the process. Instead, try this
```
chmod -R ug+rwX ~
```This will give the owner and group members read and write access plus make directories searcheable and retain execute bit on files that already have it set.

---

### Post by slickymaster on 2013-03-04
Assuming that you are referring to your home directory, you can:
```
find ~ -type d -exec chmod u+rwx \{\} \;
```
Note that this will only work for folders, not files, and will set the read, write and execute permissions for the owner of the directory.

---

### Post by Impavidus on 2013-03-04
```
chmod -R u=rwX $HOME
```

---

### Post by Lisiano on 2013-03-04
If you want to set your home directory to Read/Write for you and NOT for everyone else (Other users on the system), run this command
```
chmod -R u=rwX,g=rX,o= $HOME
```

---

