---
title: "&quot;absence of wireless drivers on ubuntu 12.04&quot;"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by Kimberlin Jude on 2012-11-11
Since I installed Ubuntu 12.04 on my computer I haven't used a wireless internet connection since it seems my Wireless interface card is not enable(absent) also the firmware is not enlightened. I would have this problem  solved.I am not so familiar with Ubuntu Operating systems.

Thanks in advance
confused:

---

### Post by BertN45 on 2012-11-11
Before we can help you, we have to know which wifi hardware you have. If you start the terminal, you could type "lspci" and copy/paste the output of that command in your next reply.

---

### Post by NikTh on 2012-11-11
Hello and Welcome to the Forums.

Please open a terminal (CTRL+ALT+T keys combo) and copy-paste from here bellow commands , one line at time. 
```
lsb_release -rcd ; uname -r
lspci -nnk | grep -iA2 net
cat /etc/network/interfaces
nmcli nm status
rfkill list all
lsmod
```Post the results back here.

**Click on "New Reply" [IMG]http://ubuntuforums.org/attachment.php?attachmentid=227046&stc=1&d=1352682474[/IMG] and put the results inside [CODE] tags to be easier to read. **[See here how]("http://i.stack.imgur.com/zADbK.png")
 
Thanks

---

