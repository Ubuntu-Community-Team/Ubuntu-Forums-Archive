---
title: "DVD::RIP Cluster setup"
date: 2009-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by ub-newbie on 2009-07-19
Setting up a DVD::RIP cluster

I'm a noob, so there might be "extra" steps in this, but this is how I got it working.  Most of this info came from me stepping through the instructions posted at [www.exit1.ort/dvdrip/doc/cluster.cipp]("http://www.exit1.ort/dvdrip/doc/cluster.cipp")  .  I added all the stuff I learned along the way, especially the Jaunty specific stuff.

Packages (software) I put on both/all computers:
DVD::RIP  - is not required on the Client
OpenSHH
Nfs-kernel-server (which should install NFS-COMMON and PORTMAP)

2 (or more) computers running Ubuntu.  I am running Jaunty.  They are networked together, with static IP's, and holes poked in each PC's firewall (no router work was required).  I am running the Cluster Control from the Server.  

Server IP – 192.168.1.1         Client IP – 192.168.1.2


First, set up a SSH public key  - I don't really remember how I did this, so you are kind of on your own for this.
Here are the changes that I remember I made to SSHD:
1. I did add "PermitUserEnvironment yes" to the bottom of SSHD, but not sure if it was required or not.
2. Set "PermitEmptyPasswords yes", it was set to "no"
3. Uncommented (deleted the # in front of) "AuthorizedKeysFile	%h/.ssh/authorized_keys"
4. Found this article on PAM
	- Empty passwords not allowed with PAM authentication.

To enable empty passwords with a version of OpenSSH built with PAM you must add the flag nullok to the end of the password checking module in the /etc/pam.d/sshd file. For example:

    auth required/lib/security/pam_unix.so shadow nodelay nullok

This must be done in addition to setting "PermitEmptyPasswords yes" in the sshd_config file.

There is one caveat when using empty passwords with PAM authentication: PAM will allow any password when authenticating an account with an empty password. This breaks the check that sshduses to determine whether an account has no password set and grant users access to the account regardless of the policy specified by PermitEmptyPasswords. For this reason, it is recommended that you do not add the nullok directive to your PAM configuration file unless you specifically wish to allow 	empty passwords.       [http://www.openssh.com/faq.html#3.2](http://www.openssh.com/faq.html#3.2)

Here are instructions I found in another forum post about how to set up the SSH key:

1. On you Server, type: ```
ssh-keygen
```    
when asked for a password, do NOT enter anything, just press ENTER.
2. Copy ID_RSA.PUB, and paste it into a file called ~/.ssh/authorized_keys on the Client  
(remember, the "." in the ".ssh" means that it is a hidden directory)
3. test your success by typing on your Server: ssh yourusername@192.168.1.2

----------------------------------------------------------
DVD::RIP Software Notes

1.  There is one change to DVD::RIP, you have to change the perl code so the SSH connection doesn't time out.  From "Ubuntuforms.org", "*Whomever21*" – 
Change the timeout from 5 to 10 in /usr/share/perl5/Video/DVDRip/Cluster/Node.pm. 
Make sure you restart dvdrip-master after that change, restart dvdrip and attempt the connection again.

2.  To run in cluster mode, "you MUST keep the default values for vob/avi/temp directories, and you must not set a base directory outside of your default database directory"  This will cause NFS problems.
-----------------------------------------------------------

Set up PORTMAP (I did this on both Server and Client)

	type: ```
sudo dpkg-reconfigure portmap
```

This will bring up a screen where you select "DO NOT BIND LOOPBACK"
-----------------------------	
On your **Server**

	type: ```
sudo gedit /etc/exports
```

to the bottom of the file add:
	/home/???/dvdripdata (rw, no_root_squash,sync,subtree_check,insecure,anonuid=????,anongid=????)

Why these settings:
	1. rw – read and wright permission
	2. no_root_squash – "lets root users on client workstations have the same privileges as the root user on the NFS file server"
	3. sync – forces writes to be done synchronously. i.e. the client waits for write to complete before returning control to the user.  Sync is default over async.			
	4.  Replace the ??? with whatever your user name is on this computer
	5.  insecure – gives NFS access to clients on non-standard ports. If you leave off the "insecure" and it doesn't work, check the logs for "illegal port"
(gksu gnome-system-log).  
	6. For the **anonuid** and **anongid** you need to open "System-Admin-System Monitor" and under the Processes tab, find the ID number of the DVD-RIP MASTER.  Use that number in place of the ???? for these 2 values.  This is ONLY NECESSARY if you are using different user names on your different computers.  

Assumptions:  
1. Your DVD::RIP data directories you set up in the Cluster Configuration are /home/???/dvdrip-data   
(replace the ??? with whatever your user name is on this computer)

Also, for Jaunty, you need to edit /ETC/DEFAULT/NFS-COMMON and set NEED_STATD=YES
(some sources say "NO", but when I tried to mount, I got "ensure rpc.statd is running", so I changed it to YES.)

If you need to manually start RPC, type ```
sudo rpc.statd
```

Now you can

	```
sudo exportfs –a –v 
```

This will cause the running NFS server to re-read the "exports" file.  If you get problems here, check your directory and file permissions (I set them to user, group, and guest RW using "shares-admin"), then reboot. 

---------------------------------------
**On your Client(s)**

Create a directory on the Client, something like 
"/home/????/dvdripdata-c"

You should now be able to test you NFS mount on the Client by typing: (this will mount it this one time, to make it permanent, you have to make changes to FSTAB.

	```
sudo mount 192.168.1.1:/home/doug/dvdrip-data /home/doug/dvdripdata-c
```

At this point, the Cluster was working, I added the Server as a Cluster member (so both computers were working on the job).  
-----------------------------------------------
To make the mount happen automagically, add this line to the end of "/etc/fstab" (type:   gksu gedit /etc/fstab)

```
192.168.1.1:/home/doug/dvdrip-data /home/doug/dvdripdata-c nfs rsize=8192,wsize=8192,timeo=15,intr
```
	
This will not take effect until you reboot.

----------------------------------------------------------------
Some handy commands.  
	to restart PORTMAP, NFS-COMMON, and NFS-Kernel-server
	sudo /etc/init.d/portmap restart
	sudo /etc/init.d/nfs-common restart
	sudo /etc/init.d/nfs-kernel-server restart

To open the Shared folder tool:
	shares-admin
I used this to share the folders.  I opened them up to user and group Read/Write

Also, if you have problems, check the logs (gksu gnome-system-log) to make sure your traffic is getting past your "/etc/hosts.allow" file. 

----------------------------------------------
If you find something I did wrong, or some changes that need to be made, please contact me.

---

### Post by clmbngbkng on 2009-08-22
Thanks for this tutorial, I'm going to give it a try soon!

---

