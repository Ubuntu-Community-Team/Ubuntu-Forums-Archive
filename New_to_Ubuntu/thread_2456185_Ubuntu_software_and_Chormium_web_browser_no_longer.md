---
title: "Ubuntu software and Chormium web browser no longer start."
date: 2021-01-06
forum: New to Ubuntu
---

### Post by tranzed on 2021-01-06
Hi guys,

Thanks in advance for any help...

I have been using 20.10 version of Ubuntu for a couple of week now and some programmes are failing to start.
First it was the Ubuntu Software app and now the Chromium web browser.

The applications are installed and visable

I have tried sudo apt-get update
and sudo apt-get upgrade
I can see some things were upgraded but still these apps don´t work
Any ideas please?

---

### Post by Frogs Hair on 2021-01-06
Hello and Welcome !

Try starting software from the terminal with the following command and reporting any errors. Chromium is a snap package , so I can't address that . 

```
gnome-software
```

---

### Post by tea for one on 2021-01-06
For Ubuntu software, try this via a terminal:-
```
snap-store
```

Both Ubuntu Software and Chromium are now [COLOR="#0000FF"]snap[/COLOR] packages.

Did you move, delete, adjust, modify any part of the [COLOR="#0000FF"]snap[/COLOR] software?

---

### Post by Frogs Hair on 2021-01-06
The command will still work for gnome-software, see above first.

---

### Post by tea for one on 2021-01-06
I am fairly sure that gnome-software is not a default package in 20.10.
Of course, it is in the repository.

---

### Post by deadflowr on 2021-01-06
If the programs are snaps then try reverting them to the older version which would still be installed.
[https://snapcraft.io/docs/getting-started#heading--revert]("https://snapcraft.io/docs/getting-started#heading--revert")

---

