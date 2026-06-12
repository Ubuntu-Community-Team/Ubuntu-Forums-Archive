---
title: "Oldest Thunderbird for Ubuntu 12.04 ?"
date: 2014-11-18
forum: New to Ubuntu
---

### Post by Greg Mueller on 2014-11-18
Rebuilding computer after hard drive screwup

Ubuntu 12.04
KDE Plasma Desktop 4.8.5
Thunderbird 31.2.0

Everything is going fine.... almost. I have salvaged everything but am having two problems that are just irritating and not catastrophic.

1) I can't get Thunderbird to start maximized.
2) I don't use the "Quick Filter Bar" Toolbar but each time I start the computer it is back

Is there a profile file that I can edit somewhere?
Is this a bug in this version of Thunderbird?
Can I install an older version of Thunderbird instead of this one?
**What is the oldest version I can use with Ubuntu 12.04?**

Thanks

---

### Post by deadflowr on 2014-11-18
11.something.

Looking at apt-cache policy for thunderbird, I see this
```
thunderbird:
  Installed: 1:31.2.0+build2-0ubuntu0.12.04.1
  Candidate: 1:31.2.0+build2-0ubuntu0.12.04.1
  Version table:
 *** 1:31.2.0+build2-0ubuntu0.12.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
        100 /var/lib/dpkg/status
     11.0.1+build1-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```
Notice that precise-updates-and precise-security list version 31.X.
But precise lists 11.X.
This was the original version.

I would not recommend going back to it, but that's the oldest version.

I would guess my main reason to not go back is that in between the 20 versions, many bugs and security holes were quashed and fixed.


As far as  maximizing the windows you can see about setting a window rule in ccsm for thunderbird.
ccsm(compizconfig-settings-manager > window rules > Maximize option +(to add) I would use grab and grab the thunderbird window.
Once you set thunderbird, or mail to open maximize, it'll open that way forever.

And as to why it keeps loading like it is a new profile(quick filter, etc) I do not know.
The profile, though, is in /home/you/.thunderbird.
In you only have one profile it should be named something like 24345treter.default, or something weird like that.
You can also try managing your profiles as well using the terminal command
```
thunderbird -ProfileManager
```

---

### Post by Habitual on 2014-11-18
"salvaged" implies a recovery of a previous ~/.thunderbird directory|profile. 
You may wish to create a new profile in Tbird and see what happens.
Here's some older versions: [http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/](http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/)

Personally, I'm stuck on Thunderbird 17.0.2 precisely **for** the quick search which didn't seem present in new versions under Linux Mint 17 Qiana / Xfce
Hope that helps.

---

### Post by Greg Mueller on 2014-11-18
> **Habitual said:**
> "salvaged" implies a recovery of a previous ~/.thunderbird directory|profile. 
You may wish to create a new profile in Tbird and see what happens.
Here's some older versions: [http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/](http://sourceforge.net/projects/ubuntuzilla/files/mozilla/apt/pool/main/t/thunderbird-mozilla-build/)

Personally, I'm stuck on Thunderbird 17.0.2 precisely **for** the quick search which didn't seem present in new versions under Linux Mint 17 Qiana / Xfce
Hope that helps.


Yes
I could access some portions of the old hard drive so I grabbed all that I could

How do I create a new profile?

---

### Post by Habitual on 2014-11-18
> **Greg Mueller said:**
> How do I create a new profile?
> **deadflowr said:**
> You can also try managing your profiles as well using the terminal command
```
thunderbird -ProfileManager
``` "Create Profile" button...
If the new profile behaves the way you like, then we can proceed with copying account meta-data and contents to the new profile directory.

If you have more than 1 mail account you only need setup one of them to see if Tbird is behaving.

Please let us know...

---

### Post by Greg Mueller on 2014-11-18
When I use the command "thunderbird -ProfileManager" in the terminal, it simply switches to the running version of Thunderbird

---

### Post by Greg Mueller on 2014-11-18
Ok wait a minute
I closed Thunderbird and ran the command and now we are getting somewhere

---

### Post by Greg Mueller on 2014-11-18
This ain't worth it
I'll just keep maximizing and resetting

fooy

---

### Post by mastablasta on 2014-11-19
I had a profile messed up on Firefox and that is exactly how you do it (on Thunderbird as well). first you would create a new profile, setup emails and then move the old data to new profile.

I am not sure why it would start minimized. you could try to remove it completely, reinstall, create new profile and then continue from that. then you would move just the emails to new profile and not the personal settings as well. or you could look at the KDE settings and do something like this but in reverse: [URL="http://askubuntu.com/questions/342481/kubuntu-13-04-run-applications-minimized-at-startup"]http://askubuntu.com/questions/342481/kubuntu-13-04-run-applications-minimized-at-startup
[/URL]
item 2: Go to **System Settings > Window Behavior > Window Rules**
modify -> size and positions

then check if it's set to minimized.

as for the quick filter bar maybe it needs to be unpinned.

if settings are not being saved perhaps the owner of files is wrong or has read only access.

---

### Post by Greg Mueller on 2014-11-19
I got the answer over at the mozilla forum
Turns out the settings in previous version were stored in a file called** localstore.rdf** I change the name to** localstore.old** and it started behaving properly. Came up fine this morning.

---

### Post by Habitual on 2014-11-19
> **Greg Mueller said:**
> I got the answer over at the mozilla forum
Turns out the settings in previous version were stored in a file called** localstore.rdf** I change the name to** localstore.old** and it started behaving properly. Came up fine this morning.

Good Job and Well Done!

---

