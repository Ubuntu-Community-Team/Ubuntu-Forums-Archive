---
title: "Cannot change Lubuntu user name using Terminal commands"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-04-17
I am trying to change my Lubuntu username from simply "name" to "RMcGinnis" but so far I have not been successful using Terminal commands. This link ( [http://www.cyberciti.biz/faq/ubuntu-linux-howto-rename-user-account/](http://www.cyberciti.biz/faq/ubuntu-linux-howto-rename-user-account/) ) tells me I can use the terminal command:
usermod -l {[COLOR=#993399]new-login-name[/COLOR]} {[COLOR=#996633]current-old-login-name[/COLOR]}

But when I use that command I get back "usermod: user name is currently used by process 1068" as below:

name@computer:~$ usermod -l RMcGinnis name
usermod: user name is currently used by process 1068

And if I put in the command "id RMcGinnis" I get "no such user" as below:

name@computer:~$ id RMcGinnis
id: RMcGinnis: no such user

QUESTION: What am I doing wrong?

Thanks,

R.

---

### Post by 23dornot23d on 2014-04-17
[h=2]CAVEATS[/h]  **usermod** will not allow you to change the name of a user who is logged in. You must make certain that the named user is not executing any processes when this command is being executed if the user's numerical user ID is being changed. You must change the owner of any crontab files manually. You must change the owner of any at jobs manually. You must make any changes involving NIS on the NIS server.

[http://www.linuxmanpages.com/man8/usermod.8.php](http://www.linuxmanpages.com/man8/usermod.8.php)

---

### Post by slickymaster on 2014-04-17
[How do I change my username]("http://askubuntu.com/questions/34074/how-do-i-change-my-username")

---

### Post by AbleTassie on 2014-04-17
> **slickymaster said:**
> [How do I change my username]("http://askubuntu.com/questions/34074/how-do-i-change-my-username")

I tried 3 of the methods at the link above ([http://askubuntu.com/questions/34074/how-do-i-change-my-username](http://askubuntu.com/questions/34074/how-do-i-change-my-username)), none of them worked. 

1) I tried creating a temporary user (Add a new user, e.g. "temporary". If you are still in TTY1:sudo adduser temporary, etc.). When I did this and entered usermod -l *new username* *old username* in the terminal I get back: user mod: Permission denied
user mod: cannot lock /etc/passwd; try again later

2) I tried making a root password (3. Set a password for the "root" account.
sudo passwd root, etc.). When I enter usermod -l <newname> -d /home/<newname> -m <oldname> I get back: user name is currently being used by process 1688 (my current username is "name")

3) I tried Restart in recovery mode and go to the root prompt shell ("Drop to root shell prompt"), etc.

When I enter mount -o remount,rw / 

I get back: mount: can't find rw/ in /etc/fstab or /etc/mtab

When I enter 
usermod -l <newname> -d /home/<newname> -m <oldname>

I get back: usermod: cannot lock etc/passwd; try again later

Not sure what to do.

QUESTION: Any ideas what I can do? I thought it would be a lot easier than this to change a username.

Thanks,

R.

[TABLE]
[TR]
[/TR]
[TR]
[TD="class: answercell"][/TD]
[/TR]
[/TABLE]

---

### Post by 23dornot23d on 2014-04-18
**sudo adduser RMcGinnis**

---

### Post by AbleTassie on 2014-04-18
> **23dornot23d said:**
> **sudo adduser RMcGinnis**

23, 

Thanks, but I already used "sudo adduser" when I made the temporary user ("sudo adduser temporary") and the command worked. I then made temporary the Administrator, etc. as described above in one of the methods. But the method did not work.

The command "sudo adduser RMcGinnis" will no doubt work, but it will simply add a new user named RMcGinnis. It would not change my current user name. That would require me to download & install all the programs and files under the old user name into the new RMcGinnis user account.

So unless I am missing something I don't think what you are suggesting will work for me.

Thanks,

R.

---

### Post by AbleTassie on 2014-04-18
> **RMcGinnis said:**
> I tried 3 of the methods at the link above ([http://askubuntu.com/questions/34074/how-do-i-change-my-username](http://askubuntu.com/questions/34074/how-do-i-change-my-username)), none of them worked. 

2) I tried making a root password (3. Set a password for the "root" account.
sudo passwd root, etc.). When I enter usermod -l <newname> -d /home/<newname> -m <oldname> I get back: user **name is currently being used by process 1688 (my current username is "name")**[TABLE]
[TR]
[/TR]
[TR]
[TD="class: answercell"][/TD]
[/TR]
[/TABLE]


I tried method 2 above several times and I get back: "name is currently being used by [a] process", e.g., 1688, 1723, I think another one was 3508. If I enter the command "kill 1688" or "kill 1723", etc., it just logs me out of the ctrl+alt+F1 screen to a GUI log in screen. Then I have to log back in through the GUI screen.

I wonder if there is some way to change the username using a Live CD or something. It just seems to me it should not be this hard to change a username.

Thanks,

R.

---

### Post by Iowan on 2014-04-18
I've considered changing a user name before - it just seemed like less trouble to create a new user.

---

### Post by steeldriver on 2014-04-18
> **RMcGinnis said:**
> 
3) I tried Restart in recovery mode and go to the root prompt shell ("Drop to root shell prompt"), etc.

When I enter mount -o remount,rw / 

I get back: mount: can't find [COLOR=#ff0000]**rw/**[/COLOR] in /etc/fstab or /etc/mtab


It looks like you typed that a bit wrong - the punctuation matters, it needs to be exactly

```
mount -o remount,rw /
```
(remount-COMMA-rw-SPACE-slash) NOT for example
```
mount -o remount, rw/
```

---

### Post by AbleTassie on 2014-04-18
> **RMcGinnis said:**
> I tried 3 of the methods at the link above ([http://askubuntu.com/questions/34074/how-do-i-change-my-username](http://askubuntu.com/questions/34074/how-do-i-change-my-username)), none of them worked. 

1) I tried creating a temporary user (Add a new user, e.g. "temporary". If you are still in TTY1:sudo adduser temporary, etc.). When I did this and entered usermod -l *new username* *old username* in the terminal I get back: user mod: Permission denied
user mod: cannot lock /etc/passwd; try again later



I tried a variation of method 1 described above AND IT WORKED!!! 

I created a temporary user and made the temporary user the/an Administrator. Then I logged out of my old username account and logged into Temporary and I used the regular Lubuntu screen (i.e., GUI, graphical user interface) in Temporary and clicked on the Lubuntu logo in the lower left screen corner and went to System tools > Users and Groups>user settings and then just changed the User name to what I wanted. Then I logged out of Temporary and logged back in to the new user name account. And it worked. I just have to delete the temporary account now. I think that should be easy by making the new user name the/a Administrator while in Temporary. Then I can delete Temporary while logged into the new user name account. There is also another way to delete Temporary using Terminal type commands that is described at the link above. 

I did not change the name of the home folder, but I don't want to do that right now. When I am sure that this method works completely, I'll mark the thread as SOLVED.

Thanks,

R.

---

### Post by AbleTassie on 2014-04-18
> **steeldriver said:**
> It looks like you typed that a bit wrong - the punctuation matters, it needs to be exactly

```
mount -o remount,rw /
```
(remount-COMMA-rw-SPACE-slash) NOT for example
```
mount -o remount, rw/
```

Thanks SteelDriver, I will keep this in mind if I need this command in the future. R.:)

---

### Post by AbleTassie on 2014-04-18
> **RMcGinnis said:**
> I tried a variation of method 1 described above AND IT WORKED!!! R.

OK everybody, the method I described above using Temporary worked as far as changing the username. I was also able to delete Temporary aftr using the method by using the regular Lubuntu screen (GUI) as described above. I am not sure about changing the home folder name though. I have not pursued that right now. The punctuation change suggested by SteelDriver also worked. But I am not sure about the subsequent commands if they would work for me while logged in as "root" in Lubuntu Recovery mode.

I am going to now mark this thread as [SOLVED].:)

Thanks to everybody,
 
R.

---

### Post by AbleTassie on 2014-04-24
I just want to add that I had to use a Terminal Command to really delete the Temporary User. The regular screen (GUI) method did not really work, i.e., "Temporary" reappeared after deletion. The Terminal Command that really worked is at the link [http://askubuntu.com/questions/34074/how-do-i-change-my-username](http://askubuntu.com/questions/34074/how-do-i-change-my-username) . 

The Terminal Command is: sudo deluser temporary

There is a similar Terminal Command for deleteing Temporary's Home Folder: sudo rm -r /home/temporary

Thanks,

R.

---

