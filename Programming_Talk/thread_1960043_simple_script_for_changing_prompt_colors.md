---
title: "simple script for changing prompt colors"
date: 2012-04-16
forum: Programming Talk
---

### Post by RedEyes101 on 2012-04-16
Hello, I'm a newb to the whole ubuntu but I wish I haad learned about this a long time ago. So heres my scenario and question. I'm trying to make a simple menu in the bash shell using gedit that allows me to select the back ground colors of the screen and to pick different variable for the prompt. One such variable is the changing of the prompt color. I've found this command 

[COLOR=#800080][B]PS1='${debian_chroot:+($debian_chroot)}\[\033[01;36m\]\u[COLOR=#ff0000]\[\033[01;31m\][/COLOR]@[COLOR=#ff0000]\[\033[01;36m\][/COLOR]\h\[\033[01;33m\]:\[\033[01;31m\]\w\[\033[01;33m\]\$ '

that allows me to do it. It works fine when I type it in the normal terminal window but when I try to make a script for it, it doesn't work. By any chance, is there something special I need to do it?

Thanks for your help!
[/B][/COLOR]

---

### Post by sisco311 on 2012-04-17
You have to run your script in the current shell:```
. path/to/script
```

---

### Post by VCoolio on 2012-04-17
A script runs in a subshell and changes the prompt there; in your current shell it doesn't have effect. So source the script like indicated above, or forget about a script and write a function in .bashrc:```
setprompt () {
export PS1='${debian_chroot:+($debian_chroot)}\[\033[01;36m\]\u\[\033[01;31m\]@\[\033[01;36m\]\h\[\033[01;33m\]:\[\033[01;31m\]\w\[\033[01;33m\]\$ '
}
```
Now run 'setprompt' (after editing .bashrc, source it or open a new shell) and done.

---

### Post by RedEyes101 on 2012-04-18
Thanks guys I'm going to give it a try. I'll get back to you if I have problems.

---

