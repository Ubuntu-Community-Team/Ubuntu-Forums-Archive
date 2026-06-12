---
title: "Can't login after update"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by fairy._.queen on 2014-03-08
Dear all,

a long time ago I tried to change Linux loading screen in the settings: although I did everything alright, it never worked, until (sadly) yesterday night.
Yesterday night I updated the kernel after a long time and, when it rebooted, I had this login screen that just doesn't let me login: there is no real "login" button, just "username" and if I type username and password and press enter I'm only prompted for username and password again. I have tried accessing the console: from there I can login (and this also shows that I'm not using the wrong user/password) but if I try "startx", which I thought was the way to make the graphic session start, I only get a black screen that stays there forever. If I could, I would post screenshots.

Thanks in advance if you can help!

---

### Post by fairy._.queen on 2014-03-08
Is there any other command to start X?

---

### Post by ajgreeny on 2014-03-08
If you are still using Kubuntu 12.04 you could try **sudo service kdm start** but make sure kubuntu uses kdm first or that will never work.  I don't use Kubuntu and have no idea which display manager it uses, so try alternatives if the first does not help, ie lightdm, etc etc.

You could also try using a different kernel from the grub menu (hold down shift after the POST when you boot to get the menu if it does not normally show).

---

### Post by NM5TF on 2014-03-08
you might have to do this:

[http://ubuntuforums.org/showthread.php?t=1859272](http://ubuntuforums.org/showthread.php?t=1859272)

this worked for me after I borked my system installing gnome flashback...I had a similar problem

just follow the steps in the thread....you may have to change something that is compatible with Kubuntu

good luck....let us know if it works

tommy

---

### Post by fairy._.queen on 2014-03-08
Hi all! Thanks a lot for your replies!

Unfortunately it didn't work: the system has kdm but not lightdm (it didn't recognise the name), so what I did was trying
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service kdm restart

it did cause something to move, but in the end the login problem wasn't solved whenever the graphic session was in place. Is there a way to remove the login window from the Console? I am sudo.

Thanks!

---

### Post by fairy._.queen on 2014-03-09
And yes, I still have Kubuntu Precise Pangolin, I think it's the best OS that can still run on my computer, which is old.

---

### Post by NM5TF on 2014-03-09
latest search says try this .....

from terminal do usual log-in....then do this....

rightALT + prtsc + k   keys for Kubuntu 12.04 to restart X server....

the printscreen key is also the SysRq key on my Dell keyboard...

hope this works for you....

tommy

---

### Post by bapoumba on 2014-03-09
Please log into the console and run **df -h** and make sure your root (/) or /home or other essential system partition (/boot etc.) is not full.

---

### Post by fairy._.queen on 2014-03-09
Problem not solved yet but... I'm finally writing from my Linux!!! Thanks guys! I'll tell you what happened:

my /home was indeed full, so I moved a lot of stuff from the Console. After that the login problem was still there when the graphic session was in place, so I tried 
rightALT + prtsc + k keys
Assuming I interpreted the key names right, this caused the Console to ask me for login again. Somehow, though, now "startx" worked, which is why I'm now able to write here from Linux!

Can you please help me remove this problem without having to login through the Console every time? Thanks!

---

### Post by fairy._.queen on 2014-03-09
More interesting information that I just found out! The sound is completely not working, and if I type 
aplay -l
it says:
aplay: device_list:252: nessuna scheda audio trovata...
which means "no sound board found". This applies even if I choose an older version of Linux from grub.

---

### Post by bapoumba on 2014-03-09
If you have made enough room on your /home, you should be able to login normally.
The sound problem should be a different one, please tart up a new thread, thanks.

---

### Post by fairy._.queen on 2014-03-09
I'm not able to login normally and the reason why I didn't start a new thread is: the way this looks to me (but I'm a beginner), somehow a lot of settings have disappeared for the main user, otherwise I don't know why using a previous version of Kubuntu just doesn't help at all.

ALL of the Kubuntu versions, including the pre-upgrade one that worked perfectly have the same problems: I can't login normally, the sound is out and who knows what else :D

Thanks for replying!

---

### Post by bapoumba on 2014-03-10
OK, to know if this is something with your regular user or with the system, please make another user and add it to the sudo group (to give it admin privileges). From the console (sorry, once again..):
```
sudo adduser <pick_a_username>
sudo adduser <picked_username> sudo
```
In the process you'll have to pick a password, and give other info (which from memory can be left blank).
Go to the graphical environment and logout, then log back in with this new user. Are things OK from there ? If so, there is something with your user. If not, there is something with the system and we can work from here.

---

### Post by fairy._.queen on 2014-03-10
I created another user and this one can log in fine, there is even the sound.
With the normal user, I can't, and I have found out that the session that I open with startx from console is not a normal session (not big deal for you, probably), in that, for example, all the network settings (e.g. password) are lost every time I close the session. I guess if I could login normally maybe it would be different?

If I'm correct, this means that I have to find out how to login normally first?

---

### Post by bapoumba on 2014-03-10
OK, I'll need to dig around and think a bit. And if it is a big deal for you, it is also a big deal for me, kinda :)
We need to find what is wrong with your user, as things are normal with a newly created one.
Please make sure your /home is at least 10% free (OTOH 7% is enough, I'll have to look). Can you confirm you have indeed renamed the .Xauthority file so that we can get this item out of the way ?

Edit : please have a look at .xsession-errors, from the console or a terminal **cat .xsession-errors** and paste the last lines here (not sure how many).

---

### Post by bapoumba on 2014-03-10
Sorry to bump, some other considerations.

Please make sure your /home and some /home files have the correct permissions :

```
bapoumba_lxde@SonyBlue:~$ ls -la .bashrc
-rw-r--r-- 1 bapoumba_lxde bapoumba_lxde 3637 août  23  2013 .bashrc
bapoumba_lxde@SonyBlue:~$ ls -la .dmrc
-rw-r--r-- 1 bapoumba_lxde bapoumba_lxde 26 mars  10 13:47 .dmrc
bapoumba_lxde@SonyBlue:~$ ls -la .ICEauthority 
-rw------- 1 bapoumba_lxde bapoumba_lxde 326 août  23  2013 .ICEauthority
bapoumba_lxde@SonyBlue:~$ ls -la .Xauthority
-rw------- 1 bapoumba_lxde bapoumba_lxde 53 mars  10 13:47 .Xauthority
bapoumba_lxde@SonyBlue:~$ ls -ld ../bapoumba_lxde /home
drwxr-xr-x 34 bapoumba_lxde bapoumba_lxde 4096 mars  10 13:47 ../bapoumba_lxde
drwxr-xr-x  5 root          root          4096 août  23  2013 /home
```

---

### Post by fairy._.queen on 2014-03-10
note: the "big deal" sentence was meant to say that maybe to you it was obvious that this type of session was different, whereas to me it was an interesting finding :-) I'm not a native speaker, forgive me...

Thanks a lot for your help! So, this is the situation:
1) I can't login normally
2) My home was 60% used, now it's 40% used
3) I had indeed renamed the .Xauthority file, I did it again for sure and nothing changed
4) some permissions were wrong (ICEauthoriy didn't exist, .dmrc's permission were different): all permission are now fine, except that ICEauthority still doesn't exist (do I have to create it? If so, what should I write on it?)
5) when I log in, there is some kind of black screen with some writings on it that I don't have the time to read and that I'm not able to screen print: it lasts a fraction of a second and then the login screen appears again - in case this information is of any use
6) this is the output of cat .xsession-errors (there's probably more to it, this is just what I was able to get in the output):
```
n(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 10
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0x928f890)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 11
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0x92c9b38)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0x928f890)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() 
virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection 
void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 10
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0x92c9b38)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished()
[/usr/bin/nepomukservicestub] virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 9
[/usr/bin/nepomukservicestub] QObject::connect: Cannot connect XSyncBasedPoller::destroyed() to (null)::_k_x11FilterDestroyed()
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xae00031
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xae00031
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 19 (X_DeleteProperty)
  Resource id:  0xae00031
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xae00031
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xae00031
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr) 
void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 10
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0x902a5a8)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0x902a5a8)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished()
[/usr/bin/nepomukservicestub] virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 9
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 10
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0x902a5a8)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0x902a5a8)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() 
virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection 
void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 9
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x9e00014
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x9e00014
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0x93fdca8)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() 
virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection 
void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 8
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 19 (X_DeleteProperty)
  Resource id:  0x9e00014
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x9e00014
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x9e00014
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x9e00014
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x9e00014
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 9
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 10
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0x9060dd8)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0x9060dd8)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() 
virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection 
void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 9
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0x93fdca8)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::LocalServer::incomingConnection(quintptr)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCorePrivate::addConnection(Soprano::Server::ServerConnection*) New connection. New count: 10
[/usr/bin/nepomukservicestub] Soprano::ODBC::Connection::Connection() Soprano::Server::ServerConnection(0x92a2760)
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0x92a2760)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() 
virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection 
void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 9
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xae00031
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xae00031
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 19 (X_DeleteProperty)
  Resource id:  0xae00031
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xae00031
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0xae00031
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
[/usr/bin/nepomukservicestub] virtual void Soprano::Server::ServerConnection::run() thread done.
[/usr/bin/nepomukservicestub] virtual Soprano::ODBC::Connection::~Connection() Soprano::Server::ServerConnection(0x93fdca8)
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished()
[/usr/bin/nepomukservicestub] virtual Soprano::Server::ServerConnection::~ServerConnection() Removing connection
[/usr/bin/nepomukservicestub] void Soprano::Server::ServerCore::serverConnectionFinished() Connection removed. Current count: 8
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#height> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Visual>. <_:e> only has the following types <_:f>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#height> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Visual>. <_:e> only has the following types <_:f>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#width> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Visual>. <_:i> only has the following types <_:j>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#width> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Visual>. <_:i> only has the following types <_:j>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#height> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Visual>. <_:m> only has the following types <_:n>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#height> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Visual>. <_:m> only has the following types <_:n>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#width> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Visual>. <_:q> only has the following types <_:r>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#width> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Visual>. <_:q> only has the following types <_:r>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/01/19/nie#url> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#DataObject>. <_:v> only has the following types <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/01/19/nie#url> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#DataObject>. <_:v> only has the following types <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#height> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Visual>. <_:y> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <_:z>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#height> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Visual>. <_:y> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <_:z>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/01/19/nie#url> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#DataObject>. <_:db> only has the following types <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/01/19/nie#url> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#DataObject>. <_:db> only has the following types <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'bbb@zzz.org'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'yyy@example.com'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'a@example.com'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Dingus Lovers <cravindogs@cravindogs.com>'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'bbb@zzz.org'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'aperson@dom.ain'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'bperson@dom.ain'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'aperson@dom.ain'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Internet-Drafts@ietf.org'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Dingus Lovers <cravindogs@cravindogs.com>'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'bbb@zzz.org'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'barry@python.org'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'barry@python.org'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'aperson@dom.ain'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'ppp@zzz.org'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'bbb@zzz.org'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Dingus Lovers <cravindogs@cravindogs.com>'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Dingus Lovers <cravindogs@cravindogs.com>'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'bperson@dom.ain'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Dingus Lovers <cravindogs@cravindogs.com>'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'barry@python.org'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'bbb@zzz.org'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Dingus Lovers <cravindogs@cravindogs.com>'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'bperson@dom.ain'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Dingus Lovers <cravindogs@cravindogs.com>'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'yyy@example.com'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Barney Dude <bdude@example.com>'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'someone@example.com'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Barney Dude <bdude@example.com>'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Barney P. Erson <bperson@dom.ain>'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'scr-admin@socal-raves.org'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'baz@bar.foo'."
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'aperson@dom.ain'."
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'Dingus Lovers <cravindogs@cravindogs.com>'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'aperson@dom.ain'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Unknown protocol '' encountered in 'timbo@jeeves.wooster.local'."
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kded(1966)/kmix sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
kmix(2272) sink_input_cb: Ignoring sink-input due to it being designated as an event and thus handled by the Event slider 
plasma-desktop(2182)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
plasma-desktop(2182)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
plasma-desktop(2182)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:nf> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:nf> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:qf> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:qf> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:tf> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:tf> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:wf> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:wf> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:zf> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:zf> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:cg> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:cg> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:fg> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:fg> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:ig> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:ig> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:lg> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:lg> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:og> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:og> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:rg> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:rg> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:ug> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:ug> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:xg> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:xg> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:ah> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:ah> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:dh> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:dh> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:gh> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:gh> only has the following types <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:jh> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "<http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#colorCount> has a rdfs:domain of <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#RasterImage>. <_:jh> only has the following types <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#FileDataObject>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#Image>, <http://www.semanticdesktop.org/ontologies/2007/03/22/nfo#TextDocument>, <http://www.semanticdesktop.org/ontologies/2007/01/19/nie#InformationElement>, <http://www.w3.org/2000/01/rdf-schema#Resource>"
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
plasma-desktop(2182)/plasma StatusNotifierItemSource::refreshCallback: DBusMenu disabled for this application 
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
[/usr/bin/nepomukservicestub] "/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
"/usr/bin/nepomukservicestub(2224)" Soprano: "Invalid argument (1)": "Cannot set values for abstract property 'font.slant'."
```

---

### Post by bapoumba on 2014-03-10
Just to make sure, it is .ICEauthoriy, with a dot (it is an hidden file). It should be recreated once you log in.

Cross checking your errors.

Here is one where virtualbox caused a change in the colormap setup : [http://forum.kde.org/viewtopic.php?f=63&t=108770](http://forum.kde.org/viewtopic.php?f=63&t=108770)

Are you using a default theme and font for your user or some custom one (the new user you created should be using the default ones) ?

Are you using proprietary video drivers ?

Some are old bugs, please make sure your system is up to date (**sudo apt-get update** and **sudo apt-get upgrade**).

Sorry, I am not an expert when it comes to video stuff :(
And no worries, I'm not a native English speaker either!

---

### Post by fairy._.queen on 2014-03-10
I confirm that .ICEauthority (or .I* for what matters) doesn't exist. There is another interesting fact: before this upgrade, as per my settings during Kubuntu installation, I was never prompted for login - it was automatic. Only after this upgrade did the login window come at all.
Other useful note: the last working upgrade wasn't made ages ago, not more than one month ago, I think.

I can't even find the exact place in the settings where ages ago I changed this (since it never worked, I never cared), but in some standard place in the settings/system preferences (I don't know what that window is called in English) I simply downloaded this theme to change the initial screen. It never worked, probably because it was a login screen, and not a "welcome screen" and I had explicitly set Linux not to ask for my password. I have the impression that something like this might be happening (forgive me if it's nonsense): during installation I set the user and the sudo password and said I wanted automatic login. It always did, now somehow it wants my password but only the sudo one was set at the time, so whatever I put can't be right. This explanation can't be completely correct, though, because I tried to modify the user password and it didn't work.

To summarise: I did nothing as complicated as what seems to be in your link - nothing involving anything else than some "install theme" button.

---

### Post by bapoumba on 2014-03-10
OK, so I'm looking for the files to modify via the terminal to have you go back to regular desktop and login window themes. I'm not that familiar with KDE. I think it could work :)
Any KDE expert around ?
Will prefix your thread accordingly.

---

### Post by fairy._.queen on 2014-03-10
It's not best practice, but I was wondering what would happen if I just copied everything I have in my home directory into the new user's and then deleted the old one. I don't think I ever installed anything locally: would I lose much?
I know it's not on the "How to make things neatly" handbook, but is there any serious drawback?

---

### Post by bapoumba on 2014-03-11
> **fairy._.queen said:**
> It's not best practice, but I was wondering what would happen if I just copied everything I have in my home directory into the new user's and then deleted the old one. I don't think I ever installed anything locally: would I lose much?
I know it's not on the "How to make things neatly" handbook, but is there any serious drawback?

Well, if no one chimes in to suggest how to repair your regular user, that could be an option. It is always good to keep backups anyway. I would save my files to an external device (usb drive, CD, cloud storage ..) and move it back to the other working user. You may lose some apps configurations, but you can either tweak them back to your needs or go see on the borked user what the config files look like. I would not move any config file by itself as I suspect some of them are messing login or display up. 

I'm sorry I cannot help you further ..

Edit : I would not delete your previous user. You never know.
And make sure your new user belong to these groups (replace my login with yours) :
```
bapoumba_lxde@SonyBlue:~$ groups
bapoumba_lxde adm sudo lpadmin sambashare

```

---

### Post by SeijiSensei on 2014-03-11
Try renaming /home/username/.kde to .kde.old, then logout and log back in.  KDE will create an entirely new profile in your home directory, which should make your account equivalent to the new user you created.  Any better?

---

### Post by fairy._.queen on 2014-03-11
Thanks for replying!

Nope, unfortunately nothing changes, I can't login :-(

---

### Post by fairy._.queen on 2014-03-13
I was able to reinstall a few things locally, so I think now almost everything important is in its place. I'm going to mark the thread as solved (if you don't think it's solved enough, you should be able to unmark it, right?).

Thank you all so much for all your help (especially bapoumba, who, incidentally, has a great user name :D), now I can finally work!

---

### Post by bapoumba on 2014-03-13
> **fairy._.queen said:**
> I was able to reinstall a few things locally, so I think now almost everything important is in its place. I'm going to mark the thread as solved (if you don't think it's solved enough, you should be able to unmark it, right?).

Thank you all so much for all your help (especially bapoumba, who, incidentally, has a great user name :D), now I can finally work!

Yes, I think you can unmark the thread (same menu). If not, please report it and someone on Staff will do it.
And you are most welcome :)
Re: username : [http://ubuntuforums.org/showthread.php?t=2159663&p=12743473#post12743473](http://ubuntuforums.org/showthread.php?t=2159663&p=12743473#post12743473) ^^

---

### Post by JKyleOKC on 2014-03-13
It's been many years since I used KDE, and I didn't mess with its configurations when I did, but in Gnome and XFCE there are "session" files and the login screens can allow you to choose a session to which to return. If such session files exist in your home directory and in that of the new user, you might rename the one in the old home directory (to keep it in case it's needed) and then copy the one from the new user over to replace it. That **might** solve the problem.

I had a similar situation happen last year, when suddenly my normal user wouldn't let me do much. I did the new user thing to test, and then when it worked, copied all its hidden files over to my normal user. That made everything work right again. I've left that added user on the system in case of any future problem but haven't needed it since...

---

