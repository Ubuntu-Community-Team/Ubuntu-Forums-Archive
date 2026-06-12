---
title: "installing bin file"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by konsta82 on 2008-08-05
im tying to install program,but received message is : cant open bin file.file is on desktop if that matters.
please help !

---

### Post by hyper_ch on 2008-08-05
what program do you want to install?

---

### Post by kpkeerthi on 2008-08-05
Open terminal
Type **cd Desktop**
Then type **sh <first few chars of the file> <tab><tab>**

---

### Post by brujoand on 2008-08-05
open a terminal (applications --> accessories --> terminal)

type "cd /home/<yourusername>/Desktop" to change directory to desktop

type "sudo chmod 755 <thefilename>.bin" to make it executable

type "sudo ./<thefilename>.bin" to install

:)

---

### Post by JT673 on 2008-08-05
It's probably a shell script with something attached.  Right-click on it, click Properties, then check "Allow executing file as program" under "Permissions"

After closing the Properties window, try double-clicking on it again.

Or you can go to the CLI and enter: "chmod a+x [file]"

---

### Post by konsta82 on 2008-08-05
helix player succesfully installed with permission change and sudo command !

---

