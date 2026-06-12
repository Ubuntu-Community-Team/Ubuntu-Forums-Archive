---
title: "Easy Samba Installation"
date: 2010-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by pricetech on 2010-12-13
Let me start by saying this has always worked for me over several installs. (I tinker a lot)

I'm currently using Ubuntu Lucid / Edubuntu Lucid with Samba installed this way.

There's very little command line work to do, so it should be easy for a beginner to follow this.

While this is certainly not the only way to deploy Samba, I do find it to be the easiest.

Start by installing Samba and the configuration tool.  I do this through Synaptic.

System - Administration - Synaptic Package Manager

Search for "system-config-samba" without the quotes of course, and select it to be installed.

Click Apply to instal Samba along with the configuration tool.

Close Synaptic.

Back up your original "smb.conf" as follows;

Open a terminal

Applications - Accessories - Terminal

and type the following;

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.orig
```

Enter your password when prompted and close the terminal when done.

You'll now find your configuration tool under

System - Administration - Samba

Where you can set your workgroup (under Preference - Server settings) add Samba users (under Preferences - Samba Users) create shares and assign access to those shares (File - Add Share or click the plus sign (+) in the toolbar and follow the prompts), etc.

When you close this tool, Samba should begin working.  All the "grunt work" is done in the background.

HOWEVER:

Because of an issue that has cropped up, though not every time, I recommend one more step.

Open a terminal again and type

```
sudo smbpasswd username
```

Replaceing "username" with one of the Samba users you set up earlier.  You'll be promted for your password, then twice again for the password associated with "username"

Once the command is finished, you can close the terminal.

Samba should now work without a hitch.

---

### Post by gilch on 2011-02-16
I tried that... went up to
System - Administration - Samba

But Samba was not there under Administration???

---

### Post by gilch on 2011-02-18
Thanks.
I had done it before and I guess it hadn't worked. I tried again and this time I can get System-Administration-Samba.
Sorry, but what do I do with Server Settings  ... %h server (Samba,Ubuntu) ?
(you're dealing here with a very uninformed bloke).
Gilles

---

