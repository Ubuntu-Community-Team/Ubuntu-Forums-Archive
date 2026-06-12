---
title: "Browsing in terminal"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by sohaikia1 on 2008-06-13
Hi, I have been using ubuntu for last 2 days and I have got to say I am in love with it. Re-lives the excitement of using computers in me to the point of abandoning windows :). Out of curiosity , I would to know is it possible to browse the internet in terminal? Thanks in advance , you guys did a great job.

---

### Post by aktiwers on 2008-06-13
Try links2
```
sudo apt-get install links2
```then
```
links2
```If I remember currect CTRL+G lets you type in URL :)

Edit:
You could also try lynx
```
sudo apt-get install lynx
```

Then:
```
lynx
```

To read about how to use the browsers or any other app just type 
```
man <appname>
```

In this case:
```
man lynx
```
and 
```
man links2
```

---

### Post by wolfen69 on 2008-06-13
lynx and elinks also

---

### Post by OffAxis on 2008-06-13
how about w3m? It's already installed.

```
w3m url
```
where url = the website you want to view

---

### Post by sohaikia1 on 2008-06-13
Thank you guys , it works.

---

