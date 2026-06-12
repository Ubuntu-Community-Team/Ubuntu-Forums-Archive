---
title: "Username Again"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by bern1939 on 2008-05-27
ok...so one final try before I give up.
I cannot get into Ubuntu 7.10 on my desktop because I cannot type the letter 'b' and several other letters from the keyboard!!

No it is not the keyboard.....I have tried others with same result.

Pressing Esc and going through 'Recovery' mode brings me to a point where I can type in the username & password no problem but am then told:

"The programs included with the Ubuntu etc. etc" and then the system reverts back to the
console with bernard@bernard-desktop:~$

Is there anything I can do to force my way into the system??


Last try and then I give up


Bern

---

### Post by Sukarn on 2008-05-27
I think you might have selected the wrong keyboard type at installation.

Someone else here might be better suited to help with that as I've always been fine with the default (US) keyboard layout.

---

### Post by sayakb on 2008-05-27
Goto recovery mode. Type:
```
nano /etc/X11/xorg.conf
```

Navigate to Input device "Keyboard" section and change the "Xkblayout" to "us"

---

### Post by bern1939 on 2008-05-27
Thanks but don't think so.....have been working with Ubuntu for a long time now with no problems until I was told I had run out of space at 47GB(Root) ???????

I am in Ireland so the keyboard config. is def.correct.

Any other ideas?

Bern

---

### Post by Sukarn on 2008-05-27
to clear up some space on your root partition, run this command -
```
sudo apt-get clean
```

This will delete all the package files (.deb files) that have been downloaded by apt-get, aptitude, synaptic, add/remove programs. Don't worry, no program will be un-installed.

---

### Post by sayakb on 2008-05-27
Do you have a common partition for / and /home?

---

### Post by bern1939 on 2008-05-27
Thanks to you both but I am afraid nothing works!

Yes I do have two partitions....one for / and one for /home

sudo apt-get clean just returns me to the bernard@bernard-desktop:~$ point

All you suggest might work if I could get into the system but I can't ???


Bern

---

### Post by sailor2001 on 2008-05-27
that's rather confusing. You say you can't type a 'b' and yet it plainly shows your user name as bernard......perhaps it's your password that isn't correct.. go into recovery and when finished type: ls /home  to verify your username and then passwd <username> and set a new password.

---

### Post by forestpixie on 2008-05-27
Have you tried to change username and password using keys that you can use so that you can get in to the system. While I can appreciate that you say that the keyboard is set correctly - have you checked?

---

### Post by forestpixie on 2008-05-27
When you try to type b do you get and x?

---

### Post by bern1939 on 2008-05-27
Thanks.....just by chance I suddenly was able to type the 'b' and have now got into Ubuntu !!! Whew!  after two days trying.

So now that I am in I need to try and recover some space.
The sda1 partition reads 43Gb and has used 43GB....hence the problem. I would never have thought that / would get to that size!!

My /home directory sda3 has 29 GB with 14GB used.
So there is scope to expand the sda1 partition.
I have tried just now to install 'gparted' but the installation fails at the ./configure point with the following comment:

"checking for XML::Parser... ok
checking for uuid_generate in -luuid... no
configure: error: *** uuid library (libuuid) not found
bernard@bernard-desktop:~/gparted/gparted-0.3.7$"

What might I be able to do now?

Many thanks again

Bern

---

### Post by forestpixie on 2008-05-27
You could try to install it - if you apt-cache search there are a few other than that not sure about the error.

If you 

df -h

you can see where the space has been taken up.

Alternatively boot the livecd and use the partition editor there.

---

### Post by bern1939 on 2008-05-27
Yes thanks ......df -h just confirms that sda1 is totally full!!

What do you mean by use the liveCD.....the one I used to install Ubuntu months ago?

If so then I have to shut down and re-run using the CD...is that correct.
I have tried that previously by using the manual installation but could not increase the affected partition.

Any tutorials as to how I might do that please.


Again many thanks to all for taking the time to help


Bern

---

### Post by forestpixie on 2008-05-27
That is correct boot using that - assuming that the version you had was gutsy at least, can't remember if feisty had the partition editor on it - I was new then.

Assuming that it is there the partition editor is in system admin I think, it is the same as the gparted you are trying to install - you don't use the partition editor that is part of the installation process.

Alternatively install gparted from the livecd as you would in your normal install, I'm sure that you can.

If you do it that way then none of your partitions, other than swap, will be mounted.
If you need to work on an extended partition that has swap within it - turn swap off

sudo swapoff

Hope that helps

---

### Post by bern1939 on 2008-05-27
Thanks I will try that.

One final point.....the experts say that you should have at least 10-15GB for the root partition.!!!
I got stuck at 46 GB !!! How come?

Am I the only one with a huge amount of progs.downloaded??


Thanks


Bern

---

### Post by forestpixie on 2008-05-27
I get along nicely enough with 6Gb - it might be woirth looking into what is actually taking the space, try running baobab and looking in root.

I'd say that you have a problem, or that files are being saved in there somewhere- of course if you don't have a seperate /home then that could account for it.

---

### Post by bern1939 on 2008-05-27
Thanks again.....no I have separate partitions but .....

Can't figure that


I am however up and running for the moment.


Thanks


Bern

---

### Post by forestpixie on 2008-05-27
baobab is the disk spce analyser - but it's easier tosay run this than go to accessories ....

you can check your drives and see where the space actually is being taken, I would be a touch concerned if I had a seperate root and home adn then root was showing usage of over 40Gb. 

Of course I don't know how you use youre system, so if you're happy then that's cool.

Night and good health to you over the water in the emerald isle :)

---

