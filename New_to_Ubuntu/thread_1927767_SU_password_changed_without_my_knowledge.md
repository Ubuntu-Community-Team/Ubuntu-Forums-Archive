---
title: "SU password changed without my knowledge"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by MrAlex on 2012-02-18
so... here I am trying to change my resolution (something that I need to do every time I boot up since I installed the ATI drivers) and boom, my password doesn't work. It's not that I forgot it, it's too simple for that, something fishy is going on.

Now, I noticed that there are some tutorials out there telling you how to reset your password, and I will try that, but I am new to Linux, I want to know how something like that could have happened!

I read that /etc/passwd and /etc/shadow are the two files that hold the password data so I tried to investigate:

```
$ls -al /etc/passwd
-rw-r--r-- 1 root root 1754 2012-02-01 23:55 /etc/passwd
$ls -al /etc/shadow
-rw-r----- 1 root shadow 1067 2012-02-18 15:17 /etc/shadow
```

Sooo passwd didn't change at all, but shadow did... today! Now, I haven't changed the password at all today and nobody had access to this computer in that time (well, unless my pet hamster somehow managed to escape his cage and hack my PC).

How can I investigate this? could it be possible that somebody ssh-ed to my PC and did some funky business? (my password is rather weak). How could I check for that?

---

### Post by MrAlex on 2012-02-18
I'm trying to find out what happened at that time:

```
alex@alex-P55A-UD3R:~$ cat /var/log/syslog | grep 15:17
Feb 18 15:17:02 alex-P55A-UD3R CRON[6719]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

so the cron jobs happened at that time... but that directory is empty...

I also get a lot of these (173 to be precise) around that time:


```
alex@alex-P55A-UD3R:~$ cat /var/log/syslog | grep atack
Feb 18 15:39:59 alex-P55A-UD3R kernel: [16567.873525] atack[7576]: segfault at 0 ip 0000000008048e33 sp 00000000ff95b470 error 4 in atack[8048000+c0000]
Feb 18 15:39:59 alex-P55A-UD3R kernel: [16567.873645] atack[7593]: segfault at 0 ip 0000000008048e33 sp 00000000ff95b470 error 4 in atack[8048000+c0000]
Feb 18 15:39:59 alex-P55A-UD3R kernel: [16567.873778] atack[7584]: segfault at 0 ip 0000000008048e33 sp 00000000ff95b470 error 4 in atack[8048000+c0000]
Feb 18 15:39:59 alex-P55A-UD3R kernel: [16567.922101] atack[7541]: segfault at 0 ip 0000000008048e33 sp 00000000ff95b470 error 4 in atack[8048000+c0000]
Feb 18 15:40:00 alex-P55A-UD3R kernel: [16568.911034] atack[7542]: segfault at 0 ip 0000000008048e33 sp 00000000ff95b470 error 4 in atack[8048000+c0000]
Feb 18 15:40:00 alex-P55A-UD3R kernel: [16569.420757] atack[7543]: segfault at 0 ip 0000000008048e33 sp 00000000ff95b470 error 4 in atack[8048000+c0000]
Feb 18 15:40:01 alex-P55A-UD3R kernel: [16570.007589] atack[7544]: segfault at 0 ip 0000000008048e33 sp 00000000ff95b470 error 4 in atack[8048000+c0000]
Feb 18 15:40:03 alex-P55A-UD3R kernel: [16571.992876] atack[7545]: segfault at 0 ip 0000000008048e33 sp 00000000ff95b470 error 4 in atack[8048000+c0000]
Feb 18 15:40:04 alex-P55A-UD3R kernel: [16572.836505] atack[7577]: segfault at 0 ip 0000000008048e33 sp 00000000ff95b470 error 4 in atack[8048000+c0000]
```

What's going on here?!!?:confused:

Edit: reset the password and did a "sudo apt-get remove openssh-server" for good measure... but what could have happened?

---

### Post by Lisiano on 2012-02-18
If your ISP doesn't allows incoming connections (Most don't without asking them), then it's your hamster. If it does, then I'm inclined to think someone bruteforced your box, take a look at /var/log/auth.log

To be honest, someone is trying to get into my box as I'm typing this so it's possible you got bruteforced.

```
Feb 19 01:21:04 Lisiano-Ubuntu sshd[2110]: User root from 180.191.200.152 not allowed because not listed in AllowUsers
Feb 19 01:21:04 Lisiano-Ubuntu sshd[2110]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=180.191.200.152  user=root
Feb 19 01:21:04 Lisiano-Ubuntu sshd[2110]: pam_winbind(sshd:auth): getting password (0x00000388)
Feb 19 01:21:04 Lisiano-Ubuntu sshd[2110]: pam_winbind(sshd:auth): pam_get_item returned a password
Feb 19 01:21:04 Lisiano-Ubuntu sshd[2110]: pam_winbind(sshd:auth): request wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: No such user
Feb 19 01:21:06 Lisiano-Ubuntu sshd[2110]: Failed password for invalid user root from 180.191.200.152 port 33703 ssh2
```
Also an example for you what to look for.

Also, unless you have a need for an SSH server running on your box, you shouldn't have it installed. I do since I log in remotely a lot.

---

### Post by duncan12 on 2012-02-18
As for trying to change your password:

First, I would disconnect your computer from the net.

Reboot your computer, choose Ubuntu, with Linux ....., **recovery mode**. Then choose "open root terminal".

Then at the prompt type ```
passwd root
```

I did this before to one box after changing the password, and it not working afterwards.

However on my main computer, pressing "open root terminal" prompts for a password - so YMMV but maybe worth a try.



EDIT: just read in your second post that you did reset the password.

---

### Post by MrAlex on 2012-02-18
> **Lisiano said:**
> If your ISP doesn't allows incoming connections (Most don't without asking them), then it's your hamster. If it does, then I'm inclined to think someone bruteforced your box, take a look at /var/log/auth.log

Oooh... yeah, that's the kind of info that I'm looking for... My ISP DOES allow incoming connections, this is why I installed sshd in the first place. I knew I had a weak password, but I figured nobody would bother to crack my home box. /var/log/auth.log contains a lot of attempts though (looks like this fella was at it for a few hours - and a few days). But it culminates with this:

```
Feb 18 15:17:34 alex-P55A-UD3R sshd[6721]: reverse mapping checking getaddrinfo for 82-137-13-73.rdsnet.ro [82.137.13.73] failed - POSSIBLE BREAK-IN ATTEMPT!
Feb 18 15:17:35 alex-P55A-UD3R sshd[6721]: Accepted password for alex from 82.137.13.73 port 20424 ssh2
Feb 18 15:17:35 alex-P55A-UD3R sshd[6721]: pam_unix(sshd:session): session opened for user alex by (uid=0)
Feb 18 15:17:50 alex-P55A-UD3R passwd[6977]: pam_unix(passwd:chauthtok): password changed for alex
Feb 18 15:17:52 alex-P55A-UD3R gnome-keyring-daemon[6980]: Gck: gck_module_new: assertion `funcs' failed
Feb 18 15:17:52 alex-P55A-UD3R gnome-keyring-daemon[6980]: module_instances: assertion `module' failed
Feb 18 15:17:52 alex-P55A-UD3R gnome-keyring-daemon[6980]: egg_error_message: assertion `error' failed
Feb 18 15:17:52 alex-P55A-UD3R gnome-keyring-daemon[6980]: couldn't find secret store module: (unknown)
Feb 18 15:17:52 alex-P55A-UD3R gnome-keyring-daemon[6980]: lookup_login_keyring: assertion `GCK_IS_SESSION (session)' failed
Feb 18 15:17:52 alex-P55A-UD3R gnome-keyring-daemon[6980]: create_credential: assertion `GCK_IS_SESSION (session)' failed
Feb 18 15:17:52 alex-P55A-UD3R gnome-keyring-daemon[6980]: egg_error_message: assertion `error' failed
Feb 18 15:17:52 alex-P55A-UD3R gnome-keyring-daemon[6980]: couldn't create new login credential: (unknown)
Feb 18 15:17:52 alex-P55A-UD3R passwd[6977]: gkr-pam: couldn't change password for the login keyring: the passwords didn't match.
............
Feb 18 17:41:52 alex-P55A-UD3R sshd[6721]: pam_unix(sshd:session): session closed for user alex

```

No further suspicious activity in that log (well, except my futile attempts at loging in), but it looks like this fella had root privileges on my machine for an hour and a half. I assume he used some manner of script so god knows what he could have done in that time.

Is there any way of knowing what he has done in that time? What is your advice in this situation?

---

### Post by winh8r on 2012-02-18
In order to prevent a future re-occurence I would suggest a look at this thread which contains all the relevant information you will need:

[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")


I hope this is of some help to you.

---

### Post by Lisiano on 2012-02-20
I'd recommend the following, ***_[SIZE="3"][COLOR="Red"]DISCONNECT THE BOX FROM THE NETWORK[/COLOR][/SIZE]_*** and probably disconnect everything else that was on the network. Reason for disconnecting is because while he might have lost your password for now, but there is no reason not to think he might have installed a backdoor on your box. You know the saying from Assassins Creed, "Nothing is true, everything is permitted". Basically, you will have to examine your box for any modifications, look at everything done past that timestamp (Feb 18 15:17:35). Although if you aren't really technically inclined or don't exactly know how to read code or aren't good with scripting, I'd advice to look if he has modified any files in your home and assume all passwords to anything you had stored (Facebook, Bank accounts, Email accounts) are compromised, I'm not trying to say they are, it's precaution, change those passwords ASAP. After examining home and if you don't find anything suspicious (Like some new files, a modified ~/.bashrc, anything) you should reinstall your system (You don't have to, just easier to do if you aren't good with code or post-break-in work). If you DO find something suspicious, still reinstall the system but don't use the same username so you don't execute the .bashrc. Post it here or somewhere like pastebin. Do the same for every other box you had connected. (Like a laptop with SSH or another desktop)

To sum it all up, examine the system, remove any traces of any backdoors, secure your system.

Good luck, you'll need it.


EDIT: You should also report the IP to the ISP of the attacker, Google whois to find the ISP and the abuse email for it. Send the whole /var/log/auth.log file for the bruteforce and any other evidence you can find. Also you should contact your own ISP and report this incident so that they can block that person from their network and take appropriate actions toward the other ISP.

---

### Post by mastablasta on 2012-02-20
> **Lisiano said:**
>  
EDIT: You should also report the IP to the ISP of the attacker, Google whois to find the ISP and the abuse email for it. Send the whole /var/log/auth.log file for the bruteforce and any other evidence you can find. Also you should contact your own ISP and report this incident so that they can block that person from their network and take appropriate actions toward the other ISP.
 
 
ofcourse if attacker spoofed the IP or if they hacked on another persons wi-fi an innocent person could be blamed...

---

### Post by Lisiano on 2012-02-20
> **mastablasta said:**
> ofcourse if attacker spoofed the IP or if they hacked on another persons wi-fi an innocent person could be blamed...

Indeed. Except IP spoofing is impossible when you need to receive incoming packets (SSH), unless you meant a proxy, which are easily traceable by the proxy owner. And regarding a innocent 3rd party, I consider all activity that is going on a private network to be the responsibility of the network owner so while the innocent person is not to blame here, he did allow a malicious user on his/her network.

Personally I don't even allow anyone on my WiFi unless I personally know them for a considerable amount of time, else if they want internet, I give them access to my PC under the Guest account and keep an eye on everything they do.

Either way, It's the OPs decision if he wishes to report the IP or not. Personally I'm 100% for the report.

---

