---
title: "Disconnected during shell script, now I'm locked out of SSH?"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by Euskadi1888 on 2014-04-11
I was logged in via SSH and executing the script [found here]("http://www.torrent-invites.com/showthread.php?t=207635") when my internet connection dropped. As soon as I was reconnected to attempted to log in again only to be told that the SSH key, which I had been using all day without issue, wasn't being accepted by my server. I was prompted to enter my password instead but kept being told it was incorrect.

Does anyone have any idea what might have caused this and how I can fix it? I really, really do not want to have to do another Ubuntu install as I already had to do that for a different problem and have spent a lot of time restoring everything (apache etc work fine, my websites are all up and running I just can't log in via SSH).

---

### Post by nerdtron on 2014-04-11
Did you change ports in ssh? Did you changed password?
Try ssh -v [ipaddress] when connecting and post the output here.

---

### Post by Euskadi1888 on 2014-04-11
This is going to sound silly but how do I type that in? I've always just used PuTTY, where the IP is entered in the configuration window before connecting.

and yes, I have changed SSH port and also changed the default password (although I've tried using the default too)

---

### Post by steeldriver on 2014-04-11
Yes that script changes your ssh port - it also may have restricted access to the newly created seedboxuser and/or sshdusers group instead of your regular user account name

```

$ grep -i ssh seedbox-from-scratch.sh
#     - Fail2ban for ssh and apache - it bans IPs that show the malicious signs -- too many password failures, seeking for exploits, etc.
#     - createSeedboxUser script now asks if you want your user jailed, to have SSH access and if it should be added to sudoers
[B]getString NO  "SSH port: " NEWSSHPORT1 21976
perl -pi -e "s/Port 22/Port $NEWSSHPORT1/g" /etc/ssh/sshd_config
[/B]perl -pi -e "s/PermitRootLogin yes/PermitRootLogin no/g" /etc/ssh/sshd_config
perl -pi -e "s/#Protocol 2/Protocol 2/g" /etc/ssh/sshd_config
perl -pi -e "s/X11Forwarding yes/X11Forwarding no/g" /etc/ssh/sshd_config
groupadd sshdusers
echo "" | tee -a /etc/ssh/sshd_config > /dev/null
echo "UseDNS no" | tee -a /etc/ssh/sshd_config > /dev/null
[B]echo "AllowGroups sshdusers" >> /etc/ssh/sshd_config
[/B]service ssh restart
echo $NEWSSHPORT1 > /etc/seedbox-from-scratch/ssh.info
[B]#  createSeedboxUser <username> <password> <user jailed?> <ssh access?> <?>
echo "Remember that your SSH port is now ======> $NEWSSHPORT1"
echo "System will reboot now, but don't close this window until you take note of the port number: $NEWSSHPORT1"
[/B]
```

You can specify a non default port on the ssh client command line using the -p switch

```

ssh -p 21976 user@host

```

Also it appears to install/configure fail2ban - so your repeated unsuccessful connection attempts may have got your IP banned (at least temporarily)

```

$ grep -i fail2ban seedbox-from-scratch.sh
[B]#     - Fail2ban for ssh and apache - it bans IPs that show the malicious signs -- too many password failures, seeking for exploits, etc.
[/B]#     - Optionally install packages JailKit, Webmin, Fail2ban and OpenVPN
getString NO  "Install Fail2ban? " INSTALLFAIL2BAN1 YES
if [ "$INSTALLFAIL2BAN1" = "YES" ]; then
  apt-get --yes install fail2ban
  cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.conf.original
  cp /etc/seedbox-from-scratch/etc.fail2ban.jail.conf.template /etc/fail2ban/jail.conf
  fail2ban-client reload

```

---

### Post by nerdtron on 2014-04-11
The best way to do log in is to locally login on the physical server. Just to make sure you have the correct password and username.
Also, try rebooting the server.

---

### Post by Euskadi1888 on 2014-04-12
I don't have physical access to the server.

I know I have the correct password because I used it just prior to setting my my SSH key.

---

### Post by nerdtron on 2014-04-12
Well, at what part of the script are you disconnected?

---

### Post by Euskadi1888 on 2014-04-12
> **nerdtron said:**
> Well, at what part of the script are you disconnected?
I don't know, it's a pretty large script and it was flying through it!

However I have managed to rectify the situation with a bit of fiddling in the sshd config files :)

---

