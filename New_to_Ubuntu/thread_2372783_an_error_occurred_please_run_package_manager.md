---
title: "an error occurred please run package manager"
date: 2017-09-28
forum: New to Ubuntu
---

### Post by luger2 on 2017-09-28
I get this error message in the top right corner i was trying to install google chrome in terminal before i got this error the next day my wifi speeds are extremely slow work normal on any other devices

An error occurred,please run package manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: Opening the cache (E:Malformed entry 1 in list file /etc/apt/sources.list.d/google-chrome.list (Suite), E:The list of sources could not be read.)'. This usually mean that your installed packages have unmet dependencies

looked everywhere for answers any help would be great TY

---

### Post by Bashing-om on 2017-09-28
luger2; Hello - Welcome to the forum.

The system is telling you that it does not accept a fetch file : /etc/apt/sources.list.d/google-chrome.list  .

Let's see what the problem here is .
Post back - Between Code Tags - the output of terminal command:
```

cat /etc/apt/sources.list.d/google-chrome.list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

ain't nothing but a thing

---

### Post by luger2 on 2017-09-28
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/)

stable main
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

---

### Post by deadflowr on 2017-09-28
You need to remove or disable that non [arch-amd64] entry
Here's quick one-liner that will/should at least disable it.
```
sudo sed -i 's/deb h/#deb h/g' /etc/apt/sources.list.d/google-chrome.list
```

---

### Post by luger2 on 2017-09-28
i just tried this it didnt show anything after i hit enter

---

### Post by Bashing-om on 2017-09-28
luger2; Well'

> **luger2 said:**
> i just tried this it didnt show anything after i hit enter

That is to be hoped for . In linux there is no response to a completed command . System does as told . Now if there is a problem then the system will so advise .

[INDENT][INDENT]silence is golden
[/INDENT][/INDENT]

---

### Post by luger2 on 2017-09-28
i dont understand do you mean thats all that can be done for this problem

and also i got a new error added it says
error: opening the cache (W:ignoring file google-chrome.list-30aug2016 'in directory' /etc/apt/sources.list.d/ as it has an invalid filename extension, E:Type 'stable' is not known on line 3 in the source list /etc/apt/sources.list.d/google-chrome.list, E:The List of sources could not be read.)'.

---

### Post by deadflowr on 2017-09-28
> **Bashing-om said:**
> luger2; Well'



That is to be hoped for . In linux there is no response to a completed command . System does as told . Now if there is a problem then the system will so advise .

[INDENT][INDENT]silence is golden
[/INDENT][/INDENT]

That

Now open software updater or run
```
sudo apt update
```
it should no longer show the error.

Basically the error is caused by the fact that google stopped support for 32-bit versions of chrome, but they had trouble fixing the repository information and so the normal deb http entry went looking for the 32-bit packages, which had since been removed and that caused a ton of trouble, and in the end they found it easier to simply add the [arch=amd64] to the line which forces it to only look for the amd64, or 64-bit, version, and now to see if I can make the sentence even longer...

Edit:

> and also i got a new error added it says
error: opening the cache (W:ignoring file google-chrome.list-30aug2016 'in directory' /etc/apt/sources.list.d/ as it has an invalid filename extension, E:Type 'stable' is not known on line 3 in the source list /etc/apt/sources.list.d/google-chrome.list, E:The List of sources could not be read.)'.
was this
```
deb http://dl.google.com/linux/chrome/deb/

stable main
deb http://dl.google.com/linux/chrome/deb/ stable main
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
the full file as is, like you copied and pasted it directly?
if so the error is right stable is invalid, so you need to disable that too.
like above
```
sudo sed -i 's/^stable/#stable/g' /etc/apt/sources.list.d/google-chrome.list
```
the ^stable will make it only # comment out the stable entry that starts the line, and not the stable in the 
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
line so that this
stable main
will look like this
#stable main
so the whole entry should look like this
```
#deb http://dl.google.com/linux/chrome/deb/

#stable main
#deb http://dl.google.com/linux/chrome/deb/ stable main
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```

or
run
```
sudo nano /etc/apt/sources.list.d/google-chrome.list
```
and remove everything but the last line
so it looks like only
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

then hit ctrl + X then hit Y and then enter, this will save and exit.


AS for the other thing, you can just delete the /etc/apt/sources.list.d/google-chrome.list-30aug2016 file, or do nothing, it's only a warning and inconsequential.

---

### Post by luger2 on 2017-09-28
i got this and software updater does not open 


N: Ignoring file 'google-chrome.list-30Aug2016' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Type 'stable' is not known on line 3 in source list /etc/apt/sources.list.d/google-chrome.list
E: The list of sources could not be read.

---

### Post by deadflowr on 2017-09-28
> **luger2 said:**
> i got this and software updater does not open 


N: Ignoring file 'google-chrome.list-30Aug2016' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Type 'stable' is not known on line 3 in source list /etc/apt/sources.list.d/google-chrome.list
E: The list of sources could not be read.

Read my last post, I edited it with more since you posted as i wrote your previous post.

---

### Post by luger2 on 2017-09-28
ok so i did all of this didnt run into any problems is this all that was left to do

---

### Post by Bashing-om on 2017-09-28
luger2; Likely -

what does apt report now :
```

sudo apt update
sudo apt full-upgrade

```

-and a tale gets told -

---

### Post by luger2 on 2017-09-28
on sudo apt upgrade i got this

Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates InRelease [89.2 kB]
Get:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [1,189 B]           
Get:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [819 B]         
Get:5 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty InRelease [15.4 kB]  
Get:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable/main amd64 Packages [1,393 B]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/multiverse i386 Packages [11.2 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 Packages [11.0 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/multiverse Translation-en [5,828 B]
Get:10 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty/main i386 Packages [16.3 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/multiverse amd64 DEP-11 Metadata [5,844 B]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates/multiverse DEP-11 64x64 Icons [9,203 B]
Get:13 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty/main amd64 Packages [16.3 kB]
Get:14 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) zesty/main Translation-en [4,876 B]
Fetched 189 kB in 2s (84.0 kB/s)                    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
N: Ignoring file 'google-chrome.list-30Aug2016' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

Then on sudo apt full-upgrade i got this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file 'google-chrome.list-30Aug2016' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

---

### Post by Bashing-om on 2017-09-28
luger2; Looks good;

" N: Ignoring file 'google-chrome.list-30Aug2016' in directory '/etc/apt/sources.list.d/' "
If you do not want to see this advisory then move the file out of apt's path - OR
If you are happy with the state of the update process this backup file is no longer needed (?) and can be deleted .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by luger2 on 2017-09-28
yea everything looks great now thanks for your help appreciate your time spent helping me

---

### Post by Bashing-om on 2017-09-28
luger2; Outstanding :)

Help is what we do .

As this mater is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away[/INDENT][/INDENT]

---

