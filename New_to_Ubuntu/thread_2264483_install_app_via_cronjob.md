---
title: "install app via cronjob"
date: 2015-02-07
forum: New to Ubuntu
---

### Post by ben5 on 2015-02-07
I have a bunch of ubuntu PC's that I have setup to regularly grab a script from my server and run it so that I can easily perform a task on each of them by just updating the script centrally. 

This works great EXCEPT it seems I can't install something.  

I put 
  ```
apt-get update
  export DEBIAN_FRONTEND=noninteractive
  apt-get -y install screen > /root/installscreen.txt
```
in my script and yet - screen will not install... not unless I run the script manually... not in a cron job. 

The output I get in the file is below... 

Any idea how I can get this to install via a script run in a cron job?  

```
Reading package lists...
Building dependency tree...
Reading state information...
Suggested packages:
  iselect screenie byobu
The following NEW packages will be installed:
  screen
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0 B/628 kB of archives.
After this operation, 958 kB of additional disk space will be used.

```

---

### Post by nerdtron on 2015-02-08
Is the crontab installed for the root user? "sudo crontab -e"
What is the crontab entry?
What is the exact contents of the bash script?

---

### Post by ben5 on 2015-02-09
Yes - it is in the root crontab

This is the crontab entry
```
1 1 * * * /root/cron/installscreen.sh
```

and the script
```
  apt-get update
  export DEBIAN_FRONTEND=noninteractive
  apt-get -y install screen > /root/installscreen.txt

```

---

### Post by Holger_Gehrke on 2015-02-10
'cron' sends (local) e-mail every time it executes a job to the owner of the crontab. You should 'sudo mail' to have a look at the mails from cron to root.

---

### Post by ben5 on 2015-02-10
You got me thinking... what might I not be seeing already in my output and I realized I am only redirecting stdout to that file... not stderr as well.... so I redirected stderr as well to that file.

  ```
apt-get -y install screen** &**> /root/installscreen.txt
```
After which I saw the error messages

```
Reading package lists...
Building dependency tree...
Reading state information...
Suggested packages:
  iselect screenie byobu
The following NEW packages will be installed:
  screen
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin: 
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0 B/628 kB of archives.
After this operation, 958 kB of additional disk space will be used.
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: warning: 'start-stop-daemon' not found in PATH or not executable
dpkg: error: 2 expected programs not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin
E: Sub-process /usr/bin/dpkg returned an error code (2)



```

The problem is that the full $PATH was not set in the cron - so I needed to set it at the top of the crontab

```
**PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin**
1 1 * * * /root/cron/installscreen.sh
```

Thanks everyone!

---

### Post by mörgæs on 2015-02-10
Please use Thread Tools for marking a thread solved.

---

