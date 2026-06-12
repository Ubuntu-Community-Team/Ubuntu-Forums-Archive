---
title: "Log on as Root"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by mikeody on 2008-08-19
I may be having a bad day but I am a little confused.
Am running Heron and its good. I am the only user on my PC and from what [I thought] I read when I installed Heron, I would automatically be given 'Administrator' [Root] access.
I am trying to update ClamAV virus definitions but keep getting the message that to do this 'I should be logged on as Root'.
OK, but how do I logon as Root ? I am not given the option at start up and ClamAV doesnt ask me for an Admistrator password.
I am sure the answer is simple but I cant seem to find it !!
Thanks.

---

### Post by iaculallad on 2008-08-19
> **mikeody said:**
> I may be having a bad day but I am a little confused.
Am running Heron and its good. I am the only user on my PC and from what [I thought] I read when I installed Heron, I would automatically be given 'Administrator' [Root] access.
I am trying to update ClamAV virus definitions but keep getting the message that to do this 'I should be logged on as Root'.
OK, but how do I logon as Root ? I am not given the option at start up and ClamAV doesnt ask me for an Admistrator password.
I am sure the answer is simple but I cant seem to find it !!
Thanks.

On your terminal, do this:

```
sudo apt-get install freshclam
sudo freshclam

```

By default, root account is disabled in Ubuntu. You have to sudo or su your command in order to get the privilege.

---

### Post by hyper_ch on 2008-08-19
why do you want to run antivirus anyway?

---

### Post by ace007 on 2008-08-19
Use the sudo command to temporarily assume root privledges. **[SIZE="2"][COLOR="Red"]NEVER LOG IN AS ROOT![/COLOR][/SIZE]** Besides being less secure, you can really mess up your computer if you do a single goof. There is no going back.

Read: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by sandysandy on 2008-08-19
have a look at this thread for root

[http://ubuntuforums.org/showthread.php?t=888202](http://ubuntuforums.org/showthread.php?t=888202)

and this for anti virus

[http://www.linux.com/articles/60208](http://www.linux.com/articles/60208)

[http://www.linuxforums.org/forum/suse-linux-help/21148-new-linux-some-basic-clarifications-required.html](http://www.linuxforums.org/forum/suse-linux-help/21148-new-linux-some-basic-clarifications-required.html)


regards

---

### Post by Ryadt on 2008-08-19
> **mikeody said:**
> I may be having a bad day but I am a little confused.
Am running Heron and its good. I am the only user on my PC and from what [I thought] I read when I installed Heron, I would automatically be given 'Administrator' [Root] access.
I am trying to update ClamAV virus definitions but keep getting the message that to do this 'I should be logged on as Root'.
OK, but how do I logon as Root ? I am not given the option at start up and ClamAV doesnt ask me for an Admistrator password.
I am sure the answer is simple but I cant seem to find it !!
Thanks.

Have a look here [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by mikeody on 2008-08-19
Thanks guys for rapid responses.
I sorted it by opening the console and using

sudo -i
sudo clamtk

And yes I know I probably dont need clamtk but am new at ubuntu and am exploring everything that moves  !

Thanks again.

---

### Post by sandysandy on 2008-08-19
see here for installing

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

regards

---

