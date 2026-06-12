---
title: "Feature request, plain-text package listings"
date: 2012-07-05
forum: Recurring Discussions
---

### Post by Rallg on 2012-07-05
This is a request for a feature that, I believe, would be very simple to do. Perhaps it can already be done by users who know how to write a good shell script, but I would like to see this as a regular package that could be used without need for scripting knowledge:

Often, after updates, some problem is introduced. This is common in beta testing, and perhaps once in a while it happens during regular use. What is needed is a "system restore" feature that does NOT rely on backup packages, just plain-text lists. It would work this way:

1. There are a few text files, usually found in /etc, which the user might manually edit. These files are small, shell scripts. Instead of having just one backup file for the last edit, keep an indefinite number of backups, each of them catalogued. The same would apply to certain hidden files in the administrator's home folder, the ones that are used for settings and initialization of various system functionality.

2. From time to time, the system makes a comprehensive, plain-text list of ALL files and folders, everywhere. The list would be for the specific file versions. There would be a way for the user to create the list upon request. The list would have an indefinite number of backups.

3. In case of severe problem, the user would login to command shell, and request that an earlier file list be restored. Then, the shell would load the requested list of packages, and restore them. If a package is the same as before, it is kept. If the listed package is older, it is fetched and restored. Normally that would require an internet connection to fetch from repositories. However, the ability to fetch from a disk (or USB) location would be helpful, because a dysfunctional system might not be able to connect to the Internet. If an older package is requested but not downloadable (due to lack of connection), then the screen would display a list of packages that could be fetched using a different computer.

Note that this does not require a great deal of disk space. The packages themselves are not being archived, just a plain-text list of every file and folder (maybe zipped).

It would be even better if the list could be passed to another computer, where a program such as WUBI could read the list, and be asked to install exactly what appears on the list.

This would allow users to restore to a "known good" configuration, and also to duplicate that "known good" configuration on a new installation.

Or, may I ask: Does this capability already exist, but I just didn't know about it? The current Backup tool, with or without Ubuntu One, does something different.

---

### Post by ventrical on 2012-07-05
Great idea. I had proposed this about 2 years ago as did many others.. but I think your idea is rather unique.

  I have been brain-storming and doing thought experiments on this, I have yet to write a flowchart but with Ubuntu , I think it would be really easy.

  I am making a side note on your idea and if I have time to contribute, I will.  Perhaps I can even write a psuedo-code flowchart.

---

### Post by Quackers on 2012-07-05
Post moved to Recurring Discussions

---

### Post by Rallg on 2012-07-05
@ventrical: Keep in mind that many of the listed files and folders are actually hard or symbolic links to others. Then there's the permissions thing.

---

