---
title: "HOWTO: Easily set up Samba on Feisty"
date: 2007-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by silhouette on 2007-08-18
This is a simple guide to connect a Linux box that acts as a Samba server to a Windows Samba client, so that your Windows box can read and write to a folder on your Linux box, since this seems to be the most popular configuration for Samba. Hope you find it helpful.

----
Here's what we'll be doing in this guide:

[list]
[*] On the Linux box
[list]
[*] Installing Samba
[*] Configuring Samba
[*] Setting up a Samba user
[*] Modifying the iptables firewall to allow incoming Samba traffic
[/list]
[*] Testing it out on the Windows box
[/list]

Before you install Samba on the Linux box, you first need to make sure that the computer that you will be transferring files to has a static IP address, if possible. If you have a true router, it should let you modify the DHCP settings such that your machines are given fixed leases. If you're a cheapskate and you went with your ISP's router (like we did), chances are this option's not available to you. In this case, you'll still be able to use Samba, but because you're not guaranteed that your Linux box (or your Windows computer, for that matter) will have the same IP address every day (because most routers set DHCP to renew the lease every 24 hours) you may have to configure both machines to "see" each other every time you want to share files. If you don't have to use Samba that much this may not bother you, but it's definitely impractical in a business environment :)

With this out of the way we can install Samba:

```

sudo aptitude -V install samba smbfs

```

Now we have to configure Samba, like so:

```

cd /etc/samba/
sudo mv -f smb.conf smb.conf.old
sudo nano smb.conf    # or gksu gedit smb.conf, or kdesu kate smb.conf

```

Copy and paste the following and place it into the file (you can remove comments if you want). You can learn more about what all these options do by running [font="monospace"]man smb.conf[/font].

```

[global]
  # Hostname on this machine (open a command prompt; it's the part after the @).
  netbios name = ...
  # Description of this machine.   
  server string = ...
  # Name of your home network (make sure this jives with what your Windows box has).
  workgroup = ...

  # Don't quite know what these do but I'm sure they're important:
  announce version = 5.0
  socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

  # The format Samba password info is stored in (don't have to touch).
  passdb backend = tdbsam
  # We want to force whoever is trying to access the Samba share to log in.
  security = user
  # You want this b/c many people leave their passwords blank.
  null passwords = yes
  # Leave this alone.
  username map = /etc/samba/smbusers
  # Don't know what this does.
  name resolve order = hosts wins bcast

  # Affects the address used to access the share folder on the Windows machine.
  # Makes it possible to enter "\\COMPUTER_NAME\public" instead of "\\192.168.1.69\public"
  # (only works if you have a static IP).
  wins support = no       
                            
  # Don't know what these do.
  syslog = 1
  syslog only = yes

# The part in brackets is the name of the share folder.
# This will be included in the address you enter in Windows to access the share.
[SHARENAME]                          
  # Name that will appear when you run "net view" in Windows.
  comment = ...
  # The path to the folder you're sharing on this machine.
  path = ...
  # Whether or not users on the other end can browse the share folder.
  browseable = yes
  # Whether or not users on the other end can change its contents.
  read only = no
  # Affects the permissions of the files that be given to files that come in from a Windows machine.
  # The DOS permissions are bitwise-AND'ed with the setting here to obtain the end permissions.
  create mask = 0777            
  # Same as above, except applies to directories.
  directory mask = 0777
  # Who will end up owning the files that come in. Probably best to just use your username,
  # since you're the one who'll be accessing this stuff :)
  force user = ...
  # You can make this the same as the last.
  force group = ...
  # Make sure that Windows knows that "FILE" and "file" are *not* the same :)
  case sensitive = yes
  # This will show up in the sidebar when viewing the share folder in Windows,
  # it doesn't really affect anything.
  fstype = Samba

```

After you're doing making the necessary changes to the config file, to make sure that you got the config file right, you can run:

```

testparm

```

If there are any errors in the config this will print warnings.

If you didn't get any warnings, you're good to go; just run

```

sudo /etc/init.d/samba restart

```

to get Samba to see the new changes.

Now, we need to create users just for Samba:

```

sudo smbpasswd -a USERNAME     # Now Samba knows about this user.
sudo smbpasswd -e USERNAME     # Now the user is enabled.

```

Make sure that [font="monospace"]USERNAME[/font] refers to an actual user on your Linux box. You can either create a dummy user to use just for Samba, or you can use your username.

Okay, configuration is complete, so let's see if we can access the share from your Windows box. In Windows, pull up Explorer (My Computer or however you like) and enter this in the address bar: [font="monospace"]\\YOUR.IP.ADDRESS\SHARENAME[/font]. [font="monospace"]YOUR.IP.ADDRESS[/font] is the IP address of the Linux box (which you can check by running [font="monospace"]ifconfig[/font]) and [font="monospace"]SHARENAME[/font] is whatever you entered in [font="monospace"]smb.conf[/font] (see above). Windows should ask you for a username and password. Enter the same ones that you just made when you ran [font="monospace"]smbpasswd[/font].

In an ideal world you would be presented with the contents of the share folder, but most likely, Windows will have trouble connecting and spit back an error. What I found I had to do was configure the firewall on my Linux box to allow incoming Samba connections. Yes, you do have a firewall, and it's called iptables. As it's more a command-line tool, I've never messed with it directly, but rather its GUI sibling, Firestarter. So the next thing you need to do is install that:

```

sudo aptitude -V install firestarter

```

After this is done, go to **System -> Administration -> Firestarter** (or, if you're not using GNOME, bring up a terminal and run [font="monospace"]firestarter[/font]), and after entering your password, click on the *Events* tab.

Now, while you watch the events list, switch to your Windows machine and try to access the share. When you get the error, look back in the events list. Do you see some messages in there like this?

```

+---------------------------------------------------------------+
|Time            | Port | Source       | Protocol | Service     |
+---------------------------------------------------------------+
|Aug 17 21:34:12 | 138  | 192.168.1.97 |   UDP    | Samba (SMB) |
|Aug 17 21:37:05 | 137  | 192.168.1.97 |   UDP    | Samba (SMB) |
+---------------------------------------------------------------+

```

These entries represent attempts by Windows to communicate with your Linux box, but Firestarter prevented that from happening. Let's show it who's boss. Switch to the *Policy* tab, pull-down the drop-down menu there, and choose [font="monospace"]Inbound traffic policy[/font]. Right-click within the first pane ("Allow connections from host") and choose [font="monospace"]Add Rule[/font]. In the text field, enter the IP address of the Windows machine (you can get this by pulling up Command Prompt and running [font="monospace"]ipconfig /all[/font]), and press OK. Then right-click within the second pane and choose [font="monospace"]Add Rule[/font]. Pull down the *Name* menu and choose [font="monospace"]Samba (SMB)[/font]; the *Port* field should be updated automatically (to [font="monospace"]137-139 445[/font]). For *When the source is* choose [font="monospace"]Anyone[/font]. Press OK. Then click on the **Apply Policy** button to save the changes.

Now you should be set! Try it out by switching back to Windows and accessing the share again. It should work. Test it out by copying a file into the folder. It should show up on your Linux box... magic, huh?

**RESOURCES**
[list]
[*] [HOWTO: Setup Samba peer-to-peer with Windows](http://ubuntuforums.org/showthread.php?t=202605) (gave me 60% of what I needed to know)
[*] [SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) (the other 40%)
[*] [Ubuntu Guide: How to share folders with read/write permissions](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_home_folders_with_read.2Fwrite_permissions_.28Authentication.3DYes.29) (helpful with configuring Firestarter)
[*] [The Samba Debug Howto](http://aeronetworks.ca/samba-debug-howto.html) (in case you get stuck, though I didn't find I need this)
[/list]
-----

Feel free to chime in if you have any comments or words of wisdom. Also, if you have any questions, I'll try to give you some help but keep in mind that I'm rather new at this stuff -- answers to more complicated sorts of things (like printer sharing) are best left to other guides.

---

