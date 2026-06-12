---
title: "Load Apache sites with priority"
date: 2006-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by gymsmoke on 2006-04-23
Apache2 uses sites-available and sites-enabled directories for loading the web sites.  The default site gets a 'priority' of 000, but the a2ensite script does not allow you to assign these priority numbers to successive sites, unless you name them that way in sites-available... Why?  Don't know, but I have a solution...
I set this script in bash (since that is the script that Ubuntians normally use...

Type this into a file (you can call it whatever you want).  I called mine jd_ensite

#!/bin/bash
MINPARAMS="2"
if [ $# -lt "$MINPARAMS" ]
then
  echo "Usage: jd_ensite <site-name> <priority>"
  echo "First look in /etc/apache2/sites-available to determine which site you want to enable"
  echo "Next look in /etc/apache2/sites-enabled to see what priority number you'd like"
  echo "Then enter jd_ensite <site-name> <priority>"
  exit 0
fi

SYSCONFDIR='/etc/apache2'

if [ -e $SYSCONFDIR/sites-enabled/$1 -o -e $SYSCONFDIR/sites-enabled/"$2"-"$1" ]
then
  echo "This site is already enabled!"
  exit 0
fi

if ! [ -e $SYSCONFDIR/sites-available/$1 ]
then
  echo "This site does not exist!"
  exit 1
fi

ln -sf $SYSCONFDIR/sites-available/$1 $SYSCONFDIR/sites-enabled/"$2"-"$1"

echo "Site $SITENAME installed; run /etc/init.d/apache2 reload to enable."


Save and exit the file.
Then type sudo chmod +x <your_file_name>

now, put this somewhere in your path (/usr/local/bin is where I put mine)

now type sudo <your_file_name> site-name <priority>

That's it... the site is enabled the same way that a2ensite does!

(don't forget to reload Apache2 afterwards, like this)
sudo apache2ctl restart

Your new site is enabled, and should be able to be seen (if your site file is correct)

---

