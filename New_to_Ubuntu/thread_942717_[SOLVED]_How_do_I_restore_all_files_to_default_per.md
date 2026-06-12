---
title: "[SOLVED] How do I restore all files to default permissions?"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by crjackson on 2008-10-09
I just did a clean install of Hardy 32. Everything has been fine until today when I installed k3b and tellico.  Neither would run.  I ran them in terminal and found permission problems with ICEAuthority and another file. I discovered the programs would run fine as root but not user. I changed permissions and the programs ran but with problems.

I removed / purged programs / cleaned cache / re-installed - Still had to change permissions again for a couple of files and programs are working fine as far as I can tell.

I changed permissions to my home folder and all it's contents to read/write access setting myself as owner / group.

What would cause this problem, and how do I restore everything to the proper / default permissions?

p.s. Forgot to mention, I had problems with mozilla-thunderbird a few days ago too.  It wouldn't let me empty the trash nor would it move any files to the trash folder. I fixed it. It turned out to be a permissions problem too.

Thanks

---

### Post by DGortze380 on 2008-10-09
> **crjackson said:**
> how do I restore everything to the proper / default permissions?

Thanks

Reinstall.

chown and chmod are powerful commands, and the OS keep no record of previous state. google around and try to find the defaults and chmod and chown they one by one, or reinstall.  Be very careful about using those commands in the future.

EDIT:

Side note. You really should install via synaptic or apt-get unless you're entirely sure of how to compile from source. Sounds to me like you installed from source without being root, hence all the initial permissions errors.

---

### Post by vanadium on 2008-10-09
If you only "havocced" your home directory, it is sufficient to recreate your account: no need for full reinstall.

* Create a new account with root permissions
* From the new account, delete your current account and delete your home directory (make sure your personal files are backed up first)
* Recreate the account for a fresh start

---

### Post by Rocket2DMn on 2008-10-09
Merged.  If you need to change a post, edit it, please don't start a new thread.  Thank you.

---

### Post by crjackson on 2008-10-09
> **DGortze380 said:**
> Reinstall.

chown and chmod are powerful commands, and the OS keep no record of previous state. google around and try to find the defaults and chmod and chown they one by one, or reinstall.  Be very careful about using those commands in the future.

EDIT:

Side note. You really should install via synaptic or apt-get unless you're entirely sure of how to compile from source. Sounds to me like you installed from source without being root, hence all the initial permissions errors.

I did install via synaptic / apt-get. I didn't use chnmod or chown on anything.

What happened was some applications that WERE installed through synaptic wouldn't work. I launched them through the termianl and it gave me permissions error.  Things were owned by root instead of my user name.

I sudo launched the non-working applications and they worked.  I then used sudo nautilus to change the permissions from root owner / group to my user name. Things worked then.

Then I decided perhaps I could just select everything in my user folder and show it owned with file read / write access for everything in the folder and sub-folders.

Everything seems to be working fine, I just thought there my be an easy way to reset everything in that folder to default settings.

I don't know how it got borked to start with. It's a fresh install and I have NEVER used any command to chown or chmod.

---

### Post by WWSmith36 on 2008-10-09
Something like this as default:

~ should be 750
~/Public should be 755
~/Private should be the encrypted folder (optional)

(all owed by `whoami`)

I wouldn't want to see any quirks instead of secure default permission on ~

Also if you your recursive option on your home folder, don´t forget to reset the $HOME/.dmrc permission, it must be 644.

---

### Post by crjackson on 2008-10-09
> **Rocket2DMn said:**
> Merged.  If you need to change a post, edit it, please don't start a new thread.  Thank you.

The first thread was about specific applications not working. I fixed those and marked as solved.

Later I found I had other permission issues and was searching for an answer on how to reset default permissions for the items in the home folder, not just 2 applications.  

I no longer needed information on how to fix those 2 specific programs. 

I realize that one was related to the other but I didn't understand that at the time, and the original is no longer descriptive of the overall question.

Can you tell me how to change the original title on a first post? I make a mistake I could re-title and edit the post.

Perhaps there is some way to actually delete a post or thread on my part, but I don't know how to do that either.  If you will tell me how to do that, it would be helpful too.

---

### Post by crjackson on 2008-10-09
> **WWSmith36 said:**
> Something like this as default:

~ should be 750
~/Public should be 755
~/Private should be the encrypted folder (optional)

(all owed by `whoami`)

I wouldn't want to see any quirks instead of secure default permission on ~

Also if you your recursive option on your home folder, don´t forget to reset the $HOME/.dmrc permission, it must be 644.

Great, that's what I was looking for. I already found out (because of a login error) about the $HOME/ .dmrc and fixed that. 

That particualr error is why I made THIS post. I was concerned that some other files may have been changed (that shouldn't have been) when I recursively changed the files (in my home/username folder to list me as the owner/group.

---

### Post by Rocket2DMn on 2008-10-09
> **crjackson said:**
> The first thread was about specific applications not working. I fixed those and marked as solved.

Later I found I had other permission issues and was searching for an answer on how to reset default permissions for the items in the home folder, not just 2 applications.  

I no longer needed information on how to fix those 2 specific programs. 

I realize that one was related to the other but I didn't understand that at the time, and the original is no longer descriptive of the overall question.

Can you tell me how to change the original title on a first post? I make a mistake I could re-title and edit the post.

Perhaps there is some way to actually delete a post or thread on my part, but I don't know how to do that either.  If you will tell me how to do that, it would be helpful too.

Look at posts 1 and 2 in this thread, you made both of those in separate threads.  I don't know these other threads of which you speak.  You cannot delete posts/threads or edit the title of threads once they have been submitted, but you can edit the content of your posts with the Edit button.  If something needs to be deleted or modified, you can use the Report button to alert a staff member.  Accidents happen, it's not a big deal.

---

### Post by crjackson on 2008-10-09
> **Rocket2DMn said:**
> Look at posts 1 and 2 in this thread, you made both of those in separate threads.  I don't know these other threads of which you speak.  You cannot delete posts/threads or edit the title of threads once they have been submitted, but you can edit the content of your posts with the Edit button.  If something needs to be deleted or modified, you can use the Report button to alert a staff member.  Accidents happen, it's not a big deal.

Yeah, I see what you mean. That was an accidental post. My browser hung and I hit the stop button. When I went back and tried it again I somehow managed to double post. I must have hit the back button or something. I have no idea how the same post wound up in separate threads. I assure you it was not an intentional act whereby I could have just edited the 1st post. I didn&#8217;t realized that it even happened that way.

edit: In fact I thought you were talking about a similar earlier thread until just now.  It WAS due to my browser hanging when I made the first post. I didn't realize it had succeeded in creating a new thread. So when I hit the stop button, and decided to add some more information and clicked saved it created a second thread. I truely was unaware of creating 2 threads for this subject. Blame it on Firefox for freezing on me.

The other thread was: [[SOLVED] Help with Tellico .DCOPserver - can't run application]("http://ubuntuforums.org/showthread.php?t=942631")

---

### Post by DGortze380 on 2008-10-09
> **crjackson said:**
>  I then used sudo nautilus to change the permissions 
[/QUTOE]

same thing as using a cli and typing chmod

[QUOTE=crjackson;5936633]
I have NEVER used any command to chown or chmod..

---

### Post by crjackson on 2008-10-09
> **DGortze380 said:**
> [QUOTE=crjackson;5936633] I then used sudo nautilus to change the permissions 
[/QUTOE]

same thing as using a cli and typing chmod

.

I meant prior to having permission issues. I did not use chmod and then have issues. I had issues and then tried to correct them using the GUI to change them.

---

### Post by crjackson on 2008-10-09
> **DGortze380 said:**
> Reinstall.
EDIT:

Side note. You really should install via synaptic or apt-get unless you're entirely sure of how to compile from source. Sounds to me like you installed from source without being root, hence all the initial permissions errors.

Incorrect - _I did not install anything from source._ This is a fresh install. I was just adding back applications (using Synaptic & apt-get) that I usually use when the problem cropped up.

---

### Post by crjackson on 2008-10-09
> **vanadium said:**
> If you only "havocced" your home directory, it is sufficient to recreate your account: no need for full reinstall.

* Create a new account with root permissions
* From the new account, delete your current account and delete your home directory (make sure your personal files are backed up first)
* Recreate the account for a fresh start

Sounds like the best way to fix this.  That's what I'll do then.

---

### Post by opscure on 2008-10-30
If you did a:
```
sudo chmod -R 777 /
```
and your system is not working right (ie no internet, no sudo, no su, etc), then you will want to do the following.

Reboot the computer into recovery mode (esc to grub and enter root prompt) and do a:
```
chmod 0440 /etc/sudoers
```
reboot back to desktop.

Then open a terminal and do a:
```
sudo dpkg-reconfigure -a
```

this will bring you through a series of menus to allow you to reconfigure all your packages and should fix any permissions issues.  Fast, easy, and the easiest way without a reinstall.

if you are having problems with mounting and unlocking some system tools then:
```
sudo gedit /etc/group
```
add your username after the line:
```
polkituser:x:122:
```

so it should look like:
```
polkituser:x:122:username
```

save and reboot.

Cheers.

---

### Post by suniyo on 2009-11-13
> **vanadium said:**
> If you only "havocced" your home directory, it is sufficient to recreate your account: no need for full reinstall.

* Create a new account with root permissions
* From the new account, delete your current account and delete your home directory (make sure your personal files are backed up first)
* Recreate the account for a fresh start


I am going through the same problem. I ran sudo chmod 777 -R * in wrong directory (to make it worse the directory was root /). So I was unable to even login to ubuntu. It threw me back to login screen even when I am logged in. It also gave me a graphical popup message saying: Install error: the config details for GNOME power manager has not been installed correctly. Contact your computer Administrator. 
Afte logging in (without letting me actually login) it gave me the error: there is problem with the configuration server. /usr/lib/libconfig2-4/gconf-sanity-check-2 exited with status 256
 
After a bit of research I did following:

in recovery mode root prompt I run following commands:
```
chmod 755 /etc/gconf/gconf.xml.system
chmod 777 /tmp
chmod 700 /home/my_user_id
chmod -R 700 /home/my_user_id
chmod 644 /home/my_user_id/.dmrc
```After that I was atleast able to login to Gnome session with root user.
Now I tried to check user/group permissions but it gave me the error: can not open unknown error occured. Wired Network devices can not load at the boot and are not editable anymore, so obviously I am not able to connect to the internet. So I am not able to do important administrative tasks and Audio is also missing. Things like System Testing is also not working. Most things that involves some kind of special privileges are not working. I need some help as there are lot many softwares (including servers/websites) installed and I don't want to reinstall ubuntu (after taking lot of backup). 

Even more research and through recovery mode root I changed /etc/sudoers permission to 0440 and was able to use sudo command in terminal but still administrative services are out of control.

I even tried to create new user but system denies to open services. So One thing I can do is to create new sudo su super user using terminal and can login with that user and change permissions in current user. Can someone tell me how to create new super user sudo user su using command line, terminal. **[COLOR=Red]OR[/COLOR]**

Can I restore my file permissions to default (0755/0644/0440 etc) by ubuntu.

Links to solution of the problem are okey...

---

