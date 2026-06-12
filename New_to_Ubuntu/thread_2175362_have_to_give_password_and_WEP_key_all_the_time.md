---
title: "have to give password and WEP key all the time"
date: 2013-09-18
forum: New to Ubuntu
---

### Post by dulce2 on 2013-09-18
i know nothing and should not be using Ubuntu but the machine was donated so here i am. no one i know here in Mexico can help much either but i've done ok for 3 years with what help i can get which includes this forum.

ever since i upgraded to 12.04 i have had to give my password at every start up. that is annoying but i put up with it.

3 days ago the power went off in this town for a few seconds, then came back on. since then, i have been asked for my WEP key at startup and even waking up the machine. this is super annoying. the field where i type the key usually but not always has a report icon (triangle with an exclamation point). 

as of this afternoon it will not accept the WEP key on waking up and i have to restart the machine, give my password and then the WEP key in order to connect with internet.

and to confuse things further i often give the WEP and then have to cancel 3-5 other internet connections, and then the correct one with the WEP again before it will accept the WEP key and connect me.

so i'm asking for help with:

1) not having to give my password at start up

2) not having to give the WEP all the time. 

thanks :)

---

### Post by VMC on 2013-09-18
I don't know about the wireless WEP, but right click the mouse on any part of the background, then go to User Accounts. Unlock your user then click "on" for the Automatic Login.

Isn't WEP info coming from your router?

---

### Post by forestG on 2013-09-18
Can you create another user and see if there is a problem there? Afterwards write what happened.  Create an administrator user preferably.  You can try as well to delete all wireless connections stored in the menu network connections. Just type network connections in dash. Try to delete all passwords stored for this user by typing passowords in dash and opening the program "passwords and keys". Afterwards report here if the problem insists.

---

### Post by dulce2 on 2013-09-19
> **forestG said:**
> Can you create another user and see if there is a problem there? Afterwards write what happened.  Create an administrator user preferably.  You can try as well to delete all wireless connections stored in the menu network connections. Just type network connections in dash. Try to delete all passwords stored for this user by typing passowords in dash and opening the program "passwords and keys". Afterwards report here if the problem insists.

i've done a search to find out what 'typing  in dash' means but it makes no sense to me. am looking for 'passwords and keys' but haven't found it. is that 'key ring access'? it won't open.

i have tried to fix this from user accounts many times. it does not save any changes i make and will not enable new accounts. it wants a password that i'm sure i never gave.

i'll work on everything else later. thanks for your replies.

---

### Post by deadflowr on 2013-09-19
You gave a password upon install.
If you didn't install Ubuntu, then look over this to reset the password and set a new one.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

To try and reset the wireless settings, try this
In the top panel bar and the right side where all the icons are, should be an icon that looks like a radio signal, or a cone/triangle.
Click on it and it should show a list of connections avaiable, and at the bottom it should say connection information and edit connections.
Click on edit connections and a window should open up.
Look to see if a listing for your wifi connection is there.
Delete it. then close the window.
Click on the radio/triangle symbol again and click on your wifi connection.
(Make sure your connection was listed the first time)
Then enter your wifi WEP password/passphrase/key(whatever it is)

This applies to Ubuntu.
If the layout I've describe is nothing like what you have, then you are running a different interface.
If running a different interface, then please describe it as best you can.

---

### Post by dulce2 on 2013-09-19
> **deadflowr said:**
> 
To try and reset the wireless settings, try this
In the top panel bar and the right side where all the icons are, should be an icon that looks like a radio signal, or a cone/triangle.
Click on it and it should show a list of connections avaiable, and at the bottom it should say connection information and edit connections.
Click on edit connections and a window should open up.
Look to see if a listing for your wifi connection is there.
Delete it. then close the window.
Click on the radio/triangle symbol again and click on your wifi connection.
(Make sure your connection was listed the first time)
Then enter your wifi WEP password/passphrase/key(whatever it is)

This applies to Ubuntu.
If the layout I've describe is nothing like what you have, then you are running a different interface.
If running a different interface, then please describe it as best you can.

yes i'm familiar with that area and can do that. swear to me that i won't lose my connection entirely. :)

---

### Post by dulce2 on 2013-09-19
> **deadflowr said:**
> You gave a password upon install.
If you didn't install Ubuntu, then look over this to reset the password and set a new one.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)



i did not install it. the original 6 letter password works, i just get too many requests for it. that one box has 5 dots as the password. reset anyway?

---

### Post by dulce2 on 2013-09-19
> **VMC said:**
> I don't know about the wireless WEP, but right click the mouse on any part of the background, then go to User Accounts. Unlock your user then click "on" for the Automatic Login.

Isn't WEP info coming from your router?

ok tried that again. maybe i was leaving it unlocked? (i told you i'm ignorant). it seems to want a 5 letter password and the only password i ever used has 6.  i'm not going to restart the compu (thats what they call it here :)) until i have more of this squared away.

about the router-- someone is going to have to explain that to me please. (i did look it up).

---

### Post by deadflowr on 2013-09-19
Deleting the entry in edit connections should have no effect in your connection.
You can investigate the contents of the entry by clicking edit.
After you delete the entry, clickong on your connections name again(in the dropdown list) and re entering the WEP stuff will generate a new one.

As far as passwords go, if you can't unlock the user accounts with the existing password, then it doesn't work, or it doesn't have admin rights.
You can easily find out if you have admin rights by using a terminal and simply enter "id" (without quotes).
The admin rights would be listed as sudo, if that is listed then you have those rights.

If you don't have those rights, then follow the link I supplied earlier and after resetting the password and before exiting for the user run this
```
adduser yourusername sudo
```
this will add your user to the sudo group giving you admin rights.
Then reboot.


Added: the 5 dot password is generic.
It simply means a password has been set.
The actual password could be 100 characters long and it would still be 5 dots.

---

### Post by dulce2 on 2013-09-19
> **deadflowr said:**
> Deleting the entry in edit connections should have no effect in your connection.
You can investigate the contents of the entry by clicking edit.
After you delete the entry, clickong on your connections name again(in the dropdown list) and re entering the WEP stuff will generate a new one.

As far as passwords go, if you can't unlock the user accounts with the existing password, then it doesn't work, or it doesn't have admin rights.
You can easily find out if you have admin rights by using a terminal and simply enter "id" (without quotes).
The admin rights would be listed as sudo, if that is listed then you have those rights.

If you don't have those rights, then follow the link I supplied earlier and after resetting the password and before exiting for the user run this
```
adduser yourusername sudo
```
this will add your user to the sudo group giving you admin rights.
Then reboot.


Added: the 5 dot password is generic.
It simply means a password has been set.
The actual password could be 100 characters long and it would still be 5 dots.

ok there are still 3 extra names on the drop down menu but none in edit connections. it took my WEP and hooked up immediately.

i'm embarrassed to say this-- i've used terminals before but i sure can't find one now in 12.04

guess i'll restart and see where i'm at....

---

### Post by dulce2 on 2013-09-19
yay! hooked me right up to internet. still had to give my password first.

---

### Post by VMC on 2013-09-19
Use "Ctrl+Alt+t" to go straight to Terminal.

---

### Post by dulce2 on 2013-09-19
> **deadflowr said:**
> Deleting the entry in edit connections should have no effect in your connection.
You can investigate the contents of the entry by clicking edit.
After you delete the entry, clickong on your connections name again(in the dropdown list) and re entering the WEP stuff will generate a new one.

As far as passwords go, if you can't unlock the user accounts with the existing password, then it doesn't work, or it doesn't have admin rights.
You can easily find out if you have admin rights by using a terminal and simply enter "id" (without quotes).
The admin rights would be listed as sudo, if that is listed then you have those rights.

If you don't have those rights, then follow the link I supplied earlier and after resetting the password and before exiting for the user run this
```
adduser yourusername sudo
```
this will add your user to the sudo group giving you admin rights.
Then reboot.


Added: the 5 dot password is generic.
It simply means a password has been set.
The actual password could be 100 characters long and it would still be 5 dots.

the terminal didn't say anything about sudo. should i post what it says or is that private? i am listed as admin in 'user accts'.

---

### Post by deadflowr on 2013-09-19
> **dulce2 said:**
> the terminal didn't say anything about sudo. should i post what it says or is that private? i am listed as admin in 'user accts'.

If it's listed as admin in the user accounts settings, then you should be an admin.

Though it is strange that there would be no sudo group listed in the id command.
It might also be listed as admin(not adm, which is a group for accessing log files)

This gives a good answer on the default groups for the systems initial user
[http://askubuntu.com/questions/219083/default-groups-for-user-in-ubuntu-12-10](http://askubuntu.com/questions/219083/default-groups-for-user-in-ubuntu-12-10)

Though it's for 12.10, it applies to 13.04, and 12.04 as well.

Edit: Edit the edit: Rereading prior post, now if you go to edit connections is there a listing for the connection?

---

### Post by dulce2 on 2013-09-19
> **deadflowr said:**
> If it's listed as admin in the user accounts settings, then you should be an admin.

Though it is strange that there would be no sudo group listed in the id command.
It might also be listed as admin(not adm, which is a group for accessing log files)

This gives a good answer on the default groups for the systems initial user
[http://askubuntu.com/questions/219083/default-groups-for-user-in-ubuntu-12-10](http://askubuntu.com/questions/219083/default-groups-for-user-in-ubuntu-12-10)

Though it's for 12.10, it applies to 13.04, and 12.04 as well.

Edit: Edit the edit: Rereading prior post, now if you go to edit connections is there a listing for the connection?

the link is too much for me. i have no background. here are the groups-- (my name),(adm),(dialout),(cdrom),(plugdev),(lpadmin),(admin),(sambashare)

---

### Post by mastablasta on 2013-09-20
the easiest way then is to reinstall the whole OS and set it up the way you want it from start (perhaps even try another version: Xubuntu Kubuntu Lubuntu). although i believe on this installed one solution can still be reached without reinstall.

Kubuntu also asks for Wi-fi password on logon. it's because the password is stored along with othe rpassword in something called KDE wallet. similar thing is probably in ubutnu using Keyring or something like that. one password in this password manager locks all  other passwords.

---

### Post by deadflowr on 2013-09-20
> **dulce2 said:**
> the link is too much for me. i have no background. here are the groups-- (my name),(adm),(dialout),(cdrom),(plugdev),(lpadmin),(admin),(sambashare)

Don't worry about the link, it's just something to read if you choose to go down that rabbit hole.

As far as groups are concerned, you have admin which is what sudo was before.
I had to re-read post #1 to realize the system was upgraded to 12.04, so it seems you have legacy group settings.
Nothing wrong there.

---

### Post by dulce2 on 2013-09-20
> **mastablasta said:**
> the easiest way then is to reinstall the whole OS and set it up the way you want it from start (perhaps even try another version: Xubuntu Kubuntu Lubuntu). although i believe on this installed one solution can still be reached without reinstall.

Kubuntu also asks for Wi-fi password on logon. it's because the password is stored along with othe rpassword in something called KDE wallet. similar thing is probably in ubutnu using Keyring or something like that. one password in this password manager locks all  other passwords.

as far as changing OS goes, i have someone who will install windows when i'm ready to give up here. :) my internet provider won't deal with me when i have a problem because of ubuntu. last time i needed them we told them we had to fix the problem because we were going to install windows and they complied.

---

### Post by VMC on 2013-09-20
> **dulce2 said:**
> as far as changing OS goes, i have someone who will install windows when i'm ready to give up here. :) my internet provider won't deal with me when i have a problem because of ubuntu. last time i needed them we told them we had to fix the problem because we were going to install windows and they complied.
Whenever I have had network issues, I **always** answer the question Windows, even though I know is in resetting the locked static port. When they tell me to do such and such, I do Windows equivalent. They have some sort of script they follow. Its always the same dance. I learn to just answer to what they want to hear. No problems anymore.

---

### Post by dulce2 on 2013-09-20
good idea...........

---

