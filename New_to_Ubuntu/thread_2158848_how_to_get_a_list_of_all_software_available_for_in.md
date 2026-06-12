---
title: "how to get a list of all software available for installation"
date: 2013-06-30
forum: New to Ubuntu
---

### Post by bdss on 2013-06-30
Hi ,

Which command can i use in terminal to get list of all software available for installation 

For Ex - 

   To install Adobe Flash Player i used sudo apt-get install flashplugin-installer

Similarly i want to install gtalk , skype etc ,how can i get package name 

Tried apt-cache but it didn't worked ,

apt-cache search skype
pidgin-skype - Skype plugin for libpurple messengers
pidgin-skype-dbg - Skype plugin for libpurple messengers (debug symbols)
earcandy - Sound level manager for PulseAudio


Thanks In Advance

---

### Post by Cheesemill on 2013-06-30
Running 'apt-cache search' would have worked if Skype was in the Ubuntu repositories, but it isn't.

To install Skype you need to download the .deb file from their website...
[http://www.skype.com/en/download-skype/skype-for-computer/](http://www.skype.com/en/download-skype/skype-for-computer/)

---

### Post by newbie-user on 2013-06-30
You would have to enable the repositories that contain those packages. For example, if you wanted to install the googletalk plugin, you'd have to add the google repo to your /etc/apt/sources.list file:
```
deb http://dl.google.com/linux/talkplugin/deb/ stable main
```
Then you can:
```
apt-cache search google-talk
```
Same goes for skype. Skype is found in the partner repository:
```
deb http://archive.canonical.com/ubuntu precise partner
```

---

### Post by newb85 on 2013-06-30
Rather than adding those repositories to the sources file manually with a text editor, you could use the add-apt-repository command, like this:

```
sudo add-apt-repository 'deb http://dl.google.com/linux/talkplugin/deb/ stable main'
```

Whichever way you add the sources, you will need to run
```
sudo apt-get update
```
before apt-cache will find the packages from the new source.

---

### Post by bdss on 2013-07-01
> **newb85 said:**
> Rather than adding those repositories to the sources file manually with a text editor, you could use the add-apt-repository command, like this:

```
sudo add-apt-repository 'deb http://dl.google.com/linux/talkplugin/deb/ stable main'
```

Whichever way you add the sources, you will need to run
```
sudo apt-get update
```
before apt-cache will find the packages from the new source.

When did [B]sudo apt-get update 

Got below warning/error ,

W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release)  Unable to find expected entry 'main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.[/B]

bdss@ubuntu:/etc/apt$ cat sources.list
# /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
[B]deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
deb-src [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main[/B]
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse

Still seems like its installed

**apt-get install google-talkplugin**

**dpkg -l google-talkplugin**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
**ii  google-talkplugin           4.0.3.0-1                   Google Talk Plugin**

**But i don't find any option to launch it**

---

### Post by newb85 on 2013-07-01
That's exactly how it looked on my Raring system last night when I tested it, and it worked.  Perhaps there's something in the format of that entry that Precise's version of apt doesn't recognize?  (I've never seen one that didn't contain the name of the release before this thread.)

Anyone else have ideas?

---

### Post by newbie-user on 2013-07-02
It if doesn't have a release name in the line, it just means that it's supposed to work on all releases. The google-talkplugin is not an actual program that runs on its own. It's a web browser plugin to enable video chatting through Google Talk.

---

