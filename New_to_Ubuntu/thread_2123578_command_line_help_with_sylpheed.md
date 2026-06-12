---
title: "command line help with sylpheed"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-03-08
cant figure out how to make all my inbox marked as read from the command line. if i use sylpheed  --mark all read it just deletes the most recent email and i have to run the command again to delete the next,etc. there must be a way because i can open the sylpheed  application (not from the terminal) and select the mark all read option and it marks all as read. tks

---

### Post by rburkartjo on 2013-03-09
figured it out
wrote this script (replace xxx with user password) and (replace nnn with your user name).  and also assuming that you are using Mail folder to store your mail.

#!/bin/bash
echo xxx | sudo -S
 rm -rf /home/nnn/Mail/inbox/*

---

