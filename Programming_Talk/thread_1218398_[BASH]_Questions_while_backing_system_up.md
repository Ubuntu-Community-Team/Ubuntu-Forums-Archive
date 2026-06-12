---
title: "[BASH]: Questions while backing system up"
date: 2009-07-20
forum: Programming Talk
---

### Post by hey_ram on 2009-07-20
hi all,

i was trying to write a bash script to back up some files and folders on my system. though the script works fine, there are some things that were not very clear to me. i was hoping someone could shed some more light on that. first, the script:

```

#this is a script to back up all the data that I do not want lost.

#!/bin/bash     #Use the bash script.

#sudo su   
#These are the things to add.
#1. Check for last version of backed up file. File should be backed up only if changes have been made to it since last backup.

if [ ! -d Backup.tar.gz ]   #check if Backup directory does not exist.
then
    #directory does not exist. create new directory.
    mkdir Backup/
else    
    echo "Backup already exists."
    echo "Deleting Backup..."
    rm -rf Backup/    #removing Backup.
    rm -rf Backup.tar.gz  
fi

#copy .vimrc.
echo "Backing up .vimrc"
cp ~/.vimrc Backup//.vimrc

#copy vim syntax folder.
echo "Backing up vim syntax folder."
cp -r ~/.vim/syntax Backup/

#copy cprogs.
echo "Backing up C programs."
cp -r ~/cprogs Backup/

#copy c++ directory.
echo "Backing up C++ programs."
cp -r ~/c++ Backup/

#copy web designing files.
echo "Backing up Web designing files."
cp -r ~/Desktop/Web\ designing\ files Backup/

#copy .bashrc and other bash files.
echo "Backing up bash files: .bashrc, .bash_history, .bash_logout"
cp ~/.bashrc Backup/
cp ~/.bash_history Backup/
cp ~/.bash_logout Backup/

#copy $PATH from printenv
echo "Backing up \$PATH environment variable."
echo $PATH > ~/path.txt
cp ~/path.txt Backup/
rm path.txt    #remove path.txt

#copy other vim files.
echo "Backing up other vim files: .viminfo, .vim"
cp ~/.viminfo Backup/
cp -r ~/.vim Backup/

#copy shell scripts.
echo "Backing up Shell scripts."
cp -r shell_scripts/ Backup/

#copy tcl programs.
echo "Backing up tcl scripts."
cp -r tclprogs/ Backup/

#copy .tomboy directory and all its contents.
echo "Backing up notes written in Tomboy."
cp -r .tomboy/ Backup/

#copy /etc/fstab.
echo "Copying /etc/fstab."
cp /etc/fstab Backup/

#copy /etc/apt. Contains sources.list, a list of all sources (repositories) that apt-get looks for when downloading/installing a software.
echo "Backing up /etc/apt."
cp -r /etc/apt Backup/

#create a compressed version of backup.
echo "Create a compressed version of the backup folder. Archiving into .tar.gz."
tar -czpf Backup.tar.gz Backup/
echo "Removing Backup/ directory."
rm -rf Backup/ #remove the directory so it does not take up more space.

#echo "Exiting root user account."
#exit    #exit root account and get back to user account.

```

the questions I had are:

1. while copying the /etc/apt directory, i get the following error messages:
Backing up /etc/apt.
cp: cannot open `/etc/apt/trustdb.gpg' for reading: Permission denied
cp: cannot open `/etc/apt/secring.gpg' for reading: Permission denied

when i look into the file permissions for these two files, they are as follows:
-rw------- 1 root root 1200 2008-09-21 18:11 /etc/apt/trustdb.gpg

is there a way around this given the following "constraints":
a. i do not want to do a sudo su, become root user and copy these files.
b. i do not want to change file permissions using chmod. i could do it on a temporary basis but that would also involve becoming the super user.

2. i was earlier doing the sudo su routine and used the "exit" command (see the 2 commented lines at the end) to exit the root user account. when i run the script, it just returns to the root user command prompt. the script does not print any of the "Backing up .." messages and neither does it exit the root user account until an explicit exit command is given. any ideas why this may be happening? this way of backing up files and folders, i realize, is dangerous since by not exiting the root user account, it gives the "normal" user extra privileges.

3. are there any files that i am missing from the list? i wanted to back up my firefox bookmarks list, but do not know where they may be on the system. any hints are most welcome.

4. how can i schedule it (from within the script) to make it run periodically?

thanks.

---

### Post by stroyan on 2009-07-20
First, something you didn't ask about.  You have the "#!/bin/bash" line as the third line of your script.  It is only effective as the first line.  The "#!" characters at the very front of a file is special.  That, combined with "chmod +x script_file", allows scriptfile to be exec'd instead of needing to be run from a bash shell.

1.  The script must run as root to be able to read the /etc/apt/trustdb.gpg and /etc/apt/secring.gpg files.  You can make that happen with sudo or by running as root from cron.  (See question 4 for more about cron.)

2. Don't use "sudo su" followed by /usr/local/bin/scriptfile.sh.  Instead use "sudo /usr/local/bin/scriptfile.sh" or "sudo bash -c /usr/local/bin/scriptfile.sh".  Then the script will be run and the sudo will exit immediately.  I don't know why you did not see any of the echo output.  That sounds like a symptom of a serious mistake.

3. Firefox bookmarks and settings are under ~/.mozilla/.  You may be much happier in the long run if you back up all of your home directory with only a few explicit exclusions.

4. The cron command can be used to schedule periodic program runs.  Look at "man cron" and "man crontab".  You can set up cron entries for your own account and other cron entries for root.  If the script is run as root you will need to be more explicit about the home directory that you refer to as "~" and the implicit current directory for the relative paths that appear in the script.

It is much better to have backup on another system rather than the same system.  (At least copying to a different disk would be a start.)

You would be safer to use a package that keeps several revisions of backup files.  An overwritten file will be lost as soon as your script does one backup of the bad file image.  There are periodic backup packages such as "backuppc" that make that relatively easy to set up.

---

### Post by lensman3 on 2009-07-20
To run the script every day at 5am say, do:

$ cat run.daily.backup
<your>/backup.sh
echo run.daily.backup | at 5am
$
Run this script and it will run daily at 5am.

This will run forever which is the next reboot. 

A better backup script is as follows.  We used it to backup changes in a production C/C++ library etc.  

echo finding newer files than update ...

cd /home/myhome/

HOME_LOC=/home/myhome/
TAR_FILE=${HOME_LOC}stage/u`date +%m%d%H%M`.tar

#run find  using the -o (or) syntax
(
 find . -newer ${HOME_LOC}/update  \
       \(     -name '*.[hcsf]' -o -name '*.asm' \
	   -o -name '*.ma*'    -o -name '*.hlp' \
	   -o -name '*.msg'    \
	   -o -name 'Makefile.*'                  \
	   -o -name '*.cmn'    -o -name '*.glb' \)  \
       -print ) | \
       egrep -v 'SCCS|stage|local.h' | tee /tmp/x.$$

echo copying files:

tar -chf ${TAR_FILE} `cat /tmp/x.$$`

# rm  /usr/tmp/x.$$

if test -r ${TAR_FILE} 
then
   touch ${HOME_LOC}/update
fi


It essentially builds a list of files you want to backup using find then strips out unwanted files using "egrep".  Then it tars the files that should be backed up.  Finally, it creates a time stamped file that will be used in the input of the next "find" ( -newer  ${HOME_LOC}/update ).  The -newer flag only looks for files that were changed from the last backup.

If you don't like the timestamp time, then use "touch" to change the date and time.

I think the $$ syntax creates a unique system temp file that is automatically deleted after the script has run.

Hope this helps.

---

### Post by hey_ram on 2009-07-24
stroyan and lensman3, thanx for the inputs. your help is most welcome. i have tried to update my Backup script with the changes you suggested. the updated version:

```

#this is a script to back up all the data that I do not want lost.

#!/bin/bash     #Use the bash script.
#These are the things to add.
#1. Check for last version of backed up file. File should be backed up only if changes have been made to it since last backup.

#The plan is as follows:
#1. Create two different directories, Backup_Linux, Backup_Windows. Names are self-explanatory.
#2. Backup_Linux is created in root.
#3. Backup_Windows is created on the external hard drive.
#4. Backup_Linux is copied into the external hard drive whenever hard drive is mounted.
#5. Backup_Windows is created and copied only when the external hard drive is mounted.

if [ -f /Backup_Linux.tar.gz ]   #check if Backup directory exists.
then
    echo "Backup_Linux already exists."
    echo "Deleting Backup_Linux..."
#   rm -f Backup_Linux.tar.gz
else
    #directory does not exist. create new directory.
    mkdir /Backup_Linux/  #this is the drive that backs up files on the linux system.
fi

#copy $PATH from printenv
echo "Backing up \$PATH environment variable."
echo $PATH > /home/sriram/path.txt

#copy /etc/fstab.
echo "Copying /etc/fstab."
cp /etc/fstab /Backup_Linux/

#copy /etc/apt. Contains sources.list, a list of all sources (repositories) that apt-get looks for when downloading/installing a software.
echo "Backing up /etc/apt."
cp -r /etc/apt /Backup_Linux/

#copy the home folder.
echo "Copying contents of /home."
#mkdir /Backup_Linux/sriram
cp -r /home/sriram/ /Backup_Linux/sriram  #copy the home folder.
rm path.txt    #remove path.txt.

#back up the backup script.
echo "Backing up the back up script."
cp backup.sh /Backup_Linux/

#create a compressed version of backup.
echo "Create a compressed version of the backup folder. Archiving into .tar.gz."
tar -czpf /Backup_Linux.tar.gz /Backup_Linux/
echo "Removing Backup/ directory."
rm -rf /Backup_Linux/ #remove the directory so it does not take up more space.

if [ -d /media/Elements ]   #check if the hard drive is plugged in.
then
    echo "Hard-drive plugged in."
    echo "Backing up Drive E: as well."
    if [ -d /media/sda5 ]
    then
        echo "Copying contents of Drive E:\ "
        if[ ! -d /media/Elements/Backup_Windows ]   #check if destination directory exists.
        then   #if it does not exist, make the directory.
            mkdir /media/Elements/Backup_Windows   #creating a directory where I can back E:\.
        fi
        cd /media/Elements      #changing to the hard drive directory.
        cp -r /media/sda5 Backup_Windows/   #copying files.
    else
        echo "E:\ not mounted. Cannot back up its contents."
    fi
else
    echo "Hard Drive not plugged in. Aborting copying of E:\ "
fi

#removing /Backup_Linux.
rm -rf /Backup_Linux
rm /home/sriram/path.txt

```

there were some questions that i had:

1. > You have the "#!/bin/bash" line as the third line of your script. It is only effective as the first line. 

i tried to make the #! the first line, but got this error message:
/bin/bash #Use the bash script: No such file or directory.

but when i put it in as i have in the code above, it seems to work without errors. any reason why that may be happening?

2. is there a way of logging in the error messages while the script is running? i want error messages from, say, the "cp" command to get logged on somewhere so that i can look at it and know what errors occurred.

3. I edited my crontab and it looks like this:
```
# m h  dom mon dow   command
00 06 * * * sudo /home/sriram/backup.sh  #cron job to run backup script every day at 6.00 am. backs up all relevant files.

```

@lensman3: your version of the backup script is really nice. i will incorporate some of them in the next "upgrade" of the script. but i need to get some basic issues thrashed out first.

---

### Post by stroyan on 2009-07-24
1. The complaint from putting your "#!/bin/bash     #Use the bash script." line in the first line happens because the "#Use the bash script" part is passed as arguments to /bin/bash.
Your first line should be just "#!/bin/bash".
If you put a "#!" line later in the file it is just a comment and has no special effect.
When you run backup.sh from a shell it will first try to exec the file.
That would allow the first line to use "#!" to choose the interpreter.
If script does not start with "#!" then exec fails and the shell will try interpreting the script itself.
When you log into your account using bash shell and run it interactively the script is interpreted by bash.
When you run it from cron the script is interpreted by /bin/sh, which is dash on ubuntu.

2. Use shell redirection into a file.
This will put standard output and standard error into /var/log/backup.sh_log
It will overwrite the file each time it is run.
exec &> /var/log/backup.sh_log

This will put standard output and standard error into /var/log/backup.sh_log
It will append to the end of the file each time.
exec >> /var/log/backup.sh_log 2>&1

You still have some local paths that could cause you trouble.
You are testing "-f /Backup_Linux.tar.gz" but creating "/Backup_Linux".
You can just create a directory with "mkdir -p /Backup_Linux" to create a directory when it doesn't exist and cause no error if the directory already exists.
PATH for jobs run by cron will be different than PATH for jobs run from a login shell.
See "man 5 crontab" for details.

---

