---
title: "Help with &quot;foruser1&quot; in root"
date: 2015-01-30
forum: New to Ubuntu
---

### Post by Juan_Caba on 2015-01-30
Hi Ubuntu Forums community,

I'm taking up a Linux class online. I have been having trouble with accessing the 'foruser1' directory in root. The command line says it doesn't exist but it does in the home. When I right on the directory, it says that I'm not the owner. Although, I'm the admin with all rights. 

I need help on this. I'm trying to do "cd /foruser1" command line for an assignment. I uploaded three screenshots.

---

### Post by steeldriver on 2015-01-30
The command line **does not** say that directory [FONT=courier new]foruser1[/FONT] doesn't exist, it says that directory [FONT=courier new][COLOR=#FF0000]**/**[/COLOR]foruser1[/FONT] does not exist: they are different things.

Directory [FONT=courier new]foruser1[/FONT] expresses a relative path - relative to the current directory; whereas [FONT=courier new]/foruser1[/FONT] expresses an absolute path i.e. a  directory called foruser1 in the root directory of the filesystem.

---

### Post by grahammechanical on 2015-01-30
When we install Ubuntu we are asked to select a user name and password. Then when we login to Ubuntu our user password will allow us to login. With Ubuntu we are both a standard user and an administrator. Most of the time we work as a standard user but when we need to do some action that requires administrator authorisation we are ask to put in our password to authenticate the action. For that task and for a limited period afterward we are working as an administrator. Then we revert to being a standard user again.

If you created the *foruser1* folder as a standard user you would be able to access the folder. But if you created it as administrator or root (to use a Linux term) then when you reverted back to being a standard user you will indeed not be the owner of that folder and will not have permission to write to that folder.

Try, in a terminal
```
ls
```

that will list all the files and folders in the /home/your username folder or directory. Then try

```
cd foruser1
```

Does that get you into the folder? It should get you inside the folder but you will not have permission to edit files inside the folder or even paste a file into the folder. If my understanding is correct.

Regards.

---

### Post by oldos2er on 2015-01-30
Moved to New to Ubuntu.

---

