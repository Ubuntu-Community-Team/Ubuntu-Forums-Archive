---
title: "Message I get when shutting down"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by Qianling on 2012-08-27
Hi, I see a message that starts with "Cannot write to..." after I initiate shutdown, but I can't read the rest of it because the message disappears after a second. My laptop still starts and shuts down as usual, but is this normal? Should I be concerned? 

If its abnormal, how can I see the full message and save it to post here for help?

Many thanks in advance. :)

--
Qianling

---

### Post by Szor3n on 2012-08-27
It sounds like you might have messed up write permissions.  Most likely that's not normal, as I haven't encountered it.  You could start by searching you logs for "Can't write" and see what comes up.

---

### Post by Qianling on 2012-08-27
Could you be more specific as to "searching your logs" please?

a) What's the name of the log file?

b) Where do I find it?

Ubuntu's file system is quite different from Windows, and I don't think I know where to start looking in Windows either! :P

Specific step-by-step instructions would be greatly appreciated.

--
Qianling

---

### Post by Szor3n on 2012-08-27
I'm sorry, I was kind of vague. 

Your system logs are stored in /var/log/

and you can search them by opening a terminal, and typeing:

```
grep -r "string to search for" /var/log/
```

This will print out all the files and lines that have that string in it.  Hopefully that will help point you in the right direction.

---

### Post by Qianling on 2012-08-28
When I typed that, I got this:

```

joan@Lenni:~$ grep -r "string to search for" /var/log/
grep: /var/log/speech-dispatcher: Permission denied
grep: /var/log/installer/partman: Permission denied
grep: /var/log/installer/debug: Permission denied
grep: /var/log/installer/version: Permission denied
grep: /var/log/installer/casper.log: Permission denied
grep: /var/log/installer/syslog: Permission denied
grep: /var/log/samba/cores: Permission denied
grep: /var/log/lightdm/x-1-greeter.log.old: Permission denied
grep: /var/log/lightdm/x-0-greeter.log: Permission denied
grep: /var/log/lightdm/x-2-greeter.log: Permission denied
grep: /var/log/lightdm/x-2.log: Permission denied
grep: /var/log/lightdm/x-0-greeter.log.old: Permission denied
grep: /var/log/lightdm/x-1.log: Permission denied
grep: /var/log/lightdm/lightdm.log: Permission denied
grep: /var/log/lightdm/x-2-greeter.log.old: Permission denied
grep: /var/log/lightdm/x-0.log: Permission denied
grep: /var/log/lightdm/x-1-greeter.log: Permission denied
grep: /var/log/upstart/container-detect.log.3.gz: Permission denied
grep: /var/log/upstart/procps-virtual-filesystems.log: Permission denied
grep: /var/log/upstart/procps-virtual-filesystems.log.3.gz: Permission denied
grep: /var/log/upstart/console-setup.log.1.gz: Permission denied
grep: /var/log/upstart/container-detect.log.1.gz: Permission denied
grep: /var/log/upstart/lightdm.log.2.gz: Permission denied
grep: /var/log/upstart/procps-static-network-up.log: Permission denied
grep: /var/log/upstart/procps-virtual-filesystems.log.2.gz: Permission denied
grep: /var/log/upstart/modemmanager.log.3.gz: Permission denied
grep: /var/log/upstart/procps-static-network-up.log.4.gz: Permission denied
grep: /var/log/upstart/ureadahead.log.1.gz: Permission denied
grep: /var/log/upstart/hybrid-gfx.log.1.gz: Permission denied
grep: /var/log/upstart/modemmanager.log.2.gz: Permission denied
grep: /var/log/upstart/hybrid-gfx.log: Permission denied
grep: /var/log/upstart/procps-static-network-up.log.2.gz: Permission denied
grep: /var/log/upstart/console-setup.log.4.gz: Permission denied
grep: /var/log/upstart/console-setup.log.2.gz: Permission denied
grep: /var/log/upstart/hybrid-gfx.log.4.gz: Permission denied
grep: /var/log/upstart/container-detect.log: Permission denied
grep: /var/log/upstart/ureadahead.log.2.gz: Permission denied
grep: /var/log/upstart/hybrid-gfx.log.2.gz: Permission denied
grep: /var/log/upstart/lightdm.log.1.gz: Permission denied
grep: /var/log/upstart/procps-static-network-up.log.1.gz: Permission denied
grep: /var/log/upstart/modemmanager.log.4.gz: Permission denied
grep: /var/log/upstart/ureadahead.log.3.gz: Permission denied
grep: /var/log/upstart/ureadahead.log.4.gz: Permission denied
grep: /var/log/upstart/modemmanager.log: Permission denied
grep: /var/log/upstart/cups.log.1.gz: Permission denied
grep: /var/log/upstart/rsyslog.log.1.gz: Permission denied
grep: /var/log/upstart/ureadahead.log: Permission denied
grep: /var/log/upstart/rsyslog.log: Permission denied
grep: /var/log/upstart/procps-virtual-filesystems.log.1.gz: Permission denied
grep: /var/log/upstart/rsyslog.log.3.gz: Permission denied
grep: /var/log/upstart/console-setup.log: Permission denied
grep: /var/log/upstart/rsyslog.log.2.gz: Permission denied
grep: /var/log/upstart/console-setup.log.3.gz: Permission denied
grep: /var/log/upstart/container-detect.log.4.gz: Permission denied
grep: /var/log/upstart/procps-static-network-up.log.3.gz: Permission denied
grep: /var/log/upstart/alsa-restore.log.2.gz: Permission denied
grep: /var/log/upstart/procps-virtual-filesystems.log.4.gz: Permission denied
grep: /var/log/upstart/alsa-restore.log.1.gz: Permission denied
grep: /var/log/upstart/hybrid-gfx.log.3.gz: Permission denied
grep: /var/log/upstart/rsyslog.log.4.gz: Permission denied
grep: /var/log/upstart/container-detect.log.2.gz: Permission denied
grep: /var/log/upstart/modemmanager.log.1.gz: Permission denied
grep: /var/log/btmp: Permission denied
joan@Lenni:~$ 

```I opened /var/log and went through the files I could see  there,  but after searching the files I could not find the line "could  not  write" in any of them. 

[IMG]http://i.imgur.com/zLiHEl.png[/IMG]

I'm quite sure "could not write" are the 1st 3 words I see, I shall keep my eyes peeled for the other lines on shutdown.

Meanwhile, are there other ways of finding out what's going on when I shut down the laptop?

--
Qianling

---

### Post by Miljet on 2012-08-28
> grep -r "string to search for" /var/log/
You were supposed to replace "string to search for" with the actual words you are looking for. In other words:
```
grep -r "could not write" /var/log/
```

It might also help to use sudo so grep can see inside files owned by root.
```
sudo grep -r "could not write" /var/log
```

---

### Post by d4m1r on 2012-08-28
Are you noticing any other issues with your Ubuntu install? If not, it is probably normal. This has been an ongoing issue where too much information is being shown in the UI during a normal shutdown procedure....The purple screen is supposed to hide all of it (its supposed to run in the background) but randomly disappears and you see exactly what it is doing.

---

### Post by Bashing-om on 2012-08-28
Qianling ;

 Hi... I do not know that one can catch the shutdown messages in all versions.

I can in my 10.04 //have to edit your grub file to do so. One only has a 3 second window to pause the output.

  advise if you want to attempt it in your version. (it is easy, but one can mess up system if not careful with the edits[ALWAYS make backup of any file you edit first])...

and nope, once the system starts shutting down, I know of no way to capture the output.

[INDENT]regards BDQ
[/INDENT]

---

### Post by Qianling on 2012-08-29
Szor3n and Miljet: Oops! I should have known that.

What I got was this:

```

joan@Lenni:~$ sudo grep -r "could not write" /var/log
[sudo] password for joan: 
/var/log/auth.log:Aug 29 21:56:28 Lenni sudo:     joan : TTY=pts/0 ; PWD=/home/joan ; USER=root ; COMMAND=/bin/grep -r could not write /var/log

```Which I'm guessing means I found nothing. :O


d4m1r: My install runs normally. I was worried only because the first three words I noticed on the screen after I initiated shut down, and before the purple screen comes up (there's a slight delay) happened to be "Could not write..."

Since it's running properly, I'll take your word for it that it's perfectly normal! :)


Bashin-om: Thanks for your reply. Due to my extremem noobishness at the moment I'd rather not take the chance! :P


Thanks for the replies, guys. I guess it's case closed for now since nothing is actually wrong with my system.

---

