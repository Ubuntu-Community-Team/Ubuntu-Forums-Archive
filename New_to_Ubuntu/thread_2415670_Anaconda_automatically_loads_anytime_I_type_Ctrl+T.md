---
title: "Anaconda automatically loads anytime I type Ctrl+T"
date: 2019-03-29
forum: New to Ubuntu
---

### Post by santimirandarp on 2019-03-29
Hi everyone!

I've installed anaconda software following the normal installation guide which is on anaconda's site ([https://docs.anaconda.com/anaconda/install/linux/](https://docs.anaconda.com/anaconda/install/linux/)). I've installed the most updated 64 bits Linux version on ubuntu 18.04. Everything went well but then, anytime I open up a terminal I get:

```
(base) x@y:
```

Would you please help me?

---

### Post by Impavidus on 2019-03-29
The installer may have left some (buggy) lines in your .bashrc, causing anaconda to start automatically when you start a shell. Check your .bashrc.

---

### Post by santimirandarp on 2019-03-29
> **Impavidus said:**
> The installer may have left some (buggy) lines in your .bashrc, causing anaconda to start automatically when you start a shell. Check your .bashrc.

I dont think I'm able to edit this:
```

__conda_setup="$(CONDA_REPORT_ERRORS=false '/home/santi/anaconda3/bin/conda' shell.bash hook 2> /dev/null)"
if [ $? -eq 0 ]; then
    \eval "$__conda_setup"
else
    if [ -f "/home/santi/anaconda3/etc/profile.d/conda.sh" ]; then
        . "/home/santi/anaconda3/etc/profile.d/conda.sh"
        CONDA_CHANGEPS1=false conda activate base
    else
        \export PATH="/home/santi/anaconda3/bin:$PATH"
    fi
fi
unset __conda_setup
```

---

### Post by santimirandarp on 2019-03-29
I've removed the lines (assuming everything written in bashrc is loaded when the terminal is popped up). If it is correct I'll add the SOLVED. I appreciatte your help and any extra comment will be welcome.

---

### Post by santimirandarp on 2019-03-29
I think it is wrong because now when type 'conda' the program doesnt respond :(

---

### Post by Impavidus on 2019-03-29
When you open a terminal (the program that allows text-based I/O), the bash shell is started (the program that shows a prompt and processes command lines up to the point of actually calling some program). When the bash shell is started, it loads .bashrc. So, yes, removing those lines should get the terminal working again. However, the installer put those lines there for a reason, so with those lines removed, anaconda may not work as intended. I don't know anaconda, so I can't debug that code.

---

### Post by monkeybrain20122 on 2019-03-29
You only need one line in your .bashrc
```
export PATH="$PATH:/home/santi/anaconda3/bin"
```

You can start conda in the terminal with a command like (conda allows different environments so you may put some names after "activate")
```
conda activate 
```


If you allow anaconda's installer to write to your .bashrc, it would put $PATH in the end (see the script quoted in your post)  so if there are different versions of the same thing (e.g python) in the system the conda version would take precedence and that may interfere with the proper functioning of your system.

---

