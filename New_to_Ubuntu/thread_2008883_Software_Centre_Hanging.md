---
title: "Software Centre Hanging"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by johnnypict on 2012-06-23
I have tried to download a Dropbox package and mid way through the software centre hung. 

I've shut down and restarted but the software centre is now trying to load searching and cancelling it.

I am unable to download anything as every other package is waiting for this one to end.

How do I stop this?


Thanks

John

---

### Post by jmfal on 2012-06-23
Welcome to Ubuntu

Open a terminal and enter this code:
```
 sudo apt-get --purge dropbox    
```

Press enter  then:

```
 sudo apt-get autoclean     
```

Press enter, then :
```
 sudo apt-get update     
```
Press enter, and last:
```
sudo apt-get upgrade  
```

Try to install something , post any errors so somebody can help, or mark SOLVED so that other will it solved your problem.

---

### Post by nipunshakya on 2012-06-23
see this:
[http://askubuntu.com/questions/154671/dropbox-fails-to-install-stuck-at-99](http://askubuntu.com/questions/154671/dropbox-fails-to-install-stuck-at-99)
some say its a bug about drobbox not being installed, while one of the forum user ended up with a reinstallation of ubuntu again... worth trying what jmfal suggested too...

---

### Post by johnnypict on 2012-06-23
Thanks,

I tried the first line, was prompted for admin passwd, entered it and terminal came back with this...

fionn@Fionn:~$ sudo apt-get --purge dropbox
[sudo] password for fionn: 
E: Invalid operation dropbox
fionn@Fionn:~$ 

John.

---

### Post by jmfal on 2012-06-23
Try the autoclean command  it might remove the parts that where installed when you stopped the installation.

---

### Post by nipunshakya on 2012-06-23
its actually ```
sudo apt-get purge nautilus-dropbox
``` then run the other codes...

Then,
if you want to install dropbox, see the following:
[http://www.liberiangeek.net/2012/04/install-dropbox-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/install-dropbox-in-ubuntu-12-04-precise-pangolin/)

---

### Post by sudodus on 2012-06-23
Try this command line instead ```
sudo apt-get purge whatever-package
``` (I think there should be no --)

---

### Post by johnnypict on 2012-06-23
Thanks for your help.

I've tried again without the -- and with nautilus 

I'm now getting this

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
fionn@Fionn:~$ 

I also tried downloading the daemon but that's just stuck in the queue...:???:

Might need a reinstall...:(

John.

---

### Post by jmfal on 2012-06-23
Make sure that the Soft ware center is closed  and try that command again.

---

### Post by ranger1021994 on 2012-06-23
> **johnnypict said:**
> Thanks for your help.

I've tried again without the -- and with nautilus 

I'm now getting this

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
fionn@Fionn:~$ 

I also tried downloading the daemon but that's just stuck in the queue...:???:

Might need a reinstall...:(

John.

If software Centre is still open then go to terminal and type 
" xkill " nd click on Software centre..and then try purge command :)

---

### Post by johnnypict on 2012-06-23
Nope I'm afraid nothing appears to be working.

Thanks for your help, a re-install is in the offing me thinks. Wont be installing dropbox either.

Thanks again.

John.

---

### Post by chubzx on 2012-06-23
Had the same issue i found this on the Dropbox site which worked for me 

```
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -
```
        
Next, run the Dropbox daemon from the newly created .dropbox-dist folder.

```
~/.dropbox-dist/dropboxd
```

can find the original site here [https://www.dropbox.com/install?os=lnx]("https://www.dropbox.com/install?os=lnx")

That is for installing Dropbox. to get around your issue use 

```
ps -e
```

then

```
sudo kill <PID>
```

Use that on every dropbox process and it will go from the Software center

---

### Post by sudodus on 2012-06-23
Did you try to reboot your computer? 'The old DOS and Windows way to get rid of processes you don't want'

If you still have problems installing/uninstalling programs from the Software Center or the command line, try ***Synaptic*** instead.

The interface of Synaptic is a little more complicated, but after a while you will appreciate, that you know more about what you are doing.

---

### Post by nipunshakya on 2012-06-23
i've said before too, the dropbox installation stucking at 'Applying changes' at the software center is a bug that has been reported too.. and a user has ended up with fresh installation of ubuntu as well. So don't get too rough on the installation. Ubuntu One is also a best option for your online storage facility. The bug is filed here:
[http://askubuntu.com/questions/154671/dropbox-fails-to-install-stuck-at-99](http://askubuntu.com/questions/154671/dropbox-fails-to-install-stuck-at-99)
[https://bugs.launchpad.net/ubuntu/+source/nautilus-dropbox/+bug/1016559](https://bugs.launchpad.net/ubuntu/+source/nautilus-dropbox/+bug/1016559)

Happy Linuxing

---

### Post by johnnypict on 2012-06-24
Hi guys,

Thanks for your help.
I've re-intsalled and will keep away from dropbox until the issue is resolved.

Thanks for your help.

John

---

### Post by nipunshakya on 2012-06-24
Hey John, the link below had a solution at post #7 ...came across it just now... sorry for you having to reinstall the whole thing man...
[http://ubuntuforums.org/showthread.php?t=2009104](http://ubuntuforums.org/showthread.php?t=2009104)

Goodluck and happy Linuxinh

---

### Post by johnnypict on 2012-06-25
Yes killed it.
I'll try synaptic and see what happens.
Reinstall wasn't too bad had nothing to loose as it was a fresh install.

I'll have a look at the solution above.

Thanks again to all for your help.

John

---

### Post by johnnypict on 2012-06-25
Here's a thing...

I tried to install dropbox via synaptic...got same problem. Install stops at 99%

After playing around and nearly attempting another install I was first going to run USB creator and got a message that the dpkg was interrupted and to run

sudo dpkg --configure -a

So I did and the machine said that it was Setting up nautilus-dropbox (0.7.1-2) ...

So I ran:  sudo apt-get purge nautilus-dropbox

My point: 
I was running:
sudo apt-get purge dropbox
and
sudo apt-get purge nautilus dropbox
and
sudo apt-get purge nautilus

but now that I have run sudo apt-get purge nautilus-dropbox it worked.

so ensuring that  'nautilus-dropbox' is what is typed into terminal should make it all work.

Small but important point.

John.

---

### Post by nipunshakya on 2012-06-25
sometimes small things do mean big ones at last buddy... it does..

---

