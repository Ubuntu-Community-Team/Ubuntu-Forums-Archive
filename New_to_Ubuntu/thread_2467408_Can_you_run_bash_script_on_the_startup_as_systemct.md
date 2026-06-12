---
title: "Can you run bash script on the startup as systemctl?"
date: 2021-09-25
forum: New to Ubuntu
---

### Post by en4ble on 2021-09-25
Please excuse my ignorance, still  learning linux. I have a script that I need to run at the start. Created  .service and setup proper permissions but getting status 203 error:[INDENT]***Process: 8121 ExecStart=/etc/myFolder/bash*** [***startscript.sh***]("https://ergostartscript.sh") ***(code=exited, status=203/EXEC)***

[/INDENT]
Here is the service snippet:[INDENT][Service]
Type=oneshot
RemainAfterExit=yes
***ExecStart=/etc/myFolder/"bash*** [***startscript.sh***]("https://ergostartscript.sh")***"***
Restart=on-failure
RestartSec=30

[/INDENT]
When running the script by itself it starts my command no problem. Any help would be greatly appreciated.

[INDENT][Unit]
Description=start java app
After=network.target
    [Service]
Type=oneshot
RemainAfterExit=yes
ExecStart="/bin/bash /etc/myFolder/startscript.sh"
Restart=on-failure
RestartSec=30

# Directory creation and permissions
####################################

# Run as admin:admin
User=admin
Group=admin
    [Install]
WantedBy=multi-user.target
[/INDENT]
 
    !whats inside the startscript bash .sh

[INDENT]java -jar javaApp.jar -c myConf.conf
[/INDENT]
 
Tried without /bin/bash with same error.

---

### Post by ActionParsnip on 2021-09-26
Did you set the script to be executable?

---

### Post by ActionParsnip on 2021-09-26
You need to specify the full path to the conf file in your script as well

---

### Post by Holger_Gehrke on 2021-09-26
There's a discrepancy between the two snippets you posted. Is it
> 
ExecStart=/etc/myFolder/"bash [startscript.sh]("https://ergostartscript.sh")"
or
> 
ExecStart="/bin/bash /etc/myFolder/startscript.sh"

?

If it's the former, then it's kind of obvious: 203 is 'can't execute this' either because the file isn't there or it's not executable or it's a script without a shebang-line (a line telling the system what interpreter to use for a script, like '#!/bin/bash') and there's no file named 'bash startscript.sh' (with a space in the file name) in /etc/myfolder/. If it's the latter, I'd try without the quotes or I'd make the script executable (sudo chmod a+x /etc/myfolder/startscript.sh), put in a shebang line as the first line of the script and change the ExecStart-line to 'ExecStart=/etc/myfolder/startscript.sh'.

Beyond that: the environment at the time services are run and in a shell after login are rather different. You might need to set a whole lot of environment variables that the Java-runtime expects which aren't set this early in the boot process.

Holger

---

