---
title: "SSH problems"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2014-01-06
My hosting company is SiteGround.
They have a control panel with a tool to generate ssh keys.
I tried using keys generated in their control panel and have had the same problem with: Denied (publickey)

I generated my own key and pasted the public key into their control panel tool.
This according to their documentation will store my public key in the correct location on their server.

I have my private key in ~/.ssh
My private key does not have a password.
I'm not worried about someone gaining access to this machine, but I am worried about someone seeing my credentials if they were passed as plain text.  So I want to connect securely. 

Starting a couple of weeks ago I noticed that I was getting errors: Denied (publickey) when I try to connect to my hosting company's server via sftp.
It seems to work if I re-add my ssh key.  That is, until I reboot the computer then I would not be able to login again until I once more ran add-ssh.
I should mention that I can connect without problem using Filezilla and SFTP with my private key loaded from ~/.ssh.
I only have trouble connecting via lftp or scp.
Readding the private key after boot does solve the problem until I restart the computer.

I guess my basic question is:

[COLOR=#ff0000][B]Why would I need to add the same passwordless ssh key every time I boot the computer?
[/B][/COLOR]
I didn't have to keep mucking around adding keys in the past.
This is really frustrating.

---

### Post by bluefrog on 2014-01-07
should ask the hosting company if they change the ssh key regularly

---

