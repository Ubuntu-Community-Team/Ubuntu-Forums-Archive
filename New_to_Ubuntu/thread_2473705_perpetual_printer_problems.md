---
title: "perpetual printer problems"
date: 2022-04-11
forum: New to Ubuntu
---

### Post by hiram89410 on 2022-04-11
I have a fairly new hp deskjet 4155e printer that has suddenly and unaccountably stopped printing from my ubuntu 20.04. It works from all my hand-held devices as well as my wife's hand-held devices. It just won't work with the desktop where I do all my work. I installed the latest hplip from hp which used to correct the problem but nothing at all. It's listed in the printer settings and everything seems just fine. It just doesn't print. Any suggestions?

---

### Post by Autodave on 2022-04-11
How is it connected to the PC.....wifi or wired?

---

### Post by yancek on 2022-04-12
Try printing from a command line which may show an error.  Also, you might try some of the commands at the link below to get info, lpinfo and lpstat commands.

[https://www.networkworld.com/article/3373502/printing-from-the-linux-command-line.html](https://www.networkworld.com/article/3373502/printing-from-the-linux-command-line.html)

---

### Post by ajgreeny on 2022-04-12
What does the command driverless show you?

As an example, here is what mine shows.

[B][I]:~$ driverless
ipp://HP%20ENVY%204520%20series%20%5BDC214D%5D._ipp._tcp.local/[/I][/B]

---

### Post by SeijiSensei on 2022-04-12
Point a browser on your client machine at [http://localhost:631](http://localhost:631). That's the interface for CUPS. It should see your printer and suggest the correct driver.

---

