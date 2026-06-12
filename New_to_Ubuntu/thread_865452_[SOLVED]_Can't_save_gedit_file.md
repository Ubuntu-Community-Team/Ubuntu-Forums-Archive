---
title: "[SOLVED] Can't save gedit file"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by TRANQU111TY on 2008-07-20
```
gksudo gedit /etc/sudoers
```

I add lines into the file but the save option is greyed out. I choose save as and this error comes up:

```

Could not save the file /etc/sudoers.

You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again.
```

---

### Post by sisco311 on 2008-07-20
try:
     ```
export EDITOR=nano
sudo -E visudo
```Ctrl+o, Enter = save
Ctrl+x = exit
Ctr+x y Enter = save and exit
Read this:[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by Joeb454 on 2008-07-20
You need to use vi to edit that file (Ubuntu *may* use Nano, I can't remember).

Open a terminal and type ```
sudo visudo
``` but be warned that if you do something even slightly wrong in that file, and you won't be able to use sudo

---

### Post by drs305 on 2008-07-20
> **TRANQU111TY said:**
> ```
gksudo gedit /etc/sudoers
```

I add lines into the file but the save option is greyed out. I choose save as and this error comes up:

```

Could not save the file /etc/sudoers.

You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again.
```

The sudoers file cannot be edited in the normal manner. You must use visudo. The command would be:
```
sudo visudo
```

To edit the sudoers file with another editor, you can use this:
```
export EDITOR=gedit && sudo -E visudo

```

---

### Post by Vivaldi Gloria on 2008-07-20
Make changes so that visudo starts with nano rather than vi:

Edit ~/.bashrc and add this line somewhere:

```
export EDITOR=/usr/bin/nano
```

Now in terminal:

```
source ~/.bashrc
```

so that the change in .bashrc takes place. Now

```
sudo -E visudo
```

starts visudo in nano rather than vi.

---

### Post by sisco311 on 2008-07-20
> **Joeb454 said:**
> You need to use vi to edit that file (Ubuntu *may* use Nano, I can't remember).

Open a terminal and type ```
sudo visudo
``` but be warned that if you do something even slightly wrong in that file, and you won't be able to use sudo
nano was the default
they changed it to vi in hardy

---

### Post by TRANQU111TY on 2008-07-20
> **sisco311 said:**
> try:
     ```
export EDITOR=nano
sudo -E visudo
```Ctrl+o, Enter = save
Ctrl+x = exit
Ctr+x y Enter = save and exit
Read this:[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

This work perfectly.

Thanks guys :)

---

### Post by sisco311 on 2008-07-20
> **drs305 said:**
> The sudoers file cannot be edited in the normal manner. You must use visudo. The command would be:
```
sudo visudo
```To edit the sudoers file with another editor, you can use this:
```
export EDITOR=gedit && sudo -E visudo

```
in my experience visudo doesn't play nice with the GUI editors

---

### Post by drs305 on 2008-07-20
> **sisco311 said:**
> in my experience visudo doesn't play nice with the GUI editors

What kind of problems? I think I've used gedit a half dozen times to edit sudoers without any troubles. 

I'm certainly open to changing to nano or vi if it would be better. I recommended gedit just because most ubuntu newbies are probably more familiar with that editor and you certainly don't want to be making mistakes with sudoers.

---

### Post by sisco311 on 2008-07-20
> **drs305 said:**
> What kind of problems? I think I've used gedit a half dozen times to edit sudoers without any troubles. 

I'm certainly open to changing to nano or vi if it would be better. I recommended gedit just because most ubuntu newbies are probably more familiar with that editor and you certainly don't want to be making mistakes with sudoers.
Did you try to save the file with syntax error?
The (e)dit option doesn't worked for me.

I don't have any GUI editors installed, so I can't test it now.
(I'm out of space on my 1gb "hard disk"=mp3 player; damn bad sectors)

---

### Post by drs305 on 2008-07-20
> **sisco311 said:**
> Did you try to save the file with syntax error?
The (e)dit option doesn't worked for me.

I don't have any GUI editors installed, so I can't test it now.
(I'm out of space on my 1gb "hard disk")

No, it never gave me a syntax error. I just tried modifying it again and no problems. 

I've always just opened it with "export EDITOR=gedit && sudo -E visudo".

However, I'm not one to press my luck unless someone else with a lot of experience of using gedit and sudoers chimes in... ;-)

---

### Post by sisco311 on 2008-07-20
> **drs305 said:**
> No, it never gave me a syntax error. I just tried modifying it again and no problems. 

I've always just opened it with "export EDITOR=gedit && sudo -E visudo".

However, I'm not one to press my luck unless someone else with a lot of experience of using gedit and sudoers chimes in... ;-)
OK.
I've installed xfe.
visudo works with xfilewriter.
I think the bug was fixed.

---

