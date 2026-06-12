---
title: "Network Problem"
date: 2006-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Kea on 2006-04-30
Hi All, 1st post im running Ubuntu 5.4 4days old have run into a  slight snag, have shared network connection with XP can access the net but cant see the other PC or find shared folders. Im a complete bunny with this OS but its fun i have run testparm and it give this error, help with eiither would be great.

root@Wellongton:/home/daviddaveross # testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
params.c:Section() - Empty section name in configuration file.
params.c:pm_process() - Failed.  Error returned from params.c:parse().
Error loading services.
root@Wellongton:/home/daviddaveross #

Cheers Kea

---

### Post by Koybe on 2006-04-30
This is more samba then network related post. Anyway, it seems that you have a section in your smb.conf with nohting in it. Just remove or comment it.
If you want more help, just post your /etc/samba/smb.conf file here.

You should find probably at the end a section starting like this :
[some_share]
And nothing below.

Just comment it or set your share.

---

### Post by Kea on 2006-04-30
[QUOTE=Koybe]This is more samba then network related post. Anyway, it seems that you have a section in your smb.conf with nohting in it. Just remove or comment it.
If you want more help, just post your /etc/samba/smb.conf file here.

You should find probably at the end a section starting like this :
[some_share]
And nothing below.

Just comment it or set your share.[/QUOTE]
Thanks fo the quick response, will give this a try.Cheers Kea

---

### Post by Kea on 2006-04-30
[QUOTE=Kea]Thanks fo the quick response, will give this a try.Cheers Kea[/QUOTE] 

I came up with this
		TDBPRIORITY=low
	fi

	db_input "$TDBPRIORITY" samba/tdbsam || true
fi

# We vary the priority of the next question depending on whether
#	the password database already exists...
if [ -e /etc/samba/smbpasswd -o -e /var/lib/samba/passdb.tdb ]; then
	PRIORITY="low"
else
	# If 'encrypt passwords' is true in smb.conf, and smbpasswd
	# does not exist, default to yes here.
	FILE=/etc/samba/smb.conf
	if [ -f "$FILE" ]; then
		ENCRYPT=`smbconf_retr "encrypt passwords"`
	        if [ "$ENCRYPT" ]; then
			ENCRYPT=`echo $ENCRYPT | tr '[A-Z]' '[a-z]'`
			if [ "$ENCRYPT" = "yes" ]; then
				ENCRYPT=true
			fi
			if [ "$ENCRYPT" = "no" ]; then
				ENCRYPT=false
			fi
		fi
                db_set samba/generate_smbpasswd "$ENCRYPT"
        fi
	PRIORITY="medium"
fi

db_input $PRIORITY samba/generate_smbpasswd || true
db_go
Might give it a miss, seems to be more trouble than its worth. Thanks.Kea

---

### Post by Koybe on 2006-04-30
This is some kind of init script. It isn't the smb.conf :o
Are you sure?
If it's your smb.conf there is no way for it to work :P
Then ask for someone with a clean one. I don't have one by hand right now.

---

### Post by geek.de.nz on 2006-04-30
Not sure about normal Ubuntu with gnome. But I think you want to open windows shares right? This, you can do with (Kubuntu) Konqueror and writing "smb://hostname" in the address bar. In gnome it should be similar in the default file browser. If that doesn't work, you can always use the command line interface smbclient (try "man smbclient" in a shell).

If you want to install konqueror in the normal Ubuntu type:
```
sudo apt-get install konqueror
``` in a shell and then start konqueror with:
```
konqueror &
``` in a shell or with <alt+f2>

Hope this helps. :-)

Also, search the forum before you post new questions ;).

---

### Post by Zimmer on 2006-04-30
Hi, try this guide, it solved my Samba issues.
[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)
Also , I have a few threads about which illuminate the Samba User issues.

You need a Samba User on the Linux box.
See these links for Info... post #10
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)

This may be useful for you, too
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
and of course the troubleshooting section at Samba.org
[http://us4.samba.org/samba/docs/man/...diagnosis.html](http://us4.samba.org/samba/docs/man/...diagnosis.html)

---

### Post by Kea on 2006-04-30
[QUOTE=Zimmer]Hi, try this guide, it solved my Samba issues.
[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)
Also , I have a few threads about which illuminate the Samba User issues.

You need a Samba User on the Linux box.
See these links for Info... post #10
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)

This may be useful for you, too
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
and of course the troubleshooting section at Samba.org
[http://us4.samba.org/samba/docs/man/...diagnosis.html](http://us4.samba.org/samba/docs/man/...diagnosis.html)[/QUOTE]
 
Thanks for all the suggestion have copied the links and will try and fix later. Cheers Kea

---

