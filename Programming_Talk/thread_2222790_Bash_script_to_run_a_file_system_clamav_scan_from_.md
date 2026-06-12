---
title: "Bash script to run a file system clamav scan from the terminal or as a cron job"
date: 2014-05-08
forum: Programming Talk
---

### Post by richard51 on 2014-05-08
Here is a little bash script I wrote to perform a clamscan. You can either run it from a terminal, or as a cron job.

You may use it if you find it useful, or alter it to your needs. And **NO**, I am not a bash programmer, I only learnt enough to get the job done. I am sure there's many other ways to do the same job, maybe better.

```
#!/bin/bash

# Clamav Virus Scan By Richard51 #

# Global variables
return_code=0

# Check for root privileges
if [[ $EUID -ne 0 ]]; then
    echo "Virus scan: only root can do that" 1>&2
    exit 1
fi

# Display initializing message
echo ""; echo "Initializing virus scan..."; echo ""

# Prepare virus scan log
sudo rm -f /var/log/virus-scan.log
sudo touch /var/log/virus-scan.log
sudo chown root:adm /var/log/virus-scan.log
sudo chmod 640 /var/log/virus-scan.log

# Display updating message
echo "Updating virus definitions..."; echo ""
sudo freshclam
return_code=$?

# Display updating failed status message and exit, if update failed
if [ $return_code -ne 0 ]; then
    echo ""; echo "Failed to updating virus definitions... Virus scan aborted"; echo ""
    exit $return_code
fi

# Commence virus scan
echo "Update completed"; echo ""; echo "Commencing virus scan... (this may take some time)"; echo ""
sudo clamscan -r / --log='/var/log/virus-scan.log' --exclude='^/var/log/virus-scan\.log$' \
--exclude-dir='^/sys|^/proc|^/mnt|^/media|^/dev' \
--exclude-dir='^/home/[^/]+/\.gvfs|^/export/[^/]+/\.gvfs|^/root/\.gvfs|^/run/user/[^/]+/gvfs'
return_code=$?

# Display virus scan status message
if [ $return_code -ne 0 ] && [ $return_code -ne 1 ]; then
    echo "";echo "Failed to complete virus scan"; echo ""
else
    echo ""; echo -n "Virus scan completed successfully, "
    if sudo grep -rl 'Infected files: 0' /var/log/virus-scan.log > /dev/null 2>&1; then
        echo "NO INFECTIONS FOUND"; echo ""
    else
        echo "INFECTIONS FOUND (please review the '/var/log/virus-scan.log' file)"; echo ""
    fi
fi

exit $return_code
```
P.S *Don't forget to set the execute bit on the file*.

Note: This doesn't remove the virus, it just logs them (*you can add the --remove=yes option, but I would advise against it*).
*You can view the log via the terminal using: **sudo tail /var/log/virus-scan.log**

Enjoy!

---

