---
title: "iPhone music sync"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by daniel_owen_uk on 2012-06-21
So far loving my foray into the land of linux, have a few priors with previous versions of ubuntu and fedora, but I have always come across something that simply isn't possible.

This time round almost everything is ok, even the wife is coming round to Ubuntu.

The one thing I can't get it to do is sync music to my iPhone.  My iPhone is a 4S that is jailbroken on 5.1.1

I after first trying to use banshee it would seem that only reads and wont write.

I tried WINE but that wouldn't work and my latest attempt is a VirtualBox windows 7 install, that I can't get to passthrough USB.

So.... is there a magic way to get the iPhone to work?  Surely something so common must be covered by something standard?

---

### Post by nothingspecial on 2012-06-21
Have you installed virtualbox guest additions?

---

### Post by daniel_owen_uk on 2012-06-21
Yes, I have.

Probably should have stated that I am on 12.04

In virtualbox under USB, Enable USB 2.0 (EHCI) controller is unticked.  Ticking it tells me I need to download a pack.

---

### Post by nothingspecial on 2012-06-21
That sounds like you don't have guest additions installed.

Are you a member of the vboxusers group?
```

sudo adduser $USER vboxusers
```

---

### Post by daniel_owen_uk on 2012-06-21
I am definitely in that group, I did a 

```
grep vbox /etc/group
```

Do I also need to do something with fstab?

---

### Post by daniel_owen_uk on 2012-06-22
Bahhhh, figured it out, it was me being dumb.

Firstly needed to add the extension pack, that was simple enough and worked through the menu.  I though that was the virtual box guest additions, as it turns out that's something different.

Which I then had to work out to use shared folders.  I had ticked the guest additions, but didn't realise that simply mounts the image, you have install them on the virtual os not the host.

Anyway, all done, itunes up and running and syncing with iPhone/iPad

---

### Post by charless1 on 2012-06-25
Thanks nothingspecial...

I appriciate your help, your comments help me as well as daniel..

Thanks a lot

---

