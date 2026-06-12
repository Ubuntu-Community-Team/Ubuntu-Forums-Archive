---
title: "HOWTO Install and Configure Likewise Open and Likewise CIFS"
date: 2011-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by hooks on 2011-03-15
For a long while, I've been toying with Likewise Open and Likewise Open CIFS for authentication on my linux machines to my windows domain at home and for file sharing on same.

On the surface, Likewise looks like the easiest alternative for AD authentication, but it is a bit quirky, and I'd like to help you (and future me) avoid the same headaches.

In this guide, I will install Likewise CIFS on a Ubuntu 10.04 32-bit VMware virtual machine. As great as Ubuntu is (it will continue to be my favorite operating systems until Canonical gives Gnome the boot), the Likewise packages in the Ubuntu repositories don't really work all that well.

Instead, download the installer directly from Likewise. Make sure you click on the Sfx link for the .sh installer script. It comes with all the prerequisites, and it's about 5.5MB. Once you have that in place on the machine, you're ready to go!

**[SIZE="3"]Install Likewise CIFS[/SIZE]**

To install Likewise CIFS using the .sh installer, first chmod the installer to make it executable:

```
$ sudo chmod a+x LikewiseCIFS-5.4.0.8046-linux-i386-deb.sh
```

Then Run the installer:

```
$ sudo ./LikewiseCIFS-5.4.0.8046-linux-i386-deb.sh
```

Answer 'Yes' to accept the licenses. Don't worry, they're all "Open Source" (GPL, BSD, etc).

Also, answer 'Yes' again to continue the install.

The script will unpack a few things, set up a few things, and finally tell you the install is complete. Now, for the next step...

**[SIZE="3"]Join your domain[/SIZE]**

Quirk #1: Before you ever fire off another Likewise executable, edit your /etc/hosts file (sudo nano /etc/hosts). You must do this for everything to work properly. Add this entry to the file just below the line beginning with "127.0.0.1":

```
[IP Address of your Domain Controller] [FQDN of you Domain Controller] [FQDN of your Domain]
```

Quirk #2: You must also edit the /etc/nsswitch.conf file. The line that reads:

```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Should be changed to read:

```
# hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Beneath that line, add this line:

```
hosts: files dns
```

When you install Likewise from the Ubuntu repositories, you get a fancy GUI you can get to by going to System > Administration > Active Directory Membership. If all you want to do is authenticate to the domain, this is a fine solution. However, the file server (Likewise CIFS) doesn't really play nicely if you do it this way. Instead, since we installed from the .sh installer script, we'll need to use the command line:

```
$ /opt/likewise/bin/domainjoin-cli join [FQDN of your Domain] [Domain Admin Account Name]
```

The program will ask you for your password. Go ahead and type it in.

At this point, go ahead and reboot your machine.

Being thorough (and a bit paranoid), I like to also confirm on the Domain Controller the computer was added.

**[SIZE="3"]Configure the file server daemon[/SIZE]**

Quirk #3: For reasons not understood nor known to me, the Likewise CIFS daemon (/etc/init.d/srvsvcd) does not start automatically when the OS boots. The beautiful thing about Linux is, though, that you can make it start by default because you can change the things you don't like!

If you want the file server to start automatically, just run these commands:

```
$ cd /etc/init.d
$ sudo update-rc.d -f srvsvcd defaults
```

Quirk #4: Likewise Open does not automatically register itself to the DNS

Create a file in /etc/init.d and call it whatever you like. I put a script there for all my Linux machines called "startup" where I add scripts that need to run just once, and I put this there.

Edit that file to look like this:

```
#!/bin/bash
/opt/likewise/bin/lw-update-dns
```

Then, make the file executable:

```
$ chmod a+x startup
```

Finally, make it run every time the OS boots just like we did with srvsvcd:

```
$ sudo update-rc.d -f startup defaults
```

Reboot your machine.

**[SIZE="3"]Create your share[/SIZE]**

Quirk #5: When you make a share, you must do it as a domain admin. I haven't been able to find a way around this and, quite frankly, it's not that important to me since I am a domain admin on the domain I'm testing with. If you know a way, feel free to leave a comment.

Final step: create the share.

Login to a Windows machine on the domain as a domain admin, Hit [Windows Key]-R for a Run prompt, and type "mmc."

Go to File > Add/Remove Snap-in...

In the dialog, select "Shared Folders" and click "Add >"

Select the "Another Computer" radio button and type the name of the file server in the text box. Click "OK"

Click "OK" again, and navigate to "Shares" under "Shared Folders" in the left-hand pane.

Right-click in the right-hand pane and select "New Share..."

In the Create Share Wizard, click "Next" to go past the welcome page.

In the next page, type the address of the folder you would like to share. In this case, instead of writing it with slashes as you would in Linux, use backslashes and ad a "C:" at the beginning of the address.

Click "Next"

Type the name of the share and, optionally, a description.

Click "Next"

Set the permissions on the share as you please.

Click "Finish"

Voila! A Windows Share with Domain permissions off a Linux machine! This is as easy as it's going to get with software that's currently available. Now on to finding the Holy Grail.

Questions? Corrections? Thanks? Don't be afraid to post it below!

---

### Post by hooks on 2011-04-07
Likewise CIFS is built on Likewise Open 5.4. Apparently, Likewise is not planning to make a version build on Likewise 6, so I found another alternative. Check out my newest post: [http://lordandhooks.com/blog/likewise-open-6-and-samba/]("http://lordandhooks.com/blog/likewise-open-6-and-samba/")

---

