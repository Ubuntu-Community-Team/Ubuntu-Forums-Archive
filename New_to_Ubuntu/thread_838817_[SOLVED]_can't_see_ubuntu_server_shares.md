---
title: "[SOLVED] can't see ubuntu server shares"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by UbuntuNerd on 2008-06-23
hello im new to linux so please  forgive me if don't make any sense sometimes any way i install ubuntu desktop on my main box and ubuntu server on a spare machine i also got a vista pc in my home network i olmost got everything running good except for samba i can see the server but when i try to open the folders is nothing there am i missing something can somebody help?

---

### Post by superprash2003 on 2008-06-23
in your ubuntuserver type smbtree and post output

---

### Post by UbuntuNerd on 2008-06-23
thanks i can see my shares on the server now but there is another problem now im prompted with a loging screen and when i enter user name and password i get acces denied(i know i got the right password):confused:

---

### Post by superprash2003 on 2008-06-24
while setting up samba, have you added samba users???and inserted them to the smbusers file??you may have your samba configured incorrectly..
for reference : [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by ukripper on 2008-06-24
If you access your server via **smb://you-server-ip** 
example:
**smb://[COLOR="Red"]192.168.1.10[/COLOR]**                          -->replace this ip address with your server's ip.

now check if you can access your shares?

---

### Post by UbuntuNerd on 2008-06-24
hello im a little new to linux so please correct me if im wrong anyway i have an Ubuntu server and Ubuntu desktop also i have a vista machine in my home network i installed samba and firestarter and i can see all the shares from all pc's but when i try to acces them im prompted with a login screen i used the right user name and password but got access denied any ideas i also try smbtree here is the output

WORKGROUP
	\\UBUNTU         		
		\\UBUNTU\share folder   	
		\\UBUNTU\PDF            	PDF
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
		\\UBUNTU\print$         	Printer Drivers
		\\UBUNTU\homes          	Home Directories
	\\THEMONKEY-PC   		
		\\THEMONKEY-PC\Users          	
		\\THEMONKEY-PC\Send To OneNote 2007	Send To OneNote 2007
		\\THEMONKEY-PC\Public         	
		\\THEMONKEY-PC\print$         	Printer Drivers
		\\THEMONKEY-PC\My Pictures    	
		\\THEMONKEY-PC\IPC$           	Remote IPC
		\\THEMONKEY-PC\D$             	Default share
		\\THEMONKEY-PC\C$             	Default share
		\\THEMONKEY-PC\C              	
		\\THEMONKEY-PC\ADMIN$         	Remote Admin
	\\JAIME-DESKTOP  		
cli_start_connection: failed to connect to JAIME-DESKTOP<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME

---

### Post by ukripper on 2008-06-24
> **jperez78 said:**
> hello im a little new to linux so please correct me if im wrong anyway i have an Ubuntu server and Ubuntu desktop also i have a vista machine in my home network i installed samba and firestarter and i can see all the shares from all pc's but when i try to acces them im prompted with a login screen i used the right user name and password but got access denied any ideas i also try smbtree here is the output

WORKGROUP
	\\UBUNTU         		
		\\UBUNTU\share folder   	
		\\UBUNTU\PDF            	PDF
		\\UBUNTU\IPC$           	IPC Service (ubuntu server (Samba, Ubuntu))
		\\UBUNTU\print$         	Printer Drivers
		\\UBUNTU\homes          	Home Directories
	\\THEMONKEY-PC   		
		\\THEMONKEY-PC\Users          	
		\\THEMONKEY-PC\Send To OneNote 2007	Send To OneNote 2007
		\\THEMONKEY-PC\Public         	
		\\THEMONKEY-PC\print$         	Printer Drivers
		\\THEMONKEY-PC\My Pictures    	
		\\THEMONKEY-PC\IPC$           	Remote IPC
		\\THEMONKEY-PC\D$             	Default share
		\\THEMONKEY-PC\C$             	Default share
		\\THEMONKEY-PC\C              	
		\\THEMONKEY-PC\ADMIN$         	Remote Admin
	\\JAIME-DESKTOP  		
cli_start_connection: failed to connect to JAIME-DESKTOP<20> (0.0.0.0). Error NT_STATUS_BAD_NETWORK_NAME

on your server in termianl do following :

```
sudo smbpasswd -L -a yourusername
```
```
sudo smbpasswd -L -e yourusername
```
replace youusername with the username you are currently logged in with on ubuntu server

and then ```
sudo /etc/init.d/samba restart
```

now try to acces your samba shares from client machine

---

### Post by UbuntuNerd on 2008-06-24
yeah im jumping in my chair i can see all of my shares and access them thank you so much :popcorn:

---

### Post by nukem_bbs on 2008-09-28
> **UbuntuNerd said:**
> yeah im jumping in my chair i can see all of my shares and access them thank you so much :popcorn:

ok, i`ve got another one, guys. smbtree has all my shares, computer is in the network places, but `empty` with no shared directories/printers. weird stuff for me. =) shall i post smb.conf? cheers

---

