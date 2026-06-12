---
title: "Launcher for terminal command - keep the window open"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Huji on 2008-10-05
I want to add a launcher on my dekstop which runs a command like this:

ssh -l [www.example.com](www.example.com) PubkeyAuthentication=yes

but keep the window open so I can use the ssh connection. When I create a launcher with that command in it, it opens a terminal window, logs in to the server, but then closes the window. What should I do?

---

### Post by olejorgen on 2008-10-06
If you type
```
gnome-terminal -x ssh -l www.example.com PubkeyAuthentication=yes
```
in a terminal, is the result the same?

---

### Post by davidryder on 2008-10-06
Try

```
gnome-terminal -e "ssh -l www.example.com PubkeyAuthentication=yes" &
```

Note: You must put the command in quotes.

---

### Post by Huji on 2008-10-06
> **davidryder said:**
> Try

```
gnome-terminal -e "ssh -l www.example.com PubkeyAuthentication=yes" &
```

Note: You must put the command in quotes.
It didn't work :( Still, a terminal window opens, a few seconds pass and login initializatio nis accomplished, then the terminal window is closed. It doesn't even let me to type the passphrase!

---

### Post by davidryder on 2008-10-06
> **Huji said:**
> It didn't work :( Still, a terminal window opens, a few seconds pass and login initializatio nis accomplished, then the terminal window is closed. It doesn't even let me to type the passphrase!

Try removing the -l and PubkeyAuthentication=yes option from the line

```
gnome-terminal -e "ssh user@www.example.com" &
```

---

### Post by caljohnsmith on 2008-10-06
Try using this syntax:
```
gnome-terminal -x bash -c "ssh -l www.example.com PubkeyAuthentication=yes;read -n1"
```
The "read -n1" will make it so the gnome-terminal won't close until you press any key. Let me know if that is what you are looking for.

---

### Post by Huji on 2008-10-06
> **davidryder said:**
> Try removing the -l and PubkeyAuthentication=yes option from the line

```
gnome-terminal -e "ssh user@www.example.com" &
```
Yes, that worked; my bad. And do I really need that & at the end? Because it works fine without that.

---

