---
title: "Can't install samba"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by Deniz343 on 2012-11-03
I uninstalled samba with this command ```
sudo apt-get remove samba
``` after this I removed samba folder from "/etc" with ```
rm "."
```
So when I try to install samba there is no "/etc/samba" folder. Please help me to reinstall samba.

Best Regards
Thanks in advance

---

### Post by newb85 on 2012-11-03
The /etc/samba directory should be present, even if you haven't yet installed samba.  In the future, rather than removing applications and trying to manually remove associated configuration files, purge the application like this:
```
sudo apt-get purge *application-name*
```
That will ensure you don't remove the wrong files.

If trying to install samba throws an error complaining that there is no /etc/samba directory, then see if it will work with an empty directory:
```
sudo mkdir /etc/samba
sudo apt-get install samba
```

---

### Post by Deniz343 on 2012-11-03
I created empty dir but it didn't worked.

---

### Post by newb85 on 2012-11-03
Please post the error message it gave.

---

### Post by Deniz343 on 2012-11-03
There is no error message. I just can't see samba folder.

---

### Post by newb85 on 2012-11-03
Did samba install?

Do you mean you can't see the folder /etc/samba?  If so, how are you trying to view it?

---

### Post by Deniz343 on 2012-11-03
[attach]226623[/attach]

---

### Post by newb85 on 2012-11-03
I've attached the contents of my /etc/samba directory in a .tar file.  I don't believe they've been altered.  You can try extracting them and placing them in your /etc/samba.

---

### Post by Deniz343 on 2012-11-03
It's working
```
deniz@HTPC:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[YouTube]"
Loaded services file OK.
Server role: ROLE_STANDALONE

```

Thank you for your interest

---

### Post by Deniz343 on 2012-11-03
And how can I edit my home folder from a windows computer. When I want to edit my home folder it says > You don't have permission to edit this folder > [YouTube]
	comment = Youtube
	path = /home/deniz/YouTube
	read only = No
	create mask = 0755
	guest ok = Yes


---

### Post by newb85 on 2012-11-03
What authentication method are using to log onto the server?

---

### Post by Deniz343 on 2012-11-03
I don't know.

---

### Post by newb85 on 2012-11-03
Well you have the samba share set up as
> read only = no
so Samba shouldn't prevent you from writing to that share.

However, you also need to deal with the file permissions.  Your YouTube folder probably gives write permissions to the user deniz and only read and execute permissions to everyone else.  So, if you're not logged into the server as deniz, you don't have write permission.

One way to fix this is to change the permissions on the YouTube folder so that everyone has write permission.

A better approach, however, is to have the Windows client machines log in as deniz.  In /etc/samba/smb.conf, in the Authentication section, there's a line
```
#   security = user
```
Un-comment that line.  (Remove the leading #.)
Then, when the Windows client machines connect, they'll have to provide deniz's credentials, and they will then have access to everything deniz has access to on the machine.

Of course, if you don't want them to have access to all of deniz's files (e.g., if family members are using the other machines) you should create different user accounts for them.

---

### Post by Deniz343 on 2012-11-04
Thanks for your reply I'll try it this evening.

---

### Post by Deniz343 on 2012-11-04
It didn't worked.

---

### Post by newb85 on 2012-11-04
Could you be more specific on what it did or didn't do?

Also, let me suggest a little reading:
[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)

---

### Post by Deniz343 on 2012-11-04
I deleted > # security = user with #. Then I tried to make change in my home folder from windows computer. But it gave me the same error > You don't have permission to edit this folder. 

---

### Post by Morbius1 on 2012-11-04
Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by newb85 on 2012-11-04
> **Deniz343 said:**
> I deleted  with #. Then I tried to make change in my home folder from windows computer. But it gave me the same error

Did you delete the #, or the whole line?

Also, you will need to restart samba for any changes to smb.conf to take effect.

---

### Post by Morbius1 on 2012-11-04
> Did you delete the #, or the whole line?It doesn't matter if he deleted the # or the whole line:
```
testparm -sv /dev/null | grep "security"
```User level security is the default in samba which is why it's commented out with a # in smb.conf. From smb.conf itself:
> # Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
[COLOR=Blue]#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here[/COLOR]This is his share:
> [YouTube]
    comment = Youtube
    path = /home/deniz/YouTube
    read only = No
    create mask = 0755
    guest ok = Yes                      Try as it might Samba has no power over Linux file permissions. The remote guest cannot write to deniz's directory because guest is not deniz. One solution is to make that guest user appear to be deniz - at least for that share:
> [YouTube]
    comment = Youtube
    path = /home/deniz/YouTube
    read only = No
    create mask = 0755
[COLOR=Blue]**force user = deniz**[/COLOR]
    guest ok = Yes                      Then restart samba:
```
sudo service smbd restart
```There may be other things amiss here which is why I wanted to see if he created a Samba usershare though Nautilus to see if it too was in conflict.

---

### Post by newb85 on 2012-11-04
I was under the (apparently mistaken) impression that security=user meant that the client had to log in to the server as a user, and then essentially was that user.  At least that's how I interpreted this blirb from Samba's website:
> If the server accepts the username/password credentials, the client expects to be able to mount shares (using a tree connection) without further specifying a password. It expects that all access rights will be as the username/password credentials set that was specified in the initial session setup.

If that's not the case, then what does security=user do?

---

### Post by Morbius1 on 2012-11-05
"security = user" does mean that the client has to log into the server however there are other parameters in place in an Ubuntu default set up that determines exactly how that is done.

I have created a guest share and have created no samba passwords for any clients since all I have is this guest share. When morbius running Windows tries to connect to the Linux box his username and password are automatically sent ( without his knowledge ) to the Linux server. Samba then tries to match that username to the samba password database but finds nothing there.

Morbius is then tagged as a "Bad User" and converted to the guest account because of another parameter ( map to guest = Bad User ). The guest account user is by default "nobody" because of yet another default parameter "guest account = nobody" ( it's in the defaults but not explicitly stated in smb.conf ).

The user "nobody" corresponds to a Linux "other" so the shared folder either has to have Linux permissions set to allow "other" to read and write or something like "force user" can be used to circumvent the "map to guest" process and make the guest appear to be the owner of the target folder.

"security = user" and "guest account = nobody" are current Samba defaults. "map to guest" defaults to Never in Samba and is the default in Debian but Ubuntu overrides that default by specifying "Bad User" in it's default smb.conf.

---

### Post by newb85 on 2012-11-05
Thanks for clearing that up.  Does that mean that if the OP creates a user account on the Client machines with identical username and password to that on the Ubuntu machine, the problem would be solved?

---

### Post by Morbius1 on 2012-11-05
> Does that mean that if the OP creates a user account on the Client  machines with identical username and password to that on the Ubuntu  machine, the problem would be solved?That is another option if the client machine is running Windows ( Linux doesn't automatically pass a username and password ) but:

** You would have to create a samba password for that user on the server.
** And that user would have to log on to his Windows box with that user name for this to be seamless.
** There's also  a privacy issue involved here. Either the client user or the server user knows the login credentials of the other user on his own machine depending on how you set this up.

I would argue that since the OP purposely created a guest share he doesn't want to mess around with samba passwords on the server so either use "force user" or change Linux permissions.

---

### Post by Deniz343 on 2012-11-06
> **Morbius1 said:**
> It doesn't matter if he deleted the # or the whole line:
```
testparm -sv /dev/null | grep "security"
```User level security is the default in samba which is why it's commented out with a # in smb.conf. From smb.conf itself:
This is his share:
Try as it might Samba has no power over Linux file permissions. The remote guest cannot write to deniz's directory because guest is not deniz. One solution is to make that guest user appear to be deniz - at least for that share:
Then restart samba:
```
sudo service smbd restart
```There may be other things amiss here which is why I wanted to see if he created a Samba usershare though Nautilus to see if it too was in conflict.

Thanks man it worked.

---

