---
title: "man works only if I sudo, please help to fix this"
date: 2019-06-23
forum: New to Ubuntu
---

### Post by mas192 on 2019-06-23
Hi All,

I recently fixed a installation error, info on that is found here [https://ubuntuforums.org/showthread.php?t=2421326&page=2](https://ubuntuforums.org/showthread.php?t=2421326&page=2)

However I am faced with some interesting problem, man does not work anymore ```
(base) samjoshva@mirraclemsi:~$ man apt(base) samjoshva@mirraclemsi:~$ man ls
(base) samjoshva@mirraclemsi:~$ man cat
(base) samjoshva@mirraclemsi:~$ sudo man apt
[sudo] password for samjoshva: 
(base) samjoshva@mirraclemsi:~$ sudo man cat
(base) samjoshva@mirraclemsi:~$ 
```

but if i prefix sudo it works. Can someone help me resolve this please this please.

Thanks,
mas192

---

### Post by TheFu on 2019-06-23
Check file permissions. It is most likely that you used sudo incorrectly and messed up the permissions somewhere. Perhaps in /tmp/ or $HOME or /usr/share/man/

Don't use sudo when it isn't needed.

---

### Post by mas192 on 2019-06-23
Okay I'll check the folders and reset the permissions. It was not my intention :-(

---

### Post by mas192 on 2019-06-23
Hi TheFu 

this is the permission for my home
```
ls -altotal 16
drwxr-xr-x  4 root      root      4096 Jun 23 13:35 .
drwxr-xr-x 24 root      root      4096 Jun 23 08:55 ..
drwxr-xr-x  2 mirracle  mirracle  4096 Jun 23 13:35 mirracle
drwxr-xr-x 31 samjoshva samjoshva 4096 Jun 23 09:41 samjoshva



```

permission in /tmp
```
ls -altotal 3112
drwxrwxrwt 23 root      root         4096 Jun 23 19:39 .
drwxr-xr-x 24 root      root         4096 Jun 23 08:55 ..
drwxrw-rw-  2 samjoshva samjoshva    4096 Jun 23 08:58 .com.google.Chrome.lEPsaC
-rw-rw-rw-  1 samjoshva samjoshva       0 Jun 23 08:57 config-err-GdNj12
drwxrwxrwt  2 root      root         4096 Jun 23 08:57 .font-unix
drwxrwxrwx  2 samjoshva samjoshva    4096 Jun 23 09:04 hsperfdata_samjoshva
drwxrwxrwt  2 root      root         4096 Jun 23 08:57 .ICE-unix
drwxrwxrwx  5 samjoshva samjoshva    4096 Jun 23 16:48 Jetty_127_0_0_1_3333_webapp____4ulpc9
drwxrw-rw-  2 samjoshva samjoshva    4096 Jun 23 16:55 lu323249g15d3.tmp
drwxrw-rw-  2 samjoshva samjoshva    4096 Jun 23 09:47 mysql-workbench-14286
srwxrwxrwx  1 samjoshva samjoshva       0 Jun 23 14:07 OSL_PIPE_1000_SingleOfficeIPC_c4e7672ca95d3dbbf2c7a971cc8d414a
drwxrw-rw-  3 root      root         4096 Jun 23 08:57 snap.canonical-livepatch
drwxrw-rw-  2 samjoshva samjoshva    4096 Jun 23 08:57 ssh-EbvH0y8b5ft2
drwxrw-rw-  3 root      root         4096 Jun 23 08:57 systemd-private-d6f52dbda51c471c8e7ea825bc3cc2e6-apache2.service-Lq0kPP
drwxrw-rw-  3 root      root         4096 Jun 23 08:57 systemd-private-d6f52dbda51c471c8e7ea825bc3cc2e6-bolt.service-NSFeRv
drwxrw-rw-  3 root      root         4096 Jun 23 08:57 systemd-private-d6f52dbda51c471c8e7ea825bc3cc2e6-colord.service-vp9R7I
drwxrw-rw-  3 root      root         4096 Jun 23 08:58 systemd-private-d6f52dbda51c471c8e7ea825bc3cc2e6-fwupd.service-Zs2l80
drwxrw-rw-  3 root      root         4096 Jun 23 08:57 systemd-private-d6f52dbda51c471c8e7ea825bc3cc2e6-ModemManager.service-P1wUQw
drwxrw-rw-  3 root      root         4096 Jun 23 08:57 systemd-private-d6f52dbda51c471c8e7ea825bc3cc2e6-rtkit-daemon.service-JOk7SZ
drwxrw-rw-  3 root      root         4096 Jun 23 08:57 systemd-private-d6f52dbda51c471c8e7ea825bc3cc2e6-systemd-resolved.service-FD4Hhp
drwxrw-rw-  3 root      root         4096 Jun 23 08:57 systemd-private-d6f52dbda51c471c8e7ea825bc3cc2e6-systemd-timesyncd.service-1AUKls
drwxrwxrwt  2 root      root         4096 Jun 23 08:57 .Test-unix
-rw-rw-rw-  1 samjoshva samjoshva 3086102 Jun 23 11:35 tmpaddon
-rw-rw-rw-  1 gdm       gdm            11 Jun 23 08:57 .X1024-lock
drwxrwxrwt  2 root      root         4096 Jun 23 08:57 .X11-unix
drwxrwxrwt  2 root      root         4096 Jun 23 08:57 .XIM-unix
drwxrw-rw-  2 samjoshva samjoshva    4096 Jun 23 14:23 zotero_samjoshva
```

and permission in /usr/share/man

```
ls -altotal 612
drwxrwxrwx  34 root root   4096 Feb  9 16:15 [COLOR=#3465A4].[/COLOR]
drwxr-xr-x 274 root root  12288 Jun 23 09:44 [COLOR=#729FCF]**..**[/COLOR]
drwxrwxrwx   6 root root   4096 Feb  9 16:15 [COLOR=#3465A4]cs[/COLOR]
drwxrwxrwx   5 root root   4096 Jan 25  2018 [COLOR=#3465A4]da[/COLOR]
drwxrwxrwx   7 root root   4096 Feb  9 16:14 [COLOR=#3465A4]de[/COLOR]
drwxrwxrwx   5 root root   4096 Feb  9 16:12 [COLOR=#3465A4]es[/COLOR]
drwxrwxrwx   3 root root   4096 Jan 25  2018 [COLOR=#3465A4]fi[/COLOR]
drwxrwxrwx   6 root root   4096 Feb  9 16:13 [COLOR=#3465A4]fr[/COLOR]
drwxrwxrwx   4 root root   4096 Feb  9 16:15 [COLOR=#3465A4]fr.ISO8859-1[/COLOR]
drwxrwxrwx   4 root root   4096 Feb  9 16:15 [COLOR=#3465A4]fr.UTF-8[/COLOR]
drwxrwxrwx   5 root root   4096 Jan 25  2018 [COLOR=#3465A4]hu[/COLOR]
drwxrwxrwx   5 root root   4096 Feb  9 16:13 [COLOR=#3465A4]id[/COLOR]
drwxrwxrwx   5 root root   4096 Mar 12  2018 [COLOR=#3465A4]it[/COLOR]
drwxrwxrwx   5 root root   4096 Mar 12  2018 [COLOR=#3465A4]ja[/COLOR]
drwxrwxrwx   5 root root   4096 Jan 25  2018 [COLOR=#3465A4]ko[/COLOR]
drwxrwxrwx   2 root root  81920 Jun 23 09:44 [COLOR=#3465A4]man1[/COLOR]
drwxrwxrwx   2 root root  28672 Jun  7 23:50 [COLOR=#3465A4]man2[/COLOR]
drwxrwxrwx   2 root root 307200 Jun 17 08:19 [COLOR=#3465A4]man3[/COLOR]
drwxrwxrwx   2 root root   4096 Jun  7 23:50 [COLOR=#3465A4]man4[/COLOR]
drwxrwxrwx   2 root root  20480 Jun 23 09:22 [COLOR=#3465A4]man5[/COLOR]
drwxrwxrwx   2 root root   4096 Feb  9 16:14 [COLOR=#3465A4]man6[/COLOR]
drwxrwxrwx   2 root root  12288 Jun 21 12:39 [COLOR=#3465A4]man7[/COLOR]
drwxrwxrwx   2 root root  45056 Jun 23 09:22 [COLOR=#3465A4]man8[/COLOR]
drwxrwxrwx   6 root root   4096 Jun  7 23:49 [COLOR=#3465A4]nl[/COLOR]
drwxrwxrwx   5 root root   4096 Mar 12  2018 [COLOR=#3465A4]pl[/COLOR]
drwxrwxrwx   5 root root   4096 Feb  9 16:12 [COLOR=#3465A4]pt[/COLOR]
drwxrwxrwx   5 root root   4096 Jan 25  2018 [COLOR=#3465A4]pt_BR[/COLOR]
drwxrwxrwx   5 root root   4096 Jan 25  2018 [COLOR=#3465A4]ru[/COLOR]
drwxrwxrwx   4 root root   4096 Dec 30  2017 [COLOR=#3465A4]sl[/COLOR]
drwxrwxrwx   5 root root   4096 Feb  9 16:13 [COLOR=#3465A4]sr[/COLOR]
drwxrwxrwx   5 root root   4096 Jan 25  2018 [COLOR=#3465A4]sv[/COLOR]
drwxrwxrwx   5 root root   4096 Jan 25  2018 [COLOR=#3465A4]tr[/COLOR]
drwxrwxrwx   5 root root   4096 Jan 25  2018 [COLOR=#3465A4]zh_CN[/COLOR] drwxrwxrwx   5 root root   4096 Jan 25  2018 [COLOR=#3465A4]zh_TW[/COLOR]
```

Do you think something is a miss in these permission please let me know. thanks

---

### Post by again? on 2019-06-24
Show the command prompt.
eg
```
[COLOR="#006400"]glen@Bionic:~$[/COLOR] ls -al
```

You appear to be showing permissions for /home

Not your home directory which would be /home/mirracle or /home/samjoshva

---

### Post by mas192 on 2019-06-24
Hi guber2, thanks so much for the reply, I am sorry that posting was while I was in middle of fixing thing, I created another user, copied all my data , deleted and recreated the samjoshva account.

Everything look okay now, please let me know if there is any oddity
this for /home/samjoshva and for /home/mirracle below that.

```
ls -altotal 144
drwxr-xr-x 26 samjoshva samjoshva 4096 Jun 24 08:00 .
drwxr-xr-x  4 root      root      4096 Jun 23 20:09 ..
drwxr-xr-x 26 samjoshva samjoshva 4096 Jun 23 20:27 anaconda3
-rw-------  1 samjoshva samjoshva  766 Jun 24 01:37 .bash_history
-rw-r--r--  1 samjoshva samjoshva  220 Jun 23 20:09 .bash_logout
-rw-r--r--  1 samjoshva samjoshva 4262 Jun 23 20:28 .bashrc
drwx------ 19 samjoshva samjoshva 4096 Jun 24 01:19 .cache
drwx------ 21 samjoshva samjoshva 4096 Jun 24 00:33 .config
drwxr-xr-x  2 samjoshva samjoshva 4096 Jun 23 20:09 Desktop
drwxr-xr-x  9 samjoshva samjoshva 4096 Jun 23 20:15 Documents
drwxr-xr-x  3 samjoshva samjoshva 4096 Jun 24 07:46 Downloads
-rw-r--r--  1 samjoshva samjoshva 8980 Jun 23 20:09 examples.desktop
drwx------  3 samjoshva samjoshva 4096 Jun 23 20:17 .gnome
drwx------  3 samjoshva samjoshva 4096 Jun 23 20:10 .gnupg
-rw-------  1 samjoshva samjoshva 1018 Jun 24 07:45 .ICEauthority
drwxr-xr-x  5 samjoshva samjoshva 4096 Jun 24 00:17 .ipython
drwxr-xr-x  2 samjoshva samjoshva 4096 Jun 24 08:00 .jupyter
drwx------  3 samjoshva samjoshva 4096 Jun 23 20:09 .local
drwx------  5 samjoshva samjoshva 4096 Jun 23 20:11 .mozilla
drwxr-xr-x  2 samjoshva samjoshva 4096 Jun 23 20:09 Music
drwx------  3 samjoshva samjoshva 4096 Jun 23 20:10 .mysql
drwx------  3 samjoshva samjoshva 4096 Jun 23 20:10 .nv
drwxr-xr-x  2 samjoshva samjoshva 4096 Jun 24 01:17 Pictures
drwx------  3 samjoshva samjoshva 4096 Jun 23 20:16 .pki
-rw-r--r--  1 samjoshva samjoshva  807 Jun 23 20:09 .profile
drwxr-xr-x  2 samjoshva samjoshva 4096 Jun 23 20:09 Public
drwxr-xr-x  5 samjoshva samjoshva 4096 Jun 23 22:58 snap
drwx------  2 samjoshva samjoshva 4096 Jun 23 20:27 .ssh
-rw-r--r--  1 samjoshva samjoshva    0 Jun 23 20:10 .sudo_as_admin_successful
drwxr-xr-x  2 samjoshva samjoshva 4096 Jun 23 20:09 Templates
drwxr-xr-x  2 samjoshva samjoshva 4096 Jun 23 20:09 Videos
-rw-------  1 samjoshva samjoshva 1769 Jun 23 23:43 .viminfo
drwxr-xr-x  7 samjoshva samjoshva 4096 Jun 24 01:35 Zotero
drwx------  3 samjoshva samjoshva 4096 Jun 23 20:11 .zotero



```

and for /home/mirracle

```
 ls -altotal 104
drwxr-xr-x 18 mirracle mirracle 4096 Jun 23 19:58 .
drwxr-xr-x  4 root     root     4096 Jun 23 20:09 ..
-rw-------  1 mirracle mirracle    8 Jun 23 19:58 .bash_history
-rw-r--r--  1 mirracle mirracle  220 Jun 23 13:35 .bash_logout
-rw-r--r--  1 mirracle mirracle 3771 Jun 23 13:35 .bashrc
drwx------ 11 mirracle mirracle 4096 Jun 23 19:58 .cache
drwx------ 11 mirracle mirracle 4096 Jun 23 19:58 .config
drwxr-xr-x  2 mirracle mirracle 4096 Jun 23 19:57 Desktop
drwxr-xr-x  2 mirracle mirracle 4096 Jun 23 19:57 Documents
drwxr-xr-x  2 mirracle mirracle 4096 Jun 23 19:57 Downloads
-rw-r--r--  1 mirracle mirracle 8980 Jun 23 13:35 examples.desktop
drwx------  3 mirracle mirracle 4096 Jun 23 19:57 .gnupg
-rw-------  1 mirracle mirracle  342 Jun 23 19:57 .ICEauthority
drwx------  3 mirracle mirracle 4096 Jun 23 19:57 .local
drwxr-xr-x  2 mirracle mirracle 4096 Jun 23 19:57 Music
drwx------  3 mirracle mirracle 4096 Jun 23 19:57 .mysql
drwx------  3 mirracle mirracle 4096 Jun 23 19:57 .nv
drwxr-xr-x  2 mirracle mirracle 4096 Jun 23 19:57 Pictures
-rw-r--r--  1 mirracle mirracle  807 Jun 23 13:35 .profile
drwxr-xr-x  2 mirracle mirracle 4096 Jun 23 19:57 Public
drwxr-xr-x  3 mirracle mirracle 4096 Jun 23 19:58 snap
drwx------  2 mirracle mirracle 4096 Jun 23 19:57 .ssh
drwxr-xr-x  2 mirracle mirracle 4096 Jun 23 19:57 Templates
drwxr-xr-x  2 mirracle mirracle 4096 Jun 23 19:57 Videos

```

Thanks so much,
mas192

---

### Post by TheFu on 2019-06-24
Looks like you've been changing permissions all over the place.  Why?
Also, it appears you might have logged in using a root account.  DON'T DO THAT.

I'm unwilling to play wack-a-mole with permissions issues.  If it was me, I'd reinstall the OS and be more careful 
a) never login with root to any GUI session (i.e. the login screen)
b) don't use sudo with any GUI programs until you know what the ramifications will be and can correct them later.
c) don't blindly change permissions on entire directory structures until you know what the ramifications will be and can correct them later.
d) never, ever, ever, use chmod 777. That is for people who don't understand, nor care at all, anything about security.

BTW, everyone does these things when they are new.  I did too.  What I've learned over the decades is there is always a better solution for each of these temptations.

The only places most users should touch permissions are inside their HOME directory, nowhere else.  Every file in a HOME directory should be owned by the userid for that HOME almost always.

Especially don't change permissions in /usr, /etc, /bin, /tmp, /lib, /var, --- basically the places for the OS.  File and directory permissions are the first layer of security for all Unix systems. There are subtle considerations in the settings. Get them incorrect and remote users can hack into the system. Local users can get root authority and completely own the system.

I have no idea how you plan to put the permissions back. There isn't any script for Ubuntu that does that.  Permissions change slightly with every release for security reasons.

---

### Post by GhX6GZMB on 2019-06-24
@TheFu, your post is one of the best I've read. I'm going to print it and hang it on my wall.

As a newbie, I try to stay far away from root, unless it's absolutely necessary. (Which it was with the persistent "flip_done timed out" after Lubuntu 19.04 installation.)

---

### Post by mas192 on 2019-06-25
Hi the Fu,

I managed to solves my woes without a reinstall, I backed up my documents, created a new user, deleted the messed up account and moved my documents back in. Everything is back to normal. Thanks so much for your advice.
Cheers,
Mas192

---

### Post by mas192 on 2019-06-26
Sorry Guber2, just saw your comment, I fixed it thanks so much

---

### Post by mas192 on 2019-06-29
More info on my problem, I found the culprit that caused the problem, here is the details
[https://askubuntu.com/questions/1154889/ubuntu-18-04-lts-on-my-msi-laptop-man-command-does-not-work-anymore?noredirect=1#comment1921047_1154889](https://askubuntu.com/questions/1154889/ubuntu-18-04-lts-on-my-msi-laptop-man-command-does-not-work-anymore?noredirect=1#comment1921047_1154889)

---

