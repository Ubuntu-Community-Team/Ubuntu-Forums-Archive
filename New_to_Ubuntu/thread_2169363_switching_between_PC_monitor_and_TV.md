---
title: "switching between PC monitor and TV"
date: 2013-08-21
forum: New to Ubuntu
---

### Post by palmgrower on 2013-08-21
I know I can switch between PC monitor and TV with "disper -s" and "disper -S" in terminal. Is there a way to simplify the process of
1) click on ubuntu icon
2) type terminal
3) click on terminal
4) type disper -S

into one icon or fewer keyboard/mouse strokes? 
Thanks.

---

### Post by papibe on 2013-08-21
Hi palmgrower.

I see a couple of alternatives:
[LIST]
[*]Create a custom unity launcher icon: [Unity Launchers]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles"), or
[*]Creating a custom keyboard shortcut: open 'Keyboard' and switch to the 'Shortcuts' tab.
[/LIST]
Both would require you put your commands on a bash script. Example:
```
#!/bin/bash
disper -S ...

```
The script needs to have execution permissions:
```
chmod a+x /path/to/script.sh
```
Hope that helps. Let us know how it goes.
Regards.

---

### Post by palmgrower on 2013-08-22
keyboard > shortcut > custom shortcuts > +. I see 2 areas: NAME and COMMAND. For NAME, "pc to tv" For command, do I type "#!/bin/bash" and "disper -S"? Where do I add "chmod a+x /path/to/script.sh"? Thanks.

---

### Post by nerdtron on 2013-08-22
No. you should write a script for it.

Open the terminal. Do the following in order.
```
cd
```
```
nano disper.sh
```
This will open the Nano text editor and type the following.
```
#!/bin/bash
disper -S 
```

Press Ctrl+O to save and Ctrl+X to exit.
Then make the file executable.
```
chmod a+x disper.sh
```

Now go the Keyboard shortcut and put a NAME you want. In the COMMAND, put 
```
/home/yourusername/disper.sh
```
Bind it to your desired keyboard shortcut. 
Test your keyboard shortcut. :)

---

### Post by jhondoty on 2013-08-22
I too have same issue and looking for simple solution.

---

