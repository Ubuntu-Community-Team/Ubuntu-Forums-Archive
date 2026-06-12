---
title: "Ran sudo apt-get install -f to fix a broken package and it didn't work"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by dtlongrifles on 2014-07-23
I Ran sudo apt-get install -f to fix a broken package and it didn't work. I still have the error icon at the top of my screen. I'm not sure what a third party repository is, I've tried to research it and everything I find assumes that one already knows what it is. I did download malwarebytes because I installed Wine and to scan files that I might send to somebody who uses windows so as not to send them a virus. Is Malwarebytes a PPA? When I ran the the command sudo apt-get install -f in a terminal, this is what I got:

---

### Post by Bucky Ball on 2014-07-23
That command needs to be run as root:

```
sudo apt-get install -f
```

Software Updater>Settings in bottom left corner>Other Software tab. If you have repos in there, you have installed third-party repos.

---

### Post by dtlongrifles on 2014-07-23
> **Bucky Ball said:**
> That command needs to be run as root:

Okay, I'm willing to do that if I only knew how

```
sudo apt-get install -f
```

Software Updater>Settings in bottom left corner>Other Software tab. If you have repos in there, you have installed third-party repos.

Software Updater? is that the same as the Ubuntu Software Center located on the Launcher bar? I'm still looking for it because the when I open the Software Center there are no features that look like the ones described,

---

### Post by Bucky Ball on 2014-07-23
No, it's the Software Updater you use to update the system. Also called 'update-manager' in a terminal. Open a terminal and type that in: 'update-manager' and hit return. Give it time to do it's thing, then when it's settled you will see the 'Settings' option, bottom left corner.

PS: I don't use Unity or Ubuntu flavour, but you may have 'Software Sources' or something like that. That's what you're looking for.

---

### Post by ian-weisser on 2014-07-23
You have a corrupt data error.
Delete the package from your /var/cache/apt/archives/ directory, and then try to install it again.

---

### Post by dtlongrifles on 2014-07-23
> **ian-weisser said:**
> You have a corrupt data error.
Delete the package from your /var/cache/apt/archives/ directory, and then try to install it again.
I am willing to do this but  I have no idea how to find this.

I was able to find the repositories and there were three there associated with pipelite that were checked so I unchecked them. The I ran the sudo apt-get -f from root with this result

 sudo -i
[sudo] password for bmacbn: 
root@bmacbn-Latitude-D520:~# sudo apt-get -f
apt 0.8.16~exp12ubuntu10.17 for i386 compiled on Jun 13 2014 17:42:18
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]


apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.


Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory


Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
root@bmacbn-Latitude-D520:~# 
And that is where it stops. after several minutes nothing more has happened but if I try to close the terminal I get a message saying that a process is still running and if I close the terminal, it will kill it.

---

### Post by ian-weisser on 2014-07-23
Well, messing around with strange commands while root is not an activity I would recommend. Fumblefingers while root can have catastrophic consequences. Everyone I know who runs as root has a war story about the day they accidentally destroyed their system.

1) Delete the corrupt package
```
sudo rm /var/cache/apt/archives/libwayland-egl1-mesa-lts-trusty_10.1.3-0ubuntu0.1~precise1_i386.deb
```
The package path or name may have a typo in it - extracting text from your screen shot error message is tedious and error-prone.
Of course, if you are running as root, omit sudo.

2) Check that your package manager works again.
```
sudo apt-get update
sudo apt-get upgrade
```
Of course, if you are running as root, omit sudo.

The problem libwayland-egl1-mesa-lts-trusty should be automatically re-downloaded and installed.

---

### Post by Impavidus on 2014-07-24
```
$ sudo -i
[sudo] password for bmacbn: 
root@bmacbn-Latitude-D520:~# sudo apt-get -f
apt 0.8.16~exp12ubuntu10.17 for i386 compiled on Jun 13 2014 17:42:18
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

(...)

root@bmacbn-Latitude-D520:~# 
```
Just to tell you a little more on what you did here: With sudo -i you started a root shell, then you ran a sudo command to run something as root. But if you are already running a root shell, you don't need to prepend sudo to your commands, and when you can prepend sudo to your command, there is no need to start a root shell first. The preferred way is just prepending sudo, not running sudo -i, as long as it doesn't get complicated.

Next, apt-get expects a command, like in this case install as in apt-get -f install. You used apt-get -f, which is incomplete and therefore apt-get gave you a help message and terminated, so that you got a new prompt (the last line in the quote). The root shell was waiting for your input, so obviously nothing happened. When you closed the terminal it warned you one process was still running, which was sudo -i.

---

### Post by dtlongrifles on 2014-07-24
This issue seems to have been resolved and I don't really know how. I checked to make sure that all of the third party repositories were disabled (Pipelight and Chrome) and they were, then I opened the Ubuntu Software Center and immediately got the message that the package was broken and nothing could be added or removed, giving me the option to repair which I tried with no success. I closed the message and tried, just for the heck of it to remove a program that I never use (Gramps). The process for removing Gramps started but stopped and I got the message again about not being able to add or remove due to broken package and I again clicked on repair and that time the repair was successful (I had probably tried this same process 20 times previously). I then opened up the software updater and added the updates without a problem and the red circle at the top of the screen went away.

---

### Post by Bucky Ball on 2014-07-24
Great news. Lets hope it stays that way. ;)

Post a new thread for any further questions/issues. Good luck.

---

