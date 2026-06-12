---
title: "cp in backup script mess things up."
date: 2006-02-07
forum: Programming Talk
---

### Post by cotn on 2006-02-07
Hi all,

I think this is a simple one but this one drives me nuts;

I'm trying to write a simple backup script to copy a directory and tar it into a package described with date and so. 

When I tell the shell to:

```
cp -rf /var/www/ /media/harddisk1/backupBase/wwwdata
```

The directory is copied properly with the included files.

But when I put it in a script called "backup" and append the file, the copied directoryname becomes "wwwdata?" instead of wwwdata.

The probelem is that it "wwwdata?" won't look very nice and that Tar gets  confused while making a descent package.

So, a little help would be appreciated.

Tnx in advance.

---

### Post by hod139 on 2006-02-07
Without seeing the script, it is hard to debug. I'm also not sure what you mean by "I put it in a script called "backup" and append the file".

In any case, you can try putting the source and dest locations as variables like this:
```

#!/bin/bash

SOURCE="/var/www/"
DEST="/media/harddisk1/backupBase/wwwdata"

cp -rf $SOURCE $DEST 

``` This also makes it easier to change later.  Hope this helps.

---

### Post by cotn on 2006-02-08
> Without seeing the script, it is hard to debug. I'm also not sure what you mean by "I put it in a script called "backup" and append the file".


Well actually, I chopped down my script till the only line that whas left was:
cp -rf /var/www/ /media/harddisk1/backupBase/wwwdata

So I opened Vi, added the line as above (cp -rf blabla) and finally saved it as "backup".

True your given script is far more structured so lets use that one.
Then I get the following messages:

```

$ sudo bash backup
:command not found
cp: cannot stat `/var/www/\r': No such file or directory

```

My script now:
```

#!/bin/bash
DATEPART=`date +-run-%Y-%m-%d`
SOURCE="/var/www/"
DEST="/media/harddisk1/backupBase/wwwdata"
cp -rf $SOURCE $DEST

```

---

### Post by hod139 on 2006-02-08
Do not run the script as:
 ```
sudo bash backup 
```  
This gives the script super user rights for the entire execution, which is not what you want. Most likely you only want certain commands to have super user rights. Put the sudo command into the script, where you need it. 
 
  ```
[FONT=monospace]
[/FONT]#!/bin/bash DATEPART=`date +-run-%Y-%m-%d` 
SOURCE="/var/www/" 
DEST="/media/harddisk1/backupBase/wwwdata" 
sudo cp -rf $SOURCE $DEST

``` 
and run the script as a normal user
```

sh backup

``` 
Or if the idea is to have this script run automatically without user interaction, remove the "sudo" and change the ownership of the script to root, or better change the group of the script to www (assuming of course that everything in SOURCE is readable by the www group and the DEST is writeable by www).

---

### Post by jerome bettis on 2006-02-08
nevermind, i have to run and need more time to fix this before i post it.

i was gonna post this interactive backup script i've been working on.  i thought it was ready but i just noticed something minor that needs fixed.

---

### Post by cotn on 2006-02-08
The way I wan't to use this script is in a cron-job, that will run as root (because in future it must tar, rm and copy priveledged folders). So I wan't to give super user rights for the entire execution, 

That's why I don't use sudo in my script but before to test what goes wrong. 

Or is it still not the proper way to deal with it ?

But I keep receiving the same error's. Does it have anything to do with the linefeed thing, in the error message: cannot stat `/var/www/\r' ??

---

### Post by cotn on 2006-02-08
> 
nevermind, i have to run and need more time to fix this before i post it.

i was gonna post this interactive backup script i've been working on. i thought it was ready but i just noticed something minor that needs fixed.

No problem, maybe next time.

---

### Post by hod139 on 2006-02-08
Just wondering, but can you do this:
```

sudo cp -rf /var/www/ /media/harddisk1/backupBase/wwwdata[COLOR=Black][COLOR=#dd0000][/COLOR][/COLOR]

``` 
I'm just wondering if sudo is messed up on your system.

---

### Post by cotn on 2006-02-08
Yup, that works fine !

---

### Post by hod139 on 2006-02-08
[quote=cotn]
Yup, that works fine !
[/quote]  I'm getting pretty confused now :-k
[quote=cotn]The way I wan't to use this script is in a cron-job, that will run as root (because in future it must tar, rm and copy priveledged folders). So I wan't to give super user rights for the entire execution, 

That's why I don't use sudo in my script but before to test what goes wrong. 

Or is it still not the proper way to deal with it ?

But I keep receiving the same error's. Does it have anything to do with the linefeed thing, in the error message: cannot stat `/var/www/\r' ??[/quote] 
If you are going to be running this as a cron job, how about trying this:
```

sudo chown root.root backup
sudo su
sh backup

``` This is just for a quick test. I would suggest not setting the owner of the script to root, but changing the group to something that has read and write access to those locations, e.g. www. Then you would only issue a```
chgrp www backup
```, and leave the owner of the script as you.  Safer that way. 
 
If this doesn't work, can you do this:
```

sudo su
sudo cp -rf /var/www/ /media/harddisk1/backupBase/wwwdata 

```

I'm beginning to just guess here though.  Hopefully these tests shed some light.

---

### Post by jerome bettis on 2006-02-09
[quote=cotn]No problem, maybe next time.[/quote] 
ok maybe it's ready now, it's pretty solid over here.  if you're running ubuntu and haven't really screwed everything up it should work.

take a look at it and run it.  let me know if it works and what you think.  i'm very open to feature requests and anything else.  i'd like it to be very flexible, possibly add a nice gui, and make it into the repositories eventually.  i'm going to start on the restore script shortly, after i get some feeback on this one.

```
#!/bin/bash
#
# backup.sh 
#
# an interactive script that generates another script to perform a backup of
# an ubuntu system.
#

# this is where all restore points will go, change as necessary
root_backup_path="/media/usb1/restore"

# put this backup into a dir structure based on the date
this_backup_path="${root_backup_path}/`date +%Y/%m/%d`"

# name of the script we're going to generate
out_file="make-backup.sh"

# add any other devices to look at here (will be interactive / more intelligent later)
devices="/dev/hda"

# don't add compression opts, we add them later
tar_opts="vcpf"

# don't change this, unless you have some weird directory in "/" you don't want.
# the script adds partitions and other devices to it intelligently
root_omit="/dev /proc /sys /lost+found"
always_omit="lost+found"

# don't change these
root_include=""
set_links=""

# this should prompt the user for things eventually.
setup()  {
    echo -e "Script will ask you questions about what you want done, and create another script with
the commands to perform the backup."
    echo -e "Lots of features & flexibility to add still, eventually a nice restore script will be in the works."
}

# start making the backup script, copy the MBR, contents of the partition table for reference,
# and the fstab for the restore script.
phase_one()  {
    echo "#!/bin/bash" > ${out_file}
    echo -e "mkdir -p ${this_backup_path}" >> ${out_file}
    for i in ${devices} ; do
        echo -e "dd if=${i} of=${this_backup_path}/${i:5}-MBR.bin count=1 bs=512" >> ${out_file}
        set_links="${set_links}${this_backup_path}/${i:5}-MBR.bin "
        echo -e "fdisk -l ${i} > ${this_backup_path}/${i:5}-parttab" >> ${out_file}
        set_links="${set_links}${this_backup_path}/${i:5}-parttab "
    done
    echo -e "cp /etc/fstab ${this_backup_path}/fstab" >> ${out_file}
    set_links="${set_links}${this_backup_path}/fstab "
}

# used to determine what partitions we are concerned with
parse_fstab()  {
    (echo ${devices} && cat /etc/fstab) | awk '
    {
        if (FNR == 1)  {
            num_devices = split($0, devices);
            getline;
        }
        for (i = 1; i <= num_devices; ++i)  {
            if (index($1, devices[i]) == 1)  {
                if (($2 != "/") && ($2 != "none"))  {
                    print $2;
                }
            }
        }
    } '
}

# prints 1 if a partition is mounted, 0 if not
is_mounted()  {
    mounted=0
    for i in `mount | awk ' { print $3 } '` ; do
        if [ ${i} == ${1} ] ; then
            mounted=1
            break
        fi
    done
    echo ${mounted}
}

# mount the partition in the backup script if we need it.
do_mount()  {
    echo -e "mount ${1}" >> ${out_file}
}

# ask the user what they want to do with a partition
backup_menu()  {
    choice=0
    if [ ${1} == "root" ] ; then
        num_choices=2
    else
        num_choices=4
    fi
    until [ ${choice} -ge 1 ] && [ ${choice} -le ${num_choices} ] ; do
        echo -e "\nSelect an action for your ${1} partition:"
        echo -e "\t1. Do not backup."
        if [ ${1} == "root" ] ; then
            echo -e "\t2. Backup."
        else
            echo -e "\t2. Backup indiviually."
            echo -e "\t3. Backup with rest of root filesystem."
            echo -e "\t4. Both 2 & 3"
        fi
        read choice
        while [ ${#choice} -lt 1 ] ; do
            read choice
        done
    done
    return ${choice}
}

# ask the user about compressing a tarball
comp_menu()  {
    choice=0
    until [ ${choice} -ge 1 ] && [ ${choice} -le  "3" ] ; do
        echo -e "\tSelect a compression level for ${1} :"
        echo -e "\t\t1. None"
        echo -e "\t\t2. Low (gzip, slower but a smaller file, recommended)"
        echo -e "\t\t3. High (bzip2, very slow and a smaller file than gzip)" #some stats or estimations would be nice here
        read choice
        while [ ${#choice} -lt 1 ] ; do
            read choice
        done
    done
    return ${choice}
}

# depending on their choice, add the flag to the tar cmd.
get_tar_opts()  {
    case "${1}" in
        "1") echo "";;
        "2") echo "z";;
        "3") echo "j";;
        *);;
    esac
}

# same as above, just add the file extension onto the tar file name.
get_file_ext()  {
    case "${1}" in
        "1") echo "";;
        "2") echo ".gz";;
        "3") echo ".bz2";;
        *);;
    esac
}

# create the cmd to backup a normal partition.
# determine what directories to exclude, ask about compression
backup_part()  {
    excluded_dirs=""
    exclude_str=""
    for i in ${always_omit} ; do
        if [ -e ${1}/${i} ] ; then
            excluded_dirs="${excluded_dirs}${this_backup_path}/excluded_dirs${1}/${i} "
            exclude_str="${exclude_str}--exclude=${i} "
        fi
    done
    if [ ${#excluded_dirs} -gt 0 ] ; then
        echo -e "mkdir -p ${excluded_dirs}" >> ${out_file}
    fi

    comp_menu ${1}
    comp_level=$?
    tar_file="${1:1}.tar`get_file_ext ${comp_level}`"
    echo -e "tar -`get_tar_opts ${comp_level}`${tar_opts} ${this_backup_path}/${tar_file} ${exclude_str} ${1}" >> ${out_file}
    set_links="${set_links}${this_backup_path}/${tar_file} "
}

# ask the user what they want to do with each partition.
# if they want to back it up, check if it is not mounted.
phase_two()  {
    parts=`parse_fstab`
    for part in ${parts} ; do
        backup_menu ${part}
        case "$?" in
            "1")
                if [ `is_mounted ${part}` == 1 ] ; then
                    root_omit="${root_omit} ${part}"
                fi;;
            "2")
                if [ `is_mounted ${part}` == 0 ] ; then
                    do_mount ${part}
                fi
                backup_part ${part}
                root_omit="${root_omit} ${part}";;
            "3")
                if [ `is_mounted ${part}` == 0 ] ; then
                    do_mount ${part}
                fi
                root_include="${root_include} ${part}";;
            "4")
                if [ `is_mounted ${part}` == 0 ] ; then
                    do_mount ${part}
                fi
                backup_part ${part}
                root_include="${root_include} ${part}";;
            *)  ;;
        esac
    done
}

# check what actual file systems are mounted
mounted_filesystems()  {
    mount | awk '
    {
        if ((index($1, "/dev/") == 1) && ($3 != "/"))  {
            print $3;
        }
    } '
}

# check the result of the above function and see if we
# want to include or exclude any mounted filesystems.
check_mounts()  {
    for i in `mounted_filesystems` ; do
        omitted=0
        for j in ${root_omit} ; do
            if [ ${i} == ${j} ] ; then
                omitted=1
                break
            fi
        done
        if [ ${omitted} -eq 0 ] ; then
            included=0
            for j in ${root_include} ; do
                if [ ${i} == ${j} ] ; then
                    included=1
                    break
                fi
            done
            if [ ${included} -eq 0 ] ; then
                echo ${i}
            fi
        fi
    done
}

# backup the root partition, pretty much the same as the
# backup_part function, look into coalescing those without too many if / else stmts.
backup_root()  {
    excluded_dirs=""
    exclude_str=""
    for i in ${root_omit}; do
        if [ -e /${i} ] ; then
            excluded_dirs="${excluded_dirs}${this_backup_path}/excluded_dirs/rootfs${i} "
            exclude_str="${exclude_str}--exclude=${i} "
        fi
    done
    if [ ${#excluded_dirs} -gt 0 ] ; then
        echo -e "mkdir -p ${excluded_dirs}" >> ${out_file}
    fi

    comp_menu "root"
    comp_level=$?
    tar_file="rootfs.tar`get_file_ext ${comp_level}`"
    echo -e "tar -`get_tar_opts ${comp_level}`${tar_opts} ${this_backup_path}/${tar_file} ${exclude_str} /" >> ${out_file}
    set_links="${set_links}${this_backup_path}/${tar_file} "
}

# asks the user whether or not they want to include a mounted
# filesystem in the root backup.
exclude_menu()  {
    choice="x"
    until [ ${choice} == "y" ] || [ ${choice} == "n" ] ; do
        echo -e "\tExclude ${1} ? (y/n)"
        read choice
        while [ ${#choice} -lt 1 ] ; do
            read choice
        done
    done
    if [ ${choice} == "y" ] ; then
        return 1
    else
        return 0
    fi
}

# ask the user about the root partition,
# first check and see what the root partition actually includes,
# and give the user the option to exclude the cdrom and any other BS we don't want.
phase_three()  {
    mounts=`check_mounts`
    num_mounts=`echo ${mounts} | wc -w`
    if [ ${num_mounts} -gt 0 ] ; then
        echo -e "\nAfter backing up partitions, the following file systems are still mounted, and"
        echo -e "currently will be included in the backup of the root file system."
        for mnt in ${mounts} ; do
            exclude_menu ${mnt}
            if [ $? == 1 ] ; then
                root_omit="${root_omit} ${mnt}"
            fi
            mounts=`check_mounts`
        done
    fi
    backup_menu "root"
    if [ $? -eq 2 ] ; then
        backup_root
    fi
}

# set symlinks for the current backup in the root_restore_path for easy access
# (remove old links first (doesn't work right yet, .gz .bz2 cause problems)
# put our script in the backup's path and make it executable.
cleanup()  {
    if [ -e ${root_backup_path} ] ; then
        rm_old_links=""
        for i in ${root_backup_path}/* ; do
             if [ -h ${i} ] ; then
                rm_old_links="${rm_old_links}${i} "
            fi
        done
        if [ ${#rm_old_links} -gt 0 ] ; then
            echo -e "rm ${rm_old_links}" >> ${out_file}
        fi
    fi

    echo -e "ln -s ${set_links} ${root_backup_path}" >> ${out_file}
    echo -e "cp ${out_file} ${this_backup_path}/${out_file}" >> ${out_file}
    chmod 755 ${out_file}
    echo -e "\nBackup script is prepared and is ready to go!"
}

# 5 phases of making the script
make_backup_script()  {
    setup
    phase_one
    phase_two
    phase_three
    cleanup
}

# after the script is prepared, ask the user what they want to do with it.
backup_script_menu()  {
    choice=0
    until [ ${choice} -ge 1 ] && [ ${choice} -le  "4" ] ; do
        echo -e "Select an action"
        echo -e "\t1. View commands to be exectued."
        echo -e "\t2. Start backup."
        echo -e "\t3. Start over."
        echo -e "\t4. Exit."
        read choice
        while [ ${#choice} -lt 1 ] ; do
            read choice
        done
    done
    return ${choice}
}

# do what they want with the script
perform_action()  {
    case "$?" in
        "1")
            echo ; cat ${out_file} ; echo
            backup_script_menu
            perform_action $?;;
        "2")
             sudo ./${out_file};; # maybe say get root instead of using sudo
        "3")
            echo -e "\n"
            make_backup_script
            backup_script_menu
            perform_action;;
        "4")
            exit;;
        *);;
    esac
}

# script starts here
# make the backup script, ask them what to do with it, and do it.
make_backup_script
backup_script_menu
perform_action $?
```

---

