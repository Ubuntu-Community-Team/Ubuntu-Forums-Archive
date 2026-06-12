---
title: "[SOLVED] Script that will write to Sudoers file"
date: 2007-12-02
forum: Programming Talk
---

### Post by mdpalow on 2007-12-02
Hi Everyone,

To edit the Sudoers file you enter:

export EDITOR=gedit && sudo visudo

However, I want to update my script to place some text in this file without actually opening it up.

I know how to do this with other files, but when I do it to Sudoers it corrupts the file in some way and then you have NO sudo priviliges anymore. Basically, you have to do a re-install.

Sudoers has 440 permissions and belongs to root.

I thought to change the permissions and even chmod it from root to user to add text and then put it back. However, that didn't work for me either.

Does anyone have an idea of how it could be done?

Thanks in advance for any help ...

---

### Post by LaRoza on 2007-12-02
> 
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.


I think they mean it...

---

### Post by mdpalow on 2007-12-02
Thanks LaRoza...

Just seems like one of those things where if you have a sudo password, you should be able to at least make it work even if you had to do a run-a-round...

---

### Post by LaRoza on 2007-12-02
It seems that since sudo is a very important security feature of Ubuntu, it has the utmost security.

---

### Post by ssam on 2007-12-03
visudo is a wrapper that makes a temp version of the sudoers file. nad then runs the command in the EDITOR variable. when that finishes it checks the syntax of the temp file, and only if it is ok, updates the actual sudoers file.

so if you make a  program that takes a file name as an argument, and inserts text into the file given. then you can set EDITOR to the path of you program, and then called visudo.

---

### Post by CptPicard on 2007-12-03
Having some other processes writing to sudoers even when they might be sudo sounds like a massive escalation hole waiting to happen. That's why it needs to be done manually by root.

---

### Post by mdpalow on 2007-12-03
thanks everyone...

---

