---
title: "How to get rid of the GUI on the log-in screen?"
date: 2012-11-19
forum: New to Ubuntu
---

### Post by Shepherd of Wolves on 2012-11-19
Hi, as of about an hour ago I am running Ubuntu 12.04LTS 64bit. For the past year or so I've been running Backtrack as root but I wanted something a bit more stable, but I'm missing some of my geeky amenities such as the lack of a GUI on the log in screen. On Backtrack you enter your username & password and then type 'startx' to, well...start X. 
     Can anyone tell me how to get rid of that GUI by default and what command I use, if it isn't still 'startx', to start the GUI for everything else?

---

### Post by cariboo on 2012-11-19
If you remove lightdm, you should be able to login from the prompt, and start X manually.

---

### Post by sisco311 on 2012-11-19
You can disable lightdm (the desktop manager) with the following command:
```
echo 'manual' | sudo tee /etc/init/lightdm.override
```

If you want to re-enable the DM, then simply delete /etc/init/lightdm.override

```
startx
```should start the X session.

---

### Post by Shepherd of Wolves on 2012-11-19
Okay, that makes sense, but are there going to be any bad side effects after I log in & startx since I'd be permanently removing lightdm?

---

### Post by Shepherd of Wolves on 2012-11-19
Oh hey, sisco, you just answered my question. thanks

---

### Post by Shepherd of Wolves on 2012-11-19
Awesomesauce! :)
That got me in as root for a minute so I could change some permissions for some files I dumped in the wrong place.
Lightdm also apparently runs the panels in 12.04 so I'm riding on the back of the terminal at the moment. It's okay though I hated those panels, although I'd like some more. Do you guys know what panel system backtrack used? It's the same as linux mint, although with mint I only ever got it to enable on at a time...

---

### Post by newb85 on 2012-11-19
> **Shepherd of Wolves said:**
> Awesomesauce! :)
That got me in as root for a minute so I could change some permissions for some files I dumped in the wrong place.
Lightdm also apparently runs the panels in 12.04 so I'm riding on the back of the terminal at the moment. It's okay though I hated those panels, although I'd like some more. Do you guys know what panel system backtrack used? It's the same as linux mint, although with mint I only ever got it to enable on at a time...

First off, couldn't you have changed those permissions using sudo, instead of logging in as root (which is generally strongly discouraged)?

I've never used BackTrack, but the screenshot on their Wiki looks like Gnome 2.  I think the easiest way to get something like that is to install gnome fallback.  Unfortunately, the specific package to install for gnome fallback differs based on which release you're running, and I don't remember off the top of my head which one is for 12.04, so I'll leave that research as an excercise for the reader/another poster.

---

### Post by Shepherd of Wolves on 2012-11-20
Once I'd gotten rid of the GUI it was easier just to get into root. I've spent enough time as root to know how to keep from doing any damage. Regardless though, I've started spending most of my time as a normal user.

I've got another problem, by the way. I can't seem to install or update anything. I've been trying to download the Ubuntu restricted extras, Ubuntu/Gnome Tweaks, and other basic stuff but I keep getting the repetitive "Failed to Fetch...Cannot Connect to [insert server here]". My connection is fine, I pinged the IPs it gave me each time & all returned 100%. 
     Anyone know what should be done here? Possibly because I just installed the OS, have I forgotten to do something?

---

### Post by cwsnyder on 2012-11-20
Open a terminal and try these:```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```Are there any additional errors reported?  You do know you must install as root or use sudo?

---

### Post by Shepherd of Wolves on 2012-11-20
Those are exactly what I've been trying. And of course I know I need root permissions, I'm not quite that big of a noob.

This is sort of in the middle. There's a lot more Err lines above the first one and many more Failed to Fetch lines after the last.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.15 80]
Fetched 702 kB in 12s (57.1 kB/s)                                              
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.15 80]

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/source/Sources)  Could not connect to ppa.launchpad.net:80 (91.189.95.83). - connect (111: Connection refused)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US](http://extras.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US)  Unable to connect to extras.ubuntu.com:http:

apt-get update looks like its going to work up until...

Fetched 651 kB in 1min 4s (10.2 kB/s)   
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources  Encountered a section with no Package: header

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/main/source/Sources)  400  Bad Request

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by cwsnyder on 2012-11-21
I am sorry if you feel insulted, just trying to make sure all of the bases were covered.  I notice you are getting a LOT of errors in fetching from the mirrors.  Do you normally have problems with your Internet connection?  Have you tried, for example, to access [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) from your browser?  You should go to a page which has Index of / at the top of a fairly standard ftp page.

---

### Post by newb85 on 2012-11-21
I believe your initial problem has been solved, and you're now pursuing the solution to a new problem.  The new problem has nothing to do with the title of this thread, so the people who know the most on the subject aren't likely to read this thread.

You're best off marking this thread as [solved] and starting a new thread for this new problem with an appropriate title.

---

