---
title: "Symbolic Links in Mythtv"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by rosco99 on 2008-08-26
I have successfully installed Ubuntu 8.04 and Mythtv using the guidance of MythTV Ubuntu Installation Guide part 1 and 2.
[http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php).  My TV card and Remote is supported. I am having a problem with the following commands
"Now all we need to do is tell the applications how to interpret the lirc events. To do this, the lircrc files needs to be in two locations: ~/.lircrc and ~/.mythtv/lircrc. The best method is to use a symbolic link:

cp lircrc ~/.lircrc
cd ~/.mythtv
ln -s ../.lircrc lircrc"

The terminal won't accept these commands there are neither commands nor locations for lircrc

Is there any other service I need to install to allow me to do the above.

---

### Post by anotherdisciple on 2008-08-26
Hmmm... I'm not exactly sure why they didn't specify a location, but open a terminal and type:

```
locate lircrc
```

that should find all the paths that include that... then just use that path. If it doesn't exist... then you must not have created it.

---

### Post by OffAxis on 2008-08-26
I'm with anotherdisciple...I think your lircrc file isn't in the right place. You can download a copy of it here:
[http://parker1.co.uk/myth/lircrc](http://parker1.co.uk/myth/lircrc)

and then just save it to your /home/user/.mythtv/ folder as **lircrc**
and then create the link.

It's worth noting that the lircrc location may have moved again, this time to ~/.lirc/mythtv; on my mythbuntu install my ~/.mythtv/lircrc file is just a link to the ~/.lirc/mythtv configuration file. I'm not sure if this re-location was within mythtv itself or just part of mythbuntu.

---

