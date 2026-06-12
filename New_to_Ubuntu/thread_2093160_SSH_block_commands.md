---
title: "SSH block commands"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by bellygrevios on 2012-12-10
Hi everyone,
I just downloaded ubuntu server edition (LTS) yesterday as my first pure linux operating system and I'm having trouble with a blatant security problem in SSH. When I connect to the server from terminal on my mac everything works perfectly, only it's too perfect. My problem is with the fact that SSH allows me to switch to the root user on the server even though I blocked it in the SSHD_config file already. If anyone knows how to block the SU command or just stop SSH users from switching accounts that'd be great.

Thanks in advance

---

### Post by HermanAB on 2012-12-10
Hmm, maybe because it is the sshd_config file?  Case is important.

---

### Post by drmrgd on 2012-12-10
I might be wrong about this, but I think you can't do what you want with an SSH configuration.  I think the ssh config will just allow or disallow users from logging in.  Once they're logged in, you'll need to limit their activities just as you would on any Linux system (group permissions, sudoers, etc.).  You can disable root from logging in to your ssh server directly.  However, once an admin user is logged in, ssh can't stop that user from su.

---

### Post by matt_symes on 2012-12-10
Hi
 
Only allow users with limited power to login.
 
Look at the AllowUsers section in the ssh_config file.
 
Kind regards

---

### Post by bellygrevios on 2012-12-10
Hi everyone thanks for replying so quickly,
My allow users is already set to two specified users seperated by spaces and I have disabled root login already. If it can't be done from ssh config how would I block to the user from switching accounts? The sudo command was already disabled by default but that doesn't seem to be helping anything
Thanks

---

### Post by sandyd on 2012-12-10
> **bellygrevios said:**
> Hi everyone thanks for replying so quickly,
My allow users is already set to two specified users seperated by spaces and I have disabled root login already. If it can't be done from ssh config how would I block to the user from switching accounts? The sudo command was already disabled by default but that doesn't seem to be helping anything
Thanks

so, if you type
```

su

```, it lets you in without a password?

If that is the case, you have a bigger issue than blocking users from switching accounts.

If it allows you to type a password,
try
```

sudo passwd -dl root
```, logout
and then, try su again

---

### Post by dannyboy79 on 2012-12-10
it appears as though you're saying these users who are allowed to log in via ssh are in the sudoers file. if you don't want users to be able to use sudo, you need to remove them from the sudoers file. give them limited capabilties

---

### Post by bellygrevios on 2012-12-10
> **sandyd said:**
> so, if you type
```

su

```, it lets you in without a password?

If that is the case, you have a bigger issue than blocking users from switching accounts.

If it allows you to type a password,
try
```

sudo passwd -dl root
```, logout
and then, try su again

No, if you type in su it still prompts me for the root password or whatever user I enter, but I don't want to give them the option of switching accounts.

---

### Post by bellygrevios on 2012-12-10
> **dannyboy79 said:**
> it appears as though you're saying these users who are allowed to log in via ssh are in the sudoers file. if you don't want users to be able to use sudo, you need to remove them from the sudoers file. give them limited capabilties

The account is not in the sudoers folder, it currently cannot use sudo but it still has the otion to switch users to an account that is in the sudoers folder such as root or my personal account on the computer

---

### Post by dannyboy79 on 2012-12-10
> **bellygrevios said:**
> The account is not in the sudoers folder, it currently cannot use sudo but it still has the otion to switch users to an account that is in the sudoers folder such as root or my personal account on the computer
sure they can try to switch accounts but if they dont know the password then it would fail right?

OR maybe look into pam_wheel

or does this help? [http://www.cyberciti.biz/tips/linux-prevent-normal-users-from-logging-into-system.html](http://www.cyberciti.biz/tips/linux-prevent-normal-users-from-logging-into-system.html)

---

### Post by bellygrevios on 2012-12-10
> **dannyboy79 said:**
> sure they can try to switch accounts but if they dont know the password then it would fail right?

OR maybe look into pam_wheel

or does this help? [http://www.cyberciti.biz/tips/linux-prevent-normal-users-from-logging-into-system.html](http://www.cyberciti.biz/tips/linux-prevent-normal-users-from-logging-into-system.html)

True... I guess the question is more to satisfy my paranoia...

---

### Post by bellygrevios on 2012-12-10
> **dannyboy79 said:**
> sure they can try to switch accounts but if they dont know the password then it would fail right?

OR maybe look into pam_wheel

or does this help? [http://www.cyberciti.biz/tips/linux-prevent-normal-users-from-logging-into-system.html](http://www.cyberciti.biz/tips/linux-prevent-normal-users-from-logging-into-system.html)

I just checked the link and it said ssh was a non effected program

---

### Post by dannyboy79 on 2012-12-10
> **bellygrevios said:**
> I just checked the link and it said ssh was a non effected program
you misread it or maybe I am not understanding what you want to do. if you change it so the user has /bin/false, then they won't be able to use su but they also won't be able to ssh or login into the system at all. LOL so never mind

---

### Post by bellygrevios on 2012-12-10
> **dannyboy79 said:**
> you misread it or maybe I am not understanding what you want to do. if you change it so the user has /bin/false, then they won't be able to use su but they also won't be able to ssh or login into the system at all. LOL so never mind

I can pretty safely say that ruins the purpose of having a user... Well it may be useful some other time but for now I need to use ssh but block su

---

### Post by drmrgd on 2012-12-10
I don't think you have it quite right.  ssh is just the connection to the server.  You can limit who logs on with ssh (disable root user or only allow specific users to log on for example).  However, once the user logs on, if you want to limit what the user does, you'll have to do that on the server side by limiting accounts.  I've seen things like the wheel account (posted above), and even such things as to chmod the 'su' command so that only root has rights to run it.  Nevertheless, you can't change command permissions with an ssh config.  You can only change who gets on.

---

### Post by bellygrevios on 2012-12-10
> **drmrgd said:**
> I don't think you have it quite right.  ssh is just the connection to the server.  You can limit who logs on with ssh (disable root user or only allow specific users to log on for example).  However, once the user logs on, if you want to limit what the user does, you'll have to do that on the server side by limiting accounts.  I've seen things like the wheel account (posted above), and even such things as to chmod the 'su' command so that only root has rights to run it.  Nevertheless, you can't change command permissions with an ssh config.  You can only change who gets on.

Would there be any way to parse the text entered from the user (check if the first 3 letters of the user input match "su ")?

---

### Post by drmrgd on 2012-12-10
Well, that would (I believe) in the end require building a unique shell for the user to log into.  Perhaps easier is to have a look at PAM and how to configure.  There's a way to disable 'su' in the /etc/pam.d/su file I believe.  I never messed with it myself, but it could be a start.  Here's something I found that might be helpful:

[http://www.tuxradar.com/content/how-pam-works](http://www.tuxradar.com/content/how-pam-works)

---

### Post by bellygrevios on 2012-12-10
> **drmrgd said:**
> Well, that would (I believe) in the end require building a unique shell for the user to log into.  Perhaps easier is to have a look at PAM and how to configure.  There's a way to disable 'su' in the /etc/pam.d/su file I believe.  I never messed with it myself, but it could be a start.  Here's something I found that might be helpful:

[http://www.tuxradar.com/content/how-pam-works](http://www.tuxradar.com/content/how-pam-works)

This looks great... but um..... I have no clue how to install applications on ubuntu...
if you could walk me through installation that'd be great

---

### Post by kevdog on 2012-12-10
Are you looking possibly to set up a Linux type jail where certainusers are logged into a jailed ddirectory tree and can only perform a limited set of commands?

---

### Post by sandyd on 2012-12-10
I think this should work


```

sudo groupadd nosu
sudo nano /etc/pam.d/su

```

You see where it says 
```

#auth required pam_wheel.so deny group=nosu
```

remove the '#' so that it looks like
```

auth required pam_wheel.so deny group=nosu
```

Save the file by pressing Control+X

now for any user you don't want to allow to su...
```

sudo usermod -a -G nosu *username*
```

Never tried it, but you can chroot using a livecd if it screws up

---

### Post by bellygrevios on 2012-12-11
> **sandyd said:**
> I think this should work


```

sudo groupadd nosu
sudo nano /etc/pam.d/su

```

You see where it says 
```

#auth required pam_wheel.so deny group=nosu
```

remove the '#' so that it looks like
```

auth required pam_wheel.so deny group=nosu
```

now for any user you don't want to allow to su...
```

sudo groupadd -a -G nosu *username*
```

Never tried it, but you can chroot using a livecd if it screws up

Sounds good I guess... How do I install pam_wheel?
Sorry, I'm still extremely new to linux

---

### Post by drmrgd on 2012-12-11
There's nothing that you need to install.  PAM is integrated into your system and already has several roles in the way it works with administering the system.  All you need to do is to modify the file '/etc/pam.d/su' to make the changes that Sandy posted above.

---

### Post by bellygrevios on 2012-12-11
> **drmrgd said:**
> There's nothing that you need to install.  PAM is integrated into your system and already has several roles in the way it works with administering the system.  All you need to do is to modify the file '/etc/pam.d/su' to make the changes that Sandy posted above.

Alright thanks, I'll try this once I get home and keep you all posted.

---

### Post by drmrgd on 2012-12-11
Hope it works the way you want it to.  Do be careful, though, and make sure that you're doing it correctly.  Messing these kinds of things up could potentially lock your from your system, and you'll have a bit of work to clean it up after.  You might read up on chrooting (something I know little about unfortunately) and doing what Sandy suggested as a trial before you commit.

---

### Post by bellygrevios on 2012-12-11
Alright so I copied and pasted Sandy's above commands, replacing username with the user that I wanted to block and got -a option not recognized.

groupadd: invalid option -- 'a'
Usage: groupadd [options] GROUP

Options:
  -f, --force                   exit successfully if the group already exists,
                                and cancel -g if the GID is already used
  -g, --gid GID                 use GID for the new group
  -h, --help                    display this help message and exit
  -K, --key KEY=VALUE           override /etc/login.defs defaults
  -o, --non-unique              allow to create groups with duplicate
                                (non-unique) GID
  -p, --password PASSWORD       use this encrypted password for the new group
  -r, --system                  create a system account

---

### Post by bellygrevios on 2012-12-11
Never mind I used:
```
sudo adduser username nosu

```
and it worked. So it worked more perfectly then I imagined. If I use su it looks normal, still prompts for user password then sends permission denied even for the right password. If I logged into the user on the computer itself I can use the exit command to switch back to the previous user however, on ssh this closes the connection instead:D:D:D:D:D


THANK YOU EVERYBODY THAT HELPED ME SO QUICKLY

---

### Post by drmrgd on 2012-12-12
> **bellygrevios said:**
> Never mind I used:
```
sudo adduser username nosu

```
and it worked. So it worked more perfectly then I imagined. If I use su it looks normal, still prompts for user password then sends permission denied even for the right password. If I logged into the user on the computer itself I can use the exit command to switch back to the previous user however, on ssh this closes the connection instead:D:D:D:D:D


THANK YOU EVERYBODY THAT HELPED ME SO QUICKLY

Excellent!  Very happy to hear this worked well for you!

---

### Post by sandyd on 2012-12-12
> **bellygrevios said:**
> Never mind I used:
```
sudo adduser username nosu

```
and it worked. So it worked more perfectly then I imagined. If I use su it looks normal, still prompts for user password then sends permission denied even for the right password. If I logged into the user on the computer itself I can use the exit command to switch back to the previous user however, on ssh this closes the connection instead:D:D:D:D:D


THANK YOU EVERYBODY THAT HELPED ME SO QUICKLY

fixed
typo on my part

---

### Post by bellygrevios on 2012-12-12
Once again, another thanks to everyone that helped me so quickly. This forum has by far the best support that I have ever seen and as I gain more experience I plan on contributing a bit more. But for now if anyone could suggest a good DLNA server that'd be great.

---

