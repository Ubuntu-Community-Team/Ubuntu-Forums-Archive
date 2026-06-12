---
title: "Back up script"
date: 2005-12-22
forum: Outdated Tutorials &amp; Tips
---

### Post by punkrockguy318 on 2005-12-22
I just wrote a simple python backup script that others may find useful.  Try it for yourself!
```

#!/usr/bin/env python
# sweetbackup version 0.1 - simple python script to backup the system using rsync
# written by lukas sabota
# 12/22/05
# 
# notes:
# * check out the globals and adjust them to your satisfaction
# * touch a backup_ok file into the directory of your back.  You may ask why.  
#       This is to ensure that the proper media is mounted to the filesystem.  It's a big
#       waste of space to backup the entire system onto the same media
# * if your backup fails you'll get a notification on your desktop
# * erm.. that's it.  i think
#
# todo:
# * maybe a conffile might be better than the globals
# * a log
# * some sort of backup notification of failure besides the file in the home folder
# * comment some stuff
# changes:
# 0.1 - initial release.  it's sweet


import os,sys,datetime,time

# important globals
backupdirs=['/etc', '/root', '/home', '/var/log', '/var/www']
dest="/media/usbdisk/backup"
binary='/usr/bin/rsync'
errorfile=os.environ['HOME']+'/Desktop/backupERROR'
options='-av --delete'

def oops(error ,n):
  message = 'Error code '+str(n)+': '+error
  print message
  file = open(errorfile, 'w')
  file.write(str(datetime.datetime.now()))
  file.write('\n')
  file.write(message)
  file.write('\n')
  file.close
  sys.exit(n)

print 'rsync: ',
if os.access(binary, os.X_OK):
  print 'okay =)'
else:
  print 'nope =('
  oops('The rsync could not be accessed at '+binary, -1)

print 'file: ',
if os.access(dest+'/backup_ok', os.F_OK):
  print 'okay! =)'
else:
  print 'nope =('
  oops(dest+'/backup_ok'+' does not exist.  Please create this file so this script knows that the installation media is available.', -2)

print 'write: ',
if os.access(dest, os.W_OK):
  print 'okay =)'
else:
  print 'nope =('

  oops('Write access is denied to '+dest, -3)
  
for x in backupdirs:
  print 'read ', x, ': '
  if os.access(x, os.R_OK):
    
    print 'good :)'
  else:
    print 'nope =('
    oops('Read access is not granted to'+x, -4)
command = binary + ' ' + options
for x in backupdirs:
  command = command + ' ' + x
command = command + ' ' + dest
if os.system(command) == 0:
  print 'success!'
  sys.exit(0)
else:
  oops('Rsync error.  Backup FAILED.', -5)
  
```

---

### Post by ubuntu_demon on 2005-12-23
thnx for your script :)

for an easy graphical backup solution :
$sudo apt-get install sbackup

You can run it from system->administration

---

### Post by viscount on 2005-12-23
Seems python backup scripts are all the rage now a days, I find that rather odd.

But I guess it makes sense being that its a good way to cut your teeth
on a new programming language.

[Here is my python backup script.]("http://http://www.ubuntuforums.org/showthread.php?p=577644#post577644") :D

I like the fact you used rsync in yours, i think its a slightly better choice
than tar which is what I went with.

---

### Post by SqdnGuns on 2005-12-25
[QUOTE=viscount][Here is my python backup script.]("http://www.ubuntuforums.org/showthread.php?p=577644#post577644") :D[/QUOTE]

Your URL was fooked so I fixed it in the "Quote"...................it was going to the Evil Empire.  :(

---

