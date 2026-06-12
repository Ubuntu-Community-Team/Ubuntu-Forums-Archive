---
title: "HOWTO: Remounting home directory with truecrypt drive on session start"
date: 2007-12-19
forum: Outdated Tutorials &amp; Tips
---

### Post by ephro on 2007-12-19
[COLOR=Red]Quick Head Up: [COLOR=Black]This is a current work in progress and is being tested by a couple of users that I know. In the future I'll have it packaged in a .deb, but don't want to go the hassle while it's still under bug fixes.[/COLOR][/COLOR]

So after searching high and low for an easier to use security system for linux I decided to roll my own. The following requirements had to be met:[LIST]
[*]Fully encrypted home directory
[*]Ability to have a plausible deniability drive (even if never used)
[*]Encrypted drive not have to be used (say if your wife/kids/friends want to look something up on the internet)
[*]Be fairly user friendly
[*]Keep all stateful session information for each drive[/LIST]In addition I also configured a random key swap and tmp directory, but that is covered in many other places on the internet and a little Googling will find it for you.

I went through quite a few revisions before coming up with the following soliution. Basically what I decieded to do was make it so that after a login the user is prompted for the encryption password. This password is used to remount the login home directory with the TrueCrypt partition that the key unlocks. If you are familiar with TrueCrypt, this means that there is just one password prompt and it will either mount the encrypted drive or the hidden drive (which is the plausible deniability drive.)

Preconfiguration not currently scripted:[LIST]
[*]Create a TrueCrypt drive in /home that is named [login_name]_home.tc
[*]Create a hidden TrueCrypt partition inside of the original partition
[*]Format the first partition to your liking (I choose ext3)
[*]Format the second partition to your liking (again I choose ext3)[/LIST]Now is where the fun starts:[LIST=1]
[*]Create a /usr/share/truehomecrypt directory
[*]Create a /usr/share/truehomecrypt/scripts directory
[*]In the /usr/share/truehomecrypt/scripts directory make a file named PostLogin with the following: ```
#!/bin/bash

appname="TrueHomeCrypt"
loginname=$1
mount_error_text=""

do_window_popup()
{
    password_line=`zenity --entry --hide-text=* --text="$1" --title=$appname`
    retcode=$?
    if [ $retcode -ne 0 ]; then 
    if [ $retcode -eq 1 ]; then
        zenity --info --text="Proceeding without a secure home directory" --title=$appname
        return 0
    fi
    return -1
    fi
    do_truecrypt_mount $loginname $password_line
    return $?
}

do_truecrypt_mount()
{
    
    password_line=$2
    mount_error_text=`truecrypt -p $password_line /home/${loginname}_home.tc /home/${loginname}`
    retcode=$?
    return $retcode
}

do_ask_for_password() 
{
    function_return=-2
    while [ $function_return -ne 0 ];
    do
    if [ "$mount_error_text" != "" ]; then
            zenity --error --text="An Error has occured:\n\n${mount_error_text}" --title=$appname
    fi
    mount_error_text=""
    do_window_popup "Enter Secure Storage Password" $loginname
    function_return=$?
    done
}

check_for_crypt_file()
{
    if [ -e "/home/${loginname}_home.tc" ]; then
    return 0
    fi
    zenity --error --text="File /home/${loginname}_home.tc does not exists" --title=$appname
    return -1
}

check_for_crypt_file "$loginname"

num=0
(
while [ -e /dev/mapper/truecrypt* ] && [ $num -lt 100 ]; do
    truecrypt -d
    (( num++ ))
    echo $num
    sleep 1
done) | stopper=`zenity --progress --text="Cleaning up old mounted drives" --title=$appname --auto-close`
if [ "${PIPESTATUS[0]}" != "0" ]; then
zenity --error --text="Session is not secured." --title="Error"
exit 1
fi


if [ $? -eq 0 ]; then
    #We have a file to process now we need to try to get a password
    do_ask_for_password $loginname
    if [ "$mount_error_text" != "" ]; then
    zenity --error --text="Password is incorrect" --title=$appname
    fi
fi

exit 0
```
[*]Rename /etc/gdm/PostLogin/Default.sample to /etc/gdm/PostLogin/Default
[*]Change /etc/gdm/PostLogin/Default to contain the following:```
#!/bin/sh
#
# Note: this is a sample and will not be run as is.  Change the name of this
# file to <gdmconfdir>/PostLogin/Default for this script to be run.  This
# script will be run before any setup is run on behalf of the user and is
# useful if you for example need to do some setup to create a home directory
# for the user or something like that.  $HOME, $LOGNAME and such will all be
# set appropriately and this script is run as root.

cd /etc/gdm/PostLogin
/usr/share/truehomecrypt/scripts/PostLogin $LOGNAME
```
[*]Edit /etc/gdm/PostSession/Default and put the following before the "exit 0":```
if [ -e /dev/mapper/truecrypt* ]; then
    loginname=`whoami`
    umount -f /home/${loginname}
    truecrypt -d
fi
```[/LIST]Now when you login you will be asked for an encryption password before your Xsession starts to load. Not hooking in before the Xsession causes major problems since files are already being written to in your home directory. If you hit 'Cancel' no encrypted drive is mounted and you can simply use your computer as normal.

[COLOR=Red]Known Issues:
[/COLOR][LIST]
[*]The PostSession doesn't actually do anything unless you don't have things such as trackerd running.
[*]This is NOT multiuser friendly yet, meaning that two or more users can't be logged in at the same time with encrypted home directories, however if one is logged in, the other simply won't be able to mount another encrypted home directory after the first.
[*]Once your drive is mounted it may not get unmounted after logout. Only shutting down your computer or relogging in without using an encryption password will force it
[*]Files in your home directory can't be accessed between session (meaning you can't have cron jobs that run from there or other such things)[/LIST]Please post any comments or code changes. This was a 4 hour hack and will get supported more and hopefully make it into distribution. It's especially useful for one user laptop installs.


ephro

---

### Post by HDave on 2007-12-20
Thanks a lot for this -- just tried it out and it works.

I booted Gutsy into single user mode in order to copy all my files from my old home directory to the TC volume.  Hit "exit" and the boot continued as normal and I was able to log in...viola.

Been a long time TC user (2+ years on WIndows and 2+ months on Ubuntu).  However,  I did notice that for some reason the read/write performance to my home directory is really slow.  Any thoughts?

---

### Post by andreyka on 2007-12-22
ephro, thanks for your solution!
but at my ubuntu  7.10 gdm postlogin script doesn't work (yes, I rename Default.sample to Default and use gnome)
how I can fix them ?

---

### Post by ephro on 2007-12-22
> **andreyka said:**
> ephro, thanks for your solution!
but at my ubuntu  7.10 gdm postlogin script doesn't work (yes, I rename Default.sample to Default and use gnome)
how I can fix them ?

What is the error that you are getting? Is it just never asking you for the additional password?


ephro

---

### Post by andreyka on 2007-12-22
Thanks for fast reply.
here is the solve :)
```
sudo chmod 0755 /usr/share/truehomecrypt/scripts/PostLogin
```
founded after
```
cat /var/log/syslog | grep gdmDec 22 16:29:48 localhost gdm[5086]: WARNING: gdm_slave_session_start: &#1057;&#1082;&#1088;&#1080;&#1087;&#1090; PostLogin &#1074;&#1077;&#1088;&#1085;&#1091;&#1083; &#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1077; > 0. &#1055;&#1088;&#1086;&#1080;&#1089;&#1093;&#1086;&#1076;&#1080;&#1090; &#1072;&#1074;&#1072;&#1088;&#1080;&#1081;&#1085;&#1086;&#1077; &#1086;&#1082;&#1086;&#1085;&#1095;&#1072;&#1085;&#1080;&#1077; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099;. 
Dec 22 16:37:15 localhost gdm[5086]: WARNING: gdm_slave_xioerror_handler: &#1060;&#1072;&#1090;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1086;&#1096;&#1080;&#1073;&#1082;&#1072; X - &#1055;&#1077;&#1088;&#1077;&#1079;&#1072;&#1087;&#1091;&#1089;&#1082; :0 
Dec 22 16:56:43 localhost gdm[5084]: WARNING: gdm_slave_session_start: &#1057;&#1082;&#1088;&#1080;&#1087;&#1090; PostLogin &#1074;&#1077;&#1088;&#1085;&#1091;&#1083; &#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1077; > 0. &#1055;&#1088;&#1086;&#1080;&#1089;&#1093;&#1086;&#1076;&#1080;&#1090; &#1072;&#1074;&#1072;&#1088;&#1080;&#1081;&#1085;&#1086;&#1077; &#1086;&#1082;&#1086;&#1085;&#1095;&#1072;&#1085;&#1080;&#1077; &#1088;&#1072;&#1073;&#1086;&#1090;&#1099;.
```
(in russian)

---

### Post by HDave on 2008-01-02
I found another approach to doing this that uses the PAM facility that comes with Ubuntu.  It worked great:

[http://www.fstab.de/twiki/bin/view/Main/PamTruecrypt](http://www.fstab.de/twiki/bin/view/Main/PamTruecrypt)

Please note that in order to get it to compile I needed add:

```
#include <sys/syslog.h>
```

in the pam_truecrypt.c file.

Other than this little glitch it works exactly like TCGINA -- and reuses your login password to mount the truecrypt partition -- without storing your password anywhere!

Cool, eh?

---

### Post by IamAcoconut on 2008-07-16
Any idea on how to do this with KDE?

BTW [http://www.fstab.de/twiki/bin/view/Main/PamTruecrypt](http://www.fstab.de/twiki/bin/view/Main/PamTruecrypt) is unavailable 
Yet cached here: [http://cc.msnscache.com/cache.aspx?q=73622812561873&mkt=en-US&setlang=en-US&w=ec7fd3f1,7c8d0bbb&FORM=CVRE](http://cc.msnscache.com/cache.aspx?q=73622812561873&mkt=en-US&setlang=en-US&w=ec7fd3f1,7c8d0bbb&FORM=CVRE)

---

### Post by _madman_ on 2009-08-17
is anyone have same issue on truecrypt usage [http://forums.truecrypt.org/viewtopic.php?t=15761](http://forums.truecrypt.org/viewtopic.php?t=15761) ?

---

### Post by natrik on 2009-12-03
> **HDave said:**
> I found another approach to doing this that uses the PAM facility that comes with Ubuntu.  It worked great:

[http://www.fstab.de/twiki/bin/view/Main/PamTruecrypt](http://www.fstab.de/twiki/bin/view/Main/PamTruecrypt)

... (Snipped for brevity) ...

Looking around, I found a very simple alternative which decrypts one user's home directory just before GDM login (the graphical ubuntu login screen).  I suppose it could work for more than one user, but I guess you'd have to know the order of the truecrypt password prompts, and cancel the ones you don't intend to decrypt.

For the details, click here: ["Using TrueCrypt to encrypt one users home folder"]("http://ubuntuforums.org/showthread.php?t=1014891") [sic] (Thank you user ragtag!)

The PAM approach to home-directory encryption which HDave suggested above (thank you Hdave!) is the most elegant method I have seen so far, albeit a bit more involved for the less initiated.

-- Nate

---

