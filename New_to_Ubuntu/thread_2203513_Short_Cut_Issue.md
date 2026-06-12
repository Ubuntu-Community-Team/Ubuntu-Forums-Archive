---
title: "Short Cut Issue"
date: 2014-02-03
forum: New to Ubuntu
---

### Post by cronotrigger1 on 2014-02-03
Very new to the Ubuntu world. I was looking to create a shortcut for my minecraft server in Ubuntu. but I am having some issues and it have to be in my directory code or elsewhere.

code in the file was this

[COLOR=#282828][FONT=Verdana]cd /home/user/minecraftserver/[/FONT][/COLOR]
[COLOR=#282828][FONT=Verdana]java -Xmx2048M -Xms1024M -jar Minecraft_server.1.7.4.jar -nogui

the file is saved as minecraftserver.sh

double click the file and click run, nothing happens
[/FONT][/COLOR][COLOR=#282828][FONT=Verdana]double click the file and click run in terminal, terminal opens them immediately closes nothing else happens.[/FONT][/COLOR][COLOR=#282828][FONT=Verdana]
The server is still not up.

removed -nogui and still nothing.
[/FONT][/COLOR][COLOR=#282828][FONT=Verdana]
Oracle Java is installed (and verified that it was there)
Minecraft server runs if I right click the .jar in the gui and select "Open with Java."

I am on Ubuntu 12.04 x64 with 4GB of RAM.[/FONT][/COLOR]

---

### Post by Dave_L on 2014-02-03
Try adding a "pound-bang" line at the beginning of the script:
```
#!/bin/sh
cd /home/user/minecraftserver/
java -Xmx2048M -Xms1024M -jar Minecraft_server.1.7.4.jar -nogui
```

and make the script executable:
```
chmod 755 minecraftserver.sh
```

---

### Post by TheFu on 2014-02-03
Java programs need more environment variables to run.  
Is JAVA_HOME set?  
Has the binary for the JRE been added to your PATH?

Linux doesn't care about extensions. Use **chmod** to enable the execute flags for the user, group, and other, if those people should be able to run (or execute) the script. Learning a little more about file permissions would be good too. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

For most server daemons, having them start and stop automatically when the system boots or shuts down is desired.  There are 20-200 example scripts in /etc/init.d/  If you create your own, be certain to enable it with **update-rc.d**.

---

