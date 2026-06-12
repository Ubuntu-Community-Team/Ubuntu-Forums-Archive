---
title: "Samba used to work now doesn't"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by masterjonny on 2008-08-01
As the title implies. I got Samba working following the tutorial found on these forums, then since it was updated it just doesn't.

I followed the guide again but no luck. I can see the shares from my Windows laptop but when I try and connect I get the error

"\\SUPANOVA\Images is not accessible. You might not have permission to use this network resource. Contact the administrator of the server to find out if you have access permissions.

The group name could not be found"

Like I say it used to work, until I updated samba of the update thingy built in (2.6 I think but I donno why, could be miles wrong lol), then my laptop just stopped being able to connect.

Any help would be good as my desktop is pretty much only a media server, so if it can't do this it fails at life lol.

---

### Post by ingeva on 2008-08-01
> **masterjonny said:**
> 
The group name could not be found"


Check if your workgroup definition is the same as the workgroup in Windows. It's in the smb.conf file. Just search for "Workgroup".

If it's OK, set up a special share for that directory, make sure you're allowed to write and in a home network you can probably set "guest ok = yes" as well.

A new share can be set up under a new section that you can call "images" for example.

Regards from a new user who have just done this.

---

