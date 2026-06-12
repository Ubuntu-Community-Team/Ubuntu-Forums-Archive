---
title: "Ubuntu: creating multiple firefox profiles command line"
date: 2016-02-28
forum: Programming Talk
---

### Post by erotavlas on 2016-02-28
Hi,
I have a strange problem with a script that creates firefox profiles via command line. I can create a single profile for the sudo user while I cannot create the profiles for the other normal and sudo users. I read here [https://developer.mozilla.org/en-US/docs/Mozilla/Command_Line_Options](https://developer.mozilla.org/en-US/docs/Mozilla/Command_Line_Options) that the correct syntax is the following *firefox -CreateProfile "JoelUser c:\internet\joelusers-moz-profile". *I found on the web a command that retrieves all the user in a system. Then I added a loop over the users and the previous command.
```

usersList=$(getent passwd | grep -vE '(nologin|false)$' | \
awk -F: -v min=`awk '/^UID_MIN/ {print $2}' /etc/login.defs` \
-v max=`awk '/^UID_MAX/ {print $2}' /etc/login.defs` \
'{if(($3 >= min)&&($3 <= max)) print $1}' | \
sort -u)

for systemUser in $usersList; do
    echo $systemUser

    firefoxProfile="/home/$systemUser/.mozilla/firefox"
    firefox -CreateProfile "profile $firefoxProfile/m4v6pi7q.profile"
    chown -R $systemUser:$systemUser "/home/$systemUser/.mozilla/"
    
done

```
The problem is that if I have four-five users, the command works only for the current user that executes the script with sudo privilegios and for the first user in the list.
 This is the output
```

admin sudo user
sudo ./user.sh 
foo

(process:19288): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Success: created profile 'profile /home/foo/.mozilla/firefox/m4v6pi7q.profile' at '/home/foo/.mozilla/firefox/m4v6pi7q.profile/prefs.js'
admin

(process:19297): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Success: created profile 'profile /home/admin/.mozilla/firefox/m4v6pi7q.profile' at '/home/admin/.mozilla/firefox/m4v6pi7q.profile/prefs.js'
jack

(process:19306): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Success: created profile 'profile /home/jack/.mozilla/firefox/m4v6pi7q.profile' at '/home/admin/.mozilla/firefox/m4v6pi7q.profile/prefs.js'
chown: cannot access ‘/home/jack/.mozilla/’: No such file or directory
zorro

(process:19315): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Success: created profile 'profile /home/zorro/.mozilla/firefox/m4v6pi7q.profile' at '/home/admin/.mozilla/firefox/m4v6pi7q.profile/prefs.js'
chown: cannot access ‘/home/zorro/.mozilla/’: No such file or directory

```

Why for the first two users is the directory for profile corretly set, while for the other is the directory of the user that executes the script /home/admin/.mozilla/firefox/m4v6pi7q.profile?
I cannot understand if it is my fault or something else...thank you

---

### Post by vasa1 on 2016-02-28
> **erotavlas said:**
>  ... I can create a single profile for the **sudo** user while I cannot create the profiles for the other normal and **sudo** users. ...
Why do you want to use *any* browser with *sudo*? Isn't that not recommended?

---

### Post by erotavlas on 2016-02-28
> **vasa1 said:**
> Why do you want to use *any* browser with *sudo*? Isn't that not recommended?

I do not want to use every browser with sudo. I only want to install the same firefox profile with all add on and settings for every user to speed up the installation. I cannot use sync function of firefox. As you can see the command
 chown -R $systemUser:$systemUser "/home/$systemUser/.mozilla/"  
allows to use each profile as not sudo. Or am I missing something?

---

### Post by erotavlas on 2016-02-28
This code works well for the current user if it is executed with sudo privilegios
```

user=$(sudo logname)
firefoxProfile="/home/$user/.mozilla/firefox"
if [ ! -d "$firefoxProfile/m4v6pi7q.profile" ]; then
    rm -rf $firefoxProfile
    firefox -CreateProfile "profile $firefoxProfile/m4v6pi7q.profile"
        
    7z x -y ./m4v6pi7q.profile.7z
    mv ./m4v6pi7q.profile/* "$firefoxProfile/m4v6pi7q.profile"
    sudo chown -R $user:$user "/home/$user/.mozilla/"
    rm -rf m4v6pi7q.profile.7z m4v6pi7q.profile
fi

```
How can I create firefox profiles from a sudo user for each user (sudo and not sudo) of the system?

---

### Post by erotavlas on 2016-02-29
Hi,
I solved with a brilliant idea. Since I need to install in many PC the same firefox profile and these PC should have only this profile, I can avoid to use the command firefox -CreateProfile "profile $firefoxProfile/m4v6pi7q.profile that is the source of the problem. I can directly move the firefox folder with profiles.ini inside plus the m4v6pi7q.profile and crash reports folders into the home folder of each user in the system. This works perfectly.
I report the Linux/Ubuntu script
```

usersList=$(getent passwd | grep -vE '(nologin|false)$' | \
awk -F: -v min=`awk '/^UID_MIN/ {print $2}' /etc/login.defs` \
-v max=`awk '/^UID_MAX/ {print $2}' /etc/login.defs` \
'{if(($3 >= min)&&($3 <= max)) print $1}' | \
sort -u)

for systemUser in $usersList; do
    firefoxProfile="/home/$systemUser/.mozilla"
    if [ ! -d "$firefoxProfile/firefox/m4v6pi7q.profile" ]; then
        echo "Installing Firefox profile for user: $systemUser"
        sudo rm -rf $firefoxProfile
        sudo mkdir -p $firefoxProfile
        7z x -y ./firefox-profile.7z > /dev/null | egrep "p7zip|Ok"
        sudo mv ./firefox "$firefoxProfile/firefox"
        sudo chown -R $systemUser:$systemUser $firefoxProfile
        rm -rf firefox-profile.7z
    fi
done

```

---

