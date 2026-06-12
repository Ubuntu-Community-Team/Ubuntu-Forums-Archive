---
title: "Ubuntu SeedDms Install"
date: 2023-04-21
forum: New to Ubuntu
---

### Post by eroms90 on 2023-04-21
Hello, I am new to Ubuntu. I am trying install seeddms on Ubuntu 22.04. I have set up the server and installed other dependencies for the seeddms but my problem now is how do i install the Seeddms. i have enter the dir for cd /var/www/html and i also tried to copy the seeddms file using cp /Home/Downloads/seeddms-quickstart-6.0.23.tar.gz so i can extract it but i keep getting this message that [B]bash: cp/Home/lg/Downloads/seeddms-quickstart-6.0.23.tar.gz: No such file or directory.
[/B]

---

### Post by yetimon_64 on 2023-04-21
Try changing your copy command path to either...```
$HOME/Downloads/seeddms-quickstart-6.0.23.tar.gz
```
or
```
/home/$USER/Downloads/seeddms-quickstart-6.0.23.tar.gz
```
You appear to have capitalised "/home" and forgot to include your user-name. Using either of the 2 paths above in your copy command  should fix your issue.
The system variable "$HOME" inserts your home folder /home/<your username>.
The system variable "$USER" simply inserts your username.

Apart from missing your username, note that Linux is case sensitive ie. you need to use "/home" not "/Home"

Regards, yeti

---

