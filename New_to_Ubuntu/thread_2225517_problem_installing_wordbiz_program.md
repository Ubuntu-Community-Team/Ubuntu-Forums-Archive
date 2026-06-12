---
title: "problem installing wordbiz program"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by newblank25 on 2014-05-21
I downloaded the linux version of wordbiz(free internet scrabble club). I extracted files into a folder named Wordbiz which I placed on desktop.
I typed in the terminal cd /home/michael/desktop/wordbiz java -jar ./wordbiz.jar and I got this bash: cd: /home/michael/downloads/wordbiz: No such file or directorymichael@michael-p7-1456c:~$ . what did i do wrong? Thx for help.

---

### Post by llamabr on 2014-05-21
Don't forget to use the little # symbol above when you type code.

Post the output of:
```
ls /home/michael/Desktop/wordbiz*
```

Also, where did you find these instructions?

---

### Post by Impavidus on 2014-05-22
> **newblank25 said:**
> I downloaded the linux version of wordbiz(free internet scrabble club). I extracted files into a folder named **[COLOR=#ff0000]W[/COLOR]**ordbiz which I placed on desktop.
I typed in the terminal cd /home/michael/**[COLOR=#0000ff]desktop[/COLOR]**/**[COLOR=#ff0000]w[/COLOR]**ordbiz java -jar ./wordbiz.jar and I got this bash: cd: /home/michael/**[COLOR=#0000ff]downloads[/COLOR]**/wordbiz: No such file or directorymichael@michael-p7-1456c:~$ . what did i do wrong? Thx for help.
So is it in Wordbiz or in wordbiz? Linux is case sensitive. Also, is it in desktop or downloads? Which are by default called Desktop and Downloads, or your local translation.

---

### Post by grumblebum2 on 2014-05-22
If it's where you say it is...
```
cd ~/Desktop/WordBiz && java -jar wordbiz.jar
```

If fails, what does this give...
```
cd && find -iname "wordbiz.jar"
```

PS I downloaded WordBiz and it runs here.

---

### Post by newblank25 on 2014-05-22
this is what I got when using terminal
cd && find -iname "wordbiz.jar"
./Downloads/WordBiz/wordbiz.jar
./Desktop/wordbiz/wordbiz.jar
./.local/share/Trash/files/WordBiz/wordbiz.jar
michael@michael-p7-1456c:~$ 
 also this was showed up
michael@michael-p7-1456c:~$ ./Downloads/WordBiz/wordbiz.jar
bash: ./Downloads/WordBiz/wordbiz.jar: Permission denied


so what commands do I need to make it go? thx for help

---

### Post by Vladlenin5000 on 2014-05-22
You can start by making sure the jar file is executable (Right-click -> Properties **-> Permissions Tab**; select the **Execute** option if not selected already). If it doesn't run and outputs the same "permission denied" error then you need to run it with privileges, ie, with "sudo" before the last command.

---

### Post by newblank25 on 2014-05-22
I'll try that thx for info

---

### Post by grumblebum2 on 2014-05-22
Either of these should work...
From the original extracted folder [COLOR="#FF0000"]**W**[/COLOR]ordbiz...
```
java -jar ~/Downloads/[COLOR="#FF0000"]**W**[/COLOR]ordBiz/wordbiz.jar
```

or

if you copied the entire contents of  ~/Downloads/[COLOR="#FF0000"]**W**[/COLOR]ordBiz to ~/Desktop/[COLOR="#FF8C00"]**w**[/COLOR]ordbiz
```
java -jar ~/Desktop/[COLOR="#FF8C00"]**w**[/COLOR]ordbiz/wordbiz.jar
```

.....providing you have java installed of course.

---

### Post by newblank25 on 2014-05-23
a big thx to grumble man. the first code works & I can get into program. have a good holiday weekend

---

### Post by grumblebum2 on 2014-05-23
No problem.
Make yourself a **.desktop** launcher if you like.
[ATTACH=CONFIG]253406[/ATTACH]

Run...
```
gedit ~/.local/share/applications/wordbiz.desktop
```
and copy and paste in the following....
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Name=Wordbiz
Comment=Online scrabble
Exec=/usr/bin/java -jar '/home/michael/Downloads/WordBiz/wordbiz.jar'
Icon=/home/michael/Downloads/WordBiz/wordbiz.png
Categories=Game;
```
Save and close.

Download the **wordbiz.png.tar.gz** attachment below, extract and place wordbiz.png in **/home/michael/Downloads/WordBiz**

Type "wordbiz" in the dash and drag and drop to the launcher.

[SIZE=3]**or**[/SIZE]

If you want a Desktop shortcut, copy **wordbiz.desktop** to your Desktop. ...
```
cp ~/.local/share/applications/wordbiz.desktop ~/Desktop
``` 

When a  .desktop file is placed on the Desktop it needs to be made executable....
```
chmod +x ~/Desktop/wordbiz.desktop
```

---

