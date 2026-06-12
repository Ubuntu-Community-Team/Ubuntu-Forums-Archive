---
title: "user input  with shell script"
date: 2010-01-21
forum: Programming Talk
---

### Post by e24ohm on 2010-01-21
User Input

Folks I am trying to develop a script, which will map a windows network share and prompt the user for their credentials.

I use the following code

#!/bin/bash
Mount –t smbfs //servername/sharename /mnt/mountdirectory –o username=windows username,password=windowspassowrd

How do I get my script to prompt the user for ‘windowsusername’ and ‘windowspassword’

---

### Post by Trumpen on 2010-01-21
With read:

[php]read -p "windows user: " winuser
read -s -p "windows passwd: " winpassword

mount –t smbfs //servername/sharename /mnt/mountdirectory –o username="$winuser",password="$winpassword"[/php]

Use "help read" for more info on read command.

---

### Post by smo0th on 2010-01-21
cool =)

---

### Post by e24ohm on 2010-01-21
> **Trumpen said:**
> With read:

[php]read -p "windows user: " winuser
read -s -p "windows passwd: " winpassword

mount –t smbfs //servername/sharename /mnt/mountdirectory –o username="$winuser",password="$winpassword"[/php]

Use "help read" for more info on read command.

thanks - looking at it right now.

---

