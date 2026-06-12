---
title: "[SOLVED] can acces shares on ubuntu network"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by UbuntuNerd on 2008-06-24
please correct me if im wrong anyway i have an Ubuntu server and Ubuntu desktop also i have a vista machine in my home network i installed samba and firestarter and i can see all the shares from all pc's but when i try to acces them im prompted with a login screen i used the right user name and password but got access denied any ideas i also try smbtree here is the output

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
 can anyone help thanks!!:confused:

---

### Post by superprash2003 on 2008-06-24
have you added samba users while configuring samba?

---

