---
title: "My first shell script, criticism welcome!"
date: 2015-05-07
forum: New to Ubuntu
---

### Post by livin2chill on 2015-05-07
Hello Ubuntu forums! ):P
I am new to Ubuntu, and so far have done several things I am quite proud of:
[LIST]
[*]Made an apache webserver with my own html (before a week ago I had never touched it)
[*]Made a stratum mining server +titcoin node
[/LIST]                                                                                                                                                                                        
And my latest project is making a shell script to backup my ENTIRE (that's right) hard drive to a huge external one. Getting to the point, I know there's quite a bit I could improve on, and I would like your opinion on it:                                                                                                                                                                
                                                                                                                                                                                               
```
#!/bin/bash                                                                                                                                                                              
read -n1 -p "Would you like to back up your system? Uno for Si, and Dos for No." input                                                                                                         
echo                                                                                                                                                                                           
case $input in                                                                                                                                                                                 
  1)  fdisk -l;                                                                                                                                                                                
      echo;                                                                                                                                                                                    
      read -p "Please enter the name of your backup disk that was displayed in the fdisk window: " disk ;
      echo;
      echo "Backups now in progress! Please be aware that backups are saved to a Backups directory which this script creates, and backups are tarred and labelled by date!";
      echo "THIS WILL TAKE A VERY VERY LONG TIME IF YOU HAVE A LARGE FILESYSTEM! PLEASE BE PATIENT!!!";
      cd /;
      sudo mkdir -p /mnt/$disk && sudo mount /dev/$disk /mnt/$disk && sudo mkdir -p /mnt/$disk/Backups && sudo tar -cp $(date +%Y%m%d).tar --directory=/ --exclude=proc --exclude=sys --exclude=dev/pts --exclude=backups . && sudo cp $(date +%Y%m%d-%H).tar /mnt/$disk/Backups;
      echo "Okay, all done! To restore your system, you will have to untar and manually do it yourself. If you have any issues, email <email-removed>@icloud.com!";;  
   2) echo "Then why are you running this script?";;
  *) echo "I'm sorry, but I can't do that..."

esac
```
Honestly, I have no idea what I am doing. Any suggestions?

---

### Post by VMC on 2015-05-07
The 'fdisk -l' needs to be run using root(sudo).

---

### Post by livin2chill on 2015-05-08
Made a ton of changes:
```
#!/bin/bash
read -n1 -p "Would you like to back up verbosely and with minimal directories?? Uno for Si, and Dos for No." input
echo
case $input in
  1)  sudo fdisk -l;
      echo;
      cd /
      mkdir TempBackup && cd TempBackup;
      read -p "Please enter the name of your backup disk that was displayed in the fdisk window: " disk ;
      echo;
      echo "Tarring your /etc/ folder, be patient!" && sudo tar -cpf etc.tar /etc && echo "etc is tarred, copying now!" && sudo cp etc.tar /mnt/$disk/Backups && echo "Tarring your /bin/ folder!" && sudo tar -cpf bin.tar /bin && echo "bin is tarred, copying now!" && sudo cp bin.tar /mnt/$disk/Backups && echo "Tarring your /home/ folder, if you use bitcoind or litecoind it will be a bit!" && sudo tar -cpf home.tar --exclude=.cache --exclude=.gvfs /home && echo "home is tarred, copying now!" && sudo cp home.tar /mnt/$disk/Backups && sudo tar -cpf var.tar /var && echo "var is tarred, copying now!" && sudo cp etc.tar /mnt/$disk/Backups && cd / && echo "Tarring usr, IT IS UNLIKELY THAT THIS FILE CAN BE COPIED ON A FAT32 FS!!! AUTOSPLIT HAS BEEN ACTIVATED!!!" && sudo tar -cpf usr.tar /usr && echo "usr is tarred, copying/splitting now!" && mkdir split-files && cd split-files && split --bytes=1G /usr.tar split.tar && sudo cp * /mnt/$disk/Backups && cat split*.tar > usr.tar && cd /TempBackup && echo "Okay, finished! Let me clean up..."  && sleep 5 && echo "Cleaning all files...." && sudo rm -rf *.tar && echo "All Done!";;
  2) sudo fdisk -l;
    echo;
    cd /
    mkdir TempBackup && cd TempBackup;
    read -p "Please enter the name of your backup disk that was displayed in the fdisk window: " disk ;
    echo;
    echo "Backups now in progress! Please be aware that backups are saved to a Backups directory which this script creates, and backups are tarred and labelled by date!";
    echo "THIS WILL TAKE A VERY VERY LONG TIME IF YOU HAVE A LARGE FILESYSTEM! PLEASE BE PATIENT!!!";
    echo "THIS IS NOT THE SAME AS THE VERBOSE MODE! THIS COPIES ALL FILES TO DISK, NOT JUST THE COMMON ONES! YOU STILL HAVE TIME TO QUIT!!!"
    sleep 10
    cd /;
    sudo mkdir -p /mnt/$disk && sudo mount /dev/$disk /mnt/$disk && sudo mkdir -p /mnt/$disk/Backups && sudo tar -cpf $(date +%Y%m%d).tar --directory=/ --exclude=proc --exclude=sys --exclude=dev pts --exclude=backups . && sudo cp $(date +%Y%m%d-%H).tar /mnt/$disk/Backups;
    echo "Okay, all done! To restore your system, you will have to untar and manually do it yourself. If you have any issues, email harmius@icloud.com!";;
  *) echo "I'm sorry, but I can't do that...";;
esac
```
Thanks for the criticism!

---

### Post by VMC on 2015-05-08
No criticism, just a comment.
Read the following regarding running 'sudo' inside a script: [http://askubuntu.com/questions/425754/how-do-i-run-sudo-command-inside-a-script](http://askubuntu.com/questions/425754/how-do-i-run-sudo-command-inside-a-script)

---

### Post by livin2chill on 2015-05-08
I literally meant thanks if you are implying I was being sarcastic :) And thanks for that link, duly noted. Anything I can do to check if the script is being run as sudo?

---

### Post by Holger_Gehrke on 2015-05-08
> **livin2chill said:**
> Anything I can do to check if the script is being run as sudo?

The 'id' command with the option '-u' outputs the numerical user id to standard output. For root (who you temporarily are when using sudo) this is always '0'. So you'd do something like
```

if [ "$(id -u)" = "0" ] ; then
 # stuff you do as root
else
 # stuff you do when not root
fi

```

---

