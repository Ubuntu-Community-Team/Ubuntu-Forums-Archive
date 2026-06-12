---
title: "python 3 ssh and feedback"
date: 2016-12-19
forum: Programming Talk
---

### Post by kingpenguin on 2016-12-19
Ok I have written a program in python3 that will ssh into my raspberry pi box running kodi from my ubuntu laptop. If i run small commands that don't need any prompts I am good. I am trying to make it so I can basically do all of my maintenance tasks from a python script to simplify my life. What I am trying to do before I make my program any larger is to update and upgrade apt-get but also see what it is doing.

```
#!/usr/bin/python3
import subprocess
import sys

# This is an attempt to ssh into the raspberry pi
host = "192.168.1.72"
command = "sudo apt-get update && sudo apt-get upgrade -y"

ssh = subprocess.Popen(['ssh', 'pi@%s' % host, command], shell=False, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
result = ssh.stdout.readlines()
if result == []:
        error = ssh.stderr.readline()
        print(sys.err, "ERROR: %s" % error)
else:
        print(result)


```

At the moment if I make command equal to something like sudo reboot it will reboot the system no problem but it does not seem to be handling the update and upgrade correctly. Any help would be awesome. I feel like I'm losing my mind trying to figure this out. Sorry if my code looks horrible I have only been coding for about a week total.

---

### Post by TheFu on 2016-12-21
As young admins, we all wrote little scripts like this believing it would save time.  Turns out that 100,000 people did basically the same things.  Chef, CFEngine, Puppet, Ansible, Rexify, SaltStack are the results. Each is extremely well-thought-out solution to the problem you are also trying to solve.

[Expect]("http://www.admin-magazine.com/Articles/Automating-with-Expect-Scripts") solved this 25+ yrs ago.

If you want to centralize maintenance of multiple systems, something like [Ansible]("https://www.cyberciti.biz/python-tutorials/linux-tutorial-install-ansible-configuration-management-and-it-automation-tool/") is the preferred way these days. There are other DevOps tools in use many places, but IMHO, Ansible is the quickest to deploy and understand. Should take about 30 minutes to be managing system settings across 1 or 2,000 systems.

OTOH, this is an itch you have to scratch, so keep going.  BTW, Ansible is written in python. The code is on github.

---

