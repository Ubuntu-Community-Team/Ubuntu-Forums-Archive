---
title: "Shell cript log file"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Tsu on 2008-11-13
Hi everyone,

Just a quick question.

I ahve a shell script and outputting the data to a log file.

echo "email moved to tmp" >>/var/log/meme

How do I add the date into here? I want the date and time of the operations performace. I tried 

echo date "email moved to tmp" >>/var/log/rocketseed/gmaillog

but that just put

"date email moved to tmp"

into the log file.

Thanks in advanced

---

### Post by Tsu on 2008-11-13
answer is place the date command in back qoutes.

#Example -

echo `date` "email moved to tmp" >>/var/log/meme

---

