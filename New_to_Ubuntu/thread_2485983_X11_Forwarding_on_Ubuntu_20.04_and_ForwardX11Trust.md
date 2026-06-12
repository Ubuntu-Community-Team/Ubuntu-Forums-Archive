---
title: "X11 Forwarding on Ubuntu 20.04 and ForwardX11Trusted"
date: 2023-04-16
forum: New to Ubuntu
---

### Post by bhubunt on 2023-04-16
Hi, 

I am not using X11 forwarding (as far as I know), but on a website about "bad security" it says it is best to set ForwardX11Trusted to "no." 

When I tried to edit the ssh_config file, I was unable to change ForwardX11Trusted to no, when I typed in the word 'no' and tried to save the file. 

I got this code:

```
(gedit:7186): Tepl-WARNING **: 18:57:37.709: GVfs metadata is not supported. Fallback to TeplMetadataManager. Either GVfs is not correctly installed or GVfs metadata are not supported on this platform. In the latter case, you should configure Tepl with --disable-gvfs-metadata.
```

---

### Post by #&amp;thj^% on 2023-04-16
How do you use gedit? That just shows a warning.
Typically I use:
```
gedit admin://<your-path and application>
```
When I bother with gnome.
Just use Nano!
before my edit:
```
# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Include /etc/ssh/ssh_config.d/*.conf

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted[ yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   IdentityFile ~/.ssh/id_ecdsa
#   IdentityFile ~/.ssh/id_ed25519
#   Port 22
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
#   RekeyLimit 1G 1h
#   UserKnownHostsFile ~/.ssh/known_hosts.d/%k
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes

```
After my edit:
```
 cat /etc/ssh/ssh_config | grep ForwardX11Trusted
#   ForwardX11Trusted no


```

---

### Post by MAFoElffen on 2023-04-16
This would be a normal error when you try to use a gnome graphical application with sudo, which you shouldn't because root doesn't have the home directory to support graphics. That specific error is saying that (if a normal user) that it is trying to write a metadata file to set a pointer, so that on reopening the file, that it starts at the last line number it was on at exit... But since you are not supposed to us gnome applications with sudo, because it can't write those files... Telling you that it cannot do that, would be normal...

Instead, you should be using 'sudoedit' to edit files with escalated permissions.

---

### Post by TheFu on 2023-04-17
ssh_config or sshd_config?  The server-side normally is the one we want to prevent ssh X11 forwarding inside. That's the sshd_config file.

+1 for using **sudoedit**.  You can use any EDITOR you like, but know that only CLI editors like nano, vim, emacs, will work on a system without a GUI (which is typical for remote servers).  Any editor can be set in your startup files (~/.bashrc) with the export EDITOR= .... same for the default PAGER you want to use.  These things have been around, probably since 1970 and are one of the very first things I setup on any new system, usually right after I purge nano. ;)

grep shows this.
/etc/ssh/ssh**d**_config:X11Forwarding yes
/etc/ssh/ssh_config:#   ForwardX11 no

The ssh_config file is system-wide for all users, but usually any settings in there would be created in each user's ~/.ssh/config file instead.  Enforce security policy inside the dæmon config file, not the client config file.

---

### Post by bhubunt on 2023-04-20
Thanks to all for the replies. I was away due to work, but will check out your recommendations.

---

### Post by bhubunt on 2023-04-20
[QUOTE=

[/code]

```
 cat /etc/ssh/ssh_config | grep ForwardX11Trusted
#   ForwardX11Trusted no


```[/QUOTE]

I just typed your command into the terminal and also got the same answer ```
  ForwardX11Trusted no 
```

So that's interesting. Even though I got that error message, see post #1, somehow the initial yes was changed into a no.

Not sure how that happened.

---

### Post by bhubunt on 2023-04-20
> **MAFoElffen said:**
> This would be a normal error when you try to use a gnome graphical application with sudo, which you shouldn't because root doesn't have the home directory to support graphics. That specific error is saying that (if a normal user) that it is trying to write a metadata file to set a pointer, so that on reopening the file, that it starts at the last line number it was on at exit... But since you are not supposed to us gnome applications with sudo, because it can't write those files... Telling you that it cannot do that, would be normal...

Instead, you should be using 'sudoedit' to edit files with escalated permissions.

Can you give an example of such a sudoedit command line?

---

### Post by #&amp;thj^% on 2023-04-20
> **bhubunt said:**
> Can you give an example of such a sudoedit command line?

Try:
```
sudoedit /etc/default/grub
```
It's much the same as nano, yourjust adding a better/safer practice when editing configs.

---

### Post by TheFu on 2023-04-20
Or 
```
sudoedit /etc/ssh/sshd_config
```
Or if you are already in the correct directory, 
```
sudoedit sshd_config
```

Works just like any other CLI editor.  _How_ it works to be safer than other methods is sorta cool.

---

