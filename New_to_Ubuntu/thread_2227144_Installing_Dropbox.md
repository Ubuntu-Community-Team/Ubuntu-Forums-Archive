---
title: "Installing Dropbox"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by chriscaraveo on 2014-05-30
please excuse my frustrations..i've been at this for the last couple of days and nothing seems to work

12.04 LTS here. i was kind of tossed into Linux after my PC guy decided to put Ubuntu on my laptop after it crashed. fun way to learn i guess. . .slowly learning that this is not the OS for people that want things to work correctly out of the box....

it's starting to appear as if nothing i download works properly on this OS, regardless of if i get it off of a website, a torrent or from Ubuntu's own official software center. I've installed Dropbox both from the software center and  .deb (both the 32 bit and 64 bit) their website and nothing is working. digging through coding is starting to get to me, so i'd really appreciate the help

i'm getting the "Dropbox requires Nautilus to restart" blah blah blah error, except, i've literally tried just about everything and it's still not working. i've tried reinstalling the 32 bit and 64 bit and when i copy/paste the command > ~/.dropbox-dist/dropboxd from this link [https://www.dropbox.com/install](https://www.dropbox.com/install) i get this message
32-Bit
> chris@chris-laptop:~$ ~/.dropbox-dist/dropboxd
Traceback (most recent call last):
  File "dropbox/client/main.py", line 10, in <module>
  File "dropbox/overrides.py", line 509, in <module>
  File "dropbox/overrides.py", line 491, in __override_ctypes_pythonapi
  File "cffi/api.py", line 55, in __init__
ImportError: /home/chris/.dropbox-dist/cffi-0.7.2-py2.7-linux-x86_64.egg/_cffi_backend.so: wrong ELF class: ELFCLASS64

after being confused about what ELFClass is (because i'm installing Dropbox, not playing D&D) i googled it and assumed i installed the wrong package, so i tried the other

64-Bit says this
> ~$ ~/.dropbox-dist/dropboxd
/home/chris/.dropbox-dist/dropbox: 1: /home/chris/.dropbox-dist/dropbox: Syntax error: "(" unexpected

so i went over to this link: [http://www.tuxgarage.com/2012/04/install-dropbox-in-ubuntu-precise.html](http://www.tuxgarage.com/2012/04/install-dropbox-in-ubuntu-precise.html) and tried doing everything it says on there (removing it, trying to reinstall)

when i get to this part:

> sudo apt-get update

it says this in the terminal:

> Fetched 3,524 B in 9s (367 B/s)                                                
W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/precise/Release](http://linux.dropbox.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'Main/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.


^^and that's just me trying every which way around the problem


when i actually had it install from the software center (the .deb files don't work, but the install from the ubuntu software center does), i click the icon, nothing happens for awhile, then i'm prompted that Nautilus needs to be restarted. i tried rebooting, logging off and logging on, nothing happens, it still gives me the same error. when i click "restart Nautilus" **ALL** of my icons on my desktop dissapear except the icon bar on the left of my screen. if i log off and log back in, i'm still prompted that Nautilus needs to be restarted.

i'm assuming the problem is that i need to change the location of folder, but alas, have no idea how to work this OS..i've tried every [SOLVED] answer on these forums and nothing seems to work

---

### Post by cariboo on 2014-05-31
I'd suggest you call your computer guy, and get him to get dropbox working for you, as it looks like he just installed an older version and left you to it. 

It take time to learn how to use an operating system no matter what it is, you've probably used Windows all your life, and spent most of that time learning how to use it. The biggest problem is that most of what you've learned about using a computer is no longer valid. 

The first thing you need to do is determine what version you are using, click the gear icon in the upper corner, then select About This Computer, the result should look something like this:

[[IMG]http://i.imgur.com/FSDXXlcl.png[/IMG]](http://imgur.com/FSDXXlc)

I'm using a devlopment version, but the screenshot should look similar, as you can see as far as OS type is concerned, I'm using the 64bit version.

Next go here:

[https://www.dropbox.com/install?os=lnx](https://www.dropbox.com/install?os=lnx)

and download dropbox for you version. You need to download one more package before continuing on, open the Software Center and run a search for gdebi and install it.

[[IMG]http://i.imgur.com/1e3YOt6l.png[/IMG]](http://imgur.com/1e3YOt6)

Next open the File Manager and navigate to Downloads, right click the package you downloaded and select Open with Gdebi Package Installer:

[[IMG]http://i.imgur.com/Eto5NOIl.png[/IMG]](http://imgur.com/Eto5NOI)

follow the prompts, and you should have a working dropbox installation.

---

### Post by deadflowr on 2014-05-31
Firstly, do this

Open the program called "Update manager".
(Ignore anything that might come up in the main window, for now)
Look for a button in the lower left corner called "settings", and click on it.

In the new window click the tab marked "other software".
Look for the entry{ies} for linux.dropbox.(or anything that might say dropbox)
Uncheck them, and then click OK.
(you'll be prompted for a password when you first uncheck the entry(ies).
When they are unchecked, close that window and now back at the main update manager window, click on the button marked "Check".
When that is done, see if the button for install is usable(meaning not greyed out) If it is usable then click on the button to install.
This will update the system to the most up-to-date state.
Most problems like this tend to be because the packages are all out of sync/out-of-date with each other.

If any problems arise, post them here, in this thread.

Once you know that the system is up-to-date, then fixing the nautilus-dropbox integration problems should a little easier to do.

Of course, at this point, I am completely unsure as to which version of dropbox is actually installed.¿

---

### Post by buzzingrobot on 2014-05-31
The  "Dropbox requires Nautilus to restart" popup can be safely ignored as long as you see that Dropbox opened a Nautilus window and has begun moving files. Worse comes to worse, it goes away when you log in and out or reboot. 

If "nautilus-dropbox" is installed from the command line ("sudo apt-get install nautils-dropbox") it displays this: ```

Please restart all running instances of Nautilus, or you will experience problems. i.e. nautilus --quit
Dropbox installation successfully completed! You can start Dropbox from your applications menu.

```

The GUI install just displays that slightly less useful message.

(In any case, all this amounts to is that small symbols are displayed on icons when Nautilus displays the Dropbox folder to indicate their synchronization status. They can't be displayed until Nautilus restarts.)

The "failed to fetch" error means just that:  The updater tried and failed to access the files in the repository addressed by that entry.  Often it means the entry is wrong (typo?) or outdated (e.g. that directory on that server no longer exists) or, sometimes, that server is temporarily offline. 

It's a "Best Practice' to look in the Ubuntu repositories for software, rather than resorting to random searches on the web. Safer, too.  Be very cautious about advice and instructions at web sites and blogs that recommend installing software from these other sites. If nothing else, they age rapidly and never seem to be removed or updated. You will see references to installing software from "PPA's". These are little repos for software that had been packaged for installation on Ubuntu but has not been accepted for inclusion in the official repos and, as such, is not supported.  I.e., you assume the risk. Often, they provide very new revisons for testing purposes.  PPA's have pages at launchpad.net and it is wise to Google that page and read what it says. 

PPA's are often very useful and widely used.  But, do your homework.

(For example, this week I've seen several sites/blogs hyping copy-and-paste instructions for installing the newest release of the Evolution mail program.  What they don't say is that it is a testing and debugging release, as the very latest releases of Linux software often are.  If you install it and run it, the first thing you see is a popup from the developers warning to expect problems and thanking you for participating in their testing efforts.)

---

### Post by chriscaraveo on 2014-05-31
i appreciate the responses. nice to see a helpful community behind this OS.
 
i'm pretty sure my system is as updated as it's going to get at this point because i'm pretty anal about that (i've been using Ubuntu for around 6 months now and haven't really had any issues up until these last couple of days), but for safe measure i installed what updates were lingering around to no avail. i already had the gdebi package installer downloaded from when i first got my hands on Ubuntu. the answer from cariboo is actually the furthest i've gotten with this though. your post was helpful in the fact that it helped me realize i'm running 32bit, so i attempted to DL the 32bit .deb from the link. Deadflowr's response was equally as helpful. I had a feeling that old version/new version's were the issue, because I've tried installing from the terminal, the software center and .debs. I did what you said and it updated. 

now i keep getting a random pop up (whenever it feels like it) instructing me to install the Dropbox Daemon, it installs it and then gets to the "unpacking dropbox" phase and stops at 98%, then the window closes after awhile, and it prompts me to install the Dropbox Daemon again


[IMG]https://imagizer.imageshack.us/v2/880x550q90/841/q9rw.png[/IMG]

---

### Post by buzzingrobot on 2014-06-01
Well, I don't know what's going on, but that is what you should see, once. The package used to install Dropbox contains that routine from Dropbox that pulls the actual Dropbox daemon down from the Dropbox server and installs it.

Your earlier mention that all the desktop icons and the panel vanish when you click "Restart Nautilus" seems to me an indication that something else is going on that is interfering with the install. I've found that popup request does not respond to clicks until the install completes, but  it's never broken the display like you report (there's may be an "Information is Available" icon in the Launcher.  Try closing it there.) (Although I don't keep icons on my desktop.) As a generic shot in the dark, you might try temporarily disabling the startup apps, etc., you've added, reboot, and try again. Also, if you done any specific non-standard modifications to the system, back them out.

---

### Post by chriscaraveo on 2014-06-12
seems like this issue is more than me just being new to Linux...bumped..can somebody please help me fix this?

---

### Post by JeQhdMD on 2014-06-12
Even though I've installed dropbox without issue on 3 systems (over the past couple years), it seems besides installing the "stand-alone" deb file, I also had to go to the dropbox and register a user name and password.  Also, have you modified the stock Ubuntu desktop - - perhaps uninstalling nautilus or replacing it with another linux file manager (like dolphin or thunar, etc.)?

Taking another approach at this, you could go into Ubuntu Software Center and install "Synaptic" - - a tried and true (and speedier) package manager than the default Ubuntu Software Center.   Then, you could try to "completely remove" dropbox (or uninstall), and then re-install via synaptic the package entitled "nautilus dropbox" . . . once installed successfully, you'll get a dropbox  icon and also the panel widget.

Another thing you can check is whether your software source directories are correct.   If you need clarification about that, please ask.

---

