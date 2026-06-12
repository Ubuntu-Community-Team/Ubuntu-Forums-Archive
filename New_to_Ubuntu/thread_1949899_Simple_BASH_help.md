---
title: "Simple BASH help"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by ubunbu on 2012-03-31
I need some basic scripting help

I have the terminal set as a startup program, but I'd like to make a  script to use instead that opens the terminal, then does some basic  things. For instance,

I tried 

#!/bin/bash
gnome-terminal

echo "Hello ..."

---

### Post by sudodus on 2012-03-31
It is very easy to open a terminal window: press ***ctrl + alt + t*** (at the same time), so you need no script for that.

But it is a good idea to learn the scripting language ***bash*** :-)

Have a look at the following link: [http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

---

### Post by ubunbu on 2012-03-31
No I know how to open a terminal.

Right now I have a terminal set to a startup program.

Instead of just opening I wanted to make it do something on startup. 

So , for instance, I set the bash script as the starup program and the script opens the terminal and then begins to do things like say "Hello"

---

### Post by santosh83 on 2012-03-31
> **ubunbu said:**
> No I know how to open a terminal.

Right now I have a terminal set to a startup program.

Instead of just opening I wanted to make it do something on startup. 

So , for instance, I set the bash script as the starup program and the script opens the terminal and then begins to do things like say "Hello"

Once you start a terminal program from within a bash script, it'll launch as a separate process, and whatever you do later-on will still be within the script itself.

If you want to routinely run one or more commands each time a terminal is started, you can add the lines to your local .bashrc. It will get executed each time you start a bash shell, though you can use tests to skip over when called non-interactively.

---

### Post by sudodus on 2012-03-31
> **ubunbu said:**
> No I know how to open a terminal.

Right now I have a terminal set to a startup program.

Instead of just opening I wanted to make it do something on startup. 

So , for instance, I set the bash script as the starup program and the script opens the terminal and then begins to do things like say "Hello"
Put the content in the two first square boxes into an editor and create the script files[FONT=Courier New][SIZE=3] t1[/SIZE][/FONT] and[FONT=Courier New][SIZE=3] t2[/SIZE][/FONT] in a directory [FONT=Courier New][SIZE=3]test[/SIZE][/FONT]
```
#!/bin/bash

xterm -e ./t2 Hello World

``````
#!/bin/bash

ans=""
echo "$*"
echo "quit with q"
while [ "$ans" != "q" ]
do
 read -sn 1 ans
done
```Make them executable with
```
chmod +x t1 t2
```And then you can run something like you might want with either of the commands
```
./t1
``` or
```
bash t1
```

---

### Post by ubunbu on 2012-03-31
thank you!

---

### Post by sudodus on 2012-03-31
> **ubunbu said:**
> thank you!
You are welcome. If this solves your problem, please click [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page to mark this thread as SOLVED :-)

---

