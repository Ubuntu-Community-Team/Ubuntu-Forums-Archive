---
title: "calibre problem."
date: 2012-09-08
forum: New to Ubuntu
---

### Post by blueshead on 2012-09-08
When I open calibre I am greeted with this..

[IMG]http://i.imgur.com/OyoYj.png[/IMG]

```
Traceback (most recent call last):
  File "/usr/lib/calibre/calibre/gui2/ui.py", line 397, in start_smartdevice
    self.iactions['Connect Share'].set_smartdevice_action_state()
  File "/usr/lib/calibre/calibre/gui2/actions/device.py", line 243, in set_smartdevice_action_state
    all_ips = get_all_ip_addresses()
  File "/usr/lib/calibre/calibre/gui2/dialogs/smartdevice.py", line 31, in get_all_ip_addresses
    for iface in get_all_ips().itervalues():
  File "/usr/lib/calibre/calibre/utils/mdns.py", line 15, in get_all_ips
    import netifaces
ImportError: No module named netifaces
```

Any fix?

---

### Post by styleeer on 2012-09-09
sudo apt-get install python-interfaces

---

### Post by joewandy on 2012-09-09
I cannot find python-interfaces .. Am I supposed to add the PPA from somewhere ?

mybox@ubuntu:~$ sudo apt-get install python-interfaces
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package python-interfaces

---

### Post by HDave on 2012-09-10
sudo apt-get install python-netifaces

---

### Post by joewandy on 2012-09-10
It works. No more error message. Thanks !

---

### Post by david alston on 2012-12-18
I still have no luck running Calibre, I've tried installing the latest version, and running it from a terminal with:
LIBOVERLAY_SCROLLBAR=0 calibre

but it still crashes Ubuntu 12.10 and throws me out to the log in screen. It worked fine in 12.04, any ideas?

---

### Post by irv on 2012-12-18
did you run this command to install calibre?
```
sudo python -c "import sys; py3 = sys.version_info[0] > 2; u = __import__('urllib.request' if py3 else 'urllib', fromlist=1); exec(u.urlopen('http://status.calibre-ebook.com/linux_installer').read()); main()"
```
And did you take the default location where to install it?

---

### Post by david alston on 2012-12-23
Yes to both questions

---

### Post by irv on 2012-12-24
The next question is what hardware are you using? Is it a Mac or PC?

---

### Post by david alston on 2012-12-25
> **irv said:**
> The next question is what hardware are you using? Is it a Mac or PC?

It's a PC

---

### Post by irv on 2012-12-25
> **david alston said:**
> It's a PC

The reason I asked was because I saw this in the screen shot in your first post.
[ATTACH]229122[/ATTACH]
Have you tried doing a re-install or have you checked for updates? Calibre does come out with updates often.
I have been using it for some time now and have not had any problems with it.

---

### Post by david alston on 2012-12-26
> **irv said:**
> The reason I asked was because I saw this in the screen shot in your first post.
[ATTACH]229122[/ATTACH]
Have you tried doing a re-install or have you checked for updates? Calibre does come out with updates often.
I have been using it for some time now and have not had any problems with it.

That wasn't my first post, I've just hijacked this thread because it seemed to be about a similar problem to mine. I've tried re-installing calibre several times from various sources but no luck.
The problem only started when I upgraded Ubuntu from 12.04 to 12.10. Before that Calibre worked fine.

---

### Post by irv on 2012-12-26
I am running Ubuntu 12.10 and Calibre version 0.9.11 and every thing seems to work. I am running the 64bit verison.

Here is the command that I used to install it.
```
sudo python -c "import sys; py3 = sys.version_info[0] > 2; u = __import__('urllib.request' if py3 else 'urllib', fromlist=1); exec(u.urlopen('http://status.calibre-ebook.com/linux_installer').read()); main()"
```
[ATTACH]229162[/ATTACH]

I did a clean install of 12.10 not an upgrade. After installing 12.10 and re-installing Calibre, I just copied the folder "Calibre Library" back over to my home folder and everything just worked.

If you did the default install of Calibre, maybe you can delete the folder calibre under /opt and rename your Calibre Library folder and then try reinstalling it.

---

### Post by Zill on 2012-12-26
> **david alston said:**
> ...I've tried re-installing calibre several times from various sources but no luck...
This statement worries me slightly.  There are only two sources you should have installed from:  The Ubuntu repos for 12.10 *or* the Calibre web site.  If you have tried to use other sources then it is *possible* dependent packages may have been corrupted.

Although I do not use Ubuntu 12.10 my experience with earlier versions of Calibre is that, contrary to most programs, it is best to install directly using the code given in the [Calibre website]("http://calibre-ebook.com/download_linux").

irv has advised you (correctly IMO) to rename your Calibre Library folder and given the website code to install Calibre v0.9.11.

I suggest you remove all traces of previous installations of Calibre and then install again with this code.  Post the output shown by the terminal during this installation process as this will help diagnose any problems.

See if a "clean" Calibre runs and, if so, then try it with the data in your old Calibre Library folder.

---

### Post by david alston on 2012-12-27
> **irv said:**
> I am running Ubuntu 12.10 and Calibre version 0.9.11 and every thing seems to work. I am running the 64bit verison.

Here is the command that I used to install it.
```
sudo python -c "import sys; py3 = sys.version_info[0] > 2; u = __import__('urllib.request' if py3 else 'urllib', fromlist=1); exec(u.urlopen('http://status.calibre-ebook.com/linux_installer').read()); main()"
```[ATTACH]229162[/ATTACH]

I did a clean install of 12.10 not an upgrade. After installing 12.10 and re-installing Calibre, I just copied the folder "Calibre Library" back over to my home folder and everything just worked.

If you did the default install of Calibre, maybe you can delete the folder calibre under /opt and rename your Calibre Library folder and then try reinstalling it.

OK, I did an upgrade to 12.10, not sure about doing a clean install as I'm not too hot with linux and would fear losing my stuff.
I just tried your suggestion, deleted all of /opt/calibre, renamed the Calibre library and no change, Calibre starts, then throws me out to the log on screen.

Thanks for the suggestions so far, I'll be away for a week, but will try any new advice over the W/E 5/6 Jan

---

### Post by irv on 2012-12-27
Next time you try running calibre, try running it from a terminal. Then post the error message you get in the terminal. This might help to tell us what is going on.
Just open up a terminal and type
```
calibre
```

---

### Post by Zill on 2012-12-27
> **david alston said:**
> OK, I did an upgrade to 12.10, not sure about doing a clean install as I'm not too hot with linux and would fear losing my stuff...
Just a quick word of friendly advice...  If your "stuff" is important to you then please *always* keep backups!  If you do this then you will have no fears about reinstalling as a backup of your data can quickly be restored.

Hard drives can (and do!) fail - often without any warning!  "Finger-trouble" can also cause loss of data.  Regular backups are the best defence against both of these mishaps. ;-)

---

### Post by david alston on 2013-01-05
> **irv said:**
> Next time you try running calibre, try running it from a terminal. Then post the error message you get in the terminal. This might help to tell us what is going on.
Just open up a terminal and type
```
calibre
```

That gives 'Error unable to open ./mtpz data for reading'

---

### Post by oldos2er on 2013-01-05
Do you have libmtp installed? ```
apt-cache policy libmtp9
```

---

### Post by david alston on 2013-01-06
> **oldos2er said:**
> Do you have libmtp installed? ```
apt-cache policy libmtp9
```

Yes.

libmtp9:
  Installed: 1.1.4-1
  Candidate: 1.1.4-1
  Version table:
 *** 1.1.4-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        500 [http://ubuntu.mirror.cambrium.nl/ubuntu/](http://ubuntu.mirror.cambrium.nl/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by Zill on 2013-01-06
> **david alston said:**
> That gives 'Error unable to open ./mtpz data for reading'
[This thread]("http://www.mobileread.com/forums/showthread.php?t=193481") gives two suggestions from  kovidgoyal, Creator of calibre:
> You have set an incorrect value for a tweak. Delete

~/.config/calibre/tweaks.py 
and
> unable to open ~/.mptz-data for reading

comes from the libmtp library and can be ignored, it is not an error.
Does Calibre actually run OK after you have deleted the "tweaks.py" file?

---

### Post by david alston on 2013-01-06
> **Zill said:**
> [This thread]("http://www.mobileread.com/forums/showthread.php?t=193481") gives two suggestions from  kovidgoyal, Creator of calibre:

and

Does Calibre actually run OK after you have deleted the "tweaks.py" file?

No, I've deleted tweaks.py and the problem remains

---

### Post by Zill on 2013-01-06
> **david alston said:**
> No, I've deleted tweaks.py and the problem remains
So, if I understand the situation correctly,,,
[LIST]
[*]Calibre was working fine with Ubuntu 12.04
[*]You upgraded Ubuntu from 12.04 to 12.10
[*]You have tried re-installing Calibre several times from various sources.
[*]You have deleted all of /opt/calibre and renamed the Calibre library.
[*]You have reinstalled the latest Calibre using the code on the Calibre website.
[*]You have deleted tweaks.py but the original problem remains.  i.e. Calibre starts, then throws you out to the log on screen.
[/LIST]
If all this is correct then it looks to me like your Ubuntu installation is borked.  All I can suggest now is that you make sure you have backups of all your data and then do a clean install of Ubuntu.  Restore all your data and reinstall Calibre using the code from the Calibre website.

---

### Post by david alston on 2013-01-07
> **Zill said:**
> So, if I understand the situation correctly,,,
[LIST]
[*]Calibre was working fine with Ubuntu 12.04
[*]You upgraded Ubuntu from 12.04 to 12.10
[*]You have tried re-installing Calibre several times from various sources.
[*]You have deleted all of /opt/calibre and renamed the Calibre library.
[*]You have reinstalled the latest Calibre using the code on the Calibre website.
[*]You have deleted tweaks.py but the original problem remains.  i.e. Calibre starts, then throws you out to the log on screen.
[/LIST]
If all this is correct then it looks to me like your Ubuntu installation is borked.  All I can suggest now is that you make sure you have backups of all your data and then do a clean install of Ubuntu.  Restore all your data and reinstall Calibre using the code from the Calibre website.


Seems a bit brutal, however nothing else has worked so I'll give it a go...

OK everything is fine now, and I don't seem to have lost any important stuff. Thanks all for the suggestions and help.

---

