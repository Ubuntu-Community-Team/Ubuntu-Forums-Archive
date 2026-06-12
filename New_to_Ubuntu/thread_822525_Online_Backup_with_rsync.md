---
title: "Online Backup with rsync"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-08
I have learnt how to use rsync (finally!) and I am really happy with it. But I would like to be able to backup some important documents online. Is there any service that is free and where I can just use the simple rsync script i have?

I don't know ANYTHING about setting up servers, or ftp, but if these can be done for free I don't mind trying them out.

Thanks!

---

### Post by superprash2003 on 2008-06-08
you could backup data from your pc to say another pc on your computer rather than doing  it online

---

### Post by abhiroopb on 2008-06-08
i'm confused? Backup data from a pc to another pc?

---

### Post by Prospero2006 on 2008-06-08
If both PC's  have an ssh server, you can run rsync over ssh.

First, you have to set up passwordless authentication over ssh so that when computer A contacts computer b, it is automatically allowed accessed based on an RSA keypair.

Then, you set up an rsync script like this:
```

rsync -r -e ssh /mydirectory root@ip_of_backup_computer:/serverbackup 

```

rsync will then run over ssh.
Add this script to a cron job and you have automated backups.

---

### Post by abhiroopb on 2008-06-08
I only have one computer and have no idea what SSH is.

---

### Post by xadder on 2008-06-08
Don't know about online solutions either, but I'll propose the solution I use. I have an external usb hard-disc. These are pretty cheap these days and v. easy to carry around if needed.

Format as a Linux file-system (e.g. ext3 or reiser) using gparted, then just do rsync to the disc when you feel like it. Works great!

(I actually use unison, which is a 2-way rsync. This lets me use the hard-disc to tranfer files to and from a stationary and portable PC - keeping all 3 systems identical)

---

### Post by abhiroopb on 2008-06-08
> **xadder said:**
> Don't know about online solutions either, but I'll propose the solution I use. I have an external usb hard-disc. These are pretty cheap these days and v. easy to carry around if needed.

Format as a Linux file-system (e.g. ext3 or reiser) using gparted, then just do rsync to the disc when you feel like it. Works great!

(I actually use unison, which is a 2-way rsync. This lets me use the hard-disc to tranfer files to and from a stationary and portable PC - keeping all 3 systems identical)

Thanks, this is what I already do with 2 external hard disks, and a cron job. Works greaat, I'm just very paranoid and so I want my most important documents (perhaps about 1gb in total) online somewhere.

---

### Post by abhiroopb on 2008-06-08
problem with external hard drive, is that (touch wood) anything PHYSICAL were to happen, such as fire, earthquake, flood, my external hard drive sits right next to the laptop and it would most likely get just as damaged.

---

