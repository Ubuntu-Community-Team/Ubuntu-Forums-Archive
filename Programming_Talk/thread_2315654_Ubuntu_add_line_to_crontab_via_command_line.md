---
title: "Ubuntu: add line to crontab via command line"
date: 2016-03-01
forum: Programming Talk
---

### Post by erotavlas on 2016-03-01
Hi,
I wrote this script in order to add a line to root crontab if it does not already contain such line. The script also checks if the crontab is empty. Is there a better way to achieve this?
```

cronList=$(sudo crontab -u root -l)
if [ $(echo $cronList | grep -c "@weekly /home/user/command") -eq 0 ]; then
    if [ -z "$cronList" ]; then
        echo "@weekly /home/user/command" | sudo crontab -u root -
    else
        (sudo crontab -u root -l; echo "@weekly /home/user/command" ) | sudo crontab -u root -
    fi
fi
```
Thank you

---

### Post by TheFu on 2016-03-02
I would use ansible.

Plus there are multiple "root" crontabs, so it would really just be easier to drop a file into /etc/cron.weekly/ if you need it to run weekly. I'd use ansible for that too, after all if you went to the trouble to script this, then you probably need to manage more than a few systems. Ansible is the easiest of those tools and really powerful.

[https://docs.ansible.com/ansible/cron_module.html](https://docs.ansible.com/ansible/cron_module.html) will help. If you are completely new to ansible, check out their "quick start video."

Ansible handles all those little details that are a hassle for us. If the result wouldn't change the file, then nothing is done.

---

### Post by Bucky Ball on 2016-03-02
*Thread moved to **Programming Talk**.*

---

### Post by erotavlas on 2016-03-03
> **TheFu said:**
> I would use ansible.

Plus there are multiple "root" crontabs, so it would really just be easier to drop a file into /etc/cron.weekly/ if you need it to run weekly. I'd use ansible for that too, after all if you went to the trouble to script this, then you probably need to manage more than a few systems. Ansible is the easiest of those tools and really powerful.

[https://docs.ansible.com/ansible/cron_module.html](https://docs.ansible.com/ansible/cron_module.html) will help. If you are completely new to ansible, check out their "quick start video."

Ansible handles all those little details that are a hassle for us. If the result wouldn't change the file, then nothing is done.

Thank you, but I prefer to use standard crontab.
I do not understand why my script command.sh is not executed at boot. Inside my script I log into a text file the execution time echo "Updating script ran successful: $(date)" >> /home/$user/updating.log. If I run manually sleep 10m && sudo /home/$user/command.sh from terminal it works.
```

user=$(sudo logname)
echo "Adding crontab job"
cronList=$(sudo crontab -u $user -l)
cronCommand="@reboot sleep 10m && sudo /home/$user/command.sh"
if [ $(echo $cronList | grep -c "$cronCommand") -eq 0 ]; then
    if [ -z "$cronList" ]; then
        echo $cronCommand | sudo crontab -u $user -
    else
        (sudo crontab -u $user -l; echo $cronCommand ) | sudo crontab -u $user -
    fi
fi

```
If I add the script to root with sudo crontab -u root it does not output log into /home/$user/updating.log since the $user is the root instead of the administrator user.
How can I execute my script in such a way the $user is not the root user even if I need root previlegios?
Thank you

---

### Post by TheFu on 2016-03-03
We have a misunderstanding.
     **Ansible doesn't replace cron.** It is a systems management tool to manage configurations and settings for all sorts of things - not just cron, but **anything** on a system. 

That script is overly complicated. All the sudo stuff just isn't needed that I can tell.

Environment variables are case-sensitive - so LOGNAME (which is set) is not the same a logname.

Assume user is "peter".  You want 
```
@reboot sleep 10m && sudo /home/peter/command.sh
```
placed into a file /etc/cron.d/peter .  Ok, you don't want that exactly, since cron files in this directory are slightly different. Also, you want it run a root, not peter.  BTW - placing a command to be run as root into an end user's HOME is crazy - extremely bad idea from a security point.  Basically, they would OWN the system. BAD, BAD, BAD idea.

This is probably what you want in that file:
```
@reboot  root /bin/sleep 10m && if [ -x /usr/local/bin/peter-command.sh ] ; then /usr/local/bin/peter-command.sh >/dev/null; fi
```

Worth mentioning - /usr/local/bin/peter-command.sh needs to have execute permissions.

---

### Post by erotavlas on 2016-03-03
Yes, maybe I did not explain precisely.
I have a script that requires sudo to be run (this is the reason for which I have to put in crontab -u root), but at the same time it requires to know the administrator user path in order to store some files, output log and to update the script itself (this is the reason for which I have to put in crontab -u user). If I run my script from terminal with sudo ./myscript the logname it will give the current logged user and it works well.
> 
Environment variables are case-sensitive - so LOGNAME (which is set) is not the same a logname.

For me LOGNAME does not work.

> @reboot  root /bin/sleep 10m && if [ -x /usr/local/bin/peter-command.sh ] ; then /usr/local/bin/peter-command.sh >/dev/null; fi

It should work. What is the best way in order to:
1) Download temp files that should not remove by reboot and that I need to check and compile where to store version v.x of the script.
2) Log properly script execution and output.

Thank you

---

### Post by TheFu on 2016-03-03
Thanks for the slight clarification.

a) sudo  is the same as running as root, but with the user's environment. same-same. There is NOTHING special about sudo. Any command you run with sudo /path/to/command.sh .... can be run by root - it just needs to correct environment - usually PATH, LD_LIBRARY_PATH and perhaps something extra like JAVA_HOME (if it is a java program). Those settings can easily be placed inside the script to be run.

Ansible is NOT installed on the remote system and doesn't leave any footprint behind, hence why I'm still pushing it for this.  It can copy files from the local workstation to the remote server or tell the remote server to grab those files from elsewhere using HTTP, FTP, SCP, methods.  I would push the files, pre-compiled, to the remote server thru ansible from my workstation, but you can scp/sftp them too, which it trivial as well.  To pull files, I'd use curl or git or some other version control tool.

Compiling on the remote server isn't something I'd do, but you can. Leaving a compiler on a server is a security liability. Best NOT to do that.  By compiling, I assume you mean running gcc with a C or C++ or java program?

Where to store the script on the remote server?  /usr/local/bin/ - that is what that directory is for. It doesn't get removed on a normal install.  If you are booting from read-only media, then that is a completely different question, but besides that, /usr/local/ is where manually installed things belong.  There is a place for everything on Unix/Linux systems. The directory structure purpose is outlined in standards:  [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html)

Cron will email the output of any job run to the configured userid based on MAILTO environment.  Of course, the MTA needs to be configured, otherwise it will fill up /var/spool/mail/.  This is normal for Unix systems. Expected behavior is important.  If you want logging to go into syslog, then  create that in the script.  Popular scripting languages all have logging modules - python, perl, ruby all do, but those modules probably are not pre-installed on systems.
Perl: [http://search.cpan.org/~athomason/Log-Syslog-Fast-0.65/lib/Log/Syslog/Fast.pm](http://search.cpan.org/~athomason/Log-Syslog-Fast-0.65/lib/Log/Syslog/Fast.pm)
Bash: [http://www.cyberciti.biz/tips/howto-linux-unix-write-to-syslog.html](http://www.cyberciti.biz/tips/howto-linux-unix-write-to-syslog.html)

All of the things you described are why Ansible was created.  Ansible doesn't get installed on the remote system. It runs from a workstation and helps control 5-50,000 other systems.  Of course, it helps if you already know how to manually manage the systems how you need, following best practices. Learning that takes time and experience, which is happening now.  

In the old days, we wrote scripts like you are trying to do now. Every system was a little different and every "site" had their own scripts, which made local knowledge about how-to do things critical.  Then the marketing guys decided to name what Unix admins had been doing for decades - they called it "devops" and a few companies have built businesses around this - Puppet, Chef, Ansible, Salt-Stack, Rexify and others.  Having a standard way to perform common tasks is a good idea.  Those are the best-of-breed tools for this.

I've looked at each of these tools over the years - really wanted to like Puppet - the setup was too complicated and involved. Same for Chef, cf-engine too. Plus those required ruby to be installed and an agent on every remote system. That was a non-starter for me.  Salt also requires a remote "minion" installed on every managed server - non-starter.  

Ansible's requirements are already installed since 10.04 - the system python.  The tool was created by an ex-puppet employee to be easier, simpler, flexible and fast.   Your remote boxes already have the minimal requirements for ansible. Nothing to install on them.  On your workstation, you either *apt-get install ansible* or (preferred), **git clone** the current repo for ansible stable.   [https://github.com/ansible/ansible](https://github.com/ansible/ansible)

Ansible is free form, but the best practices guides and methods allow tremendous reuse from task to task, system to system, site to site.  Using the standard directories for roles, tasks, settings, notifications means being able to go from site-to-site and already understanding where files are and what they do. It  is standardization of scripts like yours.  For one system and one script like this, I wouldn't bother with ansible, but you seem to have multiple systems and perhaps multiple userids to address. THAT is where ansible shines.

Pushing files unchanged - easy. Pushing files based on a template with slight changes - easy. Installing packages, updating config files, restarting services - all easy. Managing permissions, directories, and only doing something when needed - easy.   I wrote all of this trying to get you to NOT reinvent the WHEEL.  The stuff you want to do has been solved already, ansible is that solution.

I have a script I want installed on every box I manage:
```
---

- name: Create /usr/local/bin/kernel-cleanup
  copy: src=files/kernel-cleanup dest=/usr/local/bin/kernel-cleanup
        mode=0700 owner=root group=root

```
Simple. Directories will be created as needed. File permissions are set.. 
[https://stackoverflow.com/questions/28023697/ansible-creating-working-cronjobs](https://stackoverflow.com/questions/28023697/ansible-creating-working-cronjobs) has an example ansible crontab task. 

Hope this makes sense.  Don't just believe me.  [https://valdhaus.co/writings/ansible-vs-shell-scripts/](https://valdhaus.co/writings/ansible-vs-shell-scripts/) makes the same argument to use ansible instead of scripting.

---

### Post by erotavlas on 2016-03-07
> **TheFu said:**
> Thanks for the slight clarification.

a) sudo  is the same as running as root, but with the user's environment. same-same. There is NOTHING special about sudo. Any command you run with sudo /path/to/command.sh .... can be run by root - it just needs to correct environment - usually PATH, LD_LIBRARY_PATH and perhaps something extra like JAVA_HOME (if it is a java program). Those settings can easily be placed inside the script to be run.

Ansible is NOT installed on the remote system and doesn't leave any footprint behind, hence why I'm still pushing it for this.  It can copy files from the local workstation to the remote server or tell the remote server to grab those files from elsewhere using HTTP, FTP, SCP, methods.  I would push the files, pre-compiled, to the remote server thru ansible from my workstation, but you can scp/sftp them too, which it trivial as well.  To pull files, I'd use curl or git or some other version control tool.

Compiling on the remote server isn't something I'd do, but you can. Leaving a compiler on a server is a security liability. Best NOT to do that.  By compiling, I assume you mean running gcc with a C or C++ or java program?

Where to store the script on the remote server?  /usr/local/bin/ - that is what that directory is for. It doesn't get removed on a normal install.  If you are booting from read-only media, then that is a completely different question, but besides that, /usr/local/ is where manually installed things belong.  There is a place for everything on Unix/Linux systems. The directory structure purpose is outlined in standards:  [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html)

Cron will email the output of any job run to the configured userid based on MAILTO environment.  Of course, the MTA needs to be configured, otherwise it will fill up /var/spool/mail/.  This is normal for Unix systems. Expected behavior is important.  If you want logging to go into syslog, then  create that in the script.  Popular scripting languages all have logging modules - python, perl, ruby all do, but those modules probably are not pre-installed on systems.
Perl: [http://search.cpan.org/~athomason/Log-Syslog-Fast-0.65/lib/Log/Syslog/Fast.pm](http://search.cpan.org/~athomason/Log-Syslog-Fast-0.65/lib/Log/Syslog/Fast.pm)
Bash: [http://www.cyberciti.biz/tips/howto-linux-unix-write-to-syslog.html](http://www.cyberciti.biz/tips/howto-linux-unix-write-to-syslog.html)

All of the things you described are why Ansible was created.  Ansible doesn't get installed on the remote system. It runs from a workstation and helps control 5-50,000 other systems.  Of course, it helps if you already know how to manually manage the systems how you need, following best practices. Learning that takes time and experience, which is happening now.  

In the old days, we wrote scripts like you are trying to do now. Every system was a little different and every "site" had their own scripts, which made local knowledge about how-to do things critical.  Then the marketing guys decided to name what Unix admins had been doing for decades - they called it "devops" and a few companies have built businesses around this - Puppet, Chef, Ansible, Salt-Stack, Rexify and others.  Having a standard way to perform common tasks is a good idea.  Those are the best-of-breed tools for this.

I've looked at each of these tools over the years - really wanted to like Puppet - the setup was too complicated and involved. Same for Chef, cf-engine too. Plus those required ruby to be installed and an agent on every remote system. That was a non-starter for me.  Salt also requires a remote "minion" installed on every managed server - non-starter.  

Ansible's requirements are already installed since 10.04 - the system python.  The tool was created by an ex-puppet employee to be easier, simpler, flexible and fast.   Your remote boxes already have the minimal requirements for ansible. Nothing to install on them.  On your workstation, you either *apt-get install ansible* or (preferred), **git clone** the current repo for ansible stable.   [https://github.com/ansible/ansible](https://github.com/ansible/ansible)

Ansible is free form, but the best practices guides and methods allow tremendous reuse from task to task, system to system, site to site.  Using the standard directories for roles, tasks, settings, notifications means being able to go from site-to-site and already understanding where files are and what they do. It  is standardization of scripts like yours.  For one system and one script like this, I wouldn't bother with ansible, but you seem to have multiple systems and perhaps multiple userids to address. THAT is where ansible shines.

Pushing files unchanged - easy. Pushing files based on a template with slight changes - easy. Installing packages, updating config files, restarting services - all easy. Managing permissions, directories, and only doing something when needed - easy.   I wrote all of this trying to get you to NOT reinvent the WHEEL.  The stuff you want to do has been solved already, ansible is that solution.

I have a script I want installed on every box I manage:
```
---

- name: Create /usr/local/bin/kernel-cleanup
  copy: src=files/kernel-cleanup dest=/usr/local/bin/kernel-cleanup
        mode=0700 owner=root group=root

```
Simple. Directories will be created as needed. File permissions are set.. 
[https://stackoverflow.com/questions/28023697/ansible-creating-working-cronjobs](https://stackoverflow.com/questions/28023697/ansible-creating-working-cronjobs) has an example ansible crontab task. 

Hope this makes sense.  Don't just believe me.  [https://valdhaus.co/writings/ansible-vs-shell-scripts/](https://valdhaus.co/writings/ansible-vs-shell-scripts/) makes the same argument to use ansible instead of scripting.

First of all, thank you very much for the detailed information. In future, I will learn how to use ansible.
At the moment I have to solve my problem quickly and with your tips I made a lot of progresses.
Now I have my final question related to crontab (standard one :(). The following command
```

sleep 10m && (sudo /usr/local/bin/command.sh | ts '%F %T' | sudo tee --append /usr/local/command_log.out)

```
works well if executed from terminal. However, it does not work if added to crontab in both the following manners:
```

@reboot sleep 10m && (sudo /usr/local/bin/command.sh | ts '%F %T' | sudo tee --append /usr/local/command_log.out)
@reboot root sleep 10m && (/usr/local/bin/command.sh | ts '%F %T' | tee --append /usr/local/command_log.out)

```
Any suggestion?
Thank you

---

### Post by SeijiSensei on 2016-03-07
You can also run a command at boot by putting it in /etc/rc.local.  See if that helps.

---

### Post by erotavlas on 2016-03-07
> **SeijiSensei said:**
> You can also run a command at boot by putting it in /etc/rc.local.  See if that helps.

Yes of course. Why does not work via crontab?
```

sudo crontab -u root -l
[sudo] password for nedo: 
@reboot sleep 10m && (sudo /usr/local/bin/command.sh | ts '%F %T' | sudo tee --append /usr/local/my_log.out)
@reboot root sleep 10m && (/usr/local/bin/command.sh | ts '%F %T' | tee --append /usr/local/my_log.out)

```

---

### Post by SeijiSensei on 2016-03-07
I don't know. I never use that feature of cron.  I only use date/time entries.

---

### Post by TheFu on 2016-03-09
Cron doesn't have much environment, so every command needs to be specified without trusting the PATH to exist.  That means /always/put/the/full/path/to/the/bin/command here. 
* sleep?
* ts?
* tee?
You'll have to look those up - I'd use "which" - which sleep, which ts, which tee - to find the program locations.

Again, if the crontab is running as root, there is NO NEED FOR SUDO. I don't know how to say that any clearer. However, if you insist on using it - /usr/bin/sudo  in the script too.  This is a "best practice" for all scripting, including crontab scripts. [http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting) has more "best practices."

---

### Post by erotavlas on 2016-03-13
> **TheFu said:**
> Cron doesn't have much environment, so every command needs to be specified without trusting the PATH to exist.  That means /always/put/the/full/path/to/the/bin/command here. 
* sleep?
* ts?
* tee?
You'll have to look those up - I'd use "which" - which sleep, which ts, which tee - to find the program locations.

Again, if the crontab is running as root, there is NO NEED FOR SUDO. I don't know how to say that any clearer. However, if you insist on using it - /usr/bin/sudo  in the script too.  This is a "best practice" for all scripting, including crontab scripts. [http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](http://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting) has more "best practices."

Thank you for your reply. I added the full path by using which command. However, without or with SUDO it does not work. The following is a very simple code.
```

scriptHome="/usr/local"
echo "Adding crontab job"
cronList=$(sudo crontab -u root -l)
cronCommand="@reboot root sleep 10m && ($scriptHome/bin/mycommand.sh | /usr/bin/ts '%F %T' | /usr/bin/tee --append $scriptHome/mylog.out)"
#cronCommand="@reboot sleep 10m &&  (sudo $scriptHome/bin/mycommand.sh | /usr/bin/ts '%F %T' | sudo /usr/bin/tee  --append $scriptHome/mylog.out)"
if [ $(echo $cronList | grep -c "$cronCommand") -eq 0 ]; then
    if [ -z "$cronList" ]; then
        echo $cronCommand | sudo crontab -u root -
    else
        (sudo crontab -u root -l; echo $cronCommand ) | sudo crontab -u root -
    fi
fi

```
When I login into the system I expect that after 10 minutes the script should be executed and it should logs into mylog.out. Unfortunately this does not happen.
The script location is the following
```

tar -xf $scriptHome/mycommand.sh.tar.gz -C $scriptHome/bin
sudo chown root:root "$scriptHome/bin/mycommand.sh"

```
Any idea?

---

### Post by TheFu on 2016-03-13
purge a shell environment of all settings. I bet the command doesn't work anymore.  Add back to the script, those environment variables necessary to make it work.

BTW - sudo, tar, crontab,, echo, and chown also need /full/path/to/the/cmd too. EVERY COMMAND NEEDS THIS - as a best practice.  Most people create variables at the top of a script and double-check that the commands are really where they should be before continuing.

cron doesn't have much environment. Something is set in your terminal environment that doesn't exist in cron .... or there are GUI tools used. Both of these are at issue.  Are any of the programs assuming HOME to be set?  Look for things like that, but don't forget LD_LIBRARY_PATH too.

---

### Post by erotavlas on 2016-03-23
Hi,
I had only now free time to find a solution to my problem. I found where was the mistake.
The following code works well without root at the beginning of the command after @reboot
```

scriptHome="/usr/local" echo "Adding crontab job"
cronList=$(sudo crontab -u root -l)
cronCommand="@reboot sleep 10m && ($scriptHome/bin/mycommand.sh | /usr/bin/ts | /usr/bin/tee --append $scriptHome/mylog.out)"
#cronCommand="@reboot sleep 10m && ($scriptHome/bin/mycommand.sh | /usr/bin/ts >> $scriptHome/mylog.out)"
if [ $(echo $cronList | grep -c "$cronCommand") -eq 0 ]; then
    if [ -z "$cronList" ]; then
        echo $cronCommand | sudo crontab -u root -
    else
        (sudo crontab -u root -l; echo $cronCommand ) | sudo crontab -u root -
    fi
fi

```
The problem was related to the option of ts command. I tried both ts '%F %T' and ts "%F %T". However, by escaping or not single or double quotes it work only from command line while it does not work via crontab.
```

cronCommand="@reboot sleep 10m && ($scriptHome/bin/mycommand.sh | /usr/bin/ts \"%F %T\" | /usr/bin/tee --append $scriptHome/mylog.out)"

```
Any suggestions? The options are not fundamentals, but I would like to use them.

Thank you

---

### Post by kevdog on 2016-04-02
The shell provided to cron is very limited.  Although I'm not certain it seems like the shell provided to cron can't substitute %F and %T variables. I believe another way to get around this limitation would be for your cron to call a script and the script for example has a #!/bin/bash line on the top of the script.  You may want to try it this way.

---

### Post by steeldriver on 2016-04-02
The % sign is special in cron - you would need to escape all the % characters (or wrap you command in a script like kevdog suggests)

See [http://stackoverflow.com/questions/5277508/how-is-special-in-crontab](http://stackoverflow.com/questions/5277508/how-is-special-in-crontab)

---

### Post by erotavlas on 2016-04-04
> **steeldriver said:**
> The % sign is special in cron - you would need to escape all the % characters (or wrap you command in a script like kevdog suggests)

See [http://stackoverflow.com/questions/5277508/how-is-special-in-crontab](http://stackoverflow.com/questions/5277508/how-is-special-in-crontab)

Thank you very much. Escaping the % solved the problem!

```
cronCommand="@reboot sleep 10m && ($scriptHome/bin/mycommand.sh | /usr/bin/ts '\%F \%T' | /usr/bin/tee --append $scriptHome/mylog.out)
```

---

