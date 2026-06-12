---
title: "Where is the path of Trash Can?"
date: 2014-11-21
forum: New to Ubuntu
---

### Post by flaymond on 2014-11-21
Hey, I got 'root' file in trash....I can't delete it nor restore it......I can't view the file/trash can using nautilus (sudo nautilus .)


when i open trash can...it only show the short path...trash:///folder


I don't know what or where is the real path for Trash Can on Lubuntu...

I want to delete it....


I need to delete it as sudo on Terminal

---

### Post by flaymond on 2014-11-21
ahh...figured it by myself...sorry....here is the code to delete root file in Trash Can via Terminal...


```
cd ~/.local/share/Trash  
```

```
ls files
```

```
sudo rm -fr ~/.local/share/Trash/files/* # your folder or files to delete
```

Done!


**Take special care when removing files/folders as root, it is  easy to  trash an install with that command used wrongly. Always double check  the path  and ESPECIALLY when using wildcards such as "*"**. 


****
* Its a very dangerous command if you not careful with it...again..PLEASE CHECK THE PATH to make sure its a correct path or you will damaged and you will probably deleted your very important files if you misused it !!

---

