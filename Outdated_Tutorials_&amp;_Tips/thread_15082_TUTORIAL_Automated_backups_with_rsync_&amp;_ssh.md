---
title: "TUTORIAL: Automated backups with rsync &amp; ssh"
date: 2005-02-11
forum: Outdated Tutorials &amp; Tips
---

### Post by rosslaird on 2005-02-11
Several times I've had to configure automated backups for my machines, and each time I do, a long enough period has elapsed since the previous time that I forget all the important details. So this little tutorial is as much to help me remember (and to keep a record and to trace the steps) as for other users.

1.  What You Need

a) ssh (should be installed by default) and rsync ("sudo apt-get install rsync" if you don't already have it).

b) Users on both machines (the source machine and the destination machine), ideally with the same username (so: if user "ross" exists on source machine, user "ross" should also exist on destination machine).

c) ssh and rsync installed on both machines.


2. Testing ssh (also see step 4)

Start on the source machine. As user ("ross" in my case -- not root) try to login to the destination machine using ssh, specifying either an ip address or a hostname (if the hostname appears in /etc/hosts). You'll be asked for a password. This is the password for the user on the destination machine, not the local password (in my case, they're the same). For me, the destination machine is called "kids":

```
ross@ross:~$ssh kids
```

(I will show my full prompt several times in this tutorial, but obviously you just enter the last part. For above, it would be "ssh kids", or whatever your hostname/ip is.)

Type yes to the authentication message.
Enter the password. (If you are logging on as another user, you can type the username before the host, i.e.: ssh ross_other_user@kids).
All good so far. ssh works. If it doesn't use google to search for the error message.
Type "exit" to return to the source machine.

3. Setup public/private key pair

```
ross@ross:~$ ssh-keygen -t dsa
```

Follow the prompts, just hitting enter for the passphrase. This will yield the id_dsa.pub and id_dsa files (the public and private key pair):

```
...Generating public/private dsa key pair. [Enter]
...Enter file in which to save the key (/home/ross/.ssh/id_dsa): [Enter]
...Created directory '/home/ross/.ssh'. [Enter: you might not see this message]
...Enter passphrase (empty for no passphrase): [Enter]
...Enter same passphrase again: [Enter]
...Your identification has been saved in /home/ross/.ssh/id_dsa.
...Your public key has been saved in /home/rick/.ssh/id_dsa.pub.
```

4. Copy the public key to the destination machine:

```
ross@ross:~$ ssh-copy-id -i ~/.ssh/id_dsa.pub ross@kids [or enter ip address instead of hostname, e.g."kids"]
```

If you already tested ssh as in step 2 above, you'll simply be asked for the passphrase. If not, you'll get this:

```
The authenticity of host '...[host ip or name]...' can't be established.
RSA key fingerprint is ...
Are you sure you want to continue connecting (yes/no)? [type "yes"]
Warning: Permanently added '...' (RSA) to the list of known hosts.
ross@[kids]'s password: [Enter the password]
```

You should be logged in to the remote machine, and you should (might) see a test message about confirming the setup.

5. Logout of the destination machine and try getting back in without the password:

```
ssh kids
```

This (with your correct username and hostname/ip address) should get you in to the destination machine. If it works, it will work every time for all ssh connections for that user. No password required (this is actually a small security risk, but it has a big payoff  -- see next step.

6. Make a backup script (mine's in my home directory, but it could be anywhere):

```
nano backup.txt
```

Enter the rsync options and paths into the new file. The following line will login (with user "ross", for which we just setup password-less ssh logins) and rsync the home directory on my source machine with a backup directory on the destination machine ("kids"):

```
rsync -e ssh -varuzP /home/ross/ kids:/home/ross/backup/
```

The closing slashes matter. Don't leave them out. The varuzP options mean "verbose, archive, recursive, update, compress, partial". Check "rsync -h" from a command prompt to see what this all means. Basically, it will create directories if they don't exist, won't overwrite newer files on the destination, and won't delete any files on the destination that have been deleted from the source machine (for that, you use "--delete").

(If you did not setup password-less logins, the script would halt and ask for a password. And this would prevent the procedure from being automated.)

Save and close backup.txt
From the directory in which backup.txt was saved, type:

```
./backup.txt
```

If it balks (i.e. permissions), change the permissions. I would use "chmod 775 backup.txt", though this is a fairly lax permission scheme. (I have a personal network, which only I and my kids use, and I'm behind a hardware firewall. Your setup may have different requirements. At least make the script exectuable ("chmod +x backup.txt", I think, but permissions are not my specialty).

Run the backup and see how it goes. If it works and you like what it's doing, go to step 7. Otherwise, adjust it.

7. Automate the process.

make a new file called crons.cron (I think you can call it anything, but I'not sure):

```
nano crons.cron
```

Put some cron variables in there. Mine says this:

```
#Mins   Hours   Days    Months  Day of Week     Run program
   0        23        *          *            *                       /home/ross/backup.txt
```

The titles are just reminders for me. They are commented out, as you can see. This script runs my backup.txt script every day at 11pm.

Save and exit crons.cron
Add it to your crontab:

```
crontab crons.cron
```

List your crontab, to check that it's in there properly:

```
crontab -l
```

(that's an L, as in "list")

You should get a nice little message showing your cron settings.

Done.

A Final Word:

Don't just follow this tutorial willy-nilly. Your system may have a configuration that makes parts of what I'm outlining dangerous or foolish. Try to understand (at least minimally) what you are doing. This setup does one thing only: it syncronizes files from a directory on a local machine (the source) to a directory on a destination machine. It does not make multiple copies of anything (as a true backup scheme would) and it will overwrite matching files on the destination unless they are newer. Be cautious. Rsync is an amazingly powerful tool, but with great power...

___________

Other users will likely have better or more efficient ways of doing this. Please do post them so folks can see what options there are. And, of course, I may have made a host of mistakes that I don't see at the moment. Please help me correct them.

I hope this helps to keep someone's data safe.

---

### Post by burningbed on 2006-01-02
If the goal is to synchronize two computers (e.g. a laptop and a desktop), I can recommend Unison (works also great for backups):
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)
apt-get install unison unison-gtk

---

### Post by kc0dhb on 2006-01-06
Here's a quick little script I wrote for backing up a mac laptop to a linux system.  Then modified to back up an ubuntu system to another box.

basically the structure will look similar to this
(output of tree -L 3 with some cutting)
.
`-- backup
    |-- now
    |   |-- torrents
    |   `-- workspace
    `-- old
        |-- 2006-01-05-at-23.47.51
        |-- 2006-01-05-at-23.49.20
        |-- 2006-01-06-at-00.12.29
        |-- 2006-01-06-at-00.12.42
        |-- 2006-01-06-at-00.13.19
        |-- 2006-01-06-at-00.13.54
        `-- 2006-01-06-at-19.37.40

Where the stuff in old contains files/directories that were changed or deleted at that time.

Excludes may be useful if you have a large amount of data that you really could care less about if you lose it, say you akready have a backup, or the originals of the data.  

Uncomment and recomment the parts about $tobebackedup if you just want certain directories.

```

#!/usr/bin/perl
# Kyle Byerly
# 20.December.2005
# Backs up everything to another system...don't know (or care) if it backs up
# the resource fork since the system I'm backing up to is linux.
# Perhaps at some later date I will worry about this.
# Backup to a mac from a mac using rsyncX.
$user = kyle;
$base = "/home/$user";
#if no leading slash then starts in home directory of remote login user
#pay attention to what will happen with --backup-dir
$backupdir = "backup";
#@dirs = < Documents Library Pictures perl amesfug apocalyptica backups classes english software #starbuck wireless lastbackup>;
#foreach (@dirs) {
#    $tobebackedup = "$tobebackedup $base/$_";
#}
$tobebackedup = "$base/";
#path from backup directory if starting with /
#if it ends with a / it is a directory, else it is a file
#if no leading / then it will exclude if it finds the word anywhere
#be careful here
@excludes =< /DVD /Music/ /source/ /archive.org/ Cache/ /.gnome-system-monitor.kyle >;
foreach (@excludes) {
    $excluding = "$excluding --exclude=\"$_\"";
}

#the below two lines will make it so I know when the last (complete) backup was
#as lastbackup is the last dir
system "rm $base/lastbackup/*";
system "touch $base/lastbackup/\"`date +%Y-%m-%d-at-%H.%M.%S`\"";
#notice \@ to comment out the @
system "rsync -rltb -e \"ssh -p 24\" $excluding --delete --backup-dir=~/$backupdir/old/`date +%Y-%m-%d-at-%H.%M.%S`/ $tobebackedup kyle2800\@192.168.2.13:$backupdir/now";

```

you can "execute" the script with either 
```

perl nameofscript 

```
or
```

chmod +x nameofscript 
./nameofscript

```

have fun

---

### Post by dk01 on 2007-10-04
If you are running SSH on a port other than 22 (let's assume 4000 for this example).  You must alter the following steps:

Step 2 - When testing SSH:
```
ssh -p 4000 kids
```

Step 4 - When copying the key:
```
ssh-copy-id -i ~/.ssh/id_dsa.pub "-p 4000 ross@kids"
```

Step 5 - When testing SSH again:
```
ssh -p 4000 kids
```

Step 6 - When creating an rsync command:
```
rsync -e "ssh -p 4000" -varuzP /home/ross/ kids:/home/ross/backup/
```

Also be sure not to run any of these commands as root (eg. sudo ssh ...) or you will end up with keys files and keys all over the place. If for some reason you get to the end and your rsync is not running.  Make sure to run chown on the remote folder in question.  Obviously this is not a tutorial on permissions but this is a common problem that people overlook.

---

### Post by ablemike on 2007-10-12
Awesome! Can someone explain the switches?

I am also getting 
rsync: failed to set permissions on "......": Operation not permitted (1)

---

### Post by japglish on 2007-11-17
Absolutely excellent tutorial - there probably IS a tool oout there that will do all this for me automatically, but then I wouldn't have learnt all the incidental stuff that I picked up along the way. I used this tutorial to back up an opensuse 10.2 laptop to an older laptop running Ubuntu edgy and it worked perfectly.  Thanks for sharing your knowledge and in language I was able to understand!!!

---

### Post by jcup on 2008-05-13
Thank you so much for the a tutorial! I tried all day long to try and make this happen between two Windows servers, and it was a such a headache...

Now I will be using to ubuntu virtual machines to do the job...

Just wanted to say thanks and great job!

---

### Post by jcup on 2008-05-15
Thank you dk01 for adding the part about alternative ports, that was very helpful!!

---

### Post by Toky on 2008-06-21
Just FYI

Using passphrase less keys IS NOT SECURE at all... if you are doing this on a local network (ie inside your house) its "semi-ok" but not for backing up across the internet!!!

REMEMBER EMPTY PASSPHRASES ARE THE DEVIL!!!!

---

### Post by Gourgi on 2008-06-21
> **Toky said:**
> Using passphrase less keys IS NOT SECURE at all...
REMEMBER EMPTY PASSPHRASES ARE THE DEVIL!!!!

why is that ?
i 'm supposed to be secure as long as i own my private key.
isn't that correct?

---

### Post by Sir_Yaro on 2008-06-23
Exactly Gourgi.
I think it's very secure as long you keep your private key safe.

---

### Post by durus on 2008-06-25
> **kc0dhb said:**
> Here's a quick little script I wrote for backing up a mac laptop to a linux system.  Then modified to back up an ubuntu system to another box.

basically the structure will look similar to this
(output of tree -L 3 with some cutting)
.
`-- backup
    |-- now
    |   |-- torrents
    |   `-- workspace
    `-- old
        |-- 2006-01-05-at-23.47.51
        |-- 2006-01-05-at-23.49.20
        |-- 2006-01-06-at-00.12.29
        |-- 2006-01-06-at-00.12.42
        |-- 2006-01-06-at-00.13.19
        |-- 2006-01-06-at-00.13.54
        `-- 2006-01-06-at-19.37.40

Where the stuff in old contains files/directories that were changed or deleted at that time.

Excludes may be useful if you have a large amount of data that you really could care less about if you lose it, say you akready have a backup, or the originals of the data.  

Uncomment and recomment the parts about $tobebackedup if you just want certain directories.

```

#!/usr/bin/perl
# Kyle Byerly
# 20.December.2005
# Backs up everything to another system...don't know (or care) if it backs up
# the resource fork since the system I'm backing up to is linux.
# Perhaps at some later date I will worry about this.
# Backup to a mac from a mac using rsyncX.
$user = kyle;
$base = "/home/$user";
#if no leading slash then starts in home directory of remote login user
#pay attention to what will happen with --backup-dir
$backupdir = "backup";
#@dirs = < Documents Library Pictures perl amesfug apocalyptica backups classes english software #starbuck wireless lastbackup>;
#foreach (@dirs) {
#    $tobebackedup = "$tobebackedup $base/$_";
#}
$tobebackedup = "$base/";
#path from backup directory if starting with /
#if it ends with a / it is a directory, else it is a file
#if no leading / then it will exclude if it finds the word anywhere
#be careful here
@excludes =< /DVD /Music/ /source/ /archive.org/ Cache/ /.gnome-system-monitor.kyle >;
foreach (@excludes) {
    $excluding = "$excluding --exclude=\"$_\"";
}

#the below two lines will make it so I know when the last (complete) backup was
#as lastbackup is the last dir
system "rm $base/lastbackup/*";
system "touch $base/lastbackup/\"`date +%Y-%m-%d-at-%H.%M.%S`\"";
#notice \@ to comment out the @
system "rsync -rltb -e \"ssh -p 24\" $excluding --delete --backup-dir=~/$backupdir/old/`date +%Y-%m-%d-at-%H.%M.%S`/ $tobebackedup kyle2800\@192.168.2.13:$backupdir/now";

```

you can "execute" the script with either 
```

perl nameofscript 

```
or
```

chmod +x nameofscript 
./nameofscript

```

have fun

Thank you for this excellent script. Say that I have two backups
2008-06-26-at-00.05.00
2008-06-26-at-00.10.28
Then it is easy to go back to 2008-06-26-at-00.05.00, but how do I go back to 2008-06-26-at-00.10.28 ?

Thanks 
Durus

---

### Post by bayvista on 2009-01-22
i have followed your Howto, but still get asked for a password. This is what I get:

david@david-desktop:~$ ssh david-desktop
The authenticity of host 'david-desktop (127.0.1.1)' can't be established.
RSA key fingerprint is xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx (zapped by me)
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'david-desktop' (RSA) to the list of known hosts.
david@david-desktop's password: 
Linux david-desktop 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Also, I need to execute the "exportfs" command after every reboot. Is there any way of saving this info?

The only strange response was to the ssh-copy-id command. In the end, I copied the id_dsa.pub to the destination machine to /home/.ssh.

Any suggestions welcome.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)
Last login: Thu Jan 22 17:49:23 2009 from hp-laptop
david@david-desktop:~$

---

### Post by bayvista on 2009-01-23
Well, forget all that! I got it working at last by doing a keygen on the other machine. Now I can SSH to my laptop without a password. Next step is to setup Crontab.

I believe that it is important to secure the .ssh directory. I suggest that you add some instructions for this.

Thanks for an excellent Howto.

---

### Post by bayvista on 2009-01-26
Well, I spoke too soon. I can now connect OK to my laptop, but get the following errors when I RSYNC:

david@david-desktop:~$ rsync -varuzP hp-laptop:/home/pam/ /media/xpmedia/backups/hp-home-pam/>>/home/david/cronlog.txt
rsync: opendir "/home/pam/.sane" failed: Permission denied (13)
rsync: opendir "/home/pam/.nautilus/metafiles" failed: Permission denied (13)
rsync: opendir "/home/pam/.config/tracker" failed: Permission denied (13)
rsync: opendir "/home/pam/.config/gtk-2.0" failed: Permission denied (13)
rsync: opendir "/home/pam/.config/totem" failed: Permission denied (13)
rsync: opendir "/home/pam/.gnome2_private" failed: Permission denied (13)
rsync: opendir "/home/pam/.evolution/calendar/local" failed: Permission denied (13)
rsync: opendir "/home/pam/.evolution/tasks/local" failed: Permission denied (13)
rsync: opendir "/home/pam/.evolution/memos/local" failed: Permission denied (13)
rsync: opendir "/home/pam/.mozilla" failed: Permission denied (13)
rsync: opendir "/home/pam/.gnupg" failed: Permission denied (13)
rsync: opendir "/home/pam/.macromedia" failed: Permission denied (13)
rsync: opendir "/home/pam/.gconfd" failed: Permission denied (13)
rsync: opendir "/home/pam/.openoffice.org2" failed: Permission denied (13)
rsync: opendir "/home/pam/.thumbnails" failed: Permission denied (13)
rsync: opendir "/home/pam/.adobe" failed: Permission denied (13)
rsync: opendir "/home/pam/.update-notifier" failed: Permission denied (13)
rsync: opendir "/home/pam/.grsync" failed: Permission denied (13)
rsync: opendir "/home/pam/.metacity" failed: Permission denied (13)
rsync: opendir "/home/pam/.ssh" failed: Permission denied (13)
rsync: opendir "/home/pam/.gnome2" failed: Permission denied (13)
rsync: opendir "/home/pam/.gvfs" failed: Permission denied (13)
rsync: opendir "/home/pam/.local/share/Trash" failed: Permission denied (13)
rsync: opendir "/home/pam/.qt" failed: Permission denied (13)
rsync: opendir "/home/pam/.mozilla-thunderbird" failed: Permission denied (13)
rsync: opendir "/home/pam/.hplip" failed: Permission denied (13)
rsync: opendir "/home/pam/.gconf" failed: Permission denied (13)
rsync error: some files could not be transferred (code 23) at main.c(1385) [generator=2.6.9]
david@david-desktop:~$ 

Well, of course. My wife had not closed the applications. Once closed, all went fine

---

### Post by bayvista on 2009-02-04
A question for the Rsync gurus. It seems that you cannot archive an Rsync backup to a DVD. I keep getting error messages saying that I have too many directory levels. I think 6 is the maximum allowed.

To solve this problem, I am using TAR to archive my backups to DVD. Is there a cleaner way?

---

### Post by bayvista on 2009-05-03
Many thanks for this Rosslaird.

My wife's laptop died on Wed last. Blank screen. Using this Tutorial I had successfully backed up her Home directory every night to the Desktop. It was very easy to just restore the /home directory and logon as her. Bingo, everything just worked, including Email.

A great Tutorial

---

### Post by rosslaird on 2009-05-03
Glad you found it useful. This tutorial sure has had a long life. Now, I will also suggest another thing: backup your data online, using a getdropbox.com free account (2 gigs) and rsync with a local folder. Works like a charm.

Ross

---

### Post by RgnKjnVA on 2009-06-19
I was running this configuration like a champ for quite some time backing up my Hardy PC to my Intrepid laptop and vice versa but suddenly last night it stopped working. I get ssh timeouts from Intrepid laptop to Hardy PC but I can ssh the PC to the laptop although I get prompted for a password. I can also ping each machine from the other without a problem and nslookup works for each from the other. I also tried all of the above using IP instead of hostname to no avail. WTH?! Do those keys expire or something? To my knowledge I haven't done anything that would have affected networking nor connectivity.

laptop:~$ ssh -vv hardypc.home
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to hardypc.home [192.168.1.8] port 22.

---

### Post by RgnKjnVA on 2009-06-19
[SOLVED] Wife restarted the router and my laptop was assigned a different IP than it had previously. I'm off to learn how to make IPs static.

---

### Post by sloppyc on 2009-06-30
> **RgnKjnVA said:**
> [SOLVED] Wife restarted the router and my laptop was assigned a different IP than it had previously. I'm off to learn how to make IPs static.

Just happened across this post looking for answers on syncing /home directories between PCs...

..look into your router settings.  There should be a way to assign static IPs to different PCs based on the MAC address of the network adapters.  Then you can just leave all of your PCs configured to use DHCP.  I find this is the easiest way.

-------------------------------------

I have one question.  Currently I have ~/Music and ~/Videos replaced with symlinks to mounted Samba shares.  The script in the original post isn't going to try and copy the contents of those shares, is it?  It would be just fine though if it just copied the links.

---

### Post by RgnKjnVA on 2009-06-30
Thanks sloppy, I saw that as an option too and that is what I'm going to wind up doing. Turns out there is a bug with setting static IPs in Intrepid which left me just sick of messing with it and frustrated. I'll probably re-motivate and set it up via router settings the next time the issue rears its head.

wrt your question, I'm not sure what rsync will do with symlinks but you can use '--exclude=PATTERN' to make rsync skip those paths altogether.

---

### Post by sloppyc on 2009-06-30
> **RgnKjnVA said:**
> Thanks sloppy, I saw that as an option too and that is what I'm going to wind up doing. Turns out there is a bug with setting static IPs in Intrepid which left me just sick of messing with it and frustrated. I'll probably re-motivate and set it up via router settings the next time the issue rears its head.

wrt your question, I'm not sure what rsync will do with symlinks but you can use '--exclude=PATTERN' to make rsync skip those paths altogether.

No problem.  I've found it's the most pain-free way to keep things organized, particularly when I have machines that dual-boot, or if I upgrade OSs in addition to preventing headaches while setting static IPs on some machines.  Also avoids IP conflicts if/when someone brings a laptop or something in to connect to your network.

Ah cool, thanks for the tip.  So far it seems that the command as-is doesn't follow the symlinks, so I'm good for now.

EDIT:
> **rosslaird said:**
> won't delete any files on the destination that have been deleted from the source machine (for that, you use "--delete")

How do I add this to the rsync command?  I would like to be rid of files that I've deleted on the source machine; I guess I'm looking more to sync my files than simply back them up.  I understand I'm supposed to use "--delete", but when I added that to the command, it just deleted everything on the source machine.

---

### Post by asadqamber on 2009-07-02
In the command line Do:
crontab -e      
and I when the editor opens I type:

* * * * * "Print this on the terminal every minute"

but nothing happens.
can anyone help?

---

### Post by bastubis on 2009-07-03
I'm using rnsapshot to back up homes. 

Backing up evolution on the commandline used to involve forcing it to shutdown all its processes before doing the backup. I notice the new plugin also shuts down the application to make the backup. 

The question is, can rsnapshot backup Evolution 2.26 whilst it's running? 

If not, does anyone know how to automate evolution backups without corrupting data?

---

### Post by Elep.Repu on 2009-07-11
I personally use backintime, and find it wonderful.

---

### Post by bastubis on 2009-07-13
> **Elep.Repu said:**
> I personally use backintime, and find it wonderful.

Thanks, I've used timevault (which was unstable), I haven't tried Back In Time, but does it back up Evolution effectively? 

I'm happy with rsnapshot but I just can't find any info on whether Evolution settings would get corrupted? Frankly, I'll use *anything* stable that backs up evolution desktops properly. 

Anyone?

---

### Post by dgavenda on 2009-07-17
rosslaird,

Thanks for posting this tutorial.  Made it very simple.

---

### Post by soapBAR2 on 2009-08-05
> **sloppyc said:**
> Just happened across this post looking for answers on syncing /home directories between PCs...

..look into your router settings.  There should be a way to assign static IPs to different PCs based on the MAC address of the network adapters.  Then you can just leave all of your PCs configured to use DHCP.  I find this is the easiest way.

I'm not sure why you'd want to do it this way, messing around with MAC addresses and having your router do extra work (and your computer doing an unnecessary dhcp lookup). Not only that, but some routers may not have this function. On a linux machine, you can more easily do this;

```
$ sudo nano /etc/network/interfaces
```

change 

```
auto YOURIFACENAMEHERE
iface YOURIFACENAMEHERE inet dhcp # this line may or may not be in your file

```

to

```
auto YOURIFACENAMEHERE inet static
address xxx.xxx.xxx.xxx
gateway yyy.yyy.yyy.yyy
netmask 255.255.255.0

```

Where YOURIFACENAME is the name of your interface (usually something like eth0, possibly wlan0), xxx.xxx.xxx.xxx is your IP address (eg, 192.168.0.100), yyy.yyy.yyy.yyy is your router's IP address (eg, 192.168.0.1). Note that there's a tiny chance netmask may be different, but I've never heard of a consumer-grade NAT/DHCP router using anything but a /24 netmask unless it's explicitly set (and anyone who understands netmasks will already know what to do here!).

 Besides, it's important to know how to (re)configure /etc/network/interface, because you never know if your network manager might up and leave you (and you can't ask for help if your internet connection isn't working!).

---

### Post by AntsLoveSoda on 2009-09-11
For what it's worth, I would like to bring back up the debate about the insecurities of using a key instead of a password.

I agree with what's been mentioned -- as long as you keep the private key safe, it should *stay* safe, regardless if connecting over a private network or internet, correct?

For example, my private key is saved on a laptop that's system-wide encrypted, so I shouldn't have to worry...

Is there a security hole I'm missing here? :confused:

---

### Post by randyklein99 on 2010-04-17
> **AntsLoveSoda said:**
> For what it's worth, I would like to bring back up the debate about the insecurities of using a key instead of a password.

I agree with what's been mentioned -- as long as you keep the private key safe, it should *stay* safe, regardless if connecting over a private network or internet, correct?

For example, my private key is saved on a laptop that's system-wide encrypted, so I shouldn't have to worry...

Is there a security hole I'm missing here? :confused:

Bump to keep the security debate up...

---

### Post by GeekGirl1 on 2010-11-12
Thanks to this thread, both ssh and rsync are up and running. Maverick Meerkat.

*Important:* openssh-server is *not* installed by default in Ubuntu. You need to go into the Synaptic package manager and install it. Otherwise, ssh won't work on the target PC (connection refused). You can alternatively install the "ssh" package, which makes sure that both ssh and openssh-server are installed.

I used RSA keys (-t rsa) instead of DSA keys (-t dsa) for the ssh-keygen. I'm not sure it makes any difference, but RSA seems to be the most popular. Both will work.

---

