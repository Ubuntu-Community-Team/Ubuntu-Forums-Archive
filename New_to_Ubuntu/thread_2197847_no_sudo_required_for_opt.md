---
title: "no sudo required for /opt??"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-01-05
Hi,

I was trying to copy a file in /opt/google/earth and I forgot to add "sudo" before the cp command and it worked! Is this a bug or am I missing something?
(I was following oldos2er's post to fix GE's panaromio picture bug [http://ubuntuforums.org/showthread.php?t=2196304&page=3](http://ubuntuforums.org/showthread.php?t=2196304&page=3))

Ubuntu 13.10

Looks like for some reason I (not root) am the owner of the google directory

```

mb@localhost:/opt$ ls -l
drwxr-xr-x 3 root root 4096 Dec  4 23:22 extras.ubuntu.com
drwxr-xr-x 6 root root 4096 Dec 12 17:51 ffmpeg
drwxr-xr-x 5 mb mb 4096 Dec  1 21:00 google

```

---

### Post by bab1 on 2014-01-05
> **monkeybrain20122 said:**
> Hi,

I was trying to copy a file in /opt/google/earth and I forgot to add "sudo" before the cp command and it worked! Is this a bug or am I missing something?
(I was following oldos2er's post to fix GE's panaromio picture bug [http://ubuntuforums.org/showthread.php?t=2196304&page=3](http://ubuntuforums.org/showthread.php?t=2196304&page=3))

Ubuntu 13.10

What are the permissions from /opt on down?   The directory /opt is traversable by any user.  They can read but not write.  If you make a directory below /opt that is writable for all users then the cp won't need to use sudo.

---

### Post by monkeybrain20122 on 2014-01-05
Hi 

I just edited and showed the permissions.

---

### Post by bab1 on 2014-01-05
> **monkeybrain20122 said:**
> Hi 

I just edited and showed the permissions.
And as I said you will be able to manipulate all the files in the google directory because you have rwx permissions to that directory (see the red below).  ```
[COLOR="#FF0000"]**drwx**[/COLOR]r-xr-x 5 **[COLOR="#FF0000"]mb[/COLOR]** mb 4096 Dec  1 21:00 google
```

---

### Post by monkeybrain20122 on 2014-01-05
Why is that? I installed the google packages like everything else (with sudo) I never messed with the permissions.

---

### Post by bab1 on 2014-01-05
> **monkeybrain20122 said:**
> Why is that?
The installation was run as root and it made the google directory.  Then it gave the user that installed the package the permissions.
 I installed the google packages it like with everything else.
Did you install it using Ubuntu packages or a .deb file you got somewhere else?

Ultimately there is no problem with this install.  The user mb has no rights to anything else in the /opt file system other than the google directory and it's subdirectories.  remember the entire /opt file system is world (everyone) readable anyway.

[COLOR="#0000FF"]Edit:  So you did the install as root.  That's what sudo does.  The tool sudo stands for Switch User (to root) and DO the command (install).[/COLOR]

---

### Post by monkeybrain20122 on 2014-01-05
I have google-chrome, google-talk plugin and goole-earth, all installed by downloading the .deb from google.

---

### Post by bab1 on 2014-01-05
> **monkeybrain20122 said:**
> I have google-chrome, google-talk plugin and goole-earth, all installed by downloading the .deb from google.

You installed all of that as root.  This means that the installer was allowed to do whatever it wanted to do.  Do you trust Google to do the right thing?  This is why Ubuntu uses the Debian style package manager (SC, Synaptic, apt-get or aptitude).  I'm not saying the Google .deb is dangerous.  What I'm saying is YOU don't know.  Only you can decide to take a chance.  At least with the Ubuntu package managers there is some vetting of the code.

---

### Post by monkeybrain20122 on 2014-01-05
I know the risk, but if I worry about it I won't be using anything google, right? You don't get google's applications from the repo. My question is simply why I would be able to cp files in those subdirctories without being root.

---

### Post by Dave_L on 2014-01-05
You can manipulate the files in those subdirectories because you (mb) own them. The installer probably set it up like that intentionally.

---

### Post by bab1 on 2014-01-05
> **monkeybrain20122 said:**
> I know the risk, but if I worry about it I won't be using anything google, right? You don't get google's applications from the repo.

I'm not telling you anything about how you use your installations on your system.  My points have been on how and why the system works the way it does what it does.  Google is just one of many deb packages out there.  Think BEFORE you install outside of the repos.
> 
My question is simply that why I would be able to access those subfolders without being root.
I thought I answered that previously.  What didn't you understand?

---

### Post by monkeybrain20122 on 2014-01-05
> **bab1 said:**
> I'm not telling you anything about how you use your installations on your system.  My points have been on how and why the system works the way it does what it does.  Google is just one of many deb packages out there.  Think BEFORE you install outside of the repos.


Well I do install outside the repo because the repo doesn't have everything I use (e.g google) or the up to date version of foo. I am not exactly a newbie so I know the prep talk. :)

> I thought I answered that previously.  What didn't you understand?


I don't understand why the permission was set up that way. It may be something to do with google, so I will just check my other installations. I have installed other debs in /opt the past or by compiling from source and I am not aware that the permissions would be different. Maybe I just haven't noticed.

---

### Post by bab1 on 2014-01-05
> **monkeybrain20122 said:**
> I don't understand why the permission was set up that way. It may be something to do with google, so I will just check my other installations. I have installed other debs in /opt the past or by compiling from source and I am not aware that the permissions would be different. Maybe I just haven't noticed.

Why is it a big deal whether the google directory is owned by you or not.  Not everything needs to be that way.  Google has decided that you need to own the directory.  My guess is that you are the user running the google app rather than some system user that the app generates.  Some examples of system users  would be```
hplip:x:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:114:123::/home/saned:/bin/false

```...these are for HP printing and the scanner.

---

### Post by mc4man on 2014-01-05
i've got google-chrome & g-e 7.1.2.2041 installed from google created .debs & they are installed to /opt/google as expected (root owned

---

### Post by bab1 on 2014-01-05
> **mc4man said:**
> i've got google-chrome & g-e 7.1.2.2041 installed from google created .debs & they are installed to /opt/google as expected (root owned

Hmmmm, It looks like the OP is using a different deb package from Google.

---

### Post by mc4man on 2014-01-05
> **bab1 said:**
> Hmmmm, It looks like the OP is using a different deb package from Google.

Maybe, though not sure if google changes much when assembling their ubuntu .debs
Overall, as you've mentioned, doesn't *seem* to really matter in this case.

---

### Post by monkeybrain20122 on 2014-01-05
hmm.. weird I check another install (also Ubuntu 13.10) and this one looks normal. 


```
drwxr-xr-x 7 root root 4096 Nov 17 00:17 brackets
drwxr-xr-x 3 root root 4096 Oct 21 05:04 extras.ubuntu.com
drwxr-xr-x 6 root root 4096 Dec 12 00:17 ffmpeg
drwxr-xr-x 3 root root 4096 Dec 22 02:08 gcc-4.4.7
drwxr-xr-x 5 root root 4096 Dec 29 22:45 google
drwxr-xr-x 3 root root 4096 Dec 12 08:26 pencil
drwxr-xr-x 6 root root 4096 Dec 12 08:31 project-neon
```

May reinstall the google packages tonight and see what happens.

---

### Post by bab1 on 2014-01-05
> **mc4man said:**
> Maybe, though not sure if google changes much when assembling their ubuntu .debs
Overall, as you've mentioned, doesn't *seem* to really matter in this case.

Either way seems proper.  The most prevalent is to allow the 'others" bit executable on the bin file.  On first thought I would prefer **not** to have the world be able to run the executable.  I just checked one of my /opt installs.  Any user can execute that bin file.  But only root can modify or substitute the file.```
rwxr-xr-x (755) 
```

---

### Post by monkeybrain20122 on 2014-01-18
I figured it out.

```

$ ls -l /opt/google
total 12
drwxr-xr-x 8 root root 4096 Jan 14 19:44 chrome
drwxr-xr-x 3 mb  mb  4096 Jan  5 18:23 earth
drwxr-xr-x 6 root root 4096 Dec  1 21:00 talkplugin
```

So actually only google earth is not owned by root.

The reason for that is in order to install ge I have rebuilt the .deb and I did it without sudo.

---

