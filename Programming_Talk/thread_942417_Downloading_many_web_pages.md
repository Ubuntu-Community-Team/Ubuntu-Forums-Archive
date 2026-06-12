---
title: "Downloading many web pages"
date: 2008-10-09
forum: Programming Talk
---

### Post by sadda on 2008-10-09
Hi,
I would like to ask you for help. I would like to download thousands of web pages from [www.sonin.mn](www.sonin.mn) or any English web page (either the page source or better only the text, pictures and formatting are not important). These pages may be randomly chosen, but I would like to download as much as possible. One friend advised me something with wget -r, but I don't know how to do it. Do you have any advice?

Thanks for any help

---

### Post by Zugzwang on 2008-10-09
> **sadda said:**
> One friend advised me something with wget -r, but I don't know how to do it. Do you have any advice?


Yepp, read the manual of wget. Type "man wget" on the terminal.

Apart from that, not every web-master likes such exhaustive downloading from his/her site.

---

### Post by leg on 2008-10-09
Wget is a great tool but it wont work on all sites. For instance I have two sites where I use htaccess to deny access from the wget browser. There are probably ways around this but if I were you I would respect the site owners wishes on this.

---

### Post by Sinkingships7 on 2008-10-09
You could use httrack. It does a very good job of copying every file from a specific domain.

You can install it with
```
sudo aptitude install httrack
```

Run it in the terminal with the command ```
httrack
``` The directions that are provided when you run it are pretty self explanatory. For the things you don't understand, accept the default.

---

### Post by sadda on 2008-10-10
Thanks everyone, there were some problems with proxy when using wget, but httrack worked well.

---

