---
title: "Script to change fstab entries to UUID"
date: 2010-06-13
forum: Programming Talk
---

### Post by Buuntu on 2010-06-13
[CENTER][LEFT][B]

FSTAB: /dev - UUID entries[/B]

[/LEFT]
[/CENTER]
If you run an older version of Ubuntu or simply have a fstab with /dev/* entries for whatever reason, you might benefit from this script.

You can manually change the entries of your fstab file to UUID format by running
```
ls -l /dev/disk/by-uuid
```and then manually pasting the results into your /etc/fstab file.

This is tedious however, and you have to learn a little bit (not much, but still) about the format in your fstab file.
This script will automatically change all entries of the form /dev/[sh]d[a-z][0-9] to their respective UUID formats.
You can copy and paste it into your own file, or download it as an attachment.

```
#!/bin/bash
# This script will change all entries of the form /dev/sd* in /etc/fstab to their appropriate UUID names
# You must have root privelages to run this script (use sudo)
if [ `id -u` -ne 0 ]; then                                              # Checks to see if script is run as root
        echo "This script must be run as root" >&2                      # If it isn't, exit with error
        exit 1
fi

cp /etc/fstab /etc/fstab.backup
sed -n 's|^/dev/\([sh]d[a-z][0-9]\).*|\1|p' </etc/fstab >/tmp/devices   # Stores all /dev entries from fstab into a file
while read LINE; do                                                     # For each line in /tmp/devices
        UUID=`ls -l /dev/disk/by-uuid | grep "$LINE" | sed -n 's/^.* \([^ ]*\) -> .*$/\1/p'` # Sets the UUID name for that device
        sed -i "s|^/dev/${LINE}|UUID=${UUID}|" /etc/fstab               # Changes the entry in fstab to UUID form
done </tmp/devices
cat /etc/fstab                                                          # Outputs the new fstab file
printf "\n\nWrite changes to /etc/fstab? (y/n) "
read RESPONSE;
case "$RESPONSE" in
        [yY]|[yY][eE][sS])                                              # If answer is yes, keep the changes to /etc/fstab
                echo "Writing changes to /etc/fstab..."
                ;;
        [nN]|[nN][oO]|"")                                               # If answer is no, or if the user just pressed Enter
                echo "Aborting: Not saving changes..."                  # don't save the new fstab file
                cp /etc/fstab.backup /etc/fstab
                rm /etc/fstab.backup
                ;;
        *)                                                              # If answer is anything else, exit and don't save changes
                echo "Invalid Response"                                 # to fstab
                echo "Exiting"
                cp /etc/fstab.backup /etc/fstab
                rm /etc/fstab.backup
                exit 1
                ;;
esac
rm /tmp/devices
echo "DONE!"
```To run the script, save it to a file and give it executable permissions.  You must have root privelages to run it, so just use sudo.
```
chmod +x UUID_fstab.sh
sudo ./UUID_fstab.sh
```You can also run it by typing
```
sudo /bin/bash UUID_fstab.sh
```Hopefully this is useful for you.  
Enjoy.

(Tested on Ubuntu 10.04)

---

### Post by new_tolinux on 2010-06-13
I really would like someone who actually does understand the code you made to have a look at it, since my knowledge in bash scripting is very limited.

If the script's ok I save a copy of it on my fileserver, since I went through a lot of trouble to get my USB-drive in fstab.

---

### Post by Bachstelze on 2010-06-13
> **new_tolinux said:**
> 
If the script's ok I save a copy of it on my fileserver, since I went through a lot of trouble to get my USB-drive in fstab.

The script seems OK, but it will not ad your drive to your fstab for you, it will only "convert" old-style /dev/* entries to UUID ones.

---

### Post by new_tolinux on 2010-06-13
> **Bachstelze said:**
> The script seems OK, but it will not ad your drive to your fstab for you, it will only "convert" old-style /dev/* entries to UUID ones.
Thanks.

I guess I don't really need that, since the newer versions seem to do that by default (9.10 running) but I'll keep it anyway.
Although it doesn't add the USB-drive, it does prevent typos if I can add the correct /dev/.... entry instead of the UUID=.... entry.

---

### Post by Buuntu on 2010-06-13
Yeah sorry if that was confusing...

---

### Post by new_tolinux on 2010-06-13
> **Buuntu said:**
> Yeah sorry if that was confusing...
No problem, thanks anyway for the script.
Like I said, while typing an UUID-code it's easy to miss a character, number or have typos.

---

### Post by Bachstelze on 2010-06-13
> **new_tolinux said:**
> No problem, thanks anyway for the script.
Like I said, while typing an UUID-code it's easy to miss a character, number or have typos.

That's what copy-and-paste is for. ;)

---

### Post by new_tolinux on 2010-06-13
> **Bachstelze said:**
> That's what copy-and-paste is for. ;)
Since I do most of the configuring with putty that doesn't really work that well ;)

---

### Post by COKEDUDE on 2011-03-10
Nice tips :).

---

