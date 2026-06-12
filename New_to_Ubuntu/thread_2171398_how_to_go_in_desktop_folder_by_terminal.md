---
title: "how to go in desktop folder by terminal?"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by amit_samanta on 2013-08-30
in my desktop i have a folder.when i type this command on terminal "cd folder_name".iit shows that:there is no such directory.
please help me.
and how to open a hard drive through terminal?
kindly help me

---

### Post by mamamia88 on 2013-08-30
Are you using the full path?   If not try that.  And if the folder has spaces you need to surround it by quotation marks.

---

### Post by deadflowr on 2013-08-30
As it should be clear cd means change directory.
It'll only change into existing directories and folders.
Make sure the spelling you use is correct.
You can do this with the ls command to determine the correct spelling.

---

### Post by Maheriano on 2013-08-30
> **amit_samanta said:**
> in my desktop i have a folder.when i type this command on terminal "cd folder_name".iit shows that:there is no such directory.
please help me.
and how to open a hard drive through terminal?
kindly help me

Directories are case sensitive, make sure you're using the correct cases. Also if the directory has spaces, you need to escape them. You can type "ls" to list all the files in your directory so make sure it's even listed there before you try to change into it. If it is, you can also type the first couple of letters of the directory, then hit TAB and it'll complete it for you.

---

### Post by whitesmith on 2013-08-30
Copy and paste this in your terminal: ```
cd ~
``` Then repeat for this in the same terminal:```
 ls -la
``` This shows all folders in your home directory. Then just cd to the right one.

---

### Post by su:bhatta on 2013-08-30
Did you get it done? you have to give the full path, e.g.
```

cd /usr/local/src 
or
cd /home/"username"/Documents
```

replace "username" with your own user name and "Documents" with the folder name you want, remember about spellings and  case-sensitiveness.

---

### Post by amit_samanta on 2013-08-30
thanks..
but after going to desktop by cd command there is a folder name"a".how to open that?

---

### Post by su:bhatta on 2013-08-30
Do you want to open the folder "a" or some file like a word file which is located in "a" ?

---

### Post by amit_samanta on 2013-08-30
in desktop a folder has a name"a" and in that there is a logic.sh file.

---

### Post by su:bhatta on 2013-08-30
Now that is an executable file if i am not mistaken!
If you simply want to open the script you can do gedit /home/"username"/a/logic.sh

If you want to run logic.sh I Can't be of help there...:)

Suggest googling it a bit... or wait for someone who knows better to answer .

---

### Post by eternal243 on 2013-08-30
> **amit_samanta said:**
> in desktop a folder has a name"a" and in that there is a logic.sh file.

to run a shell-script you need to cd to the directory where it is located

assuming if it is in your desktop/a folder you would do it like this, but remember that foldernames and filenames are case sensitive:
```

cd /home/username/desktop/a
./logic.sh
```

---

### Post by Jonathan Precise on 2013-08-30
> **amit_samanta said:**
> in my desktop i have a folder.when i type this command on terminal "cd folder_name". It shows that:there is no such directory.
please help me.
and how to open a hard drive through terminal?
kindly help me

Try:```
cd
cd Desktop/
```

That should fix it!

---

### Post by nerdtron on 2013-08-30
```
[COLOR=#000000][FONT=Ubuntu Mono]cd /home/username/desktop/a
[/FONT][/COLOR]./logic.sh 
```

This is good. But be sure that the file logic.sh is executable. If not,
```
[COLOR=#000000][FONT=Ubuntu Mono]cd /home/username/desktop/a
[/FONT][/COLOR]bash logic.sh 
```

Oh, and be careful on what you are executing scripts. Do you know what this file contains or do you know what it will do?

---

### Post by Jonathan Precise on 2013-08-31
> **nerdtron said:**
> ```
[COLOR=#000000][FONT=Ubuntu Mono]cd /home/username/desktop/a
[/FONT][/COLOR]./logic.sh 
```

This is good. But be sure that the file logic.sh is executable. If not,
```
[COLOR=#000000][FONT=Ubuntu Mono]cd /home/username/desktop/a
[/FONT][/COLOR]bash logic.sh 
```

Oh, and be careful on what you are executing scripts. Do you know what this file contains or do you know what it will do?

He's right. **_DO NOT RUN/EXECUTE SCRIPTS IF YOU DO NOT KNOW WHAT IT EXECUTES, OR IF YOU DO NOT KNOW/TRUST THE PUBLISHER!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!_**:!: Only run a script when strictly necessary!

---

### Post by fadhil-hakadir on 2013-09-01
hi, have you solved the problem?

if you'd like to run it, maybe this could help:
askubuntu.com/questions/38661/how-do-i-run-sh-files-in-terminal

its an old fix, but should still work:
chmod +x ~/Desktop/a/logic.sh
bash ~/Desktop/a/logic.sh

hope it helps

---

### Post by dhunt84971 on 2013-09-01
I believe once you have entered the folder from the terminal you should be able to run the script using ```
sh logic.sh
```

Duh! I see that this was already answered.  Please disregard.

---

### Post by Crusty Old Fart on 2013-09-01
Now that you know where "logic.sh" is located, if it is executable you can run it from any directory with the following command:
```

/home/username/Desktop/a/logic.sh

```
if you need to make it executable, the following command will do it from anywhere:
```

chmod 755 /home/username/Desktop/a/logic.sh

```

---

