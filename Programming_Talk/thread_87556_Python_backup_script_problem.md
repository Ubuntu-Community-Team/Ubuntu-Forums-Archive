---
title: "Python backup script problem"
date: 2005-11-08
forum: Programming Talk
---

### Post by fng on 2005-11-08
I'm having this backup script problem with python.

I first wrote the backupscript in bash. Everything worked.
But then i wanted to convert the entire script to python.

When starting this script manually, everything works.
But when i run this script from the crontab, not everything is working fine.

1 of the things this script does is backing up subversion repositories.  One of those repositories is 12MB when i dump it to a file.  But the python script stops after revision 51 or 6.6MB. So only the first half of that repository is backed up with the python script :(.

It's the only repository bigger then 7MB and more then 50 revisions. All the other repositories are backing up fine.  

I have no idea what is causing this.

specifique shell script code:
```
# ----------------------------------
# Backing up subversion repositories
# ----------------------------------

for dir in $( ls $DATA_SVN )
do
  if [ -d "$DATA_SVN/$dir" ]
  then 
    svnfile="$DATE-$HOSTNAME-subversion-$dir-fullbackup.gz"
 
    echo "Creating $svnfile ..."
      `svnadmin dump "$DATA_SVN/$dir" | gzip -f9 > "$BACKUPDIR_DAILY/$svnfile"`; 
    echo "Done."
   
    showsize "$BACKUPDIR_DAILY/$svnfile" 

    echo ""
  fi
done
```


specifique python code:
```
# ---------------------
# Backing up subversion
# ---------------------

svn = path(svnpath)

# For each subdir in the svn repository that not starts with a .
for dir in svn.dirs('[!.]*'):
    repo = dir[len(svnpath)+1:] 
    repo_file = backupdir_now + os.sep + repo 
    dump_command = 'svnadmin dump ' + dir + ' > ' + repo_file + '.dump'

    print 'Backing up repository %s ...' % repo
    
    if os.system(dump_command) == 0:
        print 'Succesfully created', repo_file
    else:
        print 'Backup FAILED!'

    print ''

# Put all repositories in a single tar archive
tar_file = backupdir_now + os.sep + filename + 'svn.tar.gz'
tar_command = "tar -cz --remove-files -f '%s' %s*.dump" % (tar_file, backupdir_now + os.sep)

if os.system(tar_command) == 0:
    print 'Succesfully created', tar_file
    os.system('du -h ' + tar_file + ' | cut -f1')
else:
    print 'Backup FAILED!'

print ''
```

---

### Post by fng on 2005-11-09
*bump*

---

