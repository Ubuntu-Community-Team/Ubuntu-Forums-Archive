---
title: "Evolution at the command line"
date: 2007-11-04
forum: Programming Talk
---

### Post by brcre on 2007-11-04
evolution mailto:joe@somewhere.net
 Starts Evolution and begins composing a message to the e-mail address listed.
I was curious if there is a way to send a message auto created in an Evolution GUI?

```
evolution mailto:person@att.net?subject=Test\&body=Some%20crazy%20story%20stuff
```

Next step will be to send the message that we created:
%11%0D = ctrl return -> Doesn't work still looking for the correct solution

%20 = space
%0D%0A = line breaks
%0A = a line break in your message body (the middle one is a zero, nut o as in opera)
\&attach="/path/to/file" If you want more attachments just keep adding

Here is a solution that I was attempting with the train of thought shown above, however that seems to be a dead end since it never completely sends the message.  Below does:

Using your favorite text editor copy and paste this in there. Then change the generic information to your information as required.  Once it is saved chmod 755 the file and set up a cron job or script to execute this file as needed.  It was tested on Ubuntu 9.04 - the Jaunty Jackalope with Evolution.
```

#!/bin/bash
date '+From username@gmail.com %a %b %e %T %Y'   > /tmp/autoemail
echo "Subject: Auto_Create_Email" >> /tmp/autoemail
echo "From: A_User <username@gmail.com>" >> /tmp/autoemail
echo "To: Sent_To_Person@gmail.com, 2nd_Person@micron.com" >> /tmp/autoemail
echo "">> /tmp/autoemail
echo "This message was autocreated" >> /tmp/autoemail
echo "2nd Line" >> /tmp/autoemail
echo "">> /tmp/autoemail
cat /tmp/autoemail >> /home/user/.evolution/mail/local/Outbox
rm -f /tmp/autoemail
exit 0

```

---

### Post by brcre on 2007-11-04
Sync Palm Z22 with Evolution:  Running Gutsy 7.10
  verified this still works with: Jaunty Jackalope 9.04 (10/15/2009)
 1. Check which Kernel version you're running
     uname -r
     *2.6.22-14-generic 6.22 has something wrong with it and won't find the Palm device.  If you are running this you'll need to change your Kernel
2. sudo vi /etc/udev/rules.d/10-custom.rules I found to be unnecessary.  Also if you've tried this step a few times you might want to remove all the entries you've added at: /etc/udev/rules.d
    *BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"
    *BUS=="usb", SYSFS{product}=="Palm Handheld*", KERNEL=="ttyUSB[13579]", NAME="pilot", GROUP="uucp", MODE="0660"
3. sudo vi /etc/modules
   After the last line add
   visor
4. sudo modprobe visor
5. Now go to evolution
   *Choose Menu items: Edit/Synchronization Options
6. Plug in the Palm device to the USB cable and press HotSync

The only problem I've had with this is that I get endless amounts of Palm Screens if I leave it plugged in.  So as soon as I'm doing I get it unplugged.
To check if your connection is working try:
ls -l /dev/ttyUSB*  or
ls -l /dev/pilo*
Something must show up if the rule is working.

under gnome-pilot settings:
PDAs tab:
Name: Brent_Pilot
ID: 23574
Ownder: Brent
*I got these setting by clicking on the Get From PDA button.  Then I changed the device name and the file path at the bottom of this screen.
Brent_Pilot
/home/brcre/Brent_Pilot

Devices tab:
Cradle USB

Conduits Tab:
Backup Enabled
EAddress Synchronize
ECalendar Synchronize
EMemos Synchronize
EToDo Synchronize
Everything else listed is Disabled

If you find that after syncing the device once it won't work after that try:
System/Administration/System Monitor
find gpilotd in the Processes tab and End Process
Otherwise you can log out and back in if you don't have the remember current session selected at: System/Preferences/Sessions/Session Options
Else reboot your system.

---

### Post by brcre on 2007-11-04
To Send Mail Automatically
This worked for Feisty Fawn but after upgrading to Gutsy Gibbon it doesn't.  Now at Ubuntu 9.04 - the Jaunty Jackalope it does:
The example given works with gmail accounts.

Synaptic Package Manager: ssmtp
cd /etc/ssmtp
```
sudo vi ssmtp.conf
```

root=user_name@gmail.com
mailhub=smtp.gmail.com:587
UseSTARTTLS=YES
AuthUser=user_name
AuthPass=mail_password
rewriteDomain=gmail.com
FromLineOverride=YES
hostname=hostname can be discovered with ```
hostname -f
```

(:wq - to save and exit)
```
mail -s "Test" Going_To@hotmail.com
Testing Mail...
.
CC:

```
now the cron can be set up and the programs written can have email abilities.

---

### Post by brcre on 2007-11-05
Search Assistant
```
#!/bin/bash 
# name of the script 'l'   just the letter l

# a little bit of help in case of misuse 
if [ $# -lt 2 ] 
    then 
       echo "usage: l /directory pattern" 
       echo "example: l /etc config" 
       return 1
       exit 
fi

# $DIR is the first argument, the path to the directory 
DIR=$1

# $SEARCH is what you are looking for, and it's the second argument 
SEARCH=$2

# $RED sets the text to inverted red, changing the capabilities of the terminal via terminfo parameters 
# setaf 1 = red, smso = inverted 
RED=`tput setaf 1; tput smso`

#  $NORMAL returns text to normal attributes 
NORMAL=`tput sgr0`

# 
ls -1 $DIR | sed s/"$SEARCH"/"$RED$SEARCH$NORMAL"/ | grep $SEARCH | sort -u
```

---

