---
title: "Enabled firewall now no SSH access"
date: 2014-03-08
forum: New to Ubuntu
---

### Post by Steven_Burns on 2014-03-08
Hi,

I'm pretty new to Linux but things have been going well, until now. Like the newbie i am i enabled UFW with sudo ufw enable and upon the next reboot found myself not being able to connect via SSH. After reading up (what i should have done in the first place) i should have allowed certain things through but i didn't.

I have Ubuntu 12.04 LTS and it's running on a dedicated server so i have no local access. My provider has booted the server into recovery mode for me so i can try and fix it but my problem is i don't even know where to start and they do not provide support in this manner.  I've tried googling but most of the discussions leave out most of the info so i've ended up here looking for help. So, with that said, can someone here kindly help me through this?

Edit - something that just occurred to me. Prior to my provider booting the server into recovery mode for me FTP was still working. Would SSH have worked if i'd changed to the port FTP uses? I think it's 21. I don't want to reboot the server into normal mode and try on a hunch in case i'm wrong as i'd need to email the provider again then wait for them to boot it into recovery mode again.

---

### Post by mikewhatever on 2014-03-08
Disabling UFW would make sense, at least for now. Once you have SSH working again, look for a UFW howto.

---

### Post by raja.genupula on 2014-03-08
may be he have to allow port number of SSH in iptables. ?

does it make sense ?

I am not much  good with networking though

---

### Post by steeldriver on 2014-03-08
Hello and welcome to the forums

If you just executed 'sudo ufw enable' then by default that will be blocking ALL incoming connections, so I don't think changing ports is going to help. What other options does the VPS's recovery mode give you? Does it allow you to run actual ufw commands?

---

### Post by Steven_Burns on 2014-03-08
I tried sudo ufw disable in recovery but it threw back "zsh: correct 'sudo' to '_sudo' [nyae]?"

---

### Post by steeldriver on 2014-03-08
if recovery mode puts you directly into a root shell you probably don't need sudo - try something like

```
ufw status numbered
```

---

### Post by Steven_Burns on 2014-03-08
> **steeldriver said:**
> if recovery mode puts you directly into a root shell you probably don't need sudo - try something like

```
ufw status numbered
```

It does yes. 

I just tried that and it says "zsh: command not found: ufw"

---

### Post by steeldriver on 2014-03-08
OK this is going to be hit and miss because we have no idea how your provider's recovery mode is configured (why is it using zsh?!?) It looks like the recovery mode PATH is not configured to include the directory where ufw is located.

Let's confirm whether you are effectively root:

```
whoami
```

and you can try giving the full path to ufw

```
/usr/sbin/ufw status numbered
```

---

### Post by Steven_Burns on 2014-03-08
whoami comes back as root

/usr/sbin/ufw status numbered comes back as no such file or directory: /usr/sbin/ufw

---

### Post by ajgreeny on 2014-03-08
You would normally simply need to use the command ```
sudo ufw allow 22
``` to open up the ssh port, assuming you have used the default port for ssh, which is 22.

If you have changed that for extra security in the **/etc/ssh/sshd_config** file you will need to edit that command accordingly.

PS: You need to run the **/usr/sbin/ufw status** as root, so if you are now back in your user terminal use **sudo /usr/sbin/ufw status**

---

### Post by Steven_Burns on 2014-03-08
Unfortunately i realized that too late ajgreeny, all i did was sudo ufw enable then rebooted which locked me out of SSH

I  didn't change the SSH port, i believe the UFW simply locked it out when  i enabled it without adding rules to allow it though. Now i need to  somehow be able to allow SSH though (edit- or completely disable ufw for now) while in Recovery mode before booting back into normal.

I can't sudo anything. I'm still only logged into SSH via the Recovery mode and haven't changed anything as i don't know what i should be changing. If i boot back into normal i'll be locked out of SSH and i have no other way in as it's a remote server.

---

### Post by steeldriver on 2014-03-08
Are you sure you are running Ubuntu (not some related distro like Debian or Mint)? The default location for the ufw program should be /usr/sbin/ufw so if it's not finding it there we will need to do some more investigating.

Based on your whoami output, you appear to be logged in as root in the VPS recovery mode so there should be no problem with permissions and no need for sudo, you just need to find where the program is located.

---

### Post by ajgreeny on 2014-03-08
So if I understand you right, you enabled ufw on your remote server with no rules to allow the ssh port 22 to be open, presumably whilst logged in with ssh or webmin or similar, then logged out.

If so then I think you are going to need local access to the server, as you have now effectively locked yourself out and will be unable to disable ufw.

Interesting problem, but I think I will have to let other more knowledgeable network experts take over from here, just in case there is another way round this that I am unfamiliar with.

Good luck!!

---

### Post by Steven_Burns on 2014-03-08
> **steeldriver said:**
> Are you sure you are running Ubuntu (not  some related distro like Debian or Mint)? The default location for the  ufw program should be /usr/sbin/ufw so if it's not finding it there we  will need to do some more investigating.

Based on your whoami output, you appear to be logged in as root in the  VPS recovery mode so there should be no problem with permissions and no  need for sudo, you just need to find where the program is  located.

Yeah definitely Ubuntu, it's Ubuntu 12.04 LTS.

Bearing in mind i  don't really know what i'm doing, i browsed to /usr/sbin and did an ls  -la but ufw wasn't in the list in there if that helps.

> **ajgreeny said:**
> So if I understand you right, you enabled ufw on your remote server with no rules to allow the ssh port 22 to be open, presumably whilst logged in with ssh or webmin or similar, then logged out.

If so then I think you are going to need local access to the server, as you have now effectively locked yourself out and will be unable to disable ufw.

Interesting problem, but I think I will have to let other more knowledgeable network experts take over from here, just in case there is another way round this that I am unfamiliar with.

Good luck!!

Pretty much nail on the head yeah.

---

### Post by Steven_Burns on 2014-03-08
Just to update that i gave up trying to fix this. I re-installed Ubuntu 12.04 about an hour ago and things are back to working perfectly again. Sadly i somehow managed to lose the data on one of my storage drives in the process but thankfully 2 of them (the ones with the most data) were fine. Let's just say i won't be making that mistake again!

Going off topic.. i was surprised how easy the installation and getting everything set up properly the way i need this time round was. The last time (and first) it took me 2 days via google to learn and get done what needed to be done.

Thanks to you all for trying to help, i appreciate the fact that you spent time doing so :)

---

### Post by Iowan on 2014-03-08
We'll hope you don't get too many degrees from the School of Hard Knocks.;)

---

### Post by 3rdalbum on 2014-03-08
Learning Linux on a server that you don't have physical access to might be somewhat painful. I suggest you install Ubuntu Server onto a virtual machine on your own computer so you can play around and learn. Any major changes that you want to make on the remote server, you can try on the virtual machine first to ensure you know what to do and that everything will work later.

If you mess things up on the VM, just revert to an earlier snapshot and try again.

This is actually what real businesses do, too. Highly recommend you give it a try.

---

