---
title: "Recovery Mode Root Shell Messing Up Text Entry"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by fordman1090 on 2011-12-15
Howdy,

This is my first time to post on this site so please forgive me for any ignorance. I have some experience in ubuntu as well as mac osx, terminal, various programing languages and computers in general. I usually am able to solve most problems myself with the aid of google but this most recent one has left me a little stumped. 

I am running Ubuntu 11.10 with the 3.0.0-14-generic kernel. When I boot to recovery mode and select to drop to root I get 
*root@"desktop":~$* and read-only files like expected. I change to telinit 3 to gain file access and it returns 

[I]Ubuntu 11.10 "desktop" tty1

"desktop" login: [/I] I type "username" and press enter and it returns

[I]No command 'uenm' found, did you mean: 
uenm: not found
root@desktop:/home#[/I]  I can enter anything here and it returns
*Password:*                  I enter my password and it returns the first letter
[I]P
Login incorrect
desktop login:[/I] I enter my username and it returns
*uPassword:*   I ender my password and get
[I]P
login incorrect[/I]

I found that if i enter the first letter of both my username and password twice it will login saying 
[I]Failed to add entry for user
-Bash: no job control in this shell
username@desktop:~$[/I]

at this point, every return alternates between 
*root@desktop:/home#* which only reads every other character
and
*username@desktop:~$* which carries over the dropped characters from root. 
so you get
[I]root@desktop:home/#ping xxx.xxx.xxx.x
pn: command not found
username@desktop:$[/I] empty return
*igxxxxxxx: command not found*

I also found that as i scroll though bash history with the up arrow key, that it starts to delete by bash. So i start with 
*root@desktop:/home/user/documents#*
and after a few taps ill have
*root@desktop:/home/"some command from history"*

Im really not sure whats going on here and why its acting a so strange. I have done some searching and most things i find do give much detail because most people dont have problems logging in. Which leads me to believe i may be an idiot and doing something wrong hah. Please dont be afraid to tell me if im an idiot and im doing something stupid or not doing something simple. 

I really am interested in learning how to use this, so if yall know of any good websites that have information on this, please let me know. 

Thanks in advance for any help or insight.

---

### Post by JKyleOKC on 2011-12-15
> **fordman1090 said:**
> When I boot to recovery mode and select to drop to root I get *root@"desktop":~$* and read-only files like expected.I would not expect that prompt! The "drop to root" option logs you in as "root" so I would expect the final character of the prompt to be "#" rather than "$" -- this suggests a bit of a problem earlier in the boot sequence. Also, the files should NOT be read-only, since you should be the super user with r/w access to everything.

Incidentally, the runlevels in Ubuntu (and most if not all other distros based on Debian) are not at all like those for RedHat and its relatives. The default runlevel is 2 rather than 5, and 2 through 5 all do the exact same things. You can change things to make the system act like RedHat, but then it's no longer compatible with all future updates so that's not a good idea.

What happens if you select just a normal login, rather than using the "recovery mode" option (which simply starts at runlevel 1 when you select "drop to root")?

---

### Post by fordman1090 on 2011-12-15
Thanks for the reply,

If I select the *ubuntu with linux 3.0.0-14-generic* boot option in grub it boots normally. It seems to run fine, a little slow and laggy at times, but I think that may be a result of me multitasking cpu heavy applications.

If i select *ubuntu with linux 3.0.0-14-generic Recovery Mode* it loads *Recovery Menu (limited read-only menu)*. There I select *root*, 

However, this time it displays
*root@desktop:#* - I am 100% positive it showed *root@desktop:$* at last boot. I walked through as i was typing the post and copied it directly off the screen:confused:. Ill see if i can get it to do it again.

Anyways, they file system is still read-only. I cant change any existing files or add any new ones. Which I was taking to mean that I wasn't root and is why I was trying to login and change run levels in the first place.

Does run level 1 load basic hardware and networking utilities, so it acts as if you stop X server? Or is it minimal?

---

### Post by JKyleOKC on 2011-12-15
It's been a while since I used the recovery mode option, but I don't remember having any problem making changes to files with it. After all, its primary purpose is to recover from bad configurations, which absolutely requires the ability to edit or replace configuration files!

It's possible that something is going wrong in the boot sequence, resulting in the filesystem mounting in "ro" (read-only) mode. You might try issuing the command "mount -a" after logging into recovery mode and before making any runlevel change. This should force all filesystems to be re-mounted and at the very least should give some sort of error message if anything goes wrong. No reaction at all is the normal response; at that point you can try to create a test file to see whether r/w access came back.

The /var/log/syslog file might give you some clues, also. It contains excruciatingly fine detail about almost every action during the boot sequence; look for references to "/dev/sda" in particular.

It might also be some quirk in the version 3.0 kernel; I'm still using 2.6 and have no plan to move past that until the "minor version" number is no longer zero. I long ago learned to avoid "point zero" issues of everything and let other folk be the gamma testers...

To answer your question about runlevel 1, it forces single-user mode but otherwise loads all drivers. It's not like the "safe mode" of Windows that omits most driver packages; Linux single-user mode is intended for troubleshooting and critical system repair, so includes everything except for allowing other users to log in. It does NOT, however, automatically launch the X Windows system so supports only the command line interface by default.

---

