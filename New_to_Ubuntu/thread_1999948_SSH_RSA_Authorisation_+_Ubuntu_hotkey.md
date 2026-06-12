---
title: "SSH RSA Authorisation + Ubuntu hotkey"
date: 2012-06-08
forum: New to Ubuntu
---

### Post by jackswash on 2012-06-08
I have a laptop and a desktop with static IP (say, 12.34.56.78) and an account named 'jack' on both of em.

What I want to make is a single hotkey to open a terminal with SSH session from laptop into desktop without having to input anything.

I have already set up an RSA key pair with ssh-keygen and ssh-copy-id, so that if I open up a terminal window manually by alt+F2 or whatever and issue a 
```
ssh jack@12.34.56.78
```
command or its alias, it connects automatically.

But if I bind this command to a hotkey through gnome-keybinding-properties, the RSA autologin won't work, asking me for a password. Same happens if I create an sh/bash/python script and bind this one.

Since I have no idea whether the problem is in SSH RSA login, in keybinding for gnome, or in gnome virtual terminal, I can not even figure out what to google. Tried some although, but no result so far.

The issue is not at all critical, but it would be interesting to know, what exactly is preventing this one from working.

---

### Post by matt_symes on 2012-06-09
Hi

This is on 12.10 but should also work on 12.04.

Install ccsm 

```
sudo apt-get install compizconfig-settings-manager
```

Enable the "command" option and set up a key binding.

Change the command to read something along the lines of...

```
gnome-terminal -x ssh -p 222 user@10.0.0.1
```

The -x is the execute switch and will execute the ssh command.

-p is the port switch. If you are using the default port (22) then you do not need this switch.

Change user and the IP address as required.

This will open an instance of gnome-terminal and log straight into the ssh server if you have the keys set up correctly.

This works on my laptop.

Kind regards

---

