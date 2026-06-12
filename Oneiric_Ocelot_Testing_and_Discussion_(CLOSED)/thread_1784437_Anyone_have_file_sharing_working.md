---
title: "Anyone have file sharing working?"
date: 2011-06-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-06-16
I have looked on my two installs (32bit & 64bit) and do not have any sharing options in nautilus. When I browse for networks it is slow and fails. Is this part of gnome3 still to come or should mine be working at this point in time with a updated install?

Thanks Bill

---

### Post by cariboo on 2011-06-17
Samba has always worked for this release, and NFS now works with an updated nfs-common.

---

### Post by teh603 on 2011-06-17
I'll be honest, I tend to sidestep things by using vsftpd and opening my home folder on the laptop using an FTP share. Samba and NFS have never worked for me, either.

Surprisingly enough, they *have* worked when I was trying to connect to a Mac running MacOS...

---

### Post by Morbius1 on 2011-06-17
> I have looked on my two installs (32bit & 64bit) and do not have any sharing options in nautilus.
See if you have the following package installed: nautilus-share

---

### Post by sparker256 on 2011-06-17
> **Morbius1 said:**
> See if you have the following package installed: nautilus-share

Yes I have the following version installed 

0.7.2-14ubuntu1 which is the latest version.

Bill

---

### Post by Morbius1 on 2011-06-17
Run the following command:
```
net usershare info
```If you actually had nautilus-share working it would list all the shares you created. I'm hoping that in this case it will produce error messages that can be used to find the source of the problem.

---

### Post by sparker256 on 2011-06-17
> **Morbius1 said:**
> Run the following command:
```
net usershare info
```If you actually had nautilus-share working it would list all the shares you created. I'm hoping that in this case it will produce error messages that can be used to find the source of the problem.
Ran the command regular and sudo with no output. I guess this means that I really don't have any sharing working.
```

bill@billsim-1110-64:~$ net usershare info
bill@billsim-1110-64:~$ sudo net usershare info
[sudo] password for bill: 
bill@billsim-1110-64:~$ 

```
Bill

---

### Post by Morbius1 on 2011-06-17
You haven't created any shares so the "usershare" should have come back with nothing. I was hoping for an error message of some sort.

It looks like the problem isn't usershare ( which is samba ). It's somewhere in nautilus-share or Nautilus itself. When I get a change I'll search launchpad for bug reports on this.

---

### Post by teh603 on 2011-06-17
> **Morbius1 said:**
> You haven't created any shares so the "usershare" should have come back with nothing. I was hoping for an error message of some sort.

It looks like the problem isn't usershare ( which is samba ). It's somewhere in nautilus-share or Nautilus itself. When I get a change I'll search launchpad for bug reports on this.Y'know, I think its actually in samba, because Kubuntu had the exact same problem even with shares created. Shares just don't appear, and its impossible to connect to shares on a local system.

Which again is why I just use an FTP server and log in that way.

---

### Post by Morbius1 on 2011-06-17
Unless I'm misreading the original post the problem is that when you right click on a folder in Nautilus there should be a menu item labeled "Sharing Options". That's what's missing. The user is never given the chance to create the share through Nautilus.

---

### Post by cariboo on 2011-06-17
> **teh603 said:**
> Y'know, I think its actually in samba, because Kubuntu had the exact same problem even with shares created. Shares just don't appear, and its impossible to connect to shares on a local system.

Which again is why I just use an FTP server and log in that way.

With ftp being so insecure, why not use sftp, you don't even need to install any extra client software, just use Nautilus:

```
sftp://user@server
```

---

### Post by Morbius1 on 2011-06-17
I can find only one reference to a missing "sharing options" and that is 3 years old so I'm afraid I don't have an answer for that.

It's no longer clear to me given the direction of this topic if that is what your original problem was.

---

### Post by seeker5528 on 2011-06-17
> **Morbius1 said:**
> I can find only one reference to a missing "sharing options" and that is 3 years old so I'm afraid I don't have an answer for that.

Nautilus share is an optional action that can be installed, until these nautilus action things get updated their working/not-working status will probably be intermittent at best.

Some of these things were working for me, but none of them seem to be working at the moment.

Later, Seeker

---

### Post by sparker256 on 2011-06-17
> **Morbius1 said:**
> I can find only one reference to a missing "sharing options" and that is 3 years old so I'm afraid I don't have an answer for that.

It's no longer clear to me given the direction of this topic if that is what your original problem was.
In that case I must have something configured wrong on both installs. I have tried many things but I guess I have not found the the right thing. Nautilus looks very different on both 11.04 and 11.10 so I was hopping it was somehow related. I have tried to get a screen shot of the right click drop down menu but it disappears when I start shutter.  I have included screen shots from my 11.04 and 11.10 nautilus to see if I have some have something different.

Thanks Bill

---

### Post by Morbius1 on 2011-06-17
Here's a screenshot of Nautilus in 11.04 showing "Sharing Options":

---

### Post by sparker256 on 2011-06-18
> **Morbius1 said:**
> Here's a screenshot of Nautilus in 11.04 showing "Sharing Options":
Boy I missed it yes there was "Sharing Options" in 11.04 gnome2 but I am using 11.10 with gnome3 and I am sure they are gone there. If I boot and old live usb it looks like your screenshot but all this seemed to have change with gnome3.

Bill

---

### Post by Morbius1 on 2011-06-18
Looks like a bug: [https://groups.google.com/forum/#!topic/linux.debian.bugs.dist/0SpS9lUhr-g](https://groups.google.com/forum/#!topic/linux.debian.bugs.dist/0SpS9lUhr-g)

> Package: nautilus-share
Severity: important
Tags: experimentalnautilus-share depends on libnautilus-extension1, which conflicts with
libnautilus-extension1a. The latter is needed for nautilus, brasero,
evince, etc, etc on GNOME3. nautilus-share should depend on the newer
libnautilus-extension1a


---

### Post by jerrylamos on 2011-06-20
Half-way working.  

Narwhal on one pc can copy files from Ocelot on another over the local net.  

Ocelot can see other pc's but any attempt to select the other pc gets "Failed to load share list from server" whatever that means.  

I've got Samba installed and modified /etc/samba/smb.conf to permit read access.

Meanwhile I use sneaker net.....or email attachments.

Jerry

---

### Post by sparker256 on 2011-06-20
> **jerrylamos said:**
> Half-way working.  

Narwhal on one pc can copy files from Ocelot on another over the local net.  

Ocelot can see other pc's but any attempt to select the other pc gets "Failed to load share list from server" whatever that means.  

I've got Samba installed and modified /etc/samba/smb.conf to permit read access.

Meanwhile I use sneaker net.....or email attachments.

Jerry
I have a two fold problem. File sharing through nautilus doesn't seem to be working with gnome3 and mounting cifs doesn't not work with kernel 3.0-0. What that means to me is I have to use kernel 2.6.39 to get to my nas. I can work through it in the short term but both need fixed before release.

Bill

---

### Post by FraggedLocust on 2011-07-28
Maybe I'm missing something, but is Nautilus share the same thing as "personal file sharing" - gnome-file-share-properties - in ocelot? The software centre says it's installed, but when I bring up the window, it says it can't enable the network sharing feature because of missing packages. 

I did install the samba package from the software centre before pulling up that dialogue, so I should (in theory) have the right packages.

Though my system is plagued with report error dialogues, so I may need a new daily build to see if that fixes it.

---

### Post by Morbius1 on 2011-07-28
> but is Nautilus share the same thing as "personal file sharing"

Nautilus share = Samba ( Samba Usershare to be exact )

Personal file sharing is something else altogether. It sets up a baby apache file server and uses avahi to announce it's one and only share at /home/user-name/Public.

---

