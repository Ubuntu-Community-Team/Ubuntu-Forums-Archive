---
title: "Unauthorised access"
date: 2018-03-20
forum: New to Ubuntu
---

### Post by manish-mu on 2018-03-20
Hello,

I am fairly new to Ubuntu and I am mining cryptocurrencies. I recently noticed that commands that I did not type have been executed and some files have been changed. I googled a bit to find out commands I could use to check the issue myself and was directed to .bash_history and /var/log/auth.log files. On /var/log/auth.log I found out that sessions have been initiated through cron (may be I making a mistake here! I am not sure).

I am attaching an extract of my /var/log/auth.log file (for the time I believe the unauthorised access happened) and the jobs scheduled through cron (which i didn't configure!). Can someone please explain to me how this happened?
 
using the solution from [https://stackoverflow.com/questions/134906/how-do-i-list-all-cron-jobs-for-all-users](https://stackoverflow.com/questions/134906/how-do-i-list-all-cron-jobs-for-all-users), I get these jobs on cron:

```
mi  h  d  m  w  user  command
25  6  *  *  *  root  /etc/cron.daily/0anacron
25  6  *  *  *  root  /etc/cron.daily/apport
25  6  *  *  *  root  /etc/cron.daily/apt-compat
25  6  *  *  *  root  /etc/cron.daily/bsdmainutils
25  6  *  *  *  root  /etc/cron.daily/chrome-remote-desktop
25  6  *  *  *  root  /etc/cron.daily/cracklib-runtime
25  6  *  *  *  root  /etc/cron.daily/dpkg
25  6  *  *  *  root  /etc/cron.daily/google-chrome
25  6  *  *  *  root  /etc/cron.daily/logrotate
25  6  *  *  *  root  /etc/cron.daily/man-db
25  6  *  *  *  root  /etc/cron.daily/mlocate
25  6  *  *  *  root  /etc/cron.daily/passwd
25  6  *  *  *  root  /etc/cron.daily/popularity-contest
25  6  *  *  *  root  /etc/cron.daily/update-notifier-common
25  6  *  *  *  root  /etc/cron.daily/upstart
30  7  *  *  *  root  test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null
44  4  *  *  *  root  test -x /etc/cron.daily/popularity-contest && /etc/cron.daily/popularity-contest --crond
47  6  *  *  7  root  /etc/cron.weekly/0anacron
47  6  *  *  7  root  /etc/cron.weekly/fstrim
47  6  *  *  7  root  /etc/cron.weekly/man-db
47  6  *  *  7  root  /etc/cron.weekly/update-notifier-common
52  6  1  *  *  root  /etc/cron.monthly/0anacron
```

I feel it is through the chrome remote desktop (I don't know). I have also remote desktop sharing enabled.

Any help will be highly appreciated. Thank you.

---

### Post by TheFu on 2018-03-20
cron is normal. I don't see anything undesirable  in the list.  Nothing odd, though I wouldn't load anything from google on my systems, many other people choose to do that.

"sessions" aren't from cron. They are tied to user logins.  cron is just spawning programs, not sessions.

If you have remote desktop enabled, how it is secured? If you don't know, it is best to disable it until you figure that out.

---

### Post by manish-mu on 2018-03-20
@TheFu, Thanks for the going through my issue.

Yes, I know cron would not initiate any sessions but I was wondering probably the jobs scheduled to run under cron are doing so. Anyways.. I have uninstalled chrome and chrome remote desktop just to be sure.

I had unchecked the option where users had to authenticate every time they connect to the machine. I have enabled this option now. I have not disabled remote desktop sharing for the time being. I have also changed by passwds and plan to monitor for the 24 hours.

---

### Post by TheFu on 2018-03-20
No problem.

If your password is 20+ characters, mostly random, not following any words, keyboards, number patterns and doesn't begin with uppercase or end with numbers or punctuation, it should be fine.

Passwords really shouldn't be the main form of security for anything.  If you let an attacker have access to even attempt a login, then you've failed already.  Do not leave a service open to the entire world if only 1 other location needs access.  Block everywhere, then allow only the 1 place that needs access to every get to a login.

On the internet, if you are using passwords, then you've already failed at security.  But that is a different question, completely.  In short, use keys, not passwords. Places that require passwords, using something randomly created that is 40+ characters and you never need to type, if you use a password manager.  I couldn't tell you **any** of my online login  credentials. Might not be able to type most of them either.  Some of my login usernames are random too - which I don't know. For example, none of my bank accounts use logins that I know.

---

### Post by manish-mu on 2018-03-21
@TheFu, thanks again.

I was intrigued by the same things you said in your last reply though. Most of it did make sense but strategy you mentioned are alien to me :-) (Being a beginner is exciting and frustrating at the same time!). Could please spare some time to explain to me using some of the methods/tools/software you use not to use any passwords or use 20+ character passwords? I am a mac user as well and and I am familiar to keychain. Does it fall under the approach to handle passwords and usernames you mentioned?

Thank you.

Btw, no unauthorised access today, which is good.

---

### Post by TheFu on 2018-03-21
ssh - use ssh-keygen and ssh-copy-id.  ssh is used 98% of the time I need to remote into other systems. This uses key-based authentication. ssh is secured with dynamic firewall tools which see a failure and block that port.  If you don't travel, you can just block all external access, except from the places you usually are (home/work/library/cafe).
ssh provides sftp, scp, rsync, sshfs, SOCKS and lots of other secure, remote, access tools.

keepassXC - my password manager. It supports 2FA. The DB it uses is cross-platform, so pick 1 system to make changes on, and consider all the others as read-only copies. This is a mental thing, not something enforced, so if you are traveling and need to make changes, just be certain to push the updated DB back to the main system BEFORE any automatic push overwrites.  I use rsync nightly to push my DB to 6 other systems. There are 1,001 other uses for password managers.

openvpn/libreSwan - Sometimes a full VPN is easier than ssh, especially for smartphones and tablets to provide access to your home network.  These use 4K keys and 256-AES encryption.

LUKS - partition encryption. All portable devices should be encrypted. Period.  Things that leave your safe locations can be lost or stolen.

Versioned backups are mandatory.  Being able to see what changed between yesterday and today or last week or last month is very helpful in determining what any attacker may have done. Don't use network-storage for backups.  Use a client/server backup tool - based on ssh and librsync.  This will prevent those crypto-locker malware attacks which encrypt all storage (local and networked) they can access.  When using encrypted storage, backups are the only effective way to recover from corrupted or failed storage. Backups also make system updates much less risky.  Also, if encrypted storage has a logical failure, the backup will be the only way to restore data.

Read the sticky threads at the top of the _Security_ forum here.

Read the _Basic Ubuntu Security_ wiki page and follow the links.

If you want a deeper understanding, read Bob Toxen's book on Linux Security. Any Unix security book should begin with the basic ideas.  Least access require is the cornerstone. A userid should have the least permissions needed to accomplish required tasks. It begins with file/directory permissions and works through disabling unwanted/unneeded services and ends with restricting network access that isn't necessary.

Don't enable remote-anything without understanding the security implications.  Just because something works, doesn't mean it is secure.  Basically, with ssh and nothing else allowed, you only need 1 tcp port open and there are good methods to secure that access.  Everything else can either use ssh directly or go through an ssh-tunnel.  Have your router perform port translation for ssh from a high-port externally to the default port internally.

Don't believe marketing hype around security. It is mostly lies, but with much over-simplification.  Beware "cloudy" services. Beware IoT devices that don't work without an internet connection when you don't need anything from the internet.  Those internet connected thermostats come to mind.  When you are in an ice storm, without internet, having heat would be good, right?

Use the firewall.  Setup DENY INBOUND by default and only open the exact port you need FROM the exact remote location you must allow. This is basic security.  Much more secure and restrictive firewall rule setups are possible. The cost is convenience.

Learn Linux from the shell/CLI, not the GUI. The GUIs change every 3 yrs. The non-GUI methods last for decades and don't change much at all.  Every popular, non-Windows OS, is based on Unix. Learning what is under the GUI will pay off greatly the rest of your life. 

Prefer tools that follow standards over proprietary tools that hold the data hostage. This is especially important for security tools.

That should be enough to get started.

A few more links:
* [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)
* [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

---

### Post by manish-mu on 2018-03-21
Thanks a lot! Much appreciated.:)

Time to learn the basics.

---

