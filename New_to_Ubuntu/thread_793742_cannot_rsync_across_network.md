---
title: "cannot rsync across network"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by misterspider on 2008-05-14
I found this in the archive to backup across a network, 

rsync -avz --delete -e ssh /myfolder/ user@remotepc:/myfolder

but I cannot get this to work, I get a message "Name or service not known". Isn't the remotepc name just found at System -> Administration -> System Monitor, on the system tab? Both machines are using Hardy.

---

### Post by hyper_ch on 2008-05-14
not sure if you can use "rsync ssh local remote"... I tend to think you'd need to use "rsync ssh remote local"... I think you can only use rsync over ssh to sync from a remote computer to the local one...

---

### Post by seetho on 2008-05-14
This is my backup script to rsync my notebook to remote PC at home over ssh.

```

rsync -avz -e "ssh -p 65022" --exclude='.Trash/' --exclude='.sane/' --exclude='.mozilla/firefox/*/Cache/' --exclude='.thumbnails/' --exclude='.*~' --exclude='*~' --exclude='temp/' --delete-excluded /home/seetho/ /etc seetho@yourdomain.com:~/backup/

```

Make sure you have your SSH setup correctly.

---

### Post by misterspider on 2008-05-14
Do i even need to use ssh? All i want is to backup some music on one pc to another, both are connected to the same router. I just want a command that does an incremental transfer.

---

### Post by hyper_ch on 2008-05-14
you have to access the other computer somehow...

---

### Post by riseringseeker on 2008-05-14
> **hyper_ch said:**
> not sure if you can use "rsync ssh local remote"... I tend to think you'd need to use "rsync ssh remote local"... I think you can only use rsync over ssh to sync from a remote computer to the local one...

rsync works either way, but to be able to do backups (If I understand correctly) and retain permissions you will have to do it as root, which, unless you change the way Ubuntu has root set up you cannot do.

---

### Post by seetho on 2008-05-14
Rsync uses ssh by default.  If you never leave your internal network then the rsync man pages recommends using rsh.  I'm not sure whether you can use it without any remote shell.  

I use ssh because I can do backups even when I am away from base.  It's good practice to secure all network communications even in internal networks.

btw I just run my script as sudo.

---

### Post by misterspider on 2008-05-16
How can i check to see if i have ssh configured correctly on both machines?

---

### Post by hyper_ch on 2008-05-16
misterspider:

the machine you want to connect to need openssh-server installed...
```

sudo apt-get install openssh-server

```

Furthermore I'd recommend to install deny hosts ([http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts](http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts)) or fail2ban ([http://www.howtoforge.com/fail2ban_debian_etch](http://www.howtoforge.com/fail2ban_debian_etch)) - both howtos should be 1:1 applicable to Hardy.

You might even think about key-based ssh authorization ([http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)) otherwise you'll have to enter the password manually when running rsync over SSH.

---

### Post by misterspider on 2008-05-16
Edit:

I dont have it working at all!

I definitely have openssh installed. I have one computer called david-desktop-study and another called david-desktop, connected via a wired router. I want to copy the Music folder from desktop to desktop-study and im using this on the desktop-study machine:

sudo rsync -av -e ssh david@david-desktop:home/david/Music /home/david

It gives the following error:

david@david-desktop-study:~$ sudo rsync -av -e ssh david@david-desktop:home/david/Music /home/david
ssh: david-desktop: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(454) [receiver=2.6.9]

---

### Post by jcup on 2008-05-16
@misterspider

I've just started using rsync over shh, and i have found this tutorial to be very very helpful [http://ubuntuforums.org/showthread.php?t=15082]("http://ubuntuforums.org/showthread.php?t=15082")

Here is what you might need to do...

$ rsync -e ssh -av david@david-desktop:/home/david/Music/ /home/david/

(notice the added forward slashes!)

but-

instead of david-desktop you might need to use your IP address which you can find by using ifconfig in terminal

Do you have a firewall set up, like firestarter, if so, you may need to add a rule to allow the other computer to connect.

If you are on a local network and not doing this through the internet then you don't really need shh... just use 

rsync -av david@david-desktop:/home/david/Music/ /home/david/

you may also want to consider using some more switches like

rsync [COLOR="PaleGreen"]-avruP[/COLOR] david@david-desktop:/home/david/Music/ /home/david/

r = recursive
u = update
P = will show you what is being transfered( I believe)

check out the rsync man pages [http://rsync.samba.org/ftp/rsync/rsync.html]("http://rsync.samba.org/ftp/rsync/rsync.html")

Once you get it working refer to that tutorial to see about setting up a cron job, so that it will do it for you every night

Hope this helps!

~jcup

---

### Post by seetho on 2008-05-16
> **misterspider said:**
> How can i check to see if i have ssh configured correctly on both machines?

I followed this very nice and simple guide: [http://www.suso.org/docs/shell/ssh.sdf]("http://www.suso.org/docs/shell/ssh.sdf")  

It got me started with no problem.

---

### Post by jcup on 2008-05-19
Have a look at this "How to" it really helped get it figured out...

[http://ubuntuforums.org/showthread.php?t=15082&highlight=rsync]("http://ubuntuforums.org/showthread.php?t=15082&highlight=rsync")

I have read that you really don't need to use sudo to do this job... you should be fine with something like...

rsync -e ssh -av david@david-desktop:/home/david/music/ /home/david/

I think the -e ssh needs to go before the -av...

also I'm pretty sure you need the extra "/" that I added to the command...

If you are staying inside your home network, then you may not even need to use ssh, unless it is a wireless connection.. If it is a wired connection then you probably don't need to worry about someone sniffing the traffic between david-desktop and david-desktop-study

Also, you will want to use some more tags like

z=compression (makes it faster)
u=update
r=recursive
P=if you want to see the files moving (i think)

so, you might need something like this

rsync -e ssh -avurzP david@david-desktop:/home/david/music/ /home/david/

once you get it working you can easily add a cron job to have it run automatically nightly ( see the "how to")

finally, have a look at the rsync man pages here [http://samba.anu.edu.au/ftp/rsync/rsync.html]("http://samba.anu.edu.au/ftp/rsync/rsync.html")

Hope this helps... these resources helped me allot!


EDIT: funny, I didn't see that my first reply was on page "2", and I thought maybe it didn't post, well, here is an almost identical reply to your problem misterspider! I hope this helps

---

### Post by seetho on 2008-05-19
> **jcup said:**
> 
I have read that you really don't need to use sudo to do this job... 

Hmmm... I can't really remember why I use sudo.  I'll try it without sudo later and see what happens...

---

### Post by misterspider on 2008-05-20
Thanks,
i have successfully transferred from one computer to the other now, but had to use ifconfig to find the ip address rather than use "david-desktop". Not sure why? I thought that this address would change because i am not using a static configuration. For instance, what happens if i use that ethernet cable to plug in a laptop, and then reconnect the desktop? Does the ip address keep changing?

I'll have a read of those "how to" pages, thanks again.

---

### Post by Baelus on 2008-05-20
Your computers will almost always understand ip addresses.

If you want to use hostnames ( like 'david-desktop' ) you'll need to edit the /etc/hosts file.

You'll find "127.0.0.1  localhost" in there already. That's why you can say

```
ping localhost
```

and it will ping 127.0.0.1 ( your local machine ).

Follow the same format you find there and things should work out.

You're probably asking for a headache if you're not using a static ip though.

Every time the router's DHCP assigns a new ip address to the machine it will foul up the associations you set in the hosts file.

- B

---

