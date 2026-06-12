---
title: "HOWTO: Encrypted firefox settings, history, etc. and nautilus thumbnails"
date: 2006-08-23
forum: Outdated Tutorials &amp; Tips
---

### Post by peabody on 2006-08-23
This HOWTO describes how to keep firefox's user settings in some type of encrypted folder.

*Ahem*, well, I'm not going to go into just *why* somebody would want this, but this is a fairly good way to run a private instance of firefox.  Combined with tor and privoxy, this is a great way to surf anonymously.

**Step 1: Setup some type of encryption.**

I used [this howto](http://www.ubuntuforums.org/showthread.php?t=148600&highlight=encfs) to setup a folder with EncFS.  I then streamlined the process via [this webpage](http://gentoo-wiki.com/TIP_EncFS) at Gentoo which lists a couple of very nice GUI scripts for automating the mounting and unmounting.  However you choose to do it, find something that works for you.

**Step 2: The Script**

Copy and paste this into something like gedit and save it in the Encrypted folder.  If you want to copy over your current firefox settings, copy the .mozilla folder (it's hidden so be sure to view hidden files within nautilus) from your home to the encrypted folder.

```

#!/bin/sh

cd `dirname $0`
HOME=`pwd` firefox

```

Make sure all current instances of Firefox are closed.  Then double click the script.  If everything was done right, this Firefox will store its settings in the encrypted folder away from prying eyes.  I use a different theme with this instance of Firefox to help differentiate which version I'm running.

The current shortcoming is that you need to close all firefox instances before switching between the private and normal firefox.  The instances are separate, so bookmarks and settings aren't synced between the two.  There's probably a way around this but I'm too lazy to look into it just yet.

**And just for fun...**

Nautilus stores its thumbnails in ~/.thumbnails.  Not only can this get big (my thumbnail folder grew to over 700megs!), it's a bit scary as it can function as a sort of database for every piece of por--err, every image file you've ever looked at through Ubuntu.

First thing to do is to move it:

```
mv ~/.thumbnails /path/to/encrypted/folder
```

Then symlink that sucker back.

```
ln -s /path/to/encrypted/folder/.thumbnails ~/.thumbnails
```

This'll keep the actual thumbnails in the encrypted folder, so desktop snoops won't be able take a peek at your thumbnails if you unmount the folder.  While the folder is mounted, however, you get your nice thumbnail functionality.

Finally, if you want, you can install this cron job to zap your thumbnails on a regular basis.  Type in a terminal:

```
crontab -e
```

Paste the following into the text file somewhere:

```
0 22 * * * find $HOME/.thumbnails/ -type f -atime +90 -exec rm {} \;
```

Save quit and if you receive no error messages this should help purge your thumbnails from time to time to prevent them from gobbling up your harddisk like there's no tomorrow.

---

