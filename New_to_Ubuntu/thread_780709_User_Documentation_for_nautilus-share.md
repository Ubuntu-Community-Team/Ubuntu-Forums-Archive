---
title: "User Documentation for nautilus-share?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by ofb on 2008-05-03
It's not working on my Hardy, and I want to know what it's supposed to be able to do. Where's the documentation for the new method of Ubuntu Networking?

All I've got: [http://freshmeat.net/projects/nautilus-share/](http://freshmeat.net/projects/nautilus-share/)

"Nautilus Share allows you to quickly share a folder from the GNOME Nautilus file manager without requiring root access. It uses Samba, so your folders can be accessed by any operating system."

That's everything. The links to the nautilus-share homepage & demo don't work. 

In Hardy I right-click Sharing Options, select "Share this folder" and a name, and don't select write access or guest account. Result: nothing. The folder gets a sharing icon but the share does not show up on my Gusty machine, nor does it show up locally in the Samba Shares of the Hardy machine.

Both machines can see the Samba Shares of my Gusty machine, which are set up using shares-admin.

Both machines have identical Guarddog firewall configurations, and the same username. LAN is a null modem cable between dedicated ethernet cards.

Before upgrading my second machine to Hardy, both were Gusty using shares-admin for SMB and NFS and worked fine. So I'm kinda confused about why I can't get the nautilus-share method to work.

---

### Post by hyperair on 2008-05-03
Check out /usr/share/doc/nautilus-share/Readme.Debian.gz (Use zcat or zless to read it). Special configuration is needed by smb.conf.

---

### Post by ofb on 2008-05-04
Thanks, hyperair!

Here's the contents of README.Debian

```
nautilus-share for Debian
-------------------------

A quick and easy way to have it running (must be done as root):

#export USERSHARES_DIR="/var/lib/samba/usershare"
#export USERSHARES_GROUP="samba"
#mkdir ${USERSHARES_DIR}
#groupadd ${USERSHARES_GROUP}
#chown root:${USERSHARES_GROUP} ${USERSHARES_DIR}
#chmod 01770 ${USERSHARES_DIR}
#mv /etc/samba/smb.conf{,.bak}
#cp /usr/share/doc/nautilus-share/examples/smb.conf /etc/samba/
#/etc/init.d/samba restart

You must add users who can share folder in the usershare group, in this example the group is "samba":

#usermod -a -G samba your_username

 -- Thierry Randrianiriana <randrianiriana@gmail.com> Wed, 23 May 2007 09:14:49 +0300

```

That's so 'quick and easy' that to get the file over to this machine I typed 'share-admin' in terminal, clicked unlock, added password, clicked Add, selected folder, clicked Share, & voila: instant working SMB.

So... why on earth are we supposed to use nautilus-share instead of share-admin? It appears to be harder to use (especially for Ubuntu's target audience), and it doesn't handle NFS. What's the feature or features it adds that caused this change?

And is mine busted somehow? Are Ubuntu Hardy users actually expected to do all that, or does just right-clicking the share in Nautilus work for most people?

---

### Post by hyperair on 2008-05-04
I wasn't aware that nautilus-share was used by default. However, once set up, it provides a very easy user interface for adding Samba shares. Just right click on a folder, click Sharing properties, type a share name, tick a few checkboxes and you're done. The drawback is that Samba requires usershare support enabled in its configuration. And no, there isn't any NFS support.

---

### Post by ofb on 2008-05-04
> I wasn't aware that nautilus-share was used by default.

If I understand correctly (that's a big If), Yes. If you right-click in Nautilus to share in Gusty/Feisty/Edgy you got shares-admin. With Hardy you get nautilus-share, and shares-admin has been removed from the menu.

There's a launchpad bug thread about it for Hardy beta, but it's long and unfortunately has more sniping than information. By the end of the thread, shares-admin had been reincluded for the Hardy install (though not on the menu), but nautilus-share is considered the thing to use for reasons I haven't made out yet.

I get the idea the Desktop team thinks shares-admin is flawed. I'm not sure how because mine works. Presumably there's something it doesn't do which is desired for the greater user base. Also they think nautilus-share is easier & does something needed that I haven't figured out yet - probably the same thing.

And they don't care a fig about NFS, which I guess is fair because it's not easy for the target Ubuntu user to use. Unfortunately not all Linux apps can use SMB shares, and one of the things shares-admin did was simplify NFS setup. But if there isn't a project underway to complete the modernization of NFS, then I can see the Desktop team not caring to preserve the feature.

Anyway... thanks. A few days later I see I can just go ahead and do networking the way I always have, but I'm a little miffed that I can't manage to "get it" with how nautilus-share is supposed to work for the new user.

---

### Post by hyperair on 2008-05-04
Okay, I've checked the dependencies and it's true that nautilus-share became the default. However, Samba wasn't configured for it. If you upgraded from Ubuntu Gutsy, then your smb.conf file would have been brought along from there, and so usershare support has not been added to the configuration file. I'm not sure about the default though. If you want to use nautilus-share, you can just copy /usr/share/doc/nautilus-share/examples/smb.conf to /etc/samba/smb.conf. That'll automatically enable usershares on Samba.

In addition I think you need to add your user to the group "sambashare" via users-admin, but I'm not too sure about that.

Why they switched is probably because shares-admin required root privileges and messed aroudn with root configuration, whereas nautilus-share allows you to configure stuff separately for every user, without root privileges.

---

### Post by ofb on 2008-05-04
Mine's a fresh install over existing /home.

> In addition I think you need to add your user to the group "sambashare" via users-admin, but I'm not too sure about that.

Yeah, this is where I slow down. My thought is the Desktop team would have made the new setup at least as easy as they'd made shares-admin under Gusty. So I'm expecting nautilus-share to either work from its GUI, or have some sort of pop-up telling me to go configure something to complete the process.

Under Gusty you only become root to use share-admin to declare shares. IIRC, that's it - SMB works after that point and the only further config is for the sorry few who care to wrestle with NFS. It was impressively no-fuss.

I've got an idea that nautilus-share doesn't require root at all, enabling each user to declare shares within their own files. Ohh... I wonder if share-admin required more configuration if you had a number of users and groups. nautilus-share might cut through that more easily, which would be a blessing for the new user.

Which would leave only the question of how the new method is meant to be setup. Perhaps it's meant to work from the GUI and my system has a glitch, or perhaps there is a another step and that's the user documentation I'm after: Networking for Hardy.

We seem to be in the classic new-feature bind for Ubuntu: No initial user documentation. People complain at launchpad and get told (rightly but unhelpfully) 'that's a feature not a bug, so don't post that here.' While the greater community plays catch-up at ubuntuforums and eventually makes the documentation that should have shipped.

Result is a lot of new users are told how to do things 'the way we used to' rather than the simpler way their Ubuntu is now capable of. I've been guilty of that myself. I've been trying to avoid it with networking, which has been steadily improving, but I'm a little tripped up with Hardy.

---

### Post by bodhi.zazen on 2008-05-04
With 8.04 there is a small "bug".

To share a directory, 

1. Right click on the directory -> select share -> choose to install samba.

2. Log out and back in.

3. Repeat click on the directory -> select share -> give share name and select rw option if desired.

Described here : [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

You can edit the samba congfig file if you need / want more advances options.

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by ofb on 2008-05-04
That's odd. I'd tried rebooting but with no difference. I'll have to see what happens when I convert the second box to Heron.

---

