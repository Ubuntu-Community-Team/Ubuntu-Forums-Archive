---
title: "add-atp-reposetory: command not found"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by Shmuli on 2014-04-27
Hi
Im running Ubuntu server 12.04 on my server and Im trying to run: [COLOR=#000000]sudo add-apt-repository ppa:mapnik/boost[/COLOR]
[COLOR=#000000]and I get this message saying: [/COLOR]add-atp-reposetory: command not found.
any ideas?
Thanx

---

### Post by steeldriver on 2014-04-27
Hello and welcome to the forums

[COLOR=#000000]add-apt-repository should be part of the [/COLOR]python-software-properties package - you can install it from Software Center or from the command line using

```

sudo apt-get install python-software-properties

```

---

### Post by oldos2er on 2014-04-27
Once you install it as steeldriver advised, you can avoid any misspellings by typing ```
sudo add-a[Tab]
``` without the [. I find tab completion to be a necessity in the terminal.

---

### Post by Shmuli on 2014-04-27
[COLOR=#000000]Hello and welcome to the forums[/COLOR]

[COLOR=#000000][COLOR=#000000]add-apt-repository should be part of the [/COLOR][/COLOR][COLOR=#000000]python-software-properties package - you can install it from Software Center or from the command line using[/COLOR]

[COLOR=#000000]Code:
sudo apt-get install python-software-properties[/COLOR]

Hi
I did it, but still dosnt work

---

### Post by monkeybrain20122 on 2014-04-27
You misspelled "repository" as "reposetory". :)

---

### Post by oldos2er on 2014-04-28
> **Shmuli said:**
> I did it, but still dosnt work

Can you please copy and paste the command you used and all its output?

---

