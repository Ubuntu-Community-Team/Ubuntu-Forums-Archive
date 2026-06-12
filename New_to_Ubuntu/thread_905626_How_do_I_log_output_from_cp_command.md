---
title: "How do I log output from cp command?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by nrogers64 on 2008-08-30
Hi,

I have a dead SATA drive that Windows won't recognize. Acronis True Image sees the drive's label, so that's a good sign, but it won't copy anything from it. I put the drive in my Ubuntu box, and it came right up. However, some of the folders that I KNOW have things in them don't show anything. But when I go to the terminal and type "ls" in that folder, it shows the contents. That leads me to believe that the terminal is a little more forgiving of bad hard drives. So rather than using the GUI to copy the files, I just want to use the terminal. However, I would like a list of files that don't copy correctly. I know that cp will tell you when things don't copy correctly, but if it happens too much, eventually the list will be so long that you can no longer scroll to the top of the list. Is there a way to log the output? In DOS, you just put " > file.txt" after the command and it logs it to that file. I'm basically looking for the equivalent of that in Ubuntu. Thanks very much!

---

### Post by fwre01 on 2008-08-30
thats right, maybe try ```
 cp -R -v /source-folder/ /destination-folder/ > /tmp/copy-output 
``` that should give you some useful information

---

### Post by drubin on 2008-08-30
> **nrogers64 said:**
>  eventually the list will be so long that you can no longer scroll to the top of the list. 

You can change the mount of lines the terminal will record "scrollback"
once in the terminal to go Edit->profiles->edit: in the tab "scrolling" there are some options change them to suite you needs. 

I have my terminal scroll bad set kinda high so that I can always see the output of the commands.

---

### Post by fwre01 on 2008-08-30
you wont see the output in the terminal if it gets output to a file. so you wont need to adjust your scroll back.

Unless you DO want to output to the terminal...in which case u will.lol

---

### Post by drubin on 2008-08-30
> **fwre01 said:**
> you wont see the output in the terminal if it gets output to a file. so you wont need to adjust your scroll back.

Unless you DO want to output to the terminal...in which case u will.lol

thanks for the little addition :)

---

### Post by nrogers64 on 2008-08-30
Thanks guys! I will give those methods a try. I really appreciate the fast responses on the Ubuntu Forums. You guys are awesome!

---

### Post by drubin on 2008-08-30
Most of the ubuntu community is like this.

I forgot to welcome you to the forums!! :)  hope to see you back soon, maybe helping others as well. 

ps Dont forget to mark the thread as solved, if these sorted out your issues.  Just next to your first post, click on thread tools, mark as solved.

---

