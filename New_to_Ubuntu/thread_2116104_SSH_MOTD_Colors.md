---
title: "SSH MOTD Colors"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by zysh on 2013-02-14
Hey all,
I've got my Open SSH motd file all set up and shiny, but I'd like to add some color. I know there are some pretty great guides out there for adding color however I'm using Zshell (Still bash, not sure if that makes a difference) and I can't seem to get color enabled. Instead of showing color with 
>  \033[1;32m Color! \033[0m 
it shows the code instead.

Thanks much in advance!

---

### Post by appiehappie94 on 2013-03-18
Maybe a little late, but what file are you trying to edit? If it's /etc/motd, it will not work.

I created & edited the file ~/.bash_profile which works right away!

Just make this file in your homefolder (non-root privileges, if that makes any difference?), cut-paste your whole motd in there and you're ready to go.

Also a little note: logging in will take about ~3 seconds longer. (But I'm using a regular laptop and SSH is over wi-fi, so maybe that's the 'problem' for me)

---

