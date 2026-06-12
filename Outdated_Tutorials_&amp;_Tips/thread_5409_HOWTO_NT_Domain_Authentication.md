---
title: "HOWTO: NT Domain Authentication"
date: 2004-11-18
forum: Outdated Tutorials &amp; Tips
---

### Post by vizvayu on 2004-11-18
**NT Domain Authentication in Ubuntu HOW-TO**
by **vizvayu@gmail.com**

I'm making this tutorial because I had to set-up Ubuntu to authenticate on my company's NT Domain, so now that it's working I thought I could share my experience.
Any comments, ideas, and even some questions are welcome. There are several tutorials regarding this, but this one is made specially for Ubuntu.

First of all, I'm assuming that you are comfortable editing text files and have a basic undestanding of a linux system, including booting in recovery mode and restoring file backups. Although this procedure is not "dangerous", it could render the authentication system unusable if you make any mistake. So please, be careful and make backups of all the files changed.  =; 


To authenticate on a NT Domain, you need the following extra packets:
[list]
[*]samba
[*]winbind
[/list]

If I remeber correctly, the samba package comes with Ubuntu, but you have to download winbind separately from the universal repository.


Ok, now this is a list of the files we are touching, please make backups:
```

/etc/login.defs
/etc/nsswitch.conf
/etc/samba/smb.conf
/etc/pam.d/common-account
/etc/pam.d/common-auth
/etc/pam.d/common-password
/etc/pam.d/common-session
/etc/pam.d/sudo

```

Now, the first thing we are doing is setting up samba/winbind to work with the domain, so do a **nano /etc/samba/smb.conf** and insert the following lines:
```

workgroup = MYDOMAIN
idmap uid = 10000-20000
idmap gid = 10000-20000
template shell = /bin/bash
template homedir = /home/%D/%U
winbind enum users = yes
winbind enum groups = yes
winbind cache time = 10
winbind separator = +
security = domain
password server = *
winbind use default domain = yes

```
Remeber that this is just and example, you should/can change the values according to your needs.


After that we need to make the system to use winbind. First edit **/etc/nsswitch.conf** and replace:

```

passwd:	compat
group:	compat

```
with
```

passwd: compat winbind
group:	compat winbind

```

Now go to **/etc/pam.d** and edit the following files:

**common-account**:
```

#Commented for winbind to work
#account-required	pam_unix.so
account-required	pam_winbind.so

```

**common-auth**:
```

auth	sufficient	pam_winbind.so
auth	required	pam_unix.so nullok_secure use_first_pass

```

**common-session**:
```

session	required	pam_unix.so
session	required	pam_mkhomedir.so umask=0022 skel=/etc/skel/

```

**sudo**:
```

auth	sufficient	pam_winbind.so
auth	required	pam_unix.so use_first_pass

```


And this is an extra, not really required, but as I think the default max password lenght of 8 chars sucks (I like to use passphrases), and as we are using md5, I changed it:

**/etc/login.defs**:
```

PASS_MAX_LEN	50

```

**/etc/pam.d/common-password**:
```

password	required	pam_unix.so nullok obscure min=4 max=50 md5

```


Finally, there are only a few things left to do:

Join the domain:
```

net rpc join -D MYDOMAIN -U administrator

```

Test it with:
```

wbinfo -u
wbinfo -g

```


Make the domain home dir (users home dirs will be inside this one, but can be configured in **smb.conf**):
```

mkdir /home/MYDOMAIN

```

Reboot, and that's it, you should now have domain authentication working in Ubuntu. :D

Just a few extra comments:
[list]
[*]Remeber that if you need one user to have administration permissions, you need to include him in the **/etc/sudoers** list. Use the **visudo** command to do this. And there's no need to prepend **MYDOMAIN+** to the username since winbind is configured to use the configured domain by default.
[*]If anything goes wrong and you cannot login to the system, you have to reboot in recovery mode (press ESC when grub is starting) and replace the changed files from **/etc/pam.d** with the backups.
[*]I use NT4 domains, I don't think a W2k domain in native mode will work. You surely have to make some changes.
[*]This tutorial is just and example of how things worked for me. It's obviously not the only (or better) way to do things.  [-X 
[/list]

---

### Post by KenLin on 2005-02-07
awesome! worked like a charm. [IMG]http://ubuntuforums.org/images/smilies/eusa_clap.gif[/IMG]

---

### Post by water on 2005-04-10
Has anybody tried this with Hoary?

:water

---

### Post by kuleali on 2005-04-12
thanks, it worked

---

### Post by slipp3dstr3am on 2005-04-18
has anyone had any luck getting this to work on a win2k domain?

---

### Post by DracosX on 2005-04-19
For a win2k domain, just be sure to set security = ads as well as ream = your_realm in smb.conf and use net ads join -U administrator for the join command.

---

### Post by tonybee on 2005-04-20
This method seems to require a domain server present and connected to allow login to the local machine. How can the scripts be modifided to allow a local login if the network or domain is unavailable? ](*,)

---

### Post by JackDog on 2005-04-26
[QUOTE=water]Has anybody tried this with Hoary?

:water[/QUOTE]

I tried this on Hoary but it did not work. System users have to enter their password twice and when they finally get logged in, they get immediately logged out. Domain users to not authenticate at all. 

Nevermind, they key was specifying a default shell and default domain in smb.conf. ](*,)

---

### Post by mmrobins on 2005-04-26
I did this with Hoary Hedgehog 5.04 and now I get the message "The system administrator has disabled access to the system temporarily." when I try to logon using a domain user.  My local users can't log in now, simply saying authentication failed.  I'm trying to login to a mixed mode windows 2000 domain, so used the net join rpc command and it worked.  So I guess the good news is that it IS authenticating against the AD, but it won't let me onto the system.  Any suggestions?

---

### Post by xsdevnet on 2005-05-09
I did this and am able to login with one of the command line virtual terminals and ssh as an active directory user.  I cannot log in with XWindows though.  Any ideas what I should look at?

---

### Post by eekarum on 2005-05-23
What if my domain admin can't/won't come to my workstation and type his password? And even if he/she were willing, wouldn't that be risky if I were running a keystroke logger? 

So, how can I join my domain in this case? Our domain admins temporarily enable user accounts to join the domain, and in XP for example, we'd join using our own username and password, not theirs. (usually done over the phone)

---

### Post by JackDog on 2005-05-24
[QUOTE=eekarum]What if my domain admin can't/won't come to my workstation and type his password? And even if he/she were willing, wouldn't that be risky if I were running a keystroke logger? 

So, how can I join my domain in this case? Our domain admins temporarily enable user accounts to join the domain, and in XP for example, we'd join using our own username and password, not theirs. (usually done over the phone)[/QUOTE]

A domain admin can give your user special rights so you can add machines to your domain. This can be done without you having administrator access.

---

### Post by Philiphgray on 2005-07-04
[QUOTE=mmrobins]I did this with Hoary Hedgehog 5.04 and now I get the message "The system administrator has disabled access to the system temporarily." when I try to logon using a domain user.  My local users can't log in now, simply saying authentication failed.  I'm trying to login to a mixed mode windows 2000 domain, so used the net join rpc command and it worked.  So I guess the good news is that it IS authenticating against the AD, but it won't let me onto the system.  Any suggestions?[/QUOTE]
[QUOTE=xsdevnet]I did this and am able to login with one of the command line virtual terminals and ssh as an active directory user.  I cannot log in with XWindows though.  Any ideas what I should look at?[/QUOTE]
Hi guys - Think I might have a solution to this for you.

I was having the same problem until I went into System>Administration>login screen setup (I think you can also run "gksudo gdmsetup" to get this).  I then switched to the "security" tab and unchecked the box next to "Always disallow TCP connections to X server"

While I was there I also switched the graphical greeter to "happy gnome with browser" so that I could see domain users on bootup - just to make sure everything was looking ok!

I hope this helps.  If its wrong or if theres anything stupid contained within, then please accept my apologies - I've only been using linux for a month or so as a curiosity-project, so I don't claim to be any kind of expert, but most of that time has been spent configuring it to work with AD.  Worked for me though.

**<Rant>**
And incidentally, why does this have to be so totally painful on every distro I've tried?  So far, I've tried fedora, rhe, suse and ubuntu and all of them have made my life hell when simply trying to get hooked up to a windows domain.

Ubuntu is the only distro where I've ever got this to work (so it scores BIG points from me there) and that took a couple of days spent googling and some total trial-and-error-config-file-madness!

And whats really annoying is that all of the software is out there to make it work, you've just got to faff around for so long to get it to play.  I've been that hacked off by this that I'm seriously thinking of doing some kind of "idiots guide to joining ubuntu to a domain".  Granted, there are some good articles out there:  the one on wiki is quite handy ([https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto](https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto)) but fell over for me at "apt-get install krb5-user" which just didn't work on my default hoary install!

From my perspective, as a veteran windows user (but total linux newbie) this is the sort of thing that has to work out-of-the box, first-time and through a nice GUI.  Instead, I've been downloading and unpacking tar files for hours and now my brain is bleeding.

Something should be done.
**</Rant>**

Thanks for your time.

---

### Post by Gallows on 2005-07-08
Hoary out of the box doesn't include Libkadm55 and, as far as I know,  it isn't contained in any of the standard repositories.  So for the Hoary package of Libkadm55 (1.3.6-1), go  [Here](http://packages.ubuntu.com/hoary/libs/libkadm55) to download it

Ensure it is verison 1.3.6-1 and at the console type...

```
sudo dpkg -i [Path to deb]/libkadm55_1.3.6-1_i386.deb'
``` 

Then follow the rest of the very good HowTo as [referenced](https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto) in the previous posts. Just got it working on Hoary with it authenticating to a Win2k3 domain, and  I am *very* pleased with it / myself.

Btw - By default in Win2k3 a "normal" user can join up to 10 machines to the domain without the admin granting special rights.  So when asked to provide a username / password combo, and assuming you haven't joined a machine to the domain before, enter your username / password and you should be away.

---

### Post by webray on 2005-07-13
**Samba Domain Authentication**

I want to integrate my notebook with Kubuntu 5.04 in my network.

At my home is still running a Samba-Server as PDC based on Debian 3.1 r0a. Furthermore are there two Windows-Clients with WIndows XP Pro. The Domain-Authentication from the Windows-Clients to the Samba-Server works fine .. Each Client gets his home-directory and a global share directory. Also the Profiles were saved on the Samba-Server .. its running so beautiful  :grin: 
 
How do i get my f*** Kubuntu-Notebook into this domain ? It cannot be so difficult, or ?
My Notebook should get those two directories on startup ... and also the local notebook-profile should be stored on the Samba-Server. 

I tried lots of ways by now ...
- i edited the /etc/resolv.conf
- i changed the samba security level to domain
- i added the same user and pass as stored on the samba-server to my notebook
- ...

but nothing works :-(
webray

---

### Post by boooney on 2005-09-02
[QUOTE=DracosX]For a win2k domain, just be sure to set security = ads as well as ream = your_realm in smb.conf and use net ads join -U administrator for the join command.[/QUOTE]

Hi Guys--

I'm trying to log onto my windows 2000 domain at work and have followed your instructions, however I get the following error message:

net ads join -U dhardy
root@dhardy:/home/dhardy # net ads join -U dhardy
dhardy's password:
[2005/09/02 11:29:58, 0] utils/net_ads.c:ads_startup(191)
  ads_connect: No such file or directory 

Any idea what is going wrong?

Thanks in advance.

Dan

---

### Post by scav on 2005-09-24
Thanks for the howto, everything authenicates well, but I cant login with any users, not on ssh or gdm, if i use ssh i get that the user doesnt exist, on gdm it authenicates but it cant login, says something like "the system cannot log you on at the moment".

but my biggest problem is that i no longer can sudo or gksudo to root with my admin user!

why?

---

### Post by snowjunkie on 2005-09-27
Has anyone seen a ubuntu specific tutorial for using samba to emulate a domain controller and allow windows xp clients to authenticate against it?  I have seen a load of examples, but no ubuntu specific ones.

---

### Post by ArChAnG3L on 2005-10-24
[QUOTE=Philiphgray]Hi guys - Think I might have a solution to this for you.

I was having the same problem until I went into System>Administration>login screen setup (I think you can also run "gksudo gdmsetup" to get this).  I then switched to the "security" tab and unchecked the box next to "Always disallow TCP connections to X server"

While I was there I also switched the graphical greeter to "happy gnome with browser" so that I could see domain users on bootup - just to make sure everything was looking ok!

I hope this helps.  If its wrong or if theres anything stupid contained within, then please accept my apologies - I've only been using linux for a month or so as a curiosity-project, so I don't claim to be any kind of expert, but most of that time has been spent configuring it to work with AD.  Worked for me though.

**<Rant>**
And incidentally, why does this have to be so totally painful on every distro I've tried?  So far, I've tried fedora, rhe, suse and ubuntu and all of them have made my life hell when simply trying to get hooked up to a windows domain.

Ubuntu is the only distro where I've ever got this to work (so it scores BIG points from me there) and that took a couple of days spent googling and some total trial-and-error-config-file-madness!

And whats really annoying is that all of the software is out there to make it work, you've just got to faff around for so long to get it to play.  I've been that hacked off by this that I'm seriously thinking of doing some kind of "idiots guide to joining ubuntu to a domain".  Granted, there are some good articles out there:  the one on wiki is quite handy ([https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto](https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto)) but fell over for me at "apt-get install krb5-user" which just didn't work on my default hoary install!

From my perspective, as a veteran windows user (but total linux newbie) this is the sort of thing that has to work out-of-the box, first-time and through a nice GUI.  Instead, I've been downloading and unpacking tar files for hours and now my brain is bleeding.

Something should be done.
**</Rant>**

Thanks for your time.[/QUOTE]









Same thing happen to me..... I try this suggestion too. It did'nt work to me...
I hope there's someone can solve this problem...

---

### Post by daahli on 2005-10-27
.

---

### Post by elasticwings on 2005-11-09
[QUOTE=Philiphgray]Hi guys - Think I might have a solution to this for you.

I was having the same problem until I went into System>Administration>login screen setup (I think you can also run "gksudo gdmsetup" to get this).  I then switched to the "security" tab and unchecked the box next to "Always disallow TCP connections to X server"

While I was there I also switched the graphical greeter to "happy gnome with browser" so that I could see domain users on bootup - just to make sure everything was looking ok!

I hope this helps.  If its wrong or if theres anything stupid contained within, then please accept my apologies - I've only been using linux for a month or so as a curiosity-project, so I don't claim to be any kind of expert, but most of that time has been spent configuring it to work with AD.  Worked for me though.

**<Rant>**
And incidentally, why does this have to be so totally painful on every distro I've tried?  So far, I've tried fedora, rhe, suse and ubuntu and all of them have made my life hell when simply trying to get hooked up to a windows domain.

Ubuntu is the only distro where I've ever got this to work (so it scores BIG points from me there) and that took a couple of days spent googling and some total trial-and-error-config-file-madness!

And whats really annoying is that all of the software is out there to make it work, you've just got to faff around for so long to get it to play.  I've been that hacked off by this that I'm seriously thinking of doing some kind of "idiots guide to joining ubuntu to a domain".  Granted, there are some good articles out there:  the one on wiki is quite handy ([https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto](https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto)) but fell over for me at "apt-get install krb5-user" which just didn't work on my default hoary install!

From my perspective, as a veteran windows user (but total linux newbie) this is the sort of thing that has to work out-of-the box, first-time and through a nice GUI.  Instead, I've been downloading and unpacking tar files for hours and now my brain is bleeding.

Something should be done.
**</Rant>**

Thanks for your time.[/QUOTE]

Yay, I got it logging in and working following your directions.  I had to reboot also afterwards, but the only thing I don't have working I see so far is sound.  Does your sound work?  Did you have to do anything special for AD users to get their sound going?  I have sound for the regular user, but not for AD users.

---

### Post by elasticwings on 2005-11-10
I figured out the sound issue.  The only thing I am curious about now is if there is a way to get it to where users don't have to use the DOMAIN+username and just login with username.

---

### Post by fumidus on 2005-11-11
The auth works like a charm, i am just fiddling around with smbfs/cifsfs in fstab to get it to mount //server/share/userhomes to /home/DOMAIN so all settings and files come along.

Any ideas how to do that?


/* fumidus */

---

### Post by sparhawk on 2005-11-14
I followed the guide and found it great. I was joining a 2003 domain so I needed to change a few things but otheriwse it was dead on... good job. I just have 1 question. How do I give my domain users the sudo ability. I have added their username to the sudoers file but it still says users not in sudoers file when I try sudo. Any ideas would be welcome. I hope someday that linux does incorporate some of this stuff into the default install... you know like you boot up and it asks ... "Would you like to join a windows AD domain" and then a few answers later... DONE! that would be great.

---

### Post by talbot on 2005-12-09
[QUOTE=elasticwings]I figured out the sound issue.  The only thing I am curious about now is if there is a way to get it to where users don't have to use the DOMAIN+username and just login with username.[/QUOTE]

I'm having the same problem. how you solved that?
Thanks

---

### Post by XeroXer on 2005-12-11
Ok I made a mess yesterday.
I just searched all the forums for a way to get my network working.
And I found this and thought I'd give it a try.
The only BIG problem is that I got "Ubuntu Breezy Badger 5.10".
Stupid as I am I didn't even read what this was for.
I just started changing the files. (made backups of course)

But now I can't even log in.
When I try to log in with my regular user I just get a message saying:
**Authentication failed!**
And then the login screen comes back on.
If I write a user that does not exist or if I enter the wrong password for my user, then it just goes back to writing username and says I entered wrong information.
So it knows that I have entered the right information but the login is still broken.

This was a BIG missake bye me but hopwfully there is a way to save my precious computer...
???

---

### Post by pki on 2006-01-04
Hi !

I'm new at this forum :)

Working on Ubuntu Breezy Badger 5.10, done the modifications like described in the first post on a clean new installation.

wbinfo -u
wbinfo -g

shows the domain users and groups.

but 'getent passwd' shows only the local data. :(

How can i find the problem ??

I can't login with domain user/pass.

---

### Post by bobpaul on 2006-03-18
I basically did what you did above, but now gksudo doesn't work. Sudo works fine, as my sudoers file contains *%domain\ admins ALL=(ALL) ALL* to give domain admins access to sudo. Without gksudo, though, all of the System Administration etc icons don't work, which is annoying. 

Which I click a launcher that calls "gksudo command" absolutely nothing happens, no password or anything. It's like I didn't click anything at all.

When I run "gksudo command" from a term, I'm prompted "passowrd:" in the term just like I had used sudo, but the password is not masked when I enter it and nothing happens if I type the correct password; it just hangs until Ctrl+c.

When I run "gksudo command" from a term in which I've already successfuly used sudo, then the application launches with root privledges and I am not prompted for my password.

Any ideas ?

---

### Post by Abhi Kalyan on 2006-10-20
hi, i run Ubuntu dapper drake 6.06
need to connect to a share "sharename:lincon" in windows server 2003, this is a domain controller and the domain name is zen.local. how do i do this?
Please my head is dead tryong to figure things out!!

---

### Post by Swab on 2006-10-24
> **Abhi Kalyan said:**
> hi, i run Ubuntu dapper drake 6.06
need to connect to a share "sharename:lincon" in windows server 2003, this is a domain controller and the domain name is zen.local. how do i do this?
Please my head is dead tryong to figure things out!!

If you just want to connect to the share, you can..

- open up nautilus
- press ctrl+L
- type the path of the share into the location bar  example: \\servername\sharename\
- enter a valid username and password

---

### Post by Abhi Kalyan on 2006-10-25
Thank you vizvayu,
Great Job, 
Could understand quite a bit,
will clarify on completion.

---

### Post by Abhi Kalyan on 2006-10-25
Thank you swab,
Great help buddy. Works like a shine!
One problem though, its not accepting "servername" only accepts ip address,
Why might this be happening, Should i do something with the DNS?
Thank you once again

---

### Post by j00b on 2006-10-27
Thanks, worked great.

When I try to connect to a NT network drive using Nautilus, I'm still prompted for a password though. Is there anyway to try and authenticate using my current credentials first?

---

### Post by Swab on 2006-10-27
> **Abhi Kalyan said:**
> Thank you swab,
Great help buddy. Works like a shine!
One problem though, its not accepting "servername" only accepts ip address,
Why might this be happening, Should i do something with the DNS?
Thank you once again

Well, obviously I don´t know your setup.. but yes it´s almost certainly a DNS issue. 

Simple solution is to edit your hosts file (/etc/hosts) and add a line with the IP address of the server followed by the name of the server, for example:

192.168.1.2            servername

---

### Post by Swab on 2006-10-27
> **j00b said:**
> Thanks, worked great.

When I try to connect to a NT network drive using Nautilus, I'm still prompted for a password though. Is there anyway to try and authenticate using my current credentials first?

Yeah same here.  Previously when I was authenticating Ubuntu against AD there was a way to get a kerberos ticket.  Is there an equivalent for NT domains?

---

### Post by Abhi Kalyan on 2006-10-28
Swab Tried editing /etc/hosts file, But the IP is already taken and shows the following:
127.0.0.1 localhost l1
127.0.1.1 l1.zen.local l1

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.2 sycone-server-win2003
19.168.1.3 internet connection host-x.zen.local

What do i make off This?
Please help.
Thank you once again Swab.

---

### Post by Swab on 2006-10-28
> **Abhi Kalyan said:**
> Swab Tried editing /etc/hosts file, But the IP is already taken and shows the following:
127.0.0.1 localhost l1
127.0.1.1 l1.zen.local l1

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.2 sycone-server-win2003
19.168.1.3 internet connection host-x.zen.local

What do i make off This?
Please help.
Thank you once again Swab.


I'm assuming 192.168.1.2 is the address of the server?  You can give as many names as you like to a node.. for example you could have

192.168.1.2 sycone-server-win2003 whatevernameyoulike

In this case you would be able to use smb://whatevernameyoulike/sharename or smb://sycone-server-win2003/sharename

Try reading the manual page for hosts.  Just type "man hosts" at the terminal.  Almost every command has a man page, some are more useful than others.  Oh and press "q" to exit the man page when you are finished!

---

### Post by TrialAndError on 2006-10-31
> **talbot said:**
> I'm having the same [sound] problem. how you solved that?
Thanks

You have to look around for "group.conf" and "audio" for example.

One easy solution you find here:
[http://ubuntuforums.org/showthread.php?t=77469](http://ubuntuforums.org/showthread.php?t=77469)

---

### Post by abovett on 2007-02-08
Hi

I have a box running "SME Server" (a distro running samba which emulates an NT server), and I have successfully used this howto to set up an Ubuntu Edgy box so that it can authenticate against the SME server box for logging in.

However, I can no longer browse the shares on the server using the "Network Servers" icon on the Places menu. That's not critical - I can connect to the shares on the server if I use the "Connect to server" icon and fill in all the details, and it creates an icon for the share on the desktop,  but I still get asked for a password the first time I open it. I'd like to set it up so that my login credentials are used to access the shares and no additional passwords are required.

This is quite important because I'm planning to deploy a similar system and my users are not going to be happy if they have to retype their passwords multiple times.

Can anyone help?

Thanks

Andy B

---

### Post by Emeric Evans on 2007-02-08
I followed the guide and it sorta worked. but for some odd reason it doesn't seem to let me get into any of my administrative type apps (the one you have to type a password to get into like Login Window, Users and Groups, etc.). Whenever I change back the common-account, common-auth, common-session, common-password, and sudo then restart I don't have anymore problems. I will say that I did have the same username and password for my local account on my linux box as on the NT domain, but I tried changing my username and it still acts like this. I also don't know if I necessarily have to change all those files, I just changed all of them because they seemed to be the most likely caused and sure enough it works, but it could be one specifically I suppose. Also I can't actually login with domain user accounts.

Does anyone have any ideas what might be causing this?

---

### Post by isocles on 2007-02-23
> **vizvayu said:**
> 
Now go to **/etc/pam.d** and edit the following files:

**common-account**:
```

#Commented for winbind to work
#account-required	pam_unix.so
account-required	pam_winbind.so

```


This will break Ubuntu domain member servers and clients running Samba 3.0.24 (and possibly 3.0.23x) making it impossible to login.

**common-account** should read:

```

account sufficient pam_winbind.so
account required pam_unix.so

```

It took me hours to sort this out :)  If this works on stock Samba 3.0.22 that ships with 6.06.1 LTS, and 6.10, then you might want to edit the original post to match.

---

### Post by abovett on 2007-05-10
I've followed this howto to get an Ubuntu Feisty box to log onto a Samba server (including the fix mentioned above to /etc/pam.d/common-account). It works, but as someone mentioned before, gksudo doesn't work any more. Has anyone found a solution to this yet, or have any suggestions for tracking the problem down?

I would like to fix this because as it stands the administrative menu functions don't work. I know how to work around this via the command line, but I'm deploying this where less technical users will be using it so really I need it to work correctly.

Thanks

Andy B

---

### Post by Junio Vitorino on 2007-06-26
For me the tutorial doesn't works, i already tried everything. The connection with the domain occurs fine, but the logon of the users not happen. Only the expiration password message is show.

I tried this other [tutorial]("http://www.vivaolinux.com.br/artigos/verArtigo.php?codigo=1348&pagina=1"), i had the connection and the logon perfectly, but when the system go to create the directory of the user i get the error: xsession: Unable to create ~/.gnome2 directory: directory or file doesn't exists.

I'm without exit, some help?

---

### Post by abovett on 2007-06-26
Hi

Not sure why you can't log in after following this guide - the basics are all there though you might have to make alterations to suit your specific setup. I only speak English so I'm afraid I can't comment on the other tutorial you mentioned - a shame as it would probably be useful to compare them.

However, I can guess what's happening with the error you are getting - I suspect the problem is that you are trying to log on with a home directory that is not actually accessible - thus gnome can't create its required directories. Are you trying to locate your home directory on the samba server? If so, pam_mount may not have successfully mounted your home directory - or mounted it with the wrong permissions. Try logging in at the console and then use the mount command to check what's mounted where.

Some general suggestions:

(1) Make sure you have a reasonable understanding of how samba, pam, winbind and pam_mount work first. Read the man pages and do some reading up online. Don't just follow the tutorials by rote - understand what they are doing so you can see if you need to make alterations to make it apply to your situation. You don't need to become an expert (I most certainly am not!) but make sure you understand the basics.

(2) Take things step by step, checking what works at each stage. My suggested order would be:

(i) Make sure Samba is working properly and that you can mount shares with CIFS.
(ii) Get winbind working and join the domain (sounds like you have got this working)
(iii) Get pam_mount working _without_ moving you home directory onto the server - just get it to mount an arbitrary share and make sure that works.
(iv) once all that is working, you can think about moving your home directory onto the server.

It's a shame, but from my (limited) experience, logging a Linux PC (or at least a Ubuntu one) onto a samba or windows domain is not yet something that can be done reliably without some understanding of the processes involved. I'm sure it will improve over time but for the moment "some assembly required" as they say.

HTH

Andy B

---

### Post by 5of0 on 2007-08-29
Hey all!  I just finished successfully nailing down my technique for joining a Windows 2003 domain from Ubuntu 7.04 (Feisty Fawn), mainly using SADMS.  After three tries, I joined the domain from a fresh install within 15 minutes.  This thread (along with a few others) were very helpful, and there was a bit of trial-and-error involved as well.

I've written it all up on the Ubuntu wiki.  If any of you guys want to try it out and let me know how it goes, check it out:
[https://wiki.ubuntu.com/JoinWindowsDomain](https://wiki.ubuntu.com/JoinWindowsDomain)

Thanks!

---

### Post by ldcole on 2007-09-06
I'm trying to join to a Windows 2003 sp2 domain and I keep getting the following message. Any ideas? I used the [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto) guide, but I'm not having any luck. 

root@dpiwks-test:/home/cole# net ads join -U Administrator -W domain Administrator's password: 
Using short domain name -- domain
Failed to set servicePrincipalNames. Please ensure that
the DNS domain of this server matches the AD domain,
Or rejoin with using Domain Admin credentials.
Disabled account for 'DPIWKS-test' in realm 'DOMAIN.LOCAL'

I substituted our actual domain with 'domain' for security reasons. I'm a bit paranoid. 

The machine does show up in AD, but is disabled.

---

### Post by anselm13 on 2007-12-16
Has anyone had any troubles with using samba and winbind to join an ubuntu 7.10 "gutsy" client to an NT domain (ubuntu server as samba PDC).  It worked and still works fine using feisty clients, but doesn't seem to work in gutsy.  I actually can join (a machine account is created) but can't authenticate and wbinfo -t, wbinfo -u, and wbinfo -g give errors (getent passwd also does nothing).  I guess I'm curious if there are any issues that have crept in with gutsy?

I've used the following tutorials as guidance (plus some of this thread):
[http://www.hantslug.org.uk/cgi-bin/wiki.pl?LinuxHints/SambaAuth](http://www.hantslug.org.uk/cgi-bin/wiki.pl?LinuxHints/SambaAuth)
[http://tech.canterburyschool.org/tech/UbuntuWorkstations_2fAuthenticationSetup](http://tech.canterburyschool.org/tech/UbuntuWorkstations_2fAuthenticationSetup)
[http://tech.canterburyschool.org/tech/UbuntuWorkstations_2fSetUpSamba](http://tech.canterburyschool.org/tech/UbuntuWorkstations_2fSetUpSamba)

---

### Post by neal_ro on 2007-12-26
so close... someone give me a nudge? using Ubuntu 7.10 

Configured Samba and could browse the network etc.  After installing winbind, was able to join the domain, verified a computer account existed in active directory and passed tests with wbinfo -t, wbinfo -a, wbinfo -u  but not login to domain.  Started researching domain authentication and found this HowTo, I followed the steps to modify the pam.d files.  Rebooted thinking OK done deal, easy enough, no problem.  

Tried to login with 3 different domain accounts and just get "authorization failed" after entering the password.  Tried to log in with local ubuntu account cleveryly named "user" and cannot log in locally either, just get "autorization failed".  Entering a bogus username results in "authorization failed" before I even enter a password so it seems to be getting the user list.  

Thinking I made a typo in one of the pam.d files, I rebooted into recovery mode and checked the pam.d files but all looked OK, more research and found other tutorials and tried their recommended pam.d files.  Same thing, still cannot log in using domain or local credentials.  What am I missing?  

relevent smb.conf lines:
 workgroup = mydomain
 sercurity = domain
 encrypt passwords = yes
 password server = *
 idmap uid = 10000-20000
 idmap gid = 10000-20000
 template shell = /bin/bash
 template homedir = /home/%D/%U  
winbind separator = +
winbind enum users = yes
winbind enum groups = yes

nsswitch.conf
passwd: compat winbind
group: compat winbind

common-account:
account sufficient pam_winbind.so
account required pam_unix.so

common-auth:
auth sufficient pam_winbind.so use_first_pass
auth required pam_unix.so user_first_pass

common-session:
session required pam_unix.so
session required pam_foreground.so
session required pam_mkhomedir.so umask-0022 skel=/etc/skel

---

### Post by neal_ro on 2007-12-26
OK so I got impatient and irritated and decided to undo all I had done and start over clean a la format and reinstall  (its just a test system).  

I'm going to try to us SADMS instead of the trial and error of editing all these config files and reading endless FAQs, howtos and random posts and trying to piece it all together. 

But still if you see something incorrect in my config files from my previous post please let me know what it is.

---

### Post by sandwormblues on 2008-01-19
SADMS is great!  Methinks it should be added to the main repository..

---

### Post by clemix on 2008-05-21
hi
I tried the tutorial, and it does not work... :(
when i type: wbinfo -u
I see all the users...
but when i type wbinfo -g
I see only:
```
BUILTIN+administrators
BUILTIN+users 
```

but there are much more groups... does anybody know a solution?

---

### Post by pigna on 2009-04-30
I changed the configuration of pam to authenticate in the domain with winbind and I have enabled caching of user and password of the domain, I log the domain user (both online and offline) and mount the shared, but I have a problem when Working offline and use of certain programs that require user authentication to be run. 

Example: When I try to launch the System -> Admin -> Users and Group " from local user and I click Unlock I request the password, but when I enter the program freezes for a few minutes and then tells me:

[HTML]Unable to authenticate
An unexpected error occurred[/HTML]

And in the file auth.log I appear the following messages:

[HTML]dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.29" (uid=1001 pid=4573 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.91" (uid=1000 pid=6714 comm="/usr/lib/policykit-gnome/polkit-gnome-manager "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.59" (uid=1000 pid=5593 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.91" (uid=1000 pid=6714 comm="/usr/lib/policykit-gnome/polkit-gnome-manager "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.29" (uid=1001 pid=4573 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.92" (uid=1000 pid=6715 comm="/usr/lib/policykit/polkit-grant-helper 6706 org.fr"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.59" (uid=1000 pid=5593 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.92" (uid=1000 pid=6715 comm="/usr/lib/policykit/polkit-grant-helper 6706 org.fr"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.29" (uid=1001 pid=4573 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.93" (uid=1000 pid=6718 comm="/usr/lib/policykit/polkit-grant-helper 6706 org.fr"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.59" (uid=1000 pid=5593 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.93" (uid=1000 pid=6718 comm="/usr/lib/policykit/polkit-grant-helper 6706 org.fr"))
polkit-grant-helper-pam[6721]: pam_mount(rdconf1.c:667): path to luserconf set to /home/user1/.pam_mount.conf.xml 
polkit-grant-helper-pam[6721]: pam_winbind(polkit:auth): getting password (0x00000010)
polkit-grant-helper-pam[6721]: pam_winbind(polkit:auth): pam_get_item returned a password
polkit-grant-helper-pam[6721]: pam_winbind(polkit:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_AUTHINFO_UNAVAIL (9), NTSTATUS: NT_STATUS_NO_LOGON_SERVERS, Error message was: No logon servers
polkit-grant-helper-pam[6721]: pam_winbind(polkit:auth): internal module error (retval = PAM_AUTHINFO_UNAVAIL(9), user = 'user1')
polkit-grant-helper-pam[6721]: pam_unix(polkit:auth): authentication failure; logname= uid=1000 euid=0 tty= ruser=user1 rhost=  user=user1[/HTML]

And if you use a domain  user I have these messages appear:

[HTML]dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
57" (uid=1001 pid=4645 comm="users-admin "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
58" (uid=0 pid=4648 comm="/usr/bin/perl /usr/share/system-tools-backends-2.0"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
59" (uid=0 pid=4654 comm="/usr/bin/perl /usr/share/system-tools-backends-2.0"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
60" (uid=0 pid=4656 comm="/usr/bin/perl /usr/share/system-tools-backends-2.0"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
61" (uid=0 pid=4658 comm="/usr/bin/perl /usr/share/system-tools-backends-2.0"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
62" (uid=1001 pid=4666 comm="/usr/lib/policykit-gnome/polkit-gnome-manager "))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
63" (uid=1001 pid=4667 comm="/usr/lib/policykit/polkit-grant-helper 4645 org.fr"))
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.52" (uid=1001 pid=4575 comm="/usr/lib/indicator-applet/
indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.
64" (uid=1001 pid=4670 comm="/usr/lib/policykit/polkit-grant-helper 4645 org.fr"))
polkit-grant-helper-pam[4673]: pam_mount(rdconf1.c:667): path to luserconf set to /home/user2/.pam_mount.conf.xml
polkit-grant-helper-pam[4673]: pam_winbind(polkit:auth): getting password (0x00000210)
polkit-grant-helper-pam[4673]: pam_winbind(polkit:auth): pam_get_item returned a password
polkit-grant-helper-pam[4673]: pam_winbind(polkit:auth): user 'user2' granted access
polkit-grant-helper-pam[4673]: pam_winbind(polkit:account): user 'user2' granted access[/HTML]

This is my configuration files:

```
[common-account]
account sufficient pam_winbind.so
account required pam_unix.so

[common-auth]
auth required pam_mount.so
auth sufficient pam_winbind.so use_first_pass
#auth sufficient pam_winbind.so
auth required pam_unix.so nullok_secure use_first_pass

[common-password]
password sufficient pam_winbind.so use_authtok
#password sufficient pam_winbind.so
password required pam_unix.so nullok obscure min=4 max=9 md5

[common-session]
session required pam_unix.so nullok_secure
session required pam_mkhomedir.so skel=/etc/skel/ umask=0022
session optional pam_mount.so

[pam_winbind.conf]
[global]
#debug
cached_login = yes

[smb.conf]
workgroup = DOM1
server string = %h
security = domain
encrypt passwords = true
wins server = xxx.xxx.xxx.xxx
password server = *
domain master = false
preferred master = false
local master = no
lm announce = false
hosts allow = xxx.xxx.xxx.xxx, 127.0.0.1
hosts deny = all
socket options = TCP_NODELAY IPTOS_LOWDELAY
log file = /var/log/samba/log.%U
log level = 2
pam password change = yes
interfaces = eth0, lo
winbind uid = 1000-10000
winbind gid = 1000-10000
winbind enum users = yes
winbind enum groups = yes
winbind use default domain = yes
winbind cache time = 15
winbind offline logon = yes
template shell = /bin/bash
template homedir = /home/%U

```

	
Suggestions?

---

### Post by tkibugu on 2009-11-27
[ I deleted post contents]

---

### Post by Patophe on 2010-11-11
Hi,
 I tried this method on my server and I'm now kicked out from is as root!!!!  

After rebooting, no more root account was accessible!!! I can't roll back without admin priviledge!!  I had a ssh secure key set and it does'nt work anymore.  

  This changed the root account to another!!

Some major help please!!

 I need a way to recover this server!!

---

### Post by Patophe on 2010-11-11
I booted in recovery mode and rolled back.

It's done.

> **Patophe said:**
> Hi,
 I tried this method on my server and I'm now kicked out from is as root!!!!  

After rebooting, no more root account was accessible!!! I can't roll back without admin priviledge!!  I had a ssh secure key set and it does'nt work anymore.  

  This changed the root account to another!!

Some major help please!!

 I need a way to recover this server!!

---

### Post by cucu007 on 2010-11-11
Thank you for this contribution, I have been thinking about migrating all my server from Windows Server to Linux due to the high cost of licensing but I am still a little afraid about doing it since I might loose some functionality. I am still evaluating the possibility and this serve as a good start.:P

---

### Post by pigna on 2010-11-12
> **cucu007 said:**
> Thank you for this contribution, I have been thinking about migrating all my server from Windows Server to Linux due to the high cost of licensing but I am still a little afraid about doing it since I might loose some functionality. I am still evaluating the possibility and this serve as a good start.:P

Hi cucu007, i have the 80% of Servers with Linux (CentOS and Debian) and 20% with Windows (because some applications require Windows as SO).

Linux servers provide:

[LIST]
[*]Domain autentication (Samba)
[*]File Server (Samba)
[*]Mail (imap, pop, smtp)
[*]Groupware (with SOGo)
[*]Fax server
[*]Datawarehouse
[*]VPN
[*]Firewalling
[*]DB Server
[/LIST]

and more... ;)

In linux the cost of licensing is very cheap but in some cases the implementation requires more effort on the part of the System Administrators.

;)

---

### Post by divyabdasar on 2011-07-07
I am trying to connect ubuntu 11.04 to windows 2003 server domain. I followed  all the configuration steps as told.

After rebooting the machine i am unable to login. This is the first time i am trying to connect to windows domain.

Any help will be of great importance.

---

