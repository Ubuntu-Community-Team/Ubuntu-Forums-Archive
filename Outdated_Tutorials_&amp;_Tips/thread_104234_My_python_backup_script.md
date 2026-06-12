---
title: "My python backup script"
date: 2005-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by viscount on 2005-12-15
I've finished the backup script, it can now do the following:
- incremental backups.
- automatically deletes out of date backups
- easily restores the system based off the most recent backup

(Obviously there is probably a lot more that could be done, but those
were my intentions when I started writing and I have now accomplished
them so this is done, at least for now.)

Here is how to do it...

WARNING:testers beware!
The script needs 4 variables to be adjusted: OFFSET, BKDIR, EXCLUDE and TARGET
These are located in weekly.config
You must adjust weekly_config.py so that it knows where to look for weekly.config

OFFSET is the time to keep old backups before deleting them (default:4weeks).
BKDIR is where you wish to store your backups.
EXCLUDE is a list of files you do not wish to have backed up.
TARGET is the directory you wish to have archived.

1. Copy weekly_backup.py
2. Copy weekly.conf 
3. Make a backup directory: mkdir /backup

[B][I]WARNING: do not use your backup directory for anything
other than backups, any file older than 4 weeks inside
the backup directory will be deleted.[/I][/B]

4. Adjust the script variables OFFSET, BKDIR, EXCLUDE and TARGET
5. Chmod +x weekly_backup.py
6. sudo crontab -e

A text editor (nano) will open, type the following:
0 1 * * 1 /path/to/copy/of/weekly_backup.py

8. Save and close nano: Ctrl-o (to save) and Ctrl-x (to close)
9. All finished, sit back and relax :) 

Your system will do an incremental backed up once per week, and after 
4 weeks the oldest backup will be deleted.

You should not need to worry about system resources because the process
is set to a low nice value which means you probably wont notice when
the backup is happening.

To restore the most recent backup simply do the following:
# ./weekly_backup.py -R

If you want to restore an older backup you must do so by hand
you can look at the weekly_backup.py file to see how this can be done.

ENJOY! 

(sorry for not posting a link for downloading the files, I realize this means
many people who would have other wise been interested are probably not
going to bother copying and pasting a file. I'll try to see if I can get it up on 
sourceforge or somewhere to make it easier to download.)
weekly_backup.py
```

#!/usr/bin/env python
import os
import sys
import time
import datetime
from stat import *
from optparse import OptionParser

#PROGRAM: Weekly_Backup.py
#AUTHOR: Alexander Combas
#ORIGIN: 15Dec2005
#VERSION: 0.03
#LAST UPDATE: 23Dec2005
#
#INSTRUCTIONS: set WEEKLY_CONFIG to the location of the weekly.config file
#              then edit the weekly.config file

WEEKLY_CONFIG = "/home/viscount/work/scripts/Weekly/weekly.config"


usage = "%prog -R | -D"
mydescription = "weekly_backup.py is intended to be a simple yet powerful backup tool. To backup your system edit this script so that the WEEKLY_CONFIG variable points to the weekly.config file then edit the weekly.conf file so that it has all the correct information, afterwards set weekly_backup.py to run automatically every week with cron or crontab without any command-line options."
myversion = "Weekly_Backup-0.03"

def make_new_backup(config_dict,image):
    """mk_new_backups() will create a new backup every time it is run.
    The backups are named by date.
    """
    archive_name = config_dict['bkdir'] + "/BACKUP-" + datetime.datetime.now().strftime("%d%h%Y") + ".tar.gz"
    
    os.system("nice -10 tar -g '%s' -czvf %s %s %s" % (image.name, archive_name, config_dict['exclude'], config_dict['target']))


def delete_old_backups(location,integer,name):
    """rm_old_backups() will open a directory and deletes
    all of the files inside that are older than specified in weekly.config 
    """
    print "Deleting old backups..."
    try:
        backups = os.listdir(location)
    except OSError, (errno,strerror):
        print >>sys.stderr, "%s is not a list of files %s" % (location,strerror)
        sys.exit(1)
        
    #Takes every file in the dir, appends the path, then
    #compares the ctime of the file to the deadline, deleting
    #files older than specified.
    for f in backups:
        try:
            f = os.path.join(location,f)
        except OSError, (errno,strerror):
            print >>sys.stderr, "%s could not be joined %s" % (f,strerror)
            sys.exit(1)

        try:
            f_time = os.stat(f)[ST_CTIME]
        except OSError, (errno,strerror):
            print >>sys.stderr, "%s couldn't be stat'ed %s" % (f, strerror)
            sys.exit(1)

        if integer > f_time:
            try:
                os.remove(f)
                print "%s was deleted at %s" % (f,datetime.datetime.now().strftime("%H%M-%d%h%Y"))
            except OSError, (errno,strerror):
                print >>sys.stderr, "%s could not be removed %s" % (f,strerror)
                sys.exit(1)
        else:
            print "%s has not yet expired." % f


def restore_from_backup(config_dict):
    """Todo: everything
    """
    try:
        backups = os.listdir(config_dict['bkdir'])
    except OSError, (errno,strerror):
        print >>sys.stderr, "%s is not a list of files %s" % (config_dict['bkdir'],strerror)
        sys.exit(1)

    #put the newest backup at the top of the list
    backups.sort()
    backups.reverse()
    os.system("tar -xvf %s -C %s" % ((config_dict['bkdir'] + "/" + backups[0]), "/"))    


def set_configs(f):
    """ set_configs() reads the weekly.conf file, then transfers all the
    values from the dictionary "d" to the list "l".
    """
    try:
        dct = eval(open(f).read())
        return dct
    except IOError, (errno,strerror):
        print >>sys.stderr, "%s could not be opened %s" %(f,strerror)
        sys.exit(1)

    f.close()

def test_snap(f):
    """test_snap() opens and returns the image_snapeshot for tar
    or it throws an error and exits
    """
    try:
        foo = open(f,'a')
        return foo
    except IOError, (errno,strerror):
        print >>sys.stderr, "%s could not be opened %s" %(f,strerror)
        sys.exit(1)

def main():
    """Open weekly.config and set variables.
    Parse command line options.
    Call functions according to specific options.
    """

    conf = set_configs(WEEKLY_CONFIG)
    snap_img = conf['bkdir'] + "/001BK_SNAP.data"
    deadline = int(time.time()) - conf['offset']
    
    parser = OptionParser(usage,version=myversion,description=mydescription)
    parser.add_option("-R", "--restore", help="restore system from the most recent backup", action="store_true", dest="restore")
    parser.add_option("-D", "--delete", help="delete backups that are %i day(s) old" % (conf['offset']/60/60/24), action="store_true", dest="delete")
        
    (options,args) = parser.parse_args()
    if options.restore and options.delete:
        parser.error("options -D and -R may not be run together.")
    elif options.restore:
        restore_from_backup(conf)
    elif options.delete:
        i = test_snap(snap_img)
        delete_old_backups(conf['bkdir'],deadline,i.name)
        i.close()
    else:
        i = test_snap(snap_img)
        make_new_backup(conf,i)
        delete_old_backups(conf['bkdir'],deadline,i.name)
        i.close()

if __name__ == '__main__':
	main()

```

weekly.config
```

{
#SET BACK_UP_DIR: this is the path to the folder where you 
#will save your backups after they have been created
'bkdir': '/home/viscount/backups',

#SET OFFSET: old backups will be deleted based upon this variable,
#offset is set in seconds. The default is four weeks.
#format: 4weeks = 60seconds * 60minutes * 24hours * 28days
'offset':  (60 * 60 * 24 * 28),

#SET EXCLUDE: list file and folders you do not wish to have backed up.
'exclude': '--exclude=/home/viscount/Games/armyops --exclude=/home/viscount/Games/et-linux-2.60.x86.run --exclude=/home/viscount/Games/firefox',


#SET TARGET: backup will start at the target directory and
#work its way up the tree.
'target': '/home/viscount/Games'
}

```

---

