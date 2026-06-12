---
title: "cant save root crontab job"
date: 2020-12-29
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-29
running 20.04
okay what am i doing wrong
i run sudo crontab -e in terminal

sudo crontab -e
[sudo] password for ray: 
no crontab for root - using an empty one
889
however after i get job entered i get no option to save if i close the terminal
/tks

---

### Post by TheFu on 2020-12-29
Don't just close the terminal. 
You need to save the file and properly close the editor program.
The file must be in the correct command format or crontab sanity checks will refuse.  

How to save and close the editor is specific to the editor you use.  Normally, nano is the default edtor, yuck!  Don't just close the terminal.  o can choose a different editor t be used if you prefer.  export the EDITOR variable with the full-path to the alternate editor you'd prefer.

---

### Post by Paddy Landau on 2020-12-29
The default editor is, I think, nano. To save in nano, press Ctrl+X.

You can use a different editor. For example, if you prefer gedit (the default editor in Ubuntu 20.04), use this command:
```
sudo VISUAL=gedit crontab -e
```
The same goes if you want to edit your personal crontab.
```
VISUAL=gedit crontab -e
```
Note that you shouldn't have gedit already open when you use the above two commands, otherwise it could confuse crontab, and your changes will be lost.

**EDIT:**
TheFu mentioned using EDITOR (which you can indeed use instead of VISUAL), but your exported variable won't be carried over with sudo. Hence my suggested code.

---

### Post by rburkartjo on 2020-12-29
tks guys but still a little confused
can you give me an example of a saved crontab root job
learning appreciate it
i enter all my jobs using crontab -e using gedit
just trying to figure out how to save a root job

---

### Post by TheFu on 2020-12-29
Can you not use /etc/crontab or one of the /etc/cron.daily/ directories?

If you'd post the exact line(s) you are trying to put into the /var/spool/cron/... file, maybe the error will jump out?  There are different formats for each type.

---

### Post by ActionParsnip on 2020-12-29
the crontab is just a text file, you need to save the new file and close the editor for the crontab to updated

---

### Post by rburkartjo on 2020-12-29
tks ya'll problem was with the default conf of the program

---

### Post by TheFu on 2020-12-29
> **Paddy Landau said:**
>  
**EDIT:**
TheFu mentioned using EDITOR (which you can indeed use instead of VISUAL), but your exported variable won't be carried over with sudo. Hence my suggested code.

I didn't test my EDITOR answer and I think sudo settings prevent certain environment variables from being carried over.
This didn't work:
```
export EDITOR=geany
export VISUAL=geany
sudo crontab -e
```

Seems no matter what, those variables are ignored or blocked by sudo protections. Also tried without the "export=" for local. No joy. 

Since I purge nano as one of the first things on every new install, the settings revert to my preferred editor, vim.  Which has always worked with **crontab -e** or **sudo crontab -e**

According to the manpage for crontab, both VISUAL and EDITOR should be working.
```
       The  -e option is used to edit the current crontab using the editor specified by the **VISUAL**
       or **EDITOR** environment variables.  After you exit from the editor, the modified crontab will
       be  installed  automatically.  If neither of the environment variables is defined, then the
       default editor /usr/bin/editor is used.
```

```
$ ll /usr/bin/editor 
lrwxrwxrwx 1 root root 24 Jun 20  2020 /usr/bin/editor -> /etc/alternatives/editor*

$ ll /etc/alternatives/editor
lrwxrwxrwx 1 root root 18 Jun 20  2020 /etc/alternatives/editor -> /usr/bin/vim.basic*

```
which explains why vim is used, but not why the environment variables do not work as documented.  This is all on a 20.04 system. I would never have noticed any issue.

```
$ egrep EDITOR ~/.bash*
.bashrc:export EDITOR=/usr/bin/vi

``` could be interfering, I suppose.

---

### Post by yancek on 2020-12-29
When you first run crontab -e as a user or root you get the options shown below and you need to choose an editor.  Methods for saving files with nano or vim aren't the same as something like gedit so you will have to learn that.  I've always also used vi or vim for this purpose.

>  crontab -e
no crontab for don - using an empty one

Select an editor.  To change later, run 'select-editor'.
  1. /bin/nano        <---- easiest
  2. /usr/bin/vim.tiny
  3. /bin/ed

Choose 1-3 [1]: 2
No modification made


---

### Post by Paddy Landau on 2020-12-30
> **TheFu said:**
> Seems no matter what, those variables are ignored or blocked by sudo protections…
Correct. When you use sudo, a brand new environment is created. Only certain specific variables are passed across to sudo depending on how you use it.

Here is a little table that I drew up some time ago for my own use. It shows four different methods of invocation, and how each of four variables is affected.
```
Method  Variable   Set to       Example

sudo
        ${USER}    (target)     root
        ${HOME}    (unchanged)  /home/user
        ${PATH}    (target)     target user's path
        ${PWD}     (unchanged)  same folder

sudo -H
sudo --set-home
        ${USER}    (target)     root
        ${HOME}    (target)     /root
        ${PATH}    (target)     target user's path
        ${PWD}     (unchanged)  same folder

sudo su
        ${USER}    (target)     root
        ${HOME}    (target)     /root
        ${PATH}    (unchanged)  your path
        ${PWD}     (unchanged)  same folder

sudo -i
sudo --login
        ${USER}    (target)     root
        ${HOME}    (target)     /root
        ${PATH}    (target)     target user's path
        ${PWD}     (target)     /root
```
You can read more in [FONT=courier new]man sudo[/FONT] > ENVIRONMENT. In general, when calling a GUI app, you want to use [FONT=courier new]sudo -H[/FONT].

Note the handy exception [FONT=courier new]sudo --edit[/FONT], which is identical to using [FONT=courier new]sudoedit[/FONT]. This uses SUDO_EDITOR if set, else VISUAL if set, else EDITOR if set. In practical terms, [FONT=courier new]sudoedit *filename*[/FONT] is the same as [FONT=courier new]sudo -H gedit *filename*[/FONT] (assuming that SUDO_EDITOR, VISUAL or EDITOR is set to [FONT=courier new]gedit[/FONT]).

---

