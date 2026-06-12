---
title: "Migrating mail lists"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by hatrack on 2008-09-26
Hi all !

I am an absolute newbie to Ubuntu (2 days accumulated experience so far !) and I am trying to migrate my mail lists from Thunderbird (latest version) running under Win2k to a full Ubuntu installation on a new machine. I have set up a mail account under Thunderbird on this and confirmed that this is working correctly by sending and receiving mail.

I have followed the instructions in "Ubuntu 8.04 > Emails & mail account settings > Export Email messages from Thunderbird" down to the end of Item 4. I now have the relevant files copied to a CD. The directory structure on this is — Mail\Local Folders\ pop.xxx, etc.

I have so far spent nearly 14 hrs (!) trying to find a destination in Ubuntu into which to copy these files.

Can anyone please advise me what to do now.

Many thanks in advance ...

---

### Post by Partyboi2 on 2008-09-27
You should be able to copy your thunderbird profile (one that has a .default extension)  from windows (Documents and Settings>YourName>Application Data>Thunderbird>Profiles) over to ubuntu.
When you have copied over your windows thunderbird profile open up your /home folder and go to View>Show Hidden Files then look for a folder named .mozilla-thunderbird. Copy the windows profile folder to there. Then rename it to what the profile name is that is already in .mozilla-thunderbird. You may want to make a backup copy of the orginal  .mozilla-thunderbird default profile first.

---

