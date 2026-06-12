---
title: "HOWTO: Recieve Notifications When a Server is Done Rebooting"
date: 2010-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by ncwilde43 on 2010-05-27
**[SIZE=5]Description[/SIZE]**

One of the more annoying things about performing maintenance on a server through ssh is finding out when the server is up again after a reboot. I’m constantly trying to log into the server over ssh and checking to see if it’s up. Here’s a novel idea, why don’t I figure out how to get the server to notify me when it’s up! While reading about [make server beep after bootup]("http://ubuntuforums.org/showthread.php?t=708834") and [customizing Notify OSD notification]("http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html"), I got the idea to have the server send me an OSD notification using the rc.local script.

[IMG]http://new2ubuntu.files.wordpress.com/2010/05/server_is_up.png[/IMG]

[SIZE=4][B][COLOR=Red][SIZE=5]Warning![/SIZE]
[/COLOR][/B][/SIZE]
**This tutorial requires a password-less SSH setup between the server and client machine.  Use at your own risk.**

[SIZE=4][B][SIZE=5]References[/SIZE]
[/B][/SIZE]
[LIST]
[*][Bash script (or alias) using ssh & notify-send]("http://ubuntuforums.org/showthread.php?t=1240828")
[*][RcLocalHowto]("http://new2ubuntu.wordpress.com/community/RcLocalHowto?action=fullsearch&context=180&value=linkto%3A%22RcLocalHowto%22")
[*][rc.local not executing at reboot]("http://ubuntuforums.org/showthread.php?t=371948")
[*][make server beep after bootup]("http://ubuntuforums.org/showthread.php?t=708834")
[*][Password-less logins with OpenSSH]("http://www.debian-administration.org/articles/152")
[*][Finally an Easy Way to Customize Notify OSD Notification Bubbles]("http://www.webupd8.org/2010/05/finally-easy-way-to-customize-notify.html")
[/LIST]
 **[SIZE=5]Nomenclature:[/SIZE]**

 
[LIST]
[*]**Server** – the server machine that reboots and sends to the OSD notificaton.
[*]**Client** – the desktop machine that receives the OSD notificaton.
[*]**<client_user_name>** – the username of the client computer that recieves the OSD notifications.
[*]**<server_user_name>** – the username of the server computer.
[*]**<client_computer_name>** – the name of the client computer.
[*]**<server_computer_name>** – the name of the server computer.
[*]**<domain_name>** – the name of the network domain.
[/LIST]
[SIZE=4][B][SIZE=5]Setup
[/SIZE][/B][/SIZE]
[SIZE=4]**Client Setup**[/SIZE]

I’m using Ubuntu Lucid 10.04 as my desktop OS.
 [B]
1.  Install OpenSSH server.[/B]
 
```
sudo apt-get -y --force-yes install openssh-server
``` **[SIZE=4]Server Setup[/SIZE]**

 I’m using Ubuntu Server Karmic 9.10 as my server OS.

**1.  Install Notify OSD.**

 ```
sudo apt-get -y --force-yes install notify-osd
```**2.  Test to see if the client will recieve the OSD notification.**

 ```
ssh -X <client_user_name>@<client_computer_name>.<domain_name> 'DISPLAY=:0 notify-send "Server is up" -i "/usr/share/icons/Humanity/apps/48/bash.svg"'
```Example:
 
```
voltron43@server: ~$ ssh -X voltron43@voltron43-laptop.local 'DISPLAY=:0 notify-send "Server is up" -i "/usr/share/icons/Humanity/apps/48/bash.svg"'
``` where
 
[LIST]
[*]“Server is up” is the notification message
[*]-i “/usr/share/icons/Humanity/apps/48/bash.svg” is the location of the icon on the client computer shown in the OSD notification.
[/LIST]
 Once the test is successful, we need to move onto [password-less SSH logins]("http://www.debian-administration.org/articles/152") in order for the server to send the OSD notification without having to prompt for the client username’s password. Because rc.local uses root instead of the Server superuser, we need to setup the password-less SSH login with root.
 [B]
3.  On the Server, switch to root user.[/B]

 ```
sudo su
```**4.  Generate the RSA keys.**

 ```
ssh-keygen -t rsa
```**5.  Accept the default file and leave the passphrase blank.**

 ```
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
```**6.  Copy the RSA key to the client computer and client username.**

 ```
ssh-copy-id -i /root/.ssh/id_rsa.pub <client_user_name>@<client_computer_name>.<domain_name>
``` Example:
 ```
ssh-copy-id -i /root/.ssh/id_rsa.pub voltron43@voltron43-laptop.local
```**7.  Test the OSD notification from root to make sure there isn’t a password prompt.**

 ```
ssh -X <client_user_name>@<client_computer_name>.<domain_name> 'DISPLAY=:0 notify-send "Server is up" -i "/usr/share/icons/Humanity/apps/48/bash.svg"'
``` Example:
 ```
root@server: ~$ ssh -X voltron43@voltron43-laptop.local 'DISPLAY=:0 notify-send "Server is up" -i "/usr/share/icons/Humanity/apps/48/bash.svg"'
```**8.  Create the [rc.local]("https://help.ubuntu.com/community/RcLocalHowto") file**

 ```
sudo nano /etc/init.d/local
```The Ubuntu equivalent to rc.local is the local file located in the init.d folder.
 [B]
9.  Paste the following into the local file.[/B]

/etc/init.d/local
 ```
#!/bin/sh
sleep 10
ssh -X @. 'DISPLAY=:0 notify-send "Server is up" -i "/usr/share/icons/Humanity/apps/48/bash.svg"'
exit 0
```The *sleep 10*is used to make sure that all services are started before running the ssh command.

** 10.  Save and exit nano by pressing Ctrl+O and Ctrl+X.**

 **11.  Make the local file executable.**

 ```
sudo chmod +x /etc/init.d/local
```**12.  Link the local file with Init.**

 ```
sudo update-rc.d local defaults 80
```**13.  Restart the server and you’re done!**
 ```
sudo reboot
```[B]

[SIZE=5]Debugging[/SIZE][/B]

 To debug the script, add “> /home/<server_user_name>/error.log 2>&1&#8243; to the local file at the end of the ssh command to check for errors and “echo $(date) – Running >> /home/<server_user_name>/test.run” in the next line to see if the local file is being executed on startup.
 
The test.run file is created everytime the local file runs.  The local file should run everytime the server boots, so if you do not see the test.run file in the server home directory, the local file is not running on startup.

The error.log file is used to debug the ssh command.  If the ssh command ran successfully, the error.log file should be empty; else an error occurred.

/etc/init.d/local
```
#!/bin/sh
sleep 10
ssh -X <client_user_name>@<client_computer_name>.<domain_name> 'DISPLAY=:0 notify-send "Server is up" -i "/usr/share/icons/Humanity/apps/48/bash.svg"' > /home/<server_user_name>/error.log 2>&1
echo $(date) - Running >> /home/<server_user_name>/test.run
exit 0
```Example:
 
/etc/init.d/local
```
#!/bin/sh
sleep 10
ssh -X ssh -X voltron43@voltron43-laptop.local 'DISPLAY=:0 notify-send "Server is up" -i "/usr/share/icons/Humanity/apps/48/bash.svg"' > /home/voltron43/error.log 2>&1
echo $(date) - Running >> /home/voltron43/test.run
exit
```**[SIZE=5]Revert[/SIZE]**

Removing all applications and settings files.

**[SIZE=4]Client Computer[/SIZE]**

**1.  Remove openssh server**
```
sudo apt-get -y --force-yes --purge remove openssh-server
```**2.  Remove the SSH keys**

[SIZE=4]Server Computer[/SIZE]
[B]
1.  Remove Notify OSD
[/B]```
sudo apt-get -y --force-yes --purge remove notify-osd
```**2.  Remove local file**

[COLOR=Red]**Warning**:[/COLOR] **this assumes that the local file did not exist prior to this tutorial!**
```
sudo rm /etc/init.d/local
```**3.  Remove degugging files**
```
sudo rm ~/error.log && sudo rm ~/test.run
```

---

