---
title: "Report: system error"
date: 2014-03-11
forum: New to Ubuntu
---

### Post by dougcumiskey123 on 2014-03-11
using 12.04.

I am getting a report of a "system error" with an invitation to send a error report about it but no details of what the error is. Can any one tell me what to do?

regards Doug

---

### Post by ajgreeny on 2014-03-11
There is a Details box which will show you what the problem is.  It can be useful to developers to get these reports, so if you can send it I suggest you do so by agreeing and not unticking the box.

---

### Post by ibjsb4 on 2014-03-11
Sounds like Apport.

If you see nothing wrong with your system, just disable apport.

[https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F)

---

### Post by dougcumiskey123 on 2014-03-12
Hi all,

Using 
_____________________________________________________________________________________________________________________________________
 "Ubuntu 12.04 and later
Starting with 12.04, Apport itself is running at all times because it collects crash data for whoopsie (see ErrorTracker). However, the crash interception component is still disabled. To enable it permanently, do:

sudo nano /etc/apport/crashdb.conf
... and add a hash symbol # in the beginning of the following line:

        'problem_types': ['Bug', 'Package'],
To disable crash reporting just remove the hash symbol.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
I Get, but I can't see where to remove the hash.

regards Doug

   GNU nano 2.2.6                 File: /etc/apport/crashdb.conf                                          

# map crash database names to CrashDatabase implementations and URLs

default = 'ubuntu'

def get_oem_project():
    '''Determine OEM project name from Distribution Channel Descriptor

    Return None if it cannot be determined or does not exist.
    '''
    try:
        dcd = open('/var/lib/ubuntu_dist_channel').read()
        if dcd.startswith('canonical-oem-'):
            return dcd.split('-')[2]
    except IOError:
        return None

databases = {
    'ubuntu': {
        'impl': 'launchpad',
        'bug_pattern_url': 'http://people.canonical.com/~ubuntu-archive/bugpatterns/bugpatterns.xml',
        'dupdb_url': 'http://people.canonical.com/~ubuntu-archive/apport-duplicates',
        'distro': 'ubuntu',
        'problem_types': ['Bug', 'Package'],
        'escalation_tag': 'bugpattern-needed',
        'escalated_tag': 'bugpattern-written',
    },
    'canonical-oem': {
  GNU nano 2.2.6                 File: /etc/apport/crashdb.conf                                          

        return None

databases = {
    'ubuntu': {
        'impl': 'launchpad',
        'bug_pattern_url': 'http://people.canonical.com/~ubuntu-archive/bugpatterns/bugpatterns.xml',
        'dupdb_url': 'http://people.canonical.com/~ubuntu-archive/apport-duplicates',
        'distro': 'ubuntu',
        'problem_types': ['Bug', 'Package'],
        'escalation_tag': 'bugpattern-needed',
        'escalated_tag': 'bugpattern-written',
    },
    'canonical-oem': {
        'impl': 'launchpad',
        'bug_pattern_url': 'http://people.canonical.com/~ubuntu-archive/bugpatterns/bugpatterns.xml',
        'project': get_oem_project(),
    },
    'debug': {
        # for debugging
        'impl': 'memory',
        'bug_pattern_url': '/tmp/bugpatterns.xml',
        'distro': 'debug'
    },
}




^G Get Help      ^O WriteOut      ^R Read File     ^Y Prev Page     ^K Cut Text      ^C Cur Pos
^X Exit          ^J Justify       ^W Where Is      ^V Next Page     ^U UnCut Text    ^T To Spell

---

### Post by matt_symes on 2014-03-12
Hi

Open a terminal and copy and paste (less chance of a typing mistake) this command into it.

```
sudo sed -i 's/^/#/g' /etc/default/apport
```

Enter your password. It will not be echoed to the screen. 

It will disable apport by putting a # in front of the enabled line, and in-fact all lines, like so..
```

matthew-S206:/home/matthew % cat /etc/default/apport                  
## set this to 0 to disable apport, or to 1 to enable it
## you can temporarily override this with
## sudo service apport start force_start=1
#enabled=1
```

After a reboot, apport should be disabled.

EDIT:

If you want to see what crashed, have a look in the folder ```
/var/crash
```

Kind regards

---

