---
title: "unable to run phyton"
date: 2021-05-11
forum: New to Ubuntu
---

### Post by mkamal-amohsin on 2021-05-11
Hi all,

i recently installed ubuntu 20.04 desktop on my laptop. Found out that I can't run any phyton command, says command not found.

mus@mus-ONYX-G:/etc$ phyton --version
bash: phyton: command not found
mus@mus-ONYX-G:/etc$ phyton2 --version
bash: phyton2: command not found
mus@mus-ONYX-G:/etc$ phyton3 --version
bash: phyton3: command not found
mus@mus-ONYX-G:/etc$ whereis phyton3
phyton3:
mus@mus-ONYX-G:/etc$ whereis phyton2
phyton2:
mus@mus-ONYX-G:/etc$ whereis phyton
phyton:
mus@mus-ONYX-G:/etc$ 

but checking /usr/bin phyton existed:

lrwxrwxrwx  1 root   root           16 Mei  11 15:45  python -> /usr/bin/python3
lrwxrwxrwx  1 root   root            9 Mac  13  2020  python2 -> python2.7
-rwxr-xr-x  1 root   root      3674216 Mac   8 21:02  python2.7
lrwxrwxrwx  1 root   root           33 Mac   8 21:02  python2.7-config -> x86_64-linux-gnu-python2.7-config
lrwxrwxrwx  1 root   root           16 Mac  13  2020  python2-config -> python2.7-config
lrwxrwxrwx  1 root   root            9 Mei  10 01:55  python3 -> python3.8
-rwxr-xr-x  1 root   root      5486384 Jan  27 23:41  python3.8

Running the same on Live usb also yields the same result. Anything that I'm missing?

---

### Post by Holger_Gehrke on 2021-05-11
Sadly the command line is strictly 'do what I say' (or rather 'type'), not 'do what I mean'. Typos like 'phyton' instead of 'python' (the 'h' comes after the 't', not after the 'p') will not be corrected automatically. Normally the 'command-not-found' handler of the shell should come up and print an educated guess about what you could have meant, but in this case it doesn't.

Holger

---

### Post by tea for one on 2021-05-11
You have transposed the **h** and **y** in python

[COLOR="#FF0000"]phyton[/COLOR] should be [COLOR="#FF0000"][COLOR="#0000FF"]python[/COLOR][/COLOR]

---

### Post by mkamal-amohsin on 2021-05-11
Thank you all for pointing this out. My ignorance amuses me.....](*,)](*,)](*,)

---

### Post by TheFu on 2021-05-11
> **mkamal-amohsin said:**
> Thank you all for pointing this out. My ignorance amuses me.....](*,)](*,)](*,)

And us, but you aren't the the first person to do this.  Learn to use "tab-completion" and most issues like this will not happen anymore.
[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) -- tab-completion is 1000x harder to explain in words than to show/demonstrate.  Type 2 characters for a command, then hit {tab}{tab}.

If there's only 1 command in the PATH that begins with those 2 characters, it will be filled in.  If there are more, a list of possible commands will be shown.

**In short, if you are typing more than 2 characters at a time+{tab}, then you are doing it the hard way.**

Most CLI tools have a bash-completion file so options to the command can also be completed ... or at least input files.  Look for videos to show this stuff and make it a habit to use.

---

### Post by ActionParsnip on 2021-05-11
Could make a symlink :lolflag:

---

### Post by TheFu on 2021-05-11
> **ActionParsnip said:**
> Could make a symlink 
or an alias
```
alias phyton='python'
```
but that would only work from bash in a shell, not inside scripts.

---

### Post by mkamal-amohsin on 2021-05-11
> **TheFu said:**
> And us, but you aren't the the first person to do this.  Learn to use "tab-completion" and most issues like this will not happen anymore.
[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) -- tab-completion is 1000x harder to explain in words than to show/demonstrate.  Type 2 characters for a command, then hit {tab}{tab}.

If there's only 1 command in the PATH that begins with those 2 characters, it will be filled in.  If there are more, a list of possible commands will be shown.

**In short, if you are typing more than 2 characters at a time+{tab}, then you are doing it the hard way.**

Most CLI tools have a bash-completion file so options to the command can also be completed ... or at least input files.  Look for videos to show this stuff and make it a habit to use.

Thanks for tip. Will remember that from now on :):)

---

### Post by him610 on 2021-05-11
> ...typing more than 2 characters at a time+{tab}, then you are doing it the hard way.
My system insists on doing it the hard way :)
```

~$ py<tab>
py3clean      py3versions   pydoc3.8      pygettext3.8  pyjwt3        python3.8
py3compile    pydoc3        pygettext3    pygmentize    python3       

```

```

~$ pyt<tab>

```
results in
```
 
$ python3  

```
Am I doing something wrong?

---

### Post by grahammechanical on 2021-05-11
Another tip regarding the terminal for those like myself who make typing errors. The terminal keeps a history of the commands we type. Pressing the up arrow key will scroll through them. The down arrow key will scroll the other way. Yes, we will see the wrongly typed commands  but also those commands that we type correctly. It can reduce the opportunity for mistyping of commands.

Regards

---

### Post by TheFu on 2021-05-11
> **him610 said:**
> Am I doing something wrong?

Probably not.  Python may not be installed on newer versions of Ubuntu. python 2 was deprecated and unsupported over a year ago. As you can imagine, python3 programs are different enough from python2 programs that having a "python" program when only python3 is available/supported would cause all sorts of problems.

In short, use python3

or

use something like **pyenv** to setup virtual python environments for each specific python version you need.  This is a best practice, BTW, if you are scripting in any scripting language where you can't or don't wish so use the exact version provided by the OS.

**[COLOR="#FF0000"]WARNING[/COLOR]**: NEVER, EVER, EVER, change the system version of a scripting language.  If you do, expect your system to start having faults and at the next boot - not to work.  You've been warned.  Only use apt update and apt upgrade/full-upgrade to get system versions of scripting languages updated.  You can do whatever you like inside a pyenv environment - go crazy.  I have 3 versions of perl in my development machine, for example. They are slightly different and each have a complete set of module dependencies required for my custom code.

---

