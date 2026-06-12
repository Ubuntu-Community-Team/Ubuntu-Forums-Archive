---
title: "failure to download extra data files"
date: 2017-01-19
forum: New to Ubuntu
---

### Post by a.dusty.trail on 2017-01-19
Ttf-mscorefonts-installer

I've been seeing this error message for months. I looked into it.I know what it is.
But what I can't figure out is why if it's never going to work
('ll would think if it could be fixed it would have been by now) why is ubuntu still trying to get it

I would think that ubuntu would release an update that would bypass getting the file.

Yes I tried to get the file from the proper location
No I could not
No I'm not interested in getting the same file someplace else. 
The the file officially can be found else where why is ubuntu not looking there?

---

### Post by #&amp;thj^% on 2017-01-19
Sounds more like a rant than a help request>
Have a look here: [http://askubuntu.com/questions/766491/failure-to-download-extra-data-files-with-ttf-mscorefonts-installer-on-ubuntu](http://askubuntu.com/questions/766491/failure-to-download-extra-data-files-with-ttf-mscorefonts-installer-on-ubuntu)
Or just uninstall the fonts.
Best of Luck

---

### Post by bearlake on 2017-01-19
> **a.dusty.trail said:**
> Ttf-mscorefonts-installer

I've been seeing this error message for months. I looked into it.I know what it is.
But what I can't figure out is why if it's never going to work
('ll would think if it could be fixed it would have been by now) why is ubuntu still trying to get it

I would think that ubuntu would release an update that would bypass getting the file.

Yes I tried to get the file from the proper location
No I could not
No I'm not interested in getting the same file someplace else. 
The the file officially can be found else where why is ubuntu not looking there?

This usually works very well.

```
sudo apt purge ttf-mscorefonts-installer
```

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

1st code gets rid of the current package.

2nd to download the 3.6 version of the package to your Downloads folder.

3rd to install the new package.

---

### Post by howefield on 2017-01-19
> **a.dusty.trail said:**
> Ttf-mscorefonts-installer

I've been seeing this error message for months. I looked into it.I know what it is.
But what I can't figure out is why if it's never going to work
('ll would think if it could be fixed it would have been by now) why is ubuntu still trying to get it

I would think that ubuntu would release an update that would bypass getting the file.

Yes I tried to get the file from the proper location
No I could not
No I'm not interested in getting the same file someplace else. 
The the file officially can be found else where why is ubuntu not looking there?

You are ranting at the wrong people, go add your insight to the bug reports. 

Thread closed.

---

