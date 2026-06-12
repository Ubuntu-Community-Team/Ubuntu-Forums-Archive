---
title: "HOWTO: Load linux into ram (usefull for security, CF-cards or very slow HDD's)"
date: 2009-09-16
forum: Outdated Tutorials &amp; Tips
---

### Post by ubongo2008 on 2009-09-16
Hey guys,

well a few weeks ago i bought an Zotac Ion A mini-ITX board and i use an 16GB CF-Card as installation medium. 
I had a few choices on how to install linux on that box. Finally i decided that i wanted to have it installed
the standard way (grub, MBR ... ) so that i would be able to image it and distrubute it to other boxes as i do 
normally all the time. 

Since my CF-card can only be written to 1000 times i needed to push linux into an ram-file-system like tmpfs. 
and thats what i did.

**[COLOR=Red]well i am pretty new to bash-scripting so don't expect it to be bullet-proof or perfect ... SO USE IT ON YOUR OWN RISK[/COLOR]**

**If someone can improve on it ... you are absolutely welcome, please post improvements here. **

so what does it do?

it is an init-deamon script which should kick in right after all local filesystems have been mounted. 
It will then load some directories into an tmpfs and continue to boot. Since /usr is pretty big it will 
be squashed and made writable with aufs.

I have some old hdds flying around here which are really slow ... so that this script gives that boxes an dramatic 
speed boast when booted ... you may also find it usefull to also ramdisk your /home since then all changes or e.g.: 
mozilla stuff will be in ram and therefore not persistent which adds some anonymity/security to your box.

it may also be nice to install some stuff then reboot your box and have it back as it was before you installed that stuff.
or maybe you will experience an boost in battery live coz it will reduce hdd-access to an absolute minimum.

Anyway you will allways have the possibility to make any changes persistent by just calling:```
 "sudo /etc/init.d/ramdisk.sh sync"
```all changes will be written to your HDD and next time you boot up your box they will appear and will also be loaded into an tmpfs.

so to sum it up you just have two commands:
```

"sudo /etc/init.d/ramdisk.sh start" # => ramdisk everything
"sudo /etc/init.d/ramdisk.sh sync" # => make changes persistent

```thats it.


ok so here is the script:


```
#! /bin/sh
# /etc/init.d/ramdisk.sh
# written by christian geiler 

f_error()
{
    echo "Usage: /etc/init.d/ramdisk.sh {start|stop|sync}"
    exit 1
}

f_get_user_answer_yes_no() 
{
    local isAnswerCorrect="false"
    while [ "$isAnswerCorrect" != "true" ];
    do
        echo " * [yes|no]? " 1>&2
        local answer="yes"

        # read -t <timeout> # posix style
        STTY=`stty -g`
        stty -icanon 
        stty min 0 time 50
        stty_answer=`dd count=3 bs=1 2>/dev/null`
        stty $STTY 

        if [ -n "$stty_answer" ];
        then
          local answer=$stty_answer
        fi
        
        if [ "yes" = "`echo $answer | grep "yes"`" ];
        then
          local isAnswerCorrect="true"
        else
            if [ "no" = "`echo $answer | grep "no"`" ];
            then  
                local isAnswerCorrect="true"
            fi
        fi
    done
    echo "$answer"
}

f_update_squashfs()
{
    #Funktions parameter
    local directory=$1
    
    #locale variablen
    local hiddenPD="/.physical_disk"
    local directoryPD="$hiddenPD""$directory"
    local squashfs_file_name="`basename "$directory"".squashfs"`"
    
    #Check if the squashfs of the given directory exists, if not create it now
    test    -d "$directoryPD""/squashfs"                        || mkdir "$directoryPD""/squashfs"
    rm $directoryPD"/squashfs/"$squashfs_file_name
    test    -f $directoryPD"/squashfs/"$squashfs_file_name      || 
    ( 
        echo " * createing $directoryPD/squashfs/$squashfs_file_name";
        mksquashfs $directory $directoryPD"/squashfs/"$squashfs_file_name -check_data -nolzma; 
    )
}

f_HddDirectoryToRamdisk()
{
    #Funktions parameter
    local directory=$1                                             #directory on HDD which should be loaded into RAM
    local directoryRights=$2                                       #rights of directory
    local directoryOwner=$3                                        #owner  of directory
    local sizeOfRamdisk=$4                                         #maximum size of ramdisk
    local isSquashFS=$5

    #locale variablen
    local hiddenPD="/.physical_disk"
    local hiddenRAM="/.ramdom_access_memory"
    local directoryPD="$hiddenPD""$directory"                       #directory on HDD which is a mountpoint for HDD disk
    local directoryRAM="$hiddenRAM""$directory"                     #directory on HDD which is a mountpoint for RAM disk
    local squashfs_file_name="`basename "$directory"".squashfs"`"

    test -d $directoryPD  || ( mkdir -p $directoryPD;  chmod $directoryRights $directoryPD; )
    test -d $directoryRAM || ( mkdir -p $directoryRAM; chmod $directoryRights $directoryRAM; )
     
    echo  "[`date +"%Y-%m-%d %H:%M"`] Synching $directory Ramdisk from HDD" >> /var/log/ramdisk_sync.log
    echo  "Current memory usage is" >> /var/log/ramdisk_sync.log
    free        -t -m >> /var/log/ramdisk_sync.log

    echo  " * synching $directoryPD to ramdisk" #RueckgabeString nach stdout schreiben
    if [ "$isSquashFS" = "true" ];
    then
        #Check if the squashfs of the given directory exists, if not create it now
        test    -d "$directoryPD""/squashfs"                        || mkdir "$directoryPD""/squashfs"
        test    -f $directoryPD"/squashfs/"$squashfs_file_name      || 
        ( 
            echo " * createing $directoryPD/squashfs/$squashfs_file_name";
            mksquashfs $directory $directoryPD"/squashfs/"$squashfs_file_name -check_data -nolzma; 
        )

        #mount the old directory which is on the physical disk to "$hiddenPD""$directory""/originalfs"
        test    -d "$directoryPD""/originalfs"                      || mkdir "$directoryPD""/originalfs"
        mount   --rbind  $directory $directoryPD"/originalfs" -o noatime

        #create the ramdisk file system
        mount   -t tmpfs none $directoryRAM -o size=$sizeOfRamdisk"m"   # m=MB

        #create ramdisk directories
        test    -d "$directoryRAM""/squashfs"                        || mkdir "$directoryRAM""/squashfs"
        test    -d "$directoryRAM""/aufs"                            || mkdir "$directoryRAM""/aufs"
        test    -d "$directoryRAM""/aufs/ro"                         || ( mkdir "$directoryRAM""/aufs/ro"; chown $directoryOwner:$directoryOwner -R $directoryRAM"/aufs/ro"; )
        test    -d "$directoryRAM""/aufs/rw"                         || ( mkdir "$directoryRAM""/aufs/rw"; chown $directoryOwner:$directoryOwner -R $directoryRAM"/aufs/rw"; )
               
        #copy the squashfs file to the ramdisk
        echo   " * synching  $directoryPD/squashfs/$squashfs_file_name to $directoryRAM/squashfs/$squashfs_file_name"
        cp     $directoryPD"/squashfs/"$squashfs_file_name $directoryRAM"/squashfs/"$squashfs_file_name

        #mount $directoryRAM"/squashfs/"$squashfs_file_name into aufs readonly branch
        mount  -t squashfs -o loop,ro,noatime $directoryRAM"/squashfs/"$squashfs_file_name "$directoryRAM""/aufs/ro"
        
        #mount aufs to make $directoryRAM"/squashfs/"$squashfs_file_name writeable
        mount  -t aufs -o noatime,br="$directoryRAM""/aufs/rw":"$directoryRAM""/aufs/ro"=ro aufs  "$directory"
        chown  $directoryOwner:$directoryOwner "$directory"
    else
        mount  --rbind  $directory $directoryPD
        mount  -t tmpfs none $directoryRAM -o size=$sizeOfRamdisk"m",noatime   # m=MB
        chown  $directoryOwner:$directoryOwner "$directory"
        sh     -c  "cp -a $directory"/*" $directoryRAM"/""
        mount  --rbind  $directoryRAM  $directory -o noatime
        umount $directoryRAM
        rm     -r $directoryRAM
    fi

    echo    "Current memory usage is" >> /var/log/ramdisk_sync.log
    free    -t -m >> /var/log/ramdisk_sync.log
    echo     "[`date +"%Y-%m-%d %H:%M"`] $directory Ramdisk Synched from HDD" >> /var/log/ramdisk_sync.log
}

f_RamdiskToHddDirectory()
{
    #Funktions parameter
    local directory=$1                              #directory on RAM which should be synced with HDD
    local isSquashFS=$2
    local isUpdateOriginalFS=$3
     
    #locale variablen
    local hiddenPD="/.physical_disk"
    local hiddenRAM="/.ramdom_access_memory"
    local directoryPD="$hiddenPD""$directory"       #directory on HDD which is a mountpoint for HDD disk
    local directoryRAM="$hiddenRAM""$directory"     #directory on HDD which is a mountpoint for RAM disk

    if [ "$isSquashFS" = "true" ];
    then
        if [ "$isUpdateOriginalFS" = "true" ];
        then
            #synching the original physical disk directory
            local directoryPD=$directoryPD"/originalfs"
            echo " * synching $directoryPD" #RueckgabeString nach stdout schreiben
            rsync -av --delete $directory"/" $directoryPD"/" >> /var/log/ramdisk_sync.log
            echo "[`date +"%Y-%m-%d %H:%M"`] $directory Ramdisk Synched to HD" >> /var/log/ramdisk_sync.log
        fi
        #synching the squashfs file of the original physical disk directory
        echo " * update $directory squashfs?"
        if [ "`f_get_user_answer_yes_no`" = "yes" ];
        then
            f_update_squashfs "$directory"
        fi
        return
    fi

    if [ -n "`mount | grep "$directoryRAM on $directory"`" ];
    then
        echo " * synching $directoryPD" #RueckgabeString nach stdout schreiben
        rsync -av --delete $directory"/" $directoryPD"/" >> /var/log/ramdisk_sync.log
        echo "[`date +"%Y-%m-%d %H:%M"`] $directory Ramdisk Synched to HD" >> /var/log/ramdisk_sync.log
    else 
        echo "$directory is not a ramdisk"
    fi 
}

f_start()
{
    ####Deleteing old logfile
    rm      /var/log/ramdisk_sync.log.old                           2> /dev/null
    mv      /var/log/ramdisk_sync.log /var/log/ramdisk_sync.log.old 2> /dev/null
    touch   /var/log/ramdisk_sync.log                               2> /dev/null
    
    ####Turning of all Swap-Partitions
    echo " * Checking for swap partitions"
    if [ -n "`cat /proc/swaps  | grep /dev/`" ];
    then
        echo " * Disabling swap partitions: "
        cat /proc/swaps
        swapoff -a
    else 
        echo " * No swap-partition mounted"
    fi 

    echo " * Copying files to Ramdisk"
    
    ####MOVING /bin INTO RAMDISK
    f_HddDirectoryToRamdisk "/bin"      "755" "root" "10"   "false"

    ####MOVING /sbin INTO RAMDISK
    f_HddDirectoryToRamdisk "/sbin"     "755" "root" "10"   "false"
    
    #####MOVING /etc INTO RAMDISK
    f_HddDirectoryToRamdisk "/etc"      "755" "root" "10"   "false"
    
    #####MOVING /lib INTO RAMDISK
    f_HddDirectoryToRamdisk "/lib"      "755" "root" "400"  "false"

    #####MOVING /lib32 INTO RAMDISK
    f_HddDirectoryToRamdisk "/lib32"    "755" "root" "400"  "false"

    ####MOVING /var INTO RAMDISK
    f_HddDirectoryToRamdisk "/var"      "755" "root" "400"  "false"

    ####MOVING /usr AS SQUASHFS WITH AUFS INTO RAMDISK
    f_HddDirectoryToRamdisk "/usr"      "755" "root" "1500" "true"

}

f_sync()
{
    echo " * Synching ramdisk files to harddisk"

    ####SYNCHING /bin TO /bin-HDD
    f_RamdiskToHddDirectory "/bin"      "false" "ignored"

    ####SYNCHING /sbin TO /sbin-HDD
    f_RamdiskToHddDirectory "/sbin"     "false" "ignored"

    ####SYNCHING /etc TO /etc-HDD
    f_RamdiskToHddDirectory "/etc"      "false" "ignored"

    ####SYNCHING /lib TO /lib-HDD
    f_RamdiskToHddDirectory "/lib"      "false" "ignored"

    ####SYNCHING /lib TO /lib32-HDD
    f_RamdiskToHddDirectory "/lib32"    "false" "ignored"

    ####SYNCHING /var TO /var-HDD
    apt-get clean
    f_RamdiskToHddDirectory "/var"      "false" "ignored"

    ####SYNCHING /usr TO /usr-HDD
    f_RamdiskToHddDirectory "/usr"      "true"  "true"
    
    ####SYNCHING /var TO /var-HDD ein zweites mal um die geaenderte logdatei zu speichern
    f_RamdiskToHddDirectory "/var"      "false" "ignored"
}

case "$1" in
  start)
    echo " * Execute ramdisk script?"
    if [ "`f_get_user_answer_yes_no`" = "yes" ];
    then
        echo " * Sarting ramdisk script ..."
        f_start
    else 
        echo " * Skipping ramdisk script ..."
    fi
    ;;
  sync)
    f_sync
    ;;
  stop)
    #echo " * Execute ramdisk script?"
    #if [ "`f_get_user_answer_yes_no`" = "yes" ];
    #then
    #    echo " * Sarting ramdisk script ..."
    #    f_sync
    #else 
    #    echo " * Skipping ramdisk script ..."
    #fi
    echo " * Doing nothing ... All data in /bin /sbin /usr /var /etc /lib /lib32 will not be saved to disk!"
    ;;
  *)
    f_error
    ;;
esac
 
exit 0
```How to install?
apt-get install rsync     #rsync
apt-get install coreutils #date
apt-get install squashfs-tools aufs-tools
sudo cp ./ramdisk.sh /etc/init.d/ramdisk.sh && sudo update-rc.d ramdisk.sh start 35 S . && sudo /etc/init.d/ramdisk.sh start

How to uninstall?
uninstall: update-rc.d -f  ramdisk.sh remove


NOTE:
Add the following line to the end of function f_start() to also have your home in an tmpfs
```
f_HddDirectoryToRamdisk "/home/YOUR_USER_NAME" "777" "YOUR_USER_NAME"  "1500" "true"
```Add the following line to the function f_sync() 
```
f_RamdiskToHddDirectory "/home/YOUR_USER_NAME" "true"  "false"
```right under 
```

    ####SYNCHING /usr TO /usr-HDD
    f_RamdiskToHddDirectory "/usr"      "true"  "true"
```If you have an encrypted /home directory then execute the install procedure when in Desktop environment (gnome, xfce, kde) but notice that the USERNAME.squashfs file wont be encrypted ....

ALSO NOTE DON'T CHANGE THE RIGHTS "777" IS INDEED CORRECT, YOUR HOME WON'T HAVE THESE RIGHTS WHEN LOADED INTO RAM THEY WILL APPEAR AS THEY WHERE BEFORE


EDIT:

[COLOR=Red]Tests:
That script has been tested on 3 boxes right now they all have 4GB of memory and i would not recommend to execute it with less then 4GB.

If you experience problems with that script you may answer the question if it sould be executed with "no" and then you should be able to use your box as before.

Again i am not a professional in bash-scripting i am an newbe which some of you might notice if looking at the script!

Please test it first on an box which you don't need for production or day to day use.
It has also only been tested on single-user boxes.[/COLOR]

---

### Post by ubongo2008 on 2009-09-28
today i tweaked the skript a bit ... now it automaticly determines the rights, group and the owner of all given directories so they don't have to be specified by hand anymore. I also busted a usage bug with cp-command  (shopt dotglob) removed -nolzma option of mksquashfs (older versions don't support it) and last but not least commented out /lib32 because of the fact that this directory won't exist on 32-bit systems 

so here it is:

```

#! /bin/sh
# /etc/init.d/ramdisk.sh
#written by christian geiler

f_error()
{
    echo "Usage: /etc/init.d/ramdisk.sh {start|stop|sync}"
    exit 1
}

f_get_user_answer_yes_no() 
{
    local isAnswerCorrect="false"
    while [ "$isAnswerCorrect" != "true" ];
    do
        echo " * [yes|no]? " 1>&2
        local answer="yes"

        # read -t <timeout> # posix style
        STTY=`stty -g`
        stty -icanon 
        stty min 0 time 50
        stty_answer=`dd count=3 bs=1 2>/dev/null`
        stty $STTY 

        if [ -n "$stty_answer" ];
        then
          local answer=$stty_answer
        fi
        
        if [ "yes" = "`echo $answer | grep "yes"`" ];
        then
          local isAnswerCorrect="true"
        else
            if [ "no" = "`echo $answer | grep "no"`" ];
            then  
                local isAnswerCorrect="true"
            fi
        fi
    done
    echo "$answer"
}

f_getOctalFileRights()
{
    local file_name=$1
    echo "$( stat --format=%a $file_name;  )"
}

f_getUsernameOfOwnerOfFile()
{
    local file_owner=$1
    echo "$( stat --format=%U $file_owner; )"
}

f_getGroupnameOfFile()
{
    local file_group=$1
    echo "$( stat --format=%G $file_group; )"
}

f_update_squashfs()
{
    #Funktions parameter
    local directory=$1                                              #directory on HDD which should be loaded into RAM
    
    #locale variablen
    local hiddenPD="/.physical_disk"
    local directoryPD="$hiddenPD""$directory"                       #directory on HDD which is a mountpoint for HDD disk
    local squashfs_file_name="`basename "$directory"".squashfs"`"
    local directoryRights=`f_getOctalFileRights "$directory"`      #rights of directory
    local directoryOwner=`f_getUsernameOfOwnerOfFile "$directory"` #owner  of directory
    local directoryGroup=`f_getGroupnameOfFile "$directory"`       #group  of directory
    
    #Check if the squashfs-directory of the given directory exists, if not create it now
    test    -d "$directoryPD""/squashfs"                        ||  ( 
                                                                        mkdir  $directoryPD"/squashfs"; 
                                                                        chown  $directoryOwner:$directoryGroup $directoryPD"/squashfs";
                                                                        chmod  $directoryRights $directoryPD"/squashfs";
                                                                    )
    rm $directoryPD"/squashfs/"$squashfs_file_name

    #Check if the squashfs of the given directory exists, if not create it now
    test    -f $directoryPD"/squashfs/"$squashfs_file_name      ||  ( 
                                                                        echo " * createing $directoryPD/squashfs/$squashfs_file_name";
                                                                        mksquashfs $directory $directoryPD"/squashfs/"$squashfs_file_name -check_data;
                                                                        chown  $directoryOwner:$directoryGroup $directoryPD"/squashfs/"$squashfs_file_name;
                                                                        chmod  $directoryRights $directoryPD"/squashfs/"$squashfs_file_name;
                                                                    )

}

f_HddDirectoryToRamdisk()
{    
    #Funktions parameter
    local directory=$1                                             #directory on HDD which should be loaded into RAM
    local sizeOfRamdisk=$2                                         #maximum size of ramdisk
    local isSquashFS=$3

    #locale variablen
    local hiddenPD="/.physical_disk"
    local hiddenRAM="/.random_access_memory"
    local directoryPD="$hiddenPD""$directory"                      #directory on HDD which is a mountpoint for HDD disk
    local directoryRAM="$hiddenRAM""$directory"                    #directory on HDD which is a mountpoint for RAM disk
    local directoryRights=`f_getOctalFileRights "$directory"`      #rights of directory
    local directoryOwner=`f_getUsernameOfOwnerOfFile "$directory"` #owner  of directory
    local directoryGroup=`f_getGroupnameOfFile "$directory"`       #group  of directory
    local squashfs_file_name="`basename "$directory"".squashfs"`"

    test -d $directoryPD  || (
                                  mkdir -p  $directoryPD;
                                  chmod     $directoryRights $directoryPD;
                                  chown     $directoryOwner:$directoryGroup $directoryPD;
                             )

    test -d $directoryRAM || (
                                  mkdir -p  $directoryRAM; 
                                  chmod     $directoryRights $directoryRAM; 
                                  chown     $directoryOwner:$directoryGroup $directoryRAM;
                             )
     
    echo  "[`date +"%Y-%m-%d %H:%M"`] Synching $directory Ramdisk from HDD" >> /var/log/ramdisk_sync.log
    echo  "Current memory usage is" >> /var/log/ramdisk_sync.log
    free        -t -m >> /var/log/ramdisk_sync.log

    echo  " * synching $directoryPD to ramdisk" #RueckgabeString nach stdout schreiben
    if [ "$isSquashFS" = "true" ];
    then
        #Check if the squashfs-directory of the given directory exists, if not create it now
        test    -d "$directoryPD""/squashfs"                        ||  ( 
                                                                            mkdir  $directoryPD"/squashfs"; 
                                                                            chown  $directoryOwner:$directoryGroup $directoryPD"/squashfs";
                                                                            chmod  $directoryRights $directoryPD"/squashfs";
                                                                        )
        #Check if the squashfs of the given directory exists, if not create it now
        test    -f $directoryPD"/squashfs/"$squashfs_file_name      ||  ( 
                                                                            echo " * createing $directoryPD/squashfs/$squashfs_file_name";
                                                                            mksquashfs $directory $directoryPD"/squashfs/"$squashfs_file_name -check_data;
                                                                            chown  $directoryOwner:$directoryGroup $directoryPD"/squashfs/"$squashfs_file_name;
                                                                            chmod  $directoryRights $directoryPD"/squashfs/"$squashfs_file_name;
                                                                        )

        #mount the old directory which is on the physical disk to "$hiddenPD""$directory""/originalfs"
        test    -d "$directoryPD""/originalfs"                      ||  ( 
                                                                            mkdir  $directoryPD"/originalfs";
                                                                            chown  $directoryOwner:$directoryGroup -R $directoryPD"/originalfs";
                                                                            chmod  $directoryRights $directoryPD"/originalfs";
                                                                        )
        mount   --rbind  $directory $directoryPD"/originalfs" -o noatime

        #create the ramdisk file system
        mount   -t tmpfs none $directoryRAM -o size=$sizeOfRamdisk"m"   # m=MB

        #create ramdisk directories for squash and aufs
        test    -d "$directoryRAM""/squashfs" || ( 
                                                      mkdir  $directoryRAM"/squashfs"; 
                                                      mkdir  $directoryRAM"/aufs";
                                                      mkdir  $directoryRAM"/aufs/ro"
                                                      mkdir  $directoryRAM"/aufs/rw";   
                                                      chown  $directoryOwner:$directoryGroup -R $directoryRAM"/";
                                                      chmod  $directoryRights $directoryRAM
                                                 )
               
        #copy the squashfs file to the ramdisk
        echo   " * synching  $directoryPD/squashfs/$squashfs_file_name to $directoryRAM/squashfs/$squashfs_file_name"
        cp     $directoryPD"/squashfs/"$squashfs_file_name $directoryRAM"/squashfs/"$squashfs_file_name

        #mount $directoryRAM"/squashfs/"$squashfs_file_name into aufs readonly branch
        mount  -t squashfs -o loop,ro,noatime $directoryRAM"/squashfs/"$squashfs_file_name "$directoryRAM""/aufs/ro"
        
        #mount aufs to make $directoryRAM"/squashfs/"$squashfs_file_name writeable
        mount  -t aufs -o noatime,br="$directoryRAM""/aufs/rw":"$directoryRAM""/aufs/ro"=ro aufs  "$directory"
    else
        mount  --rbind  $directory $directoryPD
        mount  -t tmpfs none $directoryRAM -o size=$sizeOfRamdisk"m",noatime   # m=MB
        bash -c "
                     shopt -s dotglob; 
                     cp -a $directoryPD"/*"  $directoryRAM"/" 1>&2 > /dev/null;
                     shopt -u dotglob;
                "
        mount  --rbind  $directoryRAM  $directory -o noatime
        umount $directoryRAM
        rm     -r $directoryRAM
    fi

    #echo "directoryRights=$directoryRights"
    #echo "directoryOwner=$directoryOwner"
    #echo "directoryGroup=$directoryGroup"

    chown  $directoryOwner:$directoryGroup $directory
    chmod  $directoryRights                $directory

    #ls -ali $directory"/.."
 
    echo    "Current memory usage is" >> /var/log/ramdisk_sync.log
    free    -t -m >> /var/log/ramdisk_sync.log
    echo     "[`date +"%Y-%m-%d %H:%M"`] $directory Ramdisk Synched from HDD" >> /var/log/ramdisk_sync.log
}

f_RamdiskToHddDirectory()
{
    #Funktions parameter
    local directory=$1                              #directory on RAM which should be synced with HDD
    local isSquashFS=$2
    local isUpdateOriginalFS=$3
     
    #locale variablen
    local hiddenPD="/.physical_disk"
    local hiddenRAM="/.random_access_memory"
    local directoryPD="$hiddenPD""$directory"       #directory on HDD which is a mountpoint for HDD disk
    local directoryRAM="$hiddenRAM""$directory"     #directory on HDD which is a mountpoint for RAM disk

    if [ "$isSquashFS" = "true" ];
    then
        if [ "$isUpdateOriginalFS" = "true" ];
        then
            #synching the original physical disk directory
            local directoryPD=$directoryPD"/originalfs"
            echo " * synching $directoryPD" #RueckgabeString nach stdout schreiben
            rsync -av --delete $directory"/" $directoryPD"/" >> /var/log/ramdisk_sync.log
            echo "[`date +"%Y-%m-%d %H:%M"`] $directory Ramdisk Synched to HD" >> /var/log/ramdisk_sync.log
        fi
        #synching the squashfs file of the original physical disk directory
        echo " * update $directory squashfs?"
        if [ "`f_get_user_answer_yes_no`" = "yes" ];
        then
            f_update_squashfs "$directory"
        fi
        return
    fi

    if [ -n "`mount | grep "$directoryRAM on $directory"`" ];
    then
        echo " * synching $directoryPD" #RueckgabeString nach stdout schreiben
        rsync -av --delete $directory"/" $directoryPD"/" >> /var/log/ramdisk_sync.log
        echo "[`date +"%Y-%m-%d %H:%M"`] $directory Ramdisk Synched to HD" >> /var/log/ramdisk_sync.log
    else 
        echo "$directory is not a ramdisk"
    fi 
}

f_start()
{
    ####Deleteing old logfile
    rm      /var/log/ramdisk_sync.log.old                           2> /dev/null
    mv      /var/log/ramdisk_sync.log /var/log/ramdisk_sync.log.old 2> /dev/null
    touch   /var/log/ramdisk_sync.log                               2> /dev/null
    
    ####Turning of all Swap-Partitions
    echo " * Checking for swap partitions"
    if [ -n "`cat /proc/swaps  | grep /dev/`" ];
    then
        echo " * Disabling swap partitions: "
        cat /proc/swaps
        swapoff -a
    else 
        echo " * No swap-partition mounted"
    fi 

    echo " * Copying files to Ramdisk"
    
    ####MOVING /bin INTO RAMDISK
    f_HddDirectoryToRamdisk "/bin" "10" "false"

    ####MOVING /sbin INTO RAMDISK
    f_HddDirectoryToRamdisk "/sbin" "10" "false"
    
    #####MOVING /etc INTO RAMDISK
    f_HddDirectoryToRamdisk "/etc" "10" "false"
    
    #####MOVING /lib INTO RAMDISK
    f_HddDirectoryToRamdisk "/lib" "400" "false"

    #####MOVING /lib32 INTO RAMDISK
    #f_HddDirectoryToRamdisk "/lib32" "400" "false"

    ####MOVING /var INTO RAMDISK
    f_HddDirectoryToRamdisk "/var" "400" "false"

    ####MOVING /usr AS SQUASHFS WITH AUFS INTO RAMDISK
    f_HddDirectoryToRamdisk "/usr" "1000" "true"

    ####MOVING /home AS SQUASHFS WITH AUFS INTO RAMDISK
    #f_HddDirectoryToRamdisk "/home/YOURUSERNAME" "1500" "true"
    #chmod 700 /home/YOURUSERNAME
}

f_sync()
{
    echo " * Synching ramdisk files to harddisk"

    ####SYNCHING /bin TO /bin-HDD
    f_RamdiskToHddDirectory "/bin" "false" "ignored"

    ####SYNCHING /sbin TO /sbin-HDD
    f_RamdiskToHddDirectory "/sbin" "false" "ignored"

    ####SYNCHING /etc TO /etc-HDD
    f_RamdiskToHddDirectory "/etc" "false" "ignored"

    ####SYNCHING /lib TO /lib-HDD
    f_RamdiskToHddDirectory "/lib" "false" "ignored"

    ####SYNCHING /lib TO /lib32-HDD
    #f_RamdiskToHddDirectory "/lib32" "false" "ignored"

    ####SYNCHING /var TO /var-HDD
    apt-get clean
    f_RamdiskToHddDirectory "/var" "false" "ignored"

    ####SYNCHING /usr TO /usr-HDD
    f_RamdiskToHddDirectory "/usr" "true" "true"
    
    ####SYNCHING /usr TO /home/trg-HDD
    #f_RamdiskToHddDirectory "/home/YOURUSERNAME" "true" "false"
    
    ####SYNCHING /var TO /var-HDD ein zweites mal um die geaenderte logdatei zu speichern
    f_RamdiskToHddDirectory "/var" "false" "ignored"
}

case "$1" in
  start)
    echo " * Execute ramdisk script?"
    if [ "`f_get_user_answer_yes_no`" = "yes" ];
    then
        echo " * Sarting ramdisk script ..."
        f_start
    else 
        echo " * Skipping ramdisk script ..."
    fi
    ;;
  sync)
    f_sync
    ;;
  stop)
    #echo " * Execute ramdisk script?"
    #if [ "`f_get_user_answer_yes_no`" = "yes" ];
    #then
    #    echo " * Sarting ramdisk script ..."
    #    f_sync
    #else 
    #    echo " * Skipping ramdisk script ..."
    #fi
    echo " * Doing nothing ... All data in /bin /sbin /usr /var /etc /lib /lib32 will not be saved to disk!"
    ;;
  *)
    f_error
    ;;
esac
 
exit 0


```as before you may install/uninstall it with
```

    apt-get install rsync     #rsync
    apt-get install coreutils #date
    apt-get install squashfs-tools aufs-tools
    #install:   sudo cp ./ramdisk.sh /etc/init.d/ramdisk.sh && sudo update-rc.d ramdisk.sh start 35 S . && sudo /etc/init.d/ramdisk.sh start    
    #uninstall: update-rc.d -f  ramdisk.s
``` if you have an encrypted home, you'll need to execute the install command while logged in ... and note the squashfs-file won't be encrypted so your data wont be private anymore but the script will work at least 
as before use it on your owen risk ... may the force be with you

---

### Post by parul1234 on 2009-09-29
I tried this script on my machine ... of loading the linux into ram . But everything run properly but I see no changes

---

