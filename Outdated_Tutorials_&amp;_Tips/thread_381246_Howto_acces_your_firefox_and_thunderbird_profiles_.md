---
title: "Howto: acces your firefox and thunderbird profiles created in windows"
date: 2007-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by madtom on 2007-03-10
On a dual-boot system, you of course want to use the same profiles of FF and Thunderbird in ubuntu as in windows (as these profiles include settings, themes, extensions, cookies, bookmarks, emails, email-account settings and stored passwords). Here's how to do that.

if you're using winXP, your profiles will most probably be stored on a NTFS volume. To have full access to your profiles (read and write), you need to use ntfs-3g to mount the volume instead of the standard method. Read [**here**]("http://ubuntuforums.org/showthread.php?t=217009") how to set up ntfs-3g. **..of course, you'll use ntfs-3g at your own risk ** ...though i've used it quite extensively and didnt have any problems whatsoever... but i can of course only speak for myself.

now on how to actually load the profiles in ubuntu. for that, you need to go to the profile manager in both firefox and thunderbird. to do this, open a terminal and enter in the case of firefox:
```

mozilla-firefox -profilemanager

```
and in the case of thunderbird:
```

mozilla-thunderbird -profilemanager

```

there you create a new profile, and where you enter the profile name hit "choose folder". Usually the profiles are located at
/hdXX/Documents and Settings/user/Application Data/Thunderbird/Profiles/
and
/hdXX/Documents and Settings/user/Application Data/Mozilla/Firefox/Profiles/

select the profile, hit "open" and click on finish. You can now delete the initial profile if you want.

---

