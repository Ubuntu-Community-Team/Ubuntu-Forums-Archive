---
title: "copied a folder into it self how do i permenantly delete it"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Kedster on 2008-05-11
ut i just came upon somthin really displeasing, a few weeks ago (in pure stupidity) i accidentally copied a folder into it self and well it wont let me delete it and i was wondering if there is a way (in cl or gui) to delete it it u don't understand say so and ill try to describe better what is wrong

---

### Post by ctswhole on 2008-05-11
I'm not sure if I follow you correctly, but you could check your permission on the folder by right clicking it and going to "Properties".  From there click on the "Permissions" tab and see if there are any settings there holding you back.

---

### Post by Kedster on 2008-05-11
ok what i did was i copied a folder in to it self so now inside the folder is the same folder and so on it goes on like for 600 times 
 umm like its not permissions it  that like the lolder has tomany subfolder i think and well  dont no nut its really hard

---

### Post by ctswhole on 2008-05-11
> **Kedster said:**
> ok what i did was i copied a folder in to it self so now inside the folder is the same folder and so on it goes on like for 600 times 
 umm like its not permissions it  that like the lolder has tomany subfolder i think and well  dont no nut its really hard

Ok, maybe try this and see if it works...

Go to the last instance of that multiple folder and copy and paste it somewhere else.  Then from the command line try to delete the origins of the folder and all it's subdirectories.  I think the command would go something like this:

```
rm -rf /home/user/badfolder
```

After that, move the folder you copied and pasted back to it's original place.

---

### Post by bobnutfield on 2008-05-11
Make ABSOLUTELY SURE that you have copied what you want to keep from that directory into another directory and from the command line:

> rmdir --ignore-fail-on-non-empty <nameofdirectory>

REMEMBER, THIS IS GOING TO DELETE THE DIRECTORY AND ITS ENTIRE CONTENTS!

This will get rid of your problem, but don't make a mistake and delete something you want.

Hope this helps

Bob

---

### Post by drs305 on 2008-05-11
In terminal, you can use the 'rm -R' command to delete a folder and all the folders below it, but BE CAREFUL. This is a powerful command and you have to make sure you are starting at the correct point.

The safest thing is for you to tell us the location of the first/top folder you want to delete and we can give you the correct syntax.  DO NOT LET ANYONE TELL YOU TO 'rm -R /' which would wipe out your system!

---

### Post by Kedster on 2008-05-11
id post the error but i dont have my comp handy sorry

---

### Post by Kedster on 2008-05-12
/home/kedster/.local/share/Trash/files/Public
 thats the folder i want gone 


 the thing that happend is that it looks like this
/home/kedster/.local/share/Trash/files/Public/Public/Public/Public/Public/Public/Public/Public/Public/Public/Public/Public/Public/Public/Public/Public


and that og on for ever like really i doesnt stop

---

### Post by Bodsda on 2008-05-12
this command should sort it out

```
 sudo rm -rf /home/kedster/.local/share/Trash/files/Public 
```

make sure Public folder is with a capital 'P' not a little 'p'

---

### Post by Kedster on 2008-05-12
thanks hat worked really well
```
sudo rm -rf /home/kedster/.local/share/Trash/files/Public
```

whats this part do if u dont mind me asking
>  -rf 

---

### Post by inportb on 2008-05-12
Recursive, force/silent.

---

