---
title: "Beginner needs advice on server"
date: 2020-03-06
forum: New to Ubuntu
---

### Post by jerthemost on 2020-03-06
[COLOR=#000000][FONT=Arial]I am new to servers but not new to computers and technology, been at it for 60 years. I wish to set up my own IOT type platform and have signed up for a VPS to experiment with and learn. I have a choice of Debian, Ubuntu, and Centos for an OS. Also with Lamp options. I have tried Ubuntu 18.04 Lamp and 16.04 Lamp. I need an easy to use a control panel or GUI like CPcontrol panel but have not been able to get one installed and working. If I use Centos I can get CP but they charge an extra $11 per month. I would like to save some money if possible. I wish to install APPS such as Grafana, MQTT, Node-Red etc. I need a simple file manager, php-myadmin, MySQL, a way to add PHP script pages, and some easy way to get to and run these APPs. Being able to use a Wordpress front page website for demo purposes would be a plus. Does anyone have any ideas what I should do? I have spent weeks on it and gotten nowhere. Thanks in advance.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by TheFu on 2020-03-08
Most people here don't do what you are attempting.

a) we use VMs to try out stuff on our own hardware. No need to rent a VPS when 15G of storage and almost any desktop of Core2 Duo or better made the last 12 yrs will easily provide a power VM host.

b) I don't use LAMP, but many others here do - well, that isn't exactly true. I use LNPP  or LNPR .... Linux Nginx Postgress Perl/Ruby.

c) cPanel, webmin, myphpadmin aren't popular with anyone here.  Everyone has their own reasons. To me, they are just added security risks.  None, under any situation, should be available over the internet.  If you must use them, then only allow access from localhost, so an ssh-tunnel is mandatory to access those tools.

d) Never heard of any of those specific applications.  Paying for software is rarely done. It just isn't needed  and seldom provides value.

e) file management happens over ssh. Anything else is too slow, and clumsy.

f) Be very careful using wordpress addons. There are over 1 million hacked WP servers on the internet right now, mostly due to not staying patched AND choosing low-quality addons.

As for deploying your software to a remote server, automate that stuff. Use an existing tool like ansible or use CI methods or just script all the steps. Probably don't want too many dev tools on the server. Why provide any tools to the crackers who break in?

Hopefully, some of the WP gurus here will chime in.  We see people all the time who come with hacked servers seeking guidance.  The time to mitigate security issues is at design time, not after the hacks already started.

[https://ubuntuforums.org/showthread.php?t=2430231](https://ubuntuforums.org/showthread.php?t=2430231)  from SeijiSensei

A reasonable, free, no-hassle, Linux guide/ref: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  This isn't for admins. It is for people moving towards power-user skills.

Automation, consistency, reproducibility are the main goals. Constantly doing everything better across all your servers.

Sorry, I'm not any real help for what you seek.

---

### Post by mastablasta on 2020-03-11
i don't know about those apps. if they have support for Ubuntu they can easily be installed. if not, then you need to compile from source.

i use Ajenti for some GUI assistance when needed. Although mostly i just use the terminal to connect to server, while Filezilla provides a sFTP capable file manager.

there are also other alternatives to cpanel:
[https://blog.ssdnodes.com/blog/cpanel-alternatives-vps/](https://blog.ssdnodes.com/blog/cpanel-alternatives-vps/)

> **TheFu said:**
> 
Hopefully, some of the WP gurus here will chime in.  We see people all the time who come with hacked servers seeking guidance.  The time to mitigate security issues is at design time, not after the hacks already started.



the attacks are constant and hack are done fast. i was 2 days late with patching an add-on i didn't even use and got hacked. 

to help you out wordfence and sucuri are a good combo. but even more important are regular, automated, safe backups.

---

### Post by SeijiSensei on 2020-03-11
> **TheFu said:**
> [https://ubuntuforums.org/showthread.php?t=2430231](https://ubuntuforums.org/showthread.php?t=2430231)  from SeijiSensei

Thanks for the shout-out!  The specific post in that thread is this one:
[https://ubuntuforums.org/showthread.php?t=2430231&p=13902583&viewfull=1#post13902583](https://ubuntuforums.org/showthread.php?t=2430231&p=13902583&viewfull=1#post13902583)

As TheFu says, most of us manage servers from the command prompt, not via some form of GUI or web interface.  I don't know anything about the apps you listed, so I can't help with that.  If you're on Ubuntu, I recommending installing the LAMP package:
```
sudo apt install lamp-server^
```
which ensures that all the dependencies and interstitial packages are installed.

If the server has openssh-server installed, you can move files back and forth with a variety of tools that use some form of scp or sftp.  I'm a Kubuntu user, and my file manager, Dolphin, supports "fish://" and "sftp://" URLs as targets.  So on my desktop computer I can open Dolphin, then split the window and point the second window at "fish://myserver.example.com/."  Then I can drag-and-drop files to or from the server.  From Windows machines, [WinSCP]("https://winscp.net/eng/index.php") is a good sftp client.

WordPress is handy for that task as well. You can upload files via a web browser open to your WP site.

---

