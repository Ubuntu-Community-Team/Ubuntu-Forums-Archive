---
title: "Viewing Windows Network Folders"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by myst1c on 2008-06-18
I have a home network, setup on windows. I would like to share files between the windows network and my machine, which runs linuxmint, a distro based on ubuntu.

anyway, i can see the network, but when i click it, the other computers, which run windows, do not show up as being on the network. i have wireless connectivity between my linux machine and the other computers.

if any other information is needed, let me know

---

### Post by Victormd on 2008-06-18
Can you ping your windows machine from ubuntu (probably yes)?
Instead of doing what you just did, go to PLACES>NETWORK and on the top left, there is an icon that looks like a note pad, click it to togle to text-based location bar. You should now see something like this:
> network:///
remove that and type
> smb://IPADDRESS
where IPADDRESS is the ip of your windows machine, and hit enter (note that you don't have to have samba installed for this to work). This should show you the contents of your windows machine. Then you'll be able to browse your shared folders.
If you're using vista, you'll need to do some tinkering with your vista sharing/permissions to get it to work properly.

---

### Post by myst1c on 2008-06-19
alright, good ****... now... how do i view files on MY machine from the other computers?

---

### Post by webarchitect on 2008-06-19
Well you may want to try using Hamachi...maybe that can help you out to see the files faster...

---

### Post by Victormd on 2008-06-19
> **myst1c said:**
> alright, good ****... now... how do i view files on MY machine from the other computers?

1. Go to SYSTEM>ADMINISTRATION>USERS AND GROUPS, click on the Unlock button, then click on Manage Groups, scroll until you see the SAMBASHARE group (again, no need to install samba), select it, click on properties and check ROOT and your user name, click Ok, close, close, restart...

2. Then, right click the folder you want to share and click on "Sharing Options," set the sharing type you'd like and that's it.

If you don't have the SAMBASHARE group, do step 2, it will ask if you want nautilus to set the permissions for you, you answer yes, will get an error, and the SAMBASHARE group will be created, then go back to step 1.
(I'm adding this part because when I did this, I did step 2 first and due to the error, as forced to do step 1 then 2 so I don't know if the SAMBASHARE group exists by default.)

Your ubuntu machine should now show under your network places in windows.

---

### Post by myst1c on 2008-06-19
unfortunately, that didn't work... any other ideas?

---

### Post by SamerBerjawi on 2008-06-19
I have the same problem, and I did what you guys said and it also didn't work.
I can't even share a folder.. When I try to share a folder I get

'net usershare' returned error 255: net usershare add: cannot share path /media/disk/iPod Touch as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

Note that I have samba installed

---

### Post by azurepancake on 2008-06-19
> **myst1c said:**
> unfortunately, that didn't work... any other ideas?

I recommend following this guide [http://samba.netfirms.com/](http://samba.netfirms.com/). It is short and very straight forward. I used it for setting up my Ubuntu file server and it worked perfectly.

---

### Post by billgoldberg on 2008-06-19
Samba can be tricky.

That's why I prefer SSH, much easier to set up and safer.

---

### Post by Dedoimedo on 2008-06-19
Hello,

This is something I wrote, see if this helps you:

[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)

And especially the sharing part:

[http://www.dedoimedo.com/computers/linux_commands.html#network_sharing](http://www.dedoimedo.com/computers/linux_commands.html#network_sharing)

Cheers,
Dedoimedo

---

