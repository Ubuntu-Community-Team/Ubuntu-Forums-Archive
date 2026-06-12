---
title: "How to Upgrade Ubuntu Server from Feisty to Hardy,Succesfully"
date: 2008-05-10
forum: Outdated Tutorials &amp; Tips
---

### Post by nimes on 2008-05-10
**Step 1: Feisty to Gusty Upgrade**
first be sure your feisty up-to-date
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
if everything ok, ready for  upgrade to gusty. 

nano /etc/apt/source.list

all change "feisty" to "gutsy"

save and exit (ctrl-x, yes)

sudo apt-get update
sudo apt-get dist-upgrade


(one package doesn't upgrade : mailscanner 
but this step its fix: 
nano /etc/init.d/mailscanner

around 124 line (do_stop function) add 'exit 0'

do_stop()
{ exit 0 
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
	start-stop-daemon --stop --retry=TERM/30 --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2

  # Remove lockfile for cronjobs
	if [ $RETVAL -eq 0 ]; then
	    rm -f /var/lock/subsys/mailscanner
	    touch $stopped_lockfile
	fi

}


save and exit.

and re-apply 
sudo apt-get dist-upgrade 

command. its works. there some warning related with mailscanner but not important (for now)

and reboot

my server is gutsy, now.

**step 2. Gutsy to Hardy upgrade**

nano /etc/apt/source.list

all change "gutsy" to "hardy"

save and exit (ctrl-x, yes)

sudo apt-get update
sudo apt-get dist-upgrade 

one package doesn't upgrade : mailscanner  :(
but no problem :)

reboot

**mailscanner fix:**

first backup your mailscanner folder. (/etc/mailscanner)

sudo cp -R /etc/mailscanner /etc/mailscanner_backup


sudo apt-get remove --purge mailscanner

(if removing results same error,  around 124 line (do_stop function) add 'exit 0')

wget [http://http.us.debian.org/debian/pool/main/m/mailscanner/mailscanner_4.68.8-1_all.deb](http://http.us.debian.org/debian/pool/main/m/mailscanner/mailscanner_4.68.8-1_all.deb)

sudo dpkg -i mailscanner_4.68.8-1_all.deb

and 

nano /etc/default/mailscanner

# Uncomment this line once MailScanner has been fully configured.
#
run_mailscanner=1

save and exit..

replace your backup mailscanner folder (/etc/mailscanner)

sudo cp -R /etc/mailscanner_backup /etc/mailscanner

/etc/init.d/mailscanner start

ta ta taaaaaa. its work !!!!


your server are upgraded to Hardy Heron LTS

---

