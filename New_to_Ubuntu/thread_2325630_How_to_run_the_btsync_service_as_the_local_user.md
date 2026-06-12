---
title: "How to run the btsync service as the local user?"
date: 2016-05-24
forum: New to Ubuntu
---

### Post by Jeff_Bowman on 2016-05-24
I just installed the new btsync package, per [this blog post]("https://blog.getsync.com/2016/02/18/official-linux-packages-for-sync-now-available/"). All seems well, except I can't add any folders—the service is running under the newly-created btsync account. I need to find out how to run it under my local user account.


I found [this answer]("http://askubuntu.com/a/676022/248771"), but the context there is Ubuntu 15. I'm running 14.04. Then there's [this answer]("http://askubuntu.com/a/284894/248771"), but it's frighteningly sparse on details.


I tried to make sense of the Upstart documentation [here]("http://upstart.ubuntu.com/cookbook/"), but it's absolutely huge and I'm getting lost at about the second paragraph.


Could someone provide a simple step-by-step instruction of what exactly I must do to configure this? Do I need to edit a file somewhere? How would I go about editing that file?


As you can see, I'm not very handy yet with all of this. Some kind assistance will be appreciated  :-)


Thanks,
Jeff Bowman
Fairbanks, Alaska

---

### Post by nerdtron on 2016-05-24
Can you elaborate. What is the path of the folder you want to add? and what is the permissions/ownership of the parent folder?

From this post: [https://www.digitalocean.com/community/tutorials/how-to-use-bittorrent-sync-to-synchronize-directories-in-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-use-bittorrent-sync-to-synchronize-directories-in-ubuntu-14-04)

You'll need to edit the groups for you local user account and add yourself to the btsync group account
```
 sudo usermod -a -G btsync your_username 
```

Now that your user is added to the btsync group, you'll need to edit the ownership of the parent folder in which where you'll add write permissions for you btsync group.
```

sudo chown btsync:btsync /path/to/folder
sudo chmod 755 /path/to/folder 
ls -l /path/to/folder
```

After that, try to restart the btsync service and try again to create a folder.

---

### Post by Jeff_Bowman on 2016-05-25
Thank you for your reply.

I'm setting this up for a friend, so that all of his files automatically sync to my ReadyNAS. In order to make things easy for him (and prevent human error as well), I'm syncing /home/<user> and everything under it.

Given this, I'm not sure it would be prudent to transfer ownership to the btsync service. I'm thinking it'd be better to run the btsync service under his account (he's the only one using the laptop). According to the [btsync package blog post]("https://blog.getsync.com/2016/02/18/official-linux-packages-for-sync-now-available/"), however, users of sysvinit and upstart don't have this option.

I believe this must include Trusty users, because of the section just prior&#8212;**Controlling Sync**. That section states two mutually exclusive options: 1) systemd users; 2) sysvinit/upstart users. So apparently there are two camps in all of this. And then according to [this]("https://wiki.ubuntu.com/SystemdForUpstartUsers"), in turn, systemd isn't available to us.

So is my only path forward here to upgrade him to 15.04 and switch from Upstart to systemd, just so I can get btsync working without having to relinquish ownership of his profile folders? That sounds like a lot of work (during which I'm sure to make a serious mistake and fault his system).

Please advise.

---

### Post by nerdtron on 2016-05-25
Ubuntu 14.04 uses sysvinit/upstart in which btsync does not have an option to run on a different user. I think changing the group permissions is your only option here.

Then on your second option on using systemd, don't install 15.04 because it is no longer supported. Install the long term support release 16.04. The latest ubuntu uses systemd which you have the option to run the service on a different user.

---

### Post by Jeff_Bowman on 2016-05-25
I've been reading about the systemd issue and the fork. It seems there's been a bit of a row over the thing. Myself I'm not partial&#8212;if I can accomplish what I need, then I'm happy.

His is an older laptop anyway... I'll just wipe it clean and put the latest Lubuntu on it, which comes with systemd by default. Problem solved.

So thank you for the brief education  :-)

---

