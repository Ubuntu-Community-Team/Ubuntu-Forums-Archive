---
title: "System program problem detected"
date: 2020-04-15
forum: New to Ubuntu
---

### Post by wyattwhiteeagle on 2020-04-15
Why did I just get  this message on my screen?

What all do I need to do to get all the proper info on here and in the proper place?

I clicked to report the problem...I don't know if it went through

```
System program problem detected
Do you want to report the problem now?

```

---

### Post by plucky on 2020-04-16
Open a terminal and ```
cd /var/crash
ls
```
you should see a crash file in there.
To stop the notification you need to delete the file ```
sudo rm <name of file>
``` or * if multiple files

What version and flavour have you installed?
I have the occasional Lightdm crash. on Xubuntu 20.04 which causes this notification.

---

### Post by wyattwhiteeagle on 2020-04-16
```
wyatt@wyatt-Aspire-5733Z:~$ cd /var/crash
wyatt@wyatt-Aspire-5733Z:/var/crash$ ls
_usr_bin_gnome-shell.121.crash  _usr_bin_Xwayland.121.crash
wyatt@wyatt-Aspire-5733Z:/var/crash$ 

```
I have Ubuntu 18.04.4 LTS Bionic Beaver

I went to the var/crash location and noticed these files have locks on them so I couldn't see any info about what caused these files to appear.

The messages are annoying but I feel it's the systems way of letting the user know "Hey, you-ser, your system is becoming fubar. You should look into this."

To me, just stopping the messages is kinda like sweeping under the rug and not correcting the actual issues.

Are there any terminal codes, tools or utilities that would help identify the reasons files like these appear and lead us to possible solutions?

---

### Post by Impavidus on 2020-04-16
When you click to report the problem, the crash will be reported, the report will be removed and the popup won't return until the application crashes again. Or that's supposed to happen, as it doesn't always work. I don't know why, it may have to do with which user ran the process that crashed and which user tries to do the reporting. Some commands that may be useful:```
# To go to the directory with the crash reports:
cd /var/crash

# List the files with ownership
ls -l

# View the first few lines of a report
head file_name

# Remove a file owned by you
rm file_name

# Remove a file owned by someone else
sudo rm file_name
```
These crashes are often caused by bugs. Maybe the bug will get fixed. In any case, it won't hurt to remove the crash reports. Don't take it as a sign that your system is messed up.

---

### Post by wyattwhiteeagle on 2020-04-16
> **Impavidus said:**
> When you click to report the problem, the crash will be reported, the report will be removed and the popup won't return until the application crashes again. Or that's supposed to happen, as it doesn't always work. I don't know why, it may have to do with which user ran the process that crashed and which user tries to do the reporting. 


...


These crashes are often caused by bugs. Maybe the bug will get fixed. In any case, it won't hurt to remove the crash reports. Don't take it as a sign that your system is messed up.


Instead of the first few lines of a report, how may I see the whole report?


cd /var/crash
ls -l
```

wyatt@wyatt-Aspire-5733Z:~$ cd /var/crash
wyatt@wyatt-Aspire-5733Z:/var/crash$ ls -l
total 23260
-rw-r----- 1 gdm whoopsie 21595267 Apr 15 23:25 _usr_bin_gnome-shell.121.crash
-rw-r----- 1 gdm whoopsie  2217007 Apr 15 23:25 _usr_bin_Xwayland.121.crash

```


sudo head  _usr_bin_gnome-shell.121.crash
```

wyatt@wyatt-Aspire-5733Z:/var/crash$ sudo head  _usr_bin_gnome-shell.121.crash
ProblemType: Crash
Architecture: amd64
CurrentDesktop: GNOME-Greeter:GNOME
Date: Wed Apr 15 23:25:01 2020
DistroRelease: Ubuntu 18.04
ExecutablePath: /usr/bin/gnome-shell
ExecutableTimestamp: 1571973788
ProcCmdline: /usr/bin/gnome-shell
ProcCwd: /var/lib/gdm3
ProcEnviron:

```


sudo head  _usr_bin_Xwayland.121.crash
```

wyatt@wyatt-Aspire-5733Z:/var/crash$ sudo head  _usr_bin_Xwayland.121.crash
ProblemType: Crash
Architecture: amd64
CurrentDesktop: GNOME-Greeter:GNOME
Date: Wed Apr 15 23:25:32 2020
DistroRelease: Ubuntu 18.04
ExecutablePath: /usr/bin/Xwayland
ExecutableTimestamp: 1571667977
ProcCmdline: /usr/bin/Xwayland :1024 -rootless -terminate -accessx -core -listen 4 -listen 5 -displayfd 6
ProcCwd: /var/lib/gdm3
ProcEnviron:
wyatt@wyatt-Aspire-5733Z:/var/crash$ 

```

---

### Post by Impavidus on 2020-04-17
If you want to see the whole report, use something like **less** instead of **head**. It's a text viewer for in your terminal. Use arrow keys or page up/down to scroll, hit q to exit the viewer.

These crash reports are large and the interesting bits are near the start.

---

### Post by wyattwhiteeagle on 2020-04-17
> **Impavidus said:**
> If you want to see the whole report, use something like **less** instead of **head**. It's a text viewer for in your terminal. Use arrow keys or page up/down to scroll, hit q to exit the viewer.

These crash reports are large and the interesting bits are near the start.

Large...yikes :)

Is there a way I can use the terminal to create a text editor file on the desktop showing all of the same info that would appear in the terminal including -yes or --yes to have it include all the info?

---

### Post by Impavidus on 2020-04-18
The crash report is a plain text file. You can open it in any text editor you like or do any of the other things you might want to do with text files. Just don't run any GUI text editors with sudo.

---

### Post by dan3712 on 2020-04-24
Good morning.

Is it possibly a good idea to save these files somewhere  besides /var/crash instead of deleting them? Might they may  ever be useful in the future?

I've had these twice now, and they aren't deleted when I click to report the problem. I just deleted them manually.

- Dan

---

