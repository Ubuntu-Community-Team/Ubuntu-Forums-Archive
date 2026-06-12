---
title: "Having Problems Importing New SSH Key"
date: 2024-07-22
forum: New to Ubuntu
---

### Post by wyred451 on 2024-07-22
I am new to Ubuntu.  I installed Ubuntu Core 32 on a Raspberry Pi 3b.  When I booted the Pi with Ubuntu Core for the first time, it went though a setup.  I connected to my Wi-Fi and the next step was to import the Public key from my account at "login.ubuntu.com".  I generated 4096 bit public and private keys using Putty Key Gen and saved them to my hard drive.  I can't figure out how to import the new public key. The comments read "[COLOR=#111111][FONT=Ubuntu]Insert the contents of your public key (usually [/FONT][/COLOR]~/.ssh/id_rsa.pub[COLOR=#111111][FONT=Ubuntu], [/FONT][/COLOR]~/.ssh/id_dsa.pub[COLOR=#111111][FONT=Ubuntu], [/FONT][/COLOR]~/.ssh/id_ecdsa.pub[COLOR=#111111][FONT=Ubuntu] or [/FONT][/COLOR]~/.ssh/id_ed25519.pub[COLOR=#111111][FONT=Ubuntu])." and "[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Note: Only SSH v2 keys are supported."  [/FONT][/COLOR]If the files are stored on my Windows PC, what goes in the text box?  I've tried entering the file path to the public key and copying and pasting the key contents via notepad but get "[COLOR=#111111][FONT=Ubuntu]Invalid SSH key type:"

Thank you for taking the time to read this.[/FONT][/COLOR]

---

### Post by currentshaft on 2024-07-22
ssh-copy-id pi@<ip address of raspberry pi>

---

### Post by TheFu on 2024-07-22
The comments assume you are using Unix or Linux as your workstation.

I haven't used PuTTY in a long time, but I do recall that the format PuTTY keys used were non-standard.

However, the built-in ssh in Win10 and Win11 comes with ssh-keygen.exe and you can create standard keys using it.  Sadly, ssh-copy-id.exe is not part of MS-Windows, so you get to manually copy the public key to the Linux box.

I know nothing of "importing  a new key".  
The typical way is to create a new key on the client machine, then copy the public-key part to teh remote system.
```
# Step 1:  Run on the client as the normal user:
   $ ssh-keygen -t ed25519

# Step 2:  Run from the client to the server:
   $ ssh-copy-id -i ~/.ssh/id_ed25519.pub username@remote
```

That's it. If you want to have different keys for different remote systems, just run keygen with a different *-i filename* specified. 

I've never used Ubuntu Core. I don't like the idea of someone else being between my computers and me.  I suppose if you've decided to run Ubuntu Core, then there are specific reasons why that choices was made.  

Don't know how much any of this helps or even if it does.  For how to do things the PuTTY way, I suspect you'll need to read the PuTTY documentation.  If you are on a Linux workstation, there's little reason to use putty.  Just use any terminal program you like with ssh directly.  The ~/.ssh/config file can make that really, really, convenient by filling in any specific settings or/and a different identity, as needed.  Further, the  ~/.ssh/config file is used by all ssh-based tools on the system, so any settings there apply to all the tools you might use.

---

### Post by wyred451 on 2024-07-22
Unfortunately, I can't copy the key to the remote system as I haven't gotten far enough through the configuration wizard to create the root password.  I have to upload the keys to create the root password.  The Wizard will pull the public key from my ubuntu.com account but I can't figure out how to upload it to Ubuntu.com.

---

### Post by currentshaft on 2024-07-22
> **wyred451 said:**
> Unfortunately, I can't copy the key to the remote system as I haven't gotten far enough through the configuration wizard to create the root password.  I have to upload the keys to create the root password.  The Wizard will pull the public key from my ubuntu.com account but I can't figure out how to upload it to Ubuntu.com.

You don't need the root password for this.

---

### Post by ActionParsnip on 2024-07-23
your SSH key is used by your user, not root.
You will also need to run the below on the system you are connecting to
```

mkdir ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys

```

You can then paste your public key into ~/.ssh/authorized_keys

---

