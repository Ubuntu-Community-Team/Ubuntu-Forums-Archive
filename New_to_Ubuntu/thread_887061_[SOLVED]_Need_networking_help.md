---
title: "[SOLVED] Need networking help"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by kender42 on 2008-08-11
I have been trying for months to access my windows shares to no avail. I have read many of the other posts on this issue and nothing has worked. My windows share are on a network drive attached to a 2wire 2701 that handles the DHCP. When my windows laptop is away from my home network I can't access any of the shares that are on the network drive. Now, since the last update, my home network won't show up for me at all. The router says that I'm connected but no listings in Places -> Network -> Windows Network.

I have become so frustrated with this issue that I'm considering going back to Windows since neither Ubuntu nor any other distro I've tried seems to work. It all worked on a clean install with no updates. As soon as I updated Ubuntu it all went kaput.

---

### Post by halitech on 2008-08-11
> **kender42 said:**
>  When my windows laptop is away from my home network I can't access any of the shares that are on the network drive. Now, since the last update, my home network won't show up for me at all. The router says that I'm connected but no listings in Places -> Network -> Windows Network.
if the laptop is not on the same network you won't be able to access it
> 
I have become so frustrated with this issue that I'm considering going back to Windows since neither Ubuntu nor any other distro I've tried seems to work. It all worked on a clean install with no updates. As soon as I updated Ubuntu it all went kaput.

have you checked the IP addresses on all devices involved to make sure they are all on the same network?

---

### Post by kender42 on 2008-08-11
> **halitech said:**
> if the laptop is not on the same network you won't be able to access it


have you checked the IP addresses on all devices involved to make sure they are all on the same network?

Yes all the computers and the network drive are on the same network. The drive is a stand alone drive connected to the router. But when the laptop is away then I can no longer access the network drive.

My ISP gave us the router and is set to name the home network "HOME".

If you need it here's the listing of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=7a39f04e-0933-41fd-81be-9354d3c43022 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=a7b3604b-61e1-4b0d-809c-720891bd4720 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by halitech on 2008-08-11
no mention of the network drive in your fstab at all

what is the address you are trying to connect to of the network drive?

also, what is the IP address of the actual drive itself?

---

### Post by kender42 on 2008-08-11
> **halitech said:**
> no mention of the network drive in your fstab at all

what is the address you are trying to connect to of the network drive?

also, what is the IP address of the actual drive itself?


The address of the network drive is 192.168.1.67

the home network is using the default ip address allocaton of 192.168.1.*

the entire network drive is set up as a smb share. That's all it will allow me to do but Iomega told me it will work for linux but I can't get support through them. But I don't understand why it worked one day then the next it didn't. I also don't understand why when the laptop goes away the entire network is inaccessible when the laptop is not configured with any shares.

---

### Post by halitech on 2008-08-11
can you ping the network drive?

---

### Post by kender42 on 2008-08-11
yes it pings with no errors

---

### Post by halitech on 2008-08-11
ok, so what is the address you are actually trying to connect to? (ie. smb://???????)

---

### Post by kender42 on 2008-08-11
I'm trying to connect to 192.168.1.67 in the folder named Public

---

### Post by halitech on 2008-08-11
ok but how are you trying to connect? Did you go places - network, are you typing the address in Nautilus? explain how you connect to it.

---

### Post by kender42 on 2008-08-11
I use Places->Network->Windows Network but that's as far as I get now.

Used to be Places->Network->Windows Network->Netdrive->Public and there were all my files.

---

### Post by kender42 on 2008-08-11
Is this where my help ends?

---

### Post by halitech on 2008-08-11
sorry, was off putting my son to bed and watching a little tv and relaxing a little :)

try this, go to Places - COnnect to server. Select Windows Share for the service type, enter the IP address  where it says Server and any other info that is required (ie, username and password if required) and then click on connect. It should create an icon on your desktop. Open that and see if it will connect.

---

### Post by kender42 on 2008-08-12
I understand, I have 2 kids myself. 4 yr and 10 mo. ok so I did that and I keep getting a box that says that I need to enter the user name and password and there isn't even one set. I have the drive set up as a public share so it won't let me even enter a user/pass unless it's set up as private.

The screen won't let me continue

[added]
Ok so it also asks me for a domain which I assume is my network name? So I entered that as well and it just keeps giving me the dialog box asking for a user name and pass. I tried entering in the admin user name and pass and that didn't work either. I am able to access it via HTTP but not mount it. HTTP is only for the admin settings.

---

### Post by halitech on 2008-08-12
ok, so we are making some headway but not much, at least we know we can connect to it and get asked for a username and password.

if you leave the settings blank, will it allow you to click connect?

---

### Post by kender42 on 2008-08-12
> **halitech said:**
> ok, so we are making some headway but not much, at least we know we can connect to it and get asked for a username and password.

if you leave the settings blank, will it allow you to click connect?

No, here's what I get:

Can't display location "smb://192.168.1.67/"
No application is registered as handling this file

---

### Post by halitech on 2008-08-12
taking info from here:
[http://ubuntuforums.org/showthread.php?t=852029](http://ubuntuforums.org/showthread.php?t=852029)

try opening Nautilus and in the address bar type in smb://192.168.1.67/*foldername* and see if it will connect

---

### Post by kender42 on 2008-08-12
How do I open Nautilus? I can't find it in my menus


Oops ok had a brain fart. lol.  Ok I typed it into the address bar and it connected to the network drive. Thank you for that.:D  Is there a way to have a shortcut for it? If not opening it that way is not a problem.

---

### Post by halitech on 2008-08-12
with Nautilus open you can bookmark it one of 2 ways, Press CTRL-D or go to Bookmarks - Add Bookmark and then it will show in the lower left corner for you :)

if we have it solved, mark the thread solved so others will know a resolution is in this thread if they have the same problem :)

---

### Post by wpqc213 on 2008-08-14
While we're on the networking subject maybe you can shed a little light on my problem. Previously I used to be able to go to places and then network and it would show all the machines on my network now all it does is brings up a Windows network icon and if I click on that it brings a Mshome network  which is my network name but it will not display anything from that point on. I havent changed any settings at all..only difference is that I went from Cable ISP to DSL but I'm using the same router and no changes. Also I can ping both ways but thats about it!

Strange situation!

Wayne

---

### Post by halitech on 2008-08-14
would be best to start a new thread with your problem as this thread has been marked solved but have you tried the steps that were given to help Kender42?

---

### Post by wpqc213 on 2008-08-14
Yes I did.. Just got through giving those a try. I have no idea what happened in the first place. Normally when I clicked on network I got all of the boxes listed. Also another strange thing is it lets me access my ubuntu files from the Windows XP boxes without ever needing a password and it was originally setup to require that. I hate to do a complete reinstall due to having to transfer all the data.  Real stumper for me anyway!

Thanks!

Wayne

---

