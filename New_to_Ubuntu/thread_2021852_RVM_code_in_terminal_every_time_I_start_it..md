---
title: "RVM code in terminal every time I start it."
date: 2012-07-09
forum: New to Ubuntu
---

### Post by ebonygeek45 on 2012-07-09
I am trying to get into Ruby and later Ruby on rails. I am very new to Xubuntu as well.  Problem is that being used to Windows installing things...I am still getting used to the way Xubuntu does it. 

I still took on trying to install Ruby on rails. I am still not sure if the RVM was installed, Ruby seem to be fine, Rails I am not so sure about. 

Every time I pull up terminal now it comes up with code for RVM. It seems to be embedded somehow. I tried to figure out what the problem is and just can not. Researching it on the internet shows no results. I tried to reset...I tried reset and clear. 

Also do anyone know where I can download the Irb terminal.  Or is that just something that comes with windows. I look like the regular command prompt terminal but has the Irb icon on it. 

Do anyone know how to stop this from happening? 

The code that runs automatically whenever I pull up terminal is;

```

bash: /home/ebonygeek45/.
rvm/scripts/rvm: No such file or directory

$rvm_path (/usr/share/ruby-rvm) does not exist.rvm_is_a_shell_function: command not found
__rvm_teardown: command not found
ebonygeek45@sd45-Aspire-one:~$ 


```

---

### Post by papibe on 2012-07-09
Hi ebonygeek45.

That is a typical behaviour when either you or another program made a custom modification to one of the Bash start up files.

Let's start with your ~/.bashrc, and check if there are any custom code there. Could you post the result of this command?
```
diff ~/.bashrc  /etc/skel/.bashrc 

```
Regards.

---

### Post by ebonygeek45 on 2012-07-09
Ashamed to say but it could have been me. Just had such a hard time with the install in general. Still learning I'm afraid.  Thank you for getting back to me. 

Here is my results.

```
ebonygeek45@sd45-Aspire-one:~$ diff ~/.bashrc  /etc/skel/.bashrc
108,112d107
< 
< PATH=$PATH:$HOME/.rvm/bin # Add RVM to PATH for scripting
< [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.
< rvm/scripts/rvm"
< [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"

```

---

### Post by ebonygeek45 on 2012-07-10
Anyone have an idea if this maybe a problem because I didn't install RVM right. Or is it a system problem?

---

### Post by papibe on 2012-07-10
The first error you are getting is because you have a split line. Then you have a repeated line.

Edit it so it looks like this:
```
PATH="$PATH":"$HOME"/.rvm/bin # Add RVM to PATH for scripting
[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"
```
Tell us how it goes.
Regards

---

