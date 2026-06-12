---
title: "Ubuntu Desktop to Ubuntu Server issues with vi and scrolling"
date: 2023-07-03
forum: New to Ubuntu
---

### Post by markalvarez123 on 2023-07-03
Hello,

We have a server at work running the following:



Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:    22.04
Codename:    jammy


I wrote some python scripts on my local Ubuntu workstation running the same release version above and run them on our server but to my surprise, i ran into a few issues.

1. When I'm in the terminal and after I run some commands, i can see the outputs, however when I open a file in vim and close it, all the previously visible outputs disappear and the screen just shows the partial content of the previously opened file.

2. When I edit the file in vi (which runs vim instead), it messes up the tabs for my python script and I couldn't make any modifications to the script at all and keep getting indention error.

3. When i'm working in the terminal, I can no longer scroll up. Quick google search suggests that scrolling has been removed from the kernel some time ago. Is this the case?


I thought I'd run my scripts on our server to harness its processing power but with all the issues i've described above, do we have any alternative to just re-formatting the server into the desktop version?

---

### Post by markalvarez123 on 2023-07-03
I figured out the vim vs vi issue. I realized that in my local ubuntu desktop I have the following: /usr/bin/vi -> /etc/alternatives/vi -> /usr/bin/vim.tiny, whereas on the server (I have /usr/bin/vi -> /etc/alternatives/vi -> /usr/bin/vim.basic. Fixed it by changing the links. I just need to figure out how to bring the scrolling back.

---

### Post by Holger_Gehrke on 2023-07-03
The ability to scroll back on a virtual terminal was removed some time ago (kernel 5.9 I read somewhere ...) mostly because it's not a 'real' text mode anymore but some kind of framebuffer. Use 'less' for viewing files and if you absolutely need to scroll back through your interactive terminal input / output learn to use 'screen' or 'tmux'. This change went mostly unnoticed because most people will access their servers through ssh from a graphical terminal on another machine ...

I hope you didn't mess with those links directly. They are part of the debian alternatives system. Read the manual page for 'update-alternatives' to find out how that works.

Holger

---

