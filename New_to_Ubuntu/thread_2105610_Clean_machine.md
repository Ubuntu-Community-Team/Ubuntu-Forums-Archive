---
title: "Clean machine?"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by Yezinki on 2013-01-16
How often do you expert members clean your Ubuntu machine, using terminal or Bleachbit?

Thanks.

---

### Post by haqking on 2013-01-16
> **Yezinki said:**
> How often do you expert members clean your Ubuntu machine, using terminal or Bleachbit?

Thanks.

never

I keep things "clean" as i go

---

### Post by Yezinki on 2013-01-16
Thanks but what do you imply by " I keep things "clean" as i go"

---

### Post by haqking on 2013-01-16
> **Yezinki said:**
> Thanks but what do you imply by " I keep things "clean" as i go"
well what do you imply by "clean"

I dont do anything that causes things to be "unclean"

my /tmp is in RAM and Firefox Cache is in  RAM too

My browsers dont retain any data, cookies etc etc

---

### Post by Yezinki on 2013-01-16
Thanks haqking	

How do you do this, I use G Chrome?


```

I dont do anything that causes things to be "unclean"

my /tmp is in RAM and Firefox Cache is in RAM too

My browsers dont retain any data, cookies etc etc
```

---

### Post by snowpine on 2013-01-16
> **Yezinki said:**
> How often do you expert members clean your Ubuntu machine, using terminal or Bleachbit?

Thanks.

Never. I see many support requests resulting from failed attempts to "clean" a Linux system, when in fact there was nothing wrong with it in the first place. :)

---

### Post by haqking on 2013-01-16
> **snowpine said:**
> Never. I see many support requests resulting from failed attempts to "clean" a Linux system, when in fact there was nothing wrong with it in the first place. :)

+1

Bleachbit should be called Bricked-it ;-)

---

### Post by haqking on 2013-01-16
> **Yezinki said:**
> Thanks haqking    

How do you do this, I use G Chrome?


```

I dont do anything that causes things to be "unclean"

my /tmp is in RAM and Firefox Cache is in RAM too

My browsers dont retain any data, cookies etc etc
```

Putting /tmp into ram will be something like:

```
tmpfs       /tmp        tmpfs       defaults,mode=1777      0   0
```

in your /etc/fstab but it depends what exactly you want

look at 

[http://wiki.centos.org/TipsAndTricks/TmpOnTmpfs](http://wiki.centos.org/TipsAndTricks/TmpOnTmpfs)

To make Google Chrome use it then I am not sure as i dont use chrome but see here
[https://wiki.archlinux.org/index.php/Chromium_Tips_and_Tweaks](https://wiki.archlinux.org/index.php/Chromium_Tips_and_Tweaks)

and look at the tmpfs section

---

### Post by ibjsb4 on 2013-01-16
> **haqking said:**
> +1

Bleachbit should be called Bricked-it ;-)

That may be your experience, but I have been using BleachBit since 8o4 without issue and recommend it.

---

### Post by haqking on 2013-01-16
> **ibjsb4 said:**
> That may be your experience, but I have been using BleachBit since 8o4 without issue and recommend it.

it isnt my experience, I have never used it, I dont need to.

It was  response to snowpine who mentioned seeing lots of support requests about people bricking their builds due to unnecessary "cleaning", I was agreeing as i have seen many too

---

### Post by Paddy Landau on 2013-01-16
Linux tends to keep itself clean. Unlike Windows, there is no need to clean your machine. CCleaner, defrag, system cleanup… all unnecessary on Linux.

If you are incredibly short on space because of a minute hard drive, you can clean out the installation cache as follows:
```
sudo apt-get autoremove
sudo apt-get clean
```But otherwise, there is nothing to do.

Oh, there is one exception: [a current bug]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785") adds empty hidden files to your home folder. You can clear these out every month or so with:
```
rm ~/.goutputstream-*
```

---

### Post by Yezinki on 2013-01-16
They say if Free Disk Space, Memory &  Localizations are unchecked Bleachbit is fine for Ubuntu.......donno how far is that correct?

---

### Post by Yezinki on 2013-01-16
> **haqking said:**
> Putting /tmp into ram will be something like:

```
tmpfs       /tmp        tmpfs       defaults,mode=1777      0   0
```

in your /etc/fstab but it depends what exactly you want

look at 

[http://wiki.centos.org/TipsAndTricks/TmpOnTmpfs](http://wiki.centos.org/TipsAndTricks/TmpOnTmpfs)

To make Google Chrome use it then I am not sure as i dont use chrome but see here
[https://wiki.archlinux.org/index.php/Chromium_Tips_and_Tweaks](https://wiki.archlinux.org/index.php/Chromium_Tips_and_Tweaks)

and look at the tmpfs section


haqking I only have 3 partitions, /, /home & swap so how do I do what you suggested?

Thanks.

---

### Post by Paddy Landau on 2013-01-16
> **Yezinki said:**
> … how far is that correct?
I don't know, but you really, really, really do not need it. Really, don't bother. Linux cleans its own areas automatically whenever you turn off the machine.

---

### Post by haqking on 2013-01-16
> **Yezinki said:**
> haqking I only have 3 partitions, /, /home & swap so how do I do what you suggested?

Thanks.

what i posted was nothing to do with your partitions, it is about placing the /tmp folder into RAM (tmpfs)

I suggest read up using the links i posted and then decide for yourself.

Dont make major system configuration changes based on someones elses configuration, read up on tmpfs and then decide if its what you want/need, take a look at your system.

make sure you have backups/clones of system then post back when its gets overwhelming if it does ;-)

Peace

---

### Post by Yezinki on 2013-01-16
Thanks haqking.

---

### Post by Paddy Landau on 2013-01-16
I would also add that for most people, there is little point in moving [FONT=Lucida Console]/tmp[/FONT] to RAM. It is nice to do, because it can speed up a system, but you would notice an improvement only if (1) you had plenty of RAM in which to hold [FONT=Lucida Console]/tmp[/FONT]; (2) you used [FONT=Lucida Console]/tmp[/FONT] extensively, e.g. when manipulating video.

For someone like me, with a lower level of RAM, it could even slow my machine, as less RAM is available for the work being done.

So ask yourself: Do you have plenty of RAM and do you use swap intensively? If the answer to either one is "no", again, don't bother.

Also, this has nothing to do with keeping your machine clean, as Linux empties [FONT=Lucida Console]/tmp[/FONT] when you turn off your machine.

---

### Post by Yezinki on 2013-01-16
Thanks Paddy Landau for posting your expert views.

---

### Post by haqking on 2013-01-16
> **Paddy Landau said:**
> I would also add that for most people, there is little point in moving [FONT=Lucida Console]/tmp[/FONT] to RAM. It is nice to do, because it can speed up a system, but you would notice an improvement only if (1) you had plenty of RAM in which to hold [FONT=Lucida Console]/tmp[/FONT]; (2) you used [FONT=Lucida Console]/tmp[/FONT] extensively, e.g. when manipulating video.

For someone like me, with a lower level of RAM, it could even slow my machine, as less RAM is available for the work being done.

So ask yourself: Do you have plenty of RAM and do you use swap intensively? If the answer to either one is "no", again, don't bother.

Also, this has nothing to do with keeping your machine clean, as Linux empties [FONT=Lucida Console]/tmp[/FONT] when you turn off your machine.

I agree except for that another common reason today is the use of SSD and wanting to reduce writes to it, and in addition not all distros empty /tmp completely, I dont know about recent versions of Ubuntu as I dont use it but anyways yes as i said above, only do it if decided its needed

---

### Post by ibjsb4 on 2013-01-16
> **haqking said:**
> it isnt my experience, I have never used it, I dont need to.

It was  response to snowpine who mentioned seeing lots of support requests about people bricking their builds due to unnecessary "cleaning", I was agreeing as i have seen many too

Really not finding any bugs that are a big deal.  

[https://bugs.launchpad.net/ubuntu/+source/bleachbit](https://bugs.launchpad.net/ubuntu/+source/bleachbit)

Maybe your talking about "Computer Janitor", that package can mess up your day.

---

### Post by haqking on 2013-01-16
> **ibjsb4 said:**
> Really not finding any bugs that are a big deal.  

[https://bugs.launchpad.net/ubuntu/+source/bleachbit](https://bugs.launchpad.net/ubuntu/+source/bleachbit)

Maybe your talking about "Computer Janitor", that package can mess up your day.

I didnt mention "bugs"

i was referring to people using bleachbit and then bricking the machines because of the unnecessary cleaning of files they really didnt want or need to "clean"

Anyways the point is if you dont know what you are doing or cleaning then any of these tools can ruin your day, if you do know then you probably dont need them in the first place.

Peace

---

### Post by ibjsb4 on 2013-01-16
> **haqking said:**
> Anyways the point is if you dont know what you are doing or cleaning then any of these tools can ruin your day, if you do know then you probably dont need them in the first place.

Peace

That would be true of everything.  peace :)

---

### Post by Zill on 2013-01-16
> **haqking said:**
> ...i was referring to people using bleachbit and then bricking the machines because of the unnecessary cleaning of files they really didnt want or need to "clean"...
Too many newbies think (incorrectly!) that Linux has the same problems as MS Windows and so needs the same "cleaning"!

> **haqking said:**
> ...Anyways the point is if you dont know what you are doing or cleaning then any of these tools can ruin your day, if you do know then you probably dont need them in the first place.
+1  Very true!

---

### Post by oldos2er on 2013-01-16
> **Yezinki said:**
> How often do you expert members clean your Ubuntu machine, using terminal or Bleachbit?


This isn't the first thread you've start about Bleachbit or "cleaning". As was said already, we need to know what exactly you wish to clean; what is your goal?

---

### Post by ibjsb4 on 2013-01-16
> **Zill said:**
> Too many newbies think (incorrectly!) that Linux has the same problems as MS Windows and so needs the same "cleaning"

Its  a very easy to use newbie tool (like ubuntu-tweak) whats makes it so great and highly recommended.  I really don't think its the newbies thinking incorrectly.

---

