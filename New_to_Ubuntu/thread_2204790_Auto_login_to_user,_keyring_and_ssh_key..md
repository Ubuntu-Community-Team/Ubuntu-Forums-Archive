---
title: "Auto login to user, keyring and ssh key."
date: 2014-02-10
forum: New to Ubuntu
---

### Post by Rothamel82 on 2014-02-10
I am trying to get Ubuntu 13.10 x64 to auto login to a user account, the user's keyring and a ssh key so when I run rsync from the startup applications is does not ask for a password. When I set the user account to not auto login, the keyring and ssh key unlock correctly and rsync runs without asking for a password. However, when I change the user account to auto login this no longer works. I tried opening seahorse and setting the login password to blank but the ssh key was still not open on a restart with the user auto loggin in.

I also noticed that when the user account is set to auto login "off". the password pop up has a checkbox for auto login. When the user account is set to auto login "on" the check box no longer appears on the password pop up.

I want the auto login since this is my media center. It boots to the user desktop and auto starts XBMC and rsync. Rsync at startup will ensure all the new media is on it.

I tried searching the forms and google but I did not find anything that worked. This is my first Ubuntu forums post so I apologize if this is not in the correct area or I did not included needed information.

---

### Post by Rothamel82 on 2014-02-11
Password pop up when i have the user set to automatic lon in "off" under user accounts

Yet this is the Password pop up when i have the user set to automatic lon in "on" under user accounts

[IMG]https://files.one.ubuntu.com/kHRlQyQeRnS2SPKfAjZViA[/IMG]


The "expect" command works correctly with the user name and password but does not seem to work with a pop up out side of the terminal requesting the passphrase. I also tried using keychain to unlock the passphase. Keychain works correctly when the user account is not set to auto login but not when the user account is set to auto login. 

From the above it looks like the key ring does not unlock when the user is set to auto login even if the password is blank. Is there a way to get the key ring to auto login when the user auto logs in? maybe a startup script or change a default setting?

If you can't see the 2 pictures above, they are located here
[https://drive.google.com/?tab=wo&authuser=0#folders/0B7aKGA3r4b5Sd0psSGRiZTRaMms](https://drive.google.com/?tab=wo&authuser=0#folders/0B7aKGA3r4b5Sd0psSGRiZTRaMms)

---

### Post by Rothamel82 on 2014-02-16
I found a way to make this work with the user set to auto log on, the login keyring password set to the same password as the user account, and another password for the ssh passhrase (not blank). I had to remove the ssh key from seahorse. This also deleted the id_dsa file on the computer. I copied it back from a backup but did not add it to the keyring. I left the keyring locked and now use the below script to unlock the ssh key since the ssh key now asks for the passphase in the terminal instead of a pop up window when it it not stored in seahorse. I just added a line in my rsync script before rsyc is called to run the below script and now it works correctly at startup. :) I am not sure why I need the sleep command in there but it does not work without it. Now the password security risk on the server is the same as having someone get the passpharse when it is sent over the internet.

#!/usr/bin/expect
spawn ssh-add /home/USER/.ssh/id_dsa
expect "Enter passphrase for /home/USER/.ssh/id_dsa: "
send "PASSWORD\r"
sleep 2

#to ensure nobody can open this file
#chmod 700 and hide this script
#setup ssh passphase to only work from this computer
#only use the passphase for this ssh key

---

