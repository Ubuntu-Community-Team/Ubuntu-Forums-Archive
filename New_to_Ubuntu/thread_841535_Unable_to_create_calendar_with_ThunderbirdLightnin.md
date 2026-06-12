---
title: "Unable to create calendar with Thunderbird/Lightning"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by thomsany on 2008-06-26
Hi!! I installed the latest Thunderbird version .14 and Lightning version 8 to integrate Calendars into Thunderbird. For some reason. I can't create nor use any calendar when I run it.
The options are grayed out completely.

Any suggestions on what could be causing this?

Thanks much in advance.

Teo

---

### Post by rburkartjo on 2008-06-26
teo, cant help you on your problem but you might try install sunbird for a calendar it is a stand alone app and it work great in linux/cheesemaker

---

### Post by Bargeman on 2008-09-27
I have the same problem after many attempts.  Anyone have any suggestions.

Running Tbird .17 and Lightning .9 under Hardy Heron.

David

---

### Post by chiefofthejojos on 2008-10-14
This drove me bonkers for quite a while, because I kept searching for the solution and it seemed that no one was talking about it, then I finally found the solution in another thread:
```
apt-get install libstdc++5
```
Then uninstall and reinstall lightning.  I did a little further investigation and found that this is mentioned in the system requirements:
[http://www.mozilla.org/projects/calendar/lightning/system-requirements.html](http://www.mozilla.org/projects/calendar/lightning/system-requirements.html)

---

### Post by Benchamoneh on 2008-11-30
Thanks for this cheif, I got tripped up by this one. I guess this is why people should always read the system requirements!

---

### Post by Xiborg on 2009-06-08
Thank you. I never would have thought of that. Lightning works again.

---

### Post by Pepe Lebuntu on 2009-08-27
Well, you can notch up another person that was wondering about this. Thanks heaps Chief Jojo!

---

### Post by SnarlSlayer on 2009-08-28
Yet another one!  Thanks for figuring that out and posting it!

SS

---

### Post by rafttrip on 2009-10-01
Worked for me as well.

:):)Thanks!!:):)

---

### Post by Pepe Lebuntu on 2009-11-16
It appears that since I installed Ubuntu 9.10 onto my computer, this doesn't work any more. When I tried the "apt-get install libstdc++5" [FONT=monospace]trick again, it said that:
[/FONT]> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate


Any ideas?

---

### Post by spiderglobe on 2009-11-16
Same issue over here... cannot create / add a lightning calender.

Cannot install the   libstdc++5 and also the the alternative compat-libstdc++ cannot be installed.

Using Ubuntu 9.10 (32 bits)

R.

---

### Post by spiderglobe on 2009-11-16
Found the solution:

Search for "libstdc++5_3.3.6-18_i386.deb" (32 bits).

- Install the package.
- Deinstall lightning in the Add-ons of thunderbird
- Install lightning again.

This should do the trick

R.

---

### Post by emigrant on 2009-11-16
Use evolution. Works great.

---

### Post by Pepe Lebuntu on 2009-11-17
> **spiderglobe said:**
> Found the solution:

Search for "libstdc++5_3.3.6-18_i386.deb" (32 bits).

- Install the package.
- Deinstall lightning in the Add-ons of thunderbird
- Install lightning again.

This should do the trick

R.
Thanks heaps mate, that's worked tops!

---

### Post by Pepe Lebuntu on 2009-11-17
> **emigrant said:**
> Use evolution. Works great.
Ah, the good ol' 'Evolution is better then Thunderbird/Thunderbird is better than Evolution" game... :rolleyes:

---

### Post by lallalla on 2009-11-19
> **spiderglobe said:**
> Found the solution:

Search for "libstdc++5_3.3.6-18_i386.deb" (32 bits).

- Install the package.
- Deinstall lightning in the Add-ons of thunderbird
- Install lightning again.

This should do the trick

R.

great thanks! first I added 'deb [http://*ftp.de.debian.org/debian](http://*ftp.de.debian.org/debian)* lenny main ' to the repositories.when I could not find the exact package mentioned, I searched for 'libstcd' and installed libstdc++5 - 1:3.36-18. then uninstalled add-on and reinstalled again and IT WORKS :)

---

### Post by giboulet on 2009-11-26
The package is no more in Karmic. You can download it from Jaunty repository : [http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

Then re-install lightning and it will work again.

---

### Post by ttilberg on 2009-12-01
Thanks for the tips guys -- That was very difficult to find, I thought.
Upon going to their page, it really seemed to lack information -- [http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/) -- the only obvious links were for downloading. Then you select linux, and it didn't have any instructions, or even selecting a distro (which isn't necessary, as it's an add-on) -- I just felt totally in the dark.

Thanks for the help guys. Mozilla should make this more obvious. Typically things under the system requirements heading are more like processor, ram, etc. :popcorn:

---

### Post by Fole on 2009-12-03
I had the same problem with my Lightning installation. I figured out that I had downloaded and installed the add-in via the Thunderbird GUI (Extras->Add-ons->Install). After updating to Ubuntu 9.10 the calendar did not work anymore.
For remediation I uninstalled the add-on from thunderbird and installed the package "lightning-extension" ([http://packages.ubuntu.com/karmic/lightning-extension](http://packages.ubuntu.com/karmic/lightning-extension)). This is maintained in universe.

Florian

---

