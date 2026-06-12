---
title: "How to kill a process?"
date: 2023-04-03
forum: New to Ubuntu
---

### Post by kevin_jones3 on 2023-04-03
Hello, I started to edit a php file in vim. I did not close it properly and tried to switch to nano. For some reason nano informs that the file is still being edited by Vim "is being edited by root (with VIM 9.0, PID 21988); open anyway"...can any one tell me how to kill the vim. I have tried rebooting.
I was trying to download wordpress. 

t hanks Kevin Jones

---

### Post by mIk3_08 on 2023-04-03
> **kevin_jones3 said:**
> Hello, I started to edit a php file in vim.  I did not close it properly and tried to switch to nano. For some  reason nano informs that the file is still being edited by Vim "is being  edited by root (with VIM 9.0, PID 21988); open anyway"...can any one  tell me how to kill the vim. I have tried rebooting.
I was trying to download wordpress. 

t hanks Kevin Jones
I think you should have properly Save the file and exit. It will always  notify you when you open the file via vim and was not able save and exit  properly. 
To save a file and exit Vim, do the following:

 1. Switch to **command mode** by pressing the **Esc** key.
 2. Press **: **(**colon**) to open the prompt bar in the bottom left corner of the window.
 3. Type **x **after the colon and hit** Enter**. This will save the changes and exit.

---

### Post by #&amp;thj^% on 2023-04-03
> **kevin_jones3 said:**
> Hello, I started to edit a php file in vim. I did not close it properly and tried to switch to nano. For some reason nano informs that the file is still being edited by Vim "is being edited by root (with VIM 9.0, PID 21988); open anyway"...can any one tell me how to kill the vim. I have tried rebooting.
I was trying to download wordpress. 

t hanks Kevin Jones
What shows with:
```
:w !sudo sh -c "cat > %"
```

---

### Post by kevin_jones3 on 2023-04-03
[FONT=monospace][COLOR=#000000]:w !sudo sh -c "cat > %" [/COLOR]
:w sudo nano /var/www/html/info.php sh -c "cat > %" 
:w: command not found

Not sure what this means, but here is the return. 
thanks
kevin
[/FONT]

---

### Post by yancek on 2023-04-04
If you failed to save  the file properly while using vim, open it again using vim not nano then use the process explained in post 2 to properly save and close the file.  Do not try using nano until the file is saved properly in vim.

---

### Post by Impavidus on 2023-04-04
Rebooting will definitely kill a process, so that's not the issue. But when you edit a file, vim creates a swap file named .filename.swap in the same directory as the file being edited. If you kill vim, instead of properly closing it, this swap file isn't removed. Vim can use it to detect that another instance of vim is already editing the file and warn you, or it can use it to recover unsaved changes in case vim crashed or was killed.

If you want to discard unsaved changes, you can delete the swap file.

---

### Post by #&amp;thj^% on 2023-04-04
> **Impavidus said:**
> Rebooting will definitely kill a process, so that's not the issue. But when you edit a file, vim creates a swap file named .filename.swap in the same directory as the file being edited. If you kill vim, instead of properly closing it, this swap file isn't removed. Vim can use it to detect that another instance of vim is already editing the file and warn you, or it can use it to recover unsaved changes in case vim crashed or was killed.

If you want to discard unsaved changes, you can delete the swap file.

+1 Great information, we already seen the OP rebooted, so this is a good recommend. And something I too would advise.

---

### Post by TheFu on 2023-04-04
vim has unlimited undo/redo capabilities, among many other great features.  Worth the time to learn it.  I've never seen any commercial router with nano, but they all have vi. Just sayin'.  For Unix administration, vi/vim are the default editor. No need to become a power user, unless you are a professional programmer. Then vim becomes an extension of your mind and you'll do things through muscle memory that no other editor on the planet can do.  Knowing a minimal amount of vi/vim is smart for anyone running a Unix-like OS.

---

### Post by kevin_jones3 on 2023-04-05
Yes, Impavidus...I did find the swap file. Which I recovered and then saved it properly. I am not at all used to vim and did  not know what I was doing. Thanks very much for the advice/
Kevin

---

### Post by kevin_jones3 on 2023-04-05
This worked for me. thanks very much mlk3_08

---

### Post by mIk3_08 on 2023-04-05
> **kevin_jones3 said:**
> This worked for me. thanks very much mlk3_08
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

