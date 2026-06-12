---
title: "So that went well..."
date: 2022-01-18
forum: New to Ubuntu
---

### Post by oblithian on 2022-01-18
I installed Ubuntu and it runs, but it keeps stating it has a system error (not listing what the error is). When I attempt to download the boot repair, or an update, or anything, it says there is a package error and the download fails. 
I also have not had any luck with running the boot repair off a flash drive, and rufus says it is incompatible. (It also occasionally freezes and/or crashes)

Are there any other ways to remove the OS so I can do another clean install. Alternatively, do you have any suggestions to repair the issues?

I have wasted about 2 days trying to find a solution, so please no unhelpful '1.enter question into google. 2. done' comments.

---

### Post by Autodave on 2022-01-18
As far as reinstalling, just put your install medium back in like you did before and boot the machine to it.  It will tell you that there is already a system installed and give you the option to install a new one beside the old one or to erase the drive and reinstall.  Obviously, choose "erase drive and reinstall".

Just in case this matters: what version did you try to install?

---

### Post by Holger_Gehrke on 2022-01-18
At what point in the boot process do you get that message ? If it's a graphical message box (sorry, don't have a screenshot of this handy) appearing after log in with the option to send data on the crash to the developers then it might have a button to show details on the bottom left of the box which will tell you what exactly happened. Sometimes that button is missing. You can still find out what caused the crash by looking for a log file in /var/crash (should have a name that consists of the path and name of the crashed program with all '/' replaced by '_' followed by a dot, the number of the logged in user, another dot and the extension crash). It's a simple text file and should tell you in excruciating detail what went wrong. Also sometimes these errors get 'stuck', you had a crash, you got the notification, the log should have been erased but didn't and so you're stuck getting the message on each boot for a crash that happened days ago.

Holger

---

### Post by TheFu on 2022-01-18
Sometimes a crash is critical to the safety of the data on the system 
and 
sometimes it is something completely unimportant that you don't care about.
For example, if bluetooth stuff fails to start and I don't have any bluetooth devices, does that really matter?

Check the logs.  Probably the easiest is to run
```
$ journalctl -perr | tee /tmp/logs.errors
```
This will show on the terminal AND put into a temporary file all the errors logged.  You can check out those errors one at a time, but there might be thousands of the same error ... er ... like I saw on my laptop for some process I played with for a few days, then never used again.  

```
$ journalctl -xe 
```
will show just the last error.

If you want to see the latest boot log errors, 
```
$ journalctl -b -perr
```

journalctl isn't much different than logging through the log files in /var/log/ ... just a systemd logging system.   As with most commadns on the system, there is a manpage with details for how to use the command. Manpages are written in a way, sorta like a newspaper article.  The first stuff at the top is the most important big-picture ideas. As we read further into the page, more and more details are provided.  It does take some time to get used to it, but after a little bit of time, you'll see why layout they use is so smart.

---

### Post by oblithian on 2022-01-22
Thank you, I will check the logs and report back. (Yes the button to view the report details is missing)

---

### Post by oblithian on 2022-02-03
So the main issue I am having is that packet error, I believe. The warning at the top right states the following:
"An error occurred, please run package manager...
The error was \error: 'Broken Count >0'. This usually means that the installed packages have unmet dependencies"
Again, when I had first started it directed me to download things to fix an issue, then the downloads were unsuccessful "due to a packet issue".
Things seemed to have de-railed further from there.

Here are the Important log messages from this last session:
16:49:22 pulseaudio: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
16:49:08 gnome-session-b: CRITICAL: We failed, but the fail whale is dead. Sorry....
16:49:06 gdm-session-wor: gkr-pam: unable to locate daemon control file
16:48:57 kernel: amdgpu 0000:30:00.0: amdgpu: Unsupported power profile mode 0 on RENOIR
16:48:54 kernel: sd 10:0:0:0: [sda] Assuming drive cache: write through
16:48:54 kernel: sd 10:0:0:0: [sda] Assuming drive cache: write through
16:48:54 kernel: sd 10:0:0:0: [sda] No Caching mode page found

And here are the error logs (well, from one session. It mayhave been while I was messing with the BIOS):
Jan 15 17:33:25 ComputerVII kernel: amdgpu 0000:30:00.0: amdgpu: Unsupported power profile mode 0 on RENOIR
Jan 15 17:33:34 ComputerVII gdm-password][1436]: gkr-pam: unable to locate daemon control file
Jan 15 17:33:50 ComputerVII pulseaudio[1456]: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
Jan 16 00:43:41 ComputerVII kernel: watchdog: BUG: soft lockup - CPU#13 stuck for 23s! [Socket Thread:6391]
Jan 16 00:44:09 ComputerVII kernel: watchdog: BUG: soft lockup - CPU#13 stuck for 23s! [Socket Thread:6391]
Jan 16 00:44:13 ComputerVII kernel: rcu: INFO: rcu_sched self-detected stall on CPU
Jan 16 00:44:13 ComputerVII kernel: rcu:         13-....: (15000 ticks this GP) idle=48a/1/0x4000000000000000 softirq=19233/19233 fqs=6972 
Jan 16 00:44:41 ComputerVII kernel: watchdog: BUG: soft lockup - CPU#13 stuck for 23s! [Socket Thread:6391]
Jan 16 00:44:50 ComputerVII kernel: rcu: INFO: rcu_sched detected expedited stalls on CPUs/tasks: { 13-... } 15458 jiffies s: 3013 root: 0x1/.
Jan 16 00:44:50 ComputerVII kernel: rcu: blocking rcu_node structures: l=1:0-15:0x2000/.
Jan 16 00:45:09 ComputerVII kernel: watchdog: BUG: soft lockup - CPU#13 stuck for 23s! [Socket Thread:6391]
Jan 16 00:45:37 ComputerVII kernel: watchdog: BUG: soft lockup - CPU#13 stuck for 23s! [Socket Thread:6391]
Jan 16 00:45:56 ComputerVII kernel: INFO: task khugepaged:119 blocked for more than 120 seconds.
Jan 16 00:45:56 ComputerVII kernel:       Tainted: G             L    5.11.0-27-generic #29~20.04.1-Ubuntu
Jan 16 00:45:56 ComputerVII kernel: "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 16 00:45:56 ComputerVII kernel: INFO: task pool-org.gnome.:6623 blocked for more than 120 seconds.
Jan 16 00:45:56 ComputerVII kernel:       Tainted: G             L    5.11.0-27-generic #29~20.04.1-Ubuntu
Jan 16 00:45:56 ComputerVII kernel: "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Jan 16 00:46:05 ComputerVII kernel: watchdog: BUG: soft lockup - CPU#13 stuck for 23s! [Socket Thread:6391]
Jan 16 00:46:34 ComputerVII kernel: watchdog: BUG: soft lockup - CPU#13 stuck for 23s! [Socket Thread:6391]
Jan 16 00:46:52 ComputerVII gdm3[853]: Failed to contact accountsservice: Error calling StartServiceByName for org.freedesktop.Accounts: Refusing activation, D-Bus is shutting down.
Jan 16 00:46:53 ComputerVII pulseaudio[6824]: GetManagedObjects() failed: org.freedesktop.systemd1.ShuttingDown: Refusing activation, D-Bus is shutting down.
Jan 16 00:47:02 ComputerVII kernel: watchdog: BUG: soft lockup - CPU#13 stuck for 22s! [Socket Thread:6391]
Jan 16 00:47:15 ComputerVII kernel: rcu: INFO: rcu_sched self-detected stall on CPU
Jan 16 00:47:15 ComputerVII kernel: rcu:         13-....: (60003 ticks this GP) idle=48a/1/0x4000000000000000 softirq=19233/19233 fqs=26871 
Jan 16 00:47:42 ComputerVII kernel: watchdog: BUG: soft lockup - CPU#13 stuck for 22s! [Socket Thread:6391]

Then when I attempted to get the logs today it wouldn't boot at all. Then I rebooted it a few times and it got to the login screen (and froze repeatedly). More rebooting and I got to properly shut it off, and boot. Aaaand, now for some reason it successfully downloaded some updates.

Ok, so now the software updater says:
It is impossible to install or remove software. Please use package manager "synaptic" or run"sudo apt-get install -f" in terminal to fix this issue at first.
(which is what came up the first day, attempting to install gave me the packet warning).

Alright, now it's giving me the relevant information:
"Transaction failes: The package system is broken. The following packages have unmet dependencies:

libgl1-mesa-dri: Depends: libglapi-mesa (= 21.0.3-0ubuntu0.3~20.04.1) but 21.0.3-0ubuntu0.3~20.04.5 is installed
Depends: libllvm12(>= 1:9~syn298832-1~) but 1:12.0.0-3ubuntu1~20.04.4 is installed
Depends: libsensors 5 (>= 1:3.5.0) but 1:6.0-2ubuntu1 is installed
Depends: zlib1g(>= 1:1.1.4) but 1:1.2.11.dfsg-2ubuntu1.2 is installed

After running: sudo apt-get install -f 
in _terminal it seems to have downloaded sucessfully this time?

I am now selecting 'try again' on Software Updater
(too many keyboards, I keep typing on the wrong one)
Part-way through the installation, the package warning has disappeared from the top right.
Download appears to have been successful.
Restarting...
Reboot successful
Logs:
18:25:22 pulseaudio: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
18:25:12 gdm-session-wor: gkr-pam: unable to locate daemon control file

So, I don't know what these other log issues are. However, the initial issue seems to have been resolved.
I would assume the fix was done developer-side, and if so, thank you. If not... (massive shug)?

Perhaps this will help someone else, or someone will point out what these other problems are.
I am just going to roll with it for today.

Thanks again (I think I need to download a list of terminal commands)

---

### Post by TheFu on 2022-02-04
> **oblithian said:**
>  
Thanks again (I think I need to download a list of terminal commands)

Happy you are happy.  Updates that mis-install usually leave a system in strange states.  That's why automatic, daily, versioned, backups are so important.  

A fat-finger by someone creating a package and have terrible impacts if they get a package dependency wrong. You and I don't have any control over this, but we can control how good our automatic, daily, versioned, backups are.  Think of all the hassles you've had.  When a 15 min restore effort would have solved it. weeks ago, assuming you do not allow automatic patching.

Down load a list of commands?  Why. They are all on your system already and have instructions for using them there too.  Plus, there are certainly commands on my system that don't exist on your and vice versa.  Every system is unique.
Nearly all the program are in /usr/bin/ or /bin/ directories.  System programs are in /sbin/ and /usr/sbin/ .   There are standards for which programs belong where. It is fully documented in the "*Linux File System Hierarchy Standards*" - but you probably only need to understand the overview, not the details.  Google it. Spend 3 minutes.

Unfortunately, Linux and Unix are huge. After many decades there is always something more to know and both are always changing, but at least with terminal command, the change is slower and old options tend to remain viable and useful for 10+ years, unlike having to learn a new GUI every 3 yrs.  Here's a free download, overview book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) . When I was teaching Beginning Linux, that is what we used. We'd cover the first 250-ish pages 1 chapter per week.  Then the remaining of the book was used as a reference.  Learning things in a specific order allows for the base knowledge to be used in the topics learned after. Order matters, at least in the beginning stages of learning.  And forget the GUI.  It provides only about 20% of the power that your system has.

I'm joking a bit about ignoring the GUI. Use it when it makes sense, but expect 80% of what any program can do NOT to be available through the GUI. Just don't get too hung up on it.  If you are typing more than 2-3 characters at a time, then you are entering commands wrong.  Look up "tab-completion" - it is hard to explain, but easy to use and understand. Find a video about it and start building the habit. You'll never have the wrong command, command options or filename again.  It is a huge time-saver.

---

