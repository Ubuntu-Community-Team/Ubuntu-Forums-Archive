---
title: "Error messages no matter what I'm trying to install"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by rcmfo on 2012-02-28
Hi everyone,

I have been trying to install a few programs through the Software Center, but no matter what I choose to install (even what seems to be the most common and well-liked programs), I get the following two messages, one after the other:

**1.  Failed to Download Package Files - Check your internet connection**

Which isn't true, as I have an active internet connection...

and, then

**2.  Requires installation of untrusted packages - the action would require the installation of packages from not authenticated sources**

Which makes no sense to me, because, again, it doesn't matter what I'm trying to install, I keep getting the same message.

Anybody know how I should go about fixing this?

Thanks in advance,
Rhonda

---

### Post by lechien73 on 2012-02-28
Hello & welcome to the forums,

Please could you open a terminal window and type:

```
sudo apt-get update
```

Are any errors reported? If not, please try the Software Center again.

---

### Post by rcmfo on 2012-02-28
I *did* get error messages, unfortunately...

---

### Post by matt_symes on 2012-02-28
Hi

We need to see the error messages from the command posted above by lechien73. 

Copy and paste then from the terminal into your next post.

Kind regards

---

### Post by rcmfo on 2012-02-28
So sorry!  Here you go:

```
W: GPG error: http://us.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/source/Sources  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/source/Sources  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/source/Sources  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/source/Sources  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.184 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Thanks again.  I'm just a lowly end user, so I have no idea what's wrong.  But I am so grateful to you for your help.

---

### Post by QIII on 2012-02-28
It's not your internet connection.

Did someone else set this machine up for you?

Your sources.list has references to repos from an old version that is long past its end of life.  Those don't exist where they are being looked for.

Oneiric shouldn't be looking for them, I wouldn't think.

---

### Post by audiomick on 2012-02-28
> **QIII said:**
> 
Oneiric shouldn't be looking for them, I wouldn't think.

No, I wouldn't think so, either.

---

### Post by QIII on 2012-02-28
rcmfo --

Audiomick and I are not talking around you or the problem, just wondering how you got to this state.

---

### Post by audiomick on 2012-02-28
Yes. I don't really know with any certainty what to do, either. 

I think you could try and edit thos sources out of your sources list.

If you do
```
gksudo gedit /etc/apt/sources.list
```

you will be asked for a password, and then the text editor will open with a file that has your sources listed.

Bear in mind that you are now working with root priviliges on a file that is pretty important.

What I would try is to go through and put a # at the start of any line that has "intrepid-backports" in it.

The # will comment out the line, i.e. it will be ignored. 

Try updating or installing again. If this doesn't make any difference, you can go back and remove the # easily, and you are back where you started.

---

### Post by matt_symes on 2012-02-28
Hi

The intrepid repos references definitely need to go.

This is one way to do it.

First make a back copy of your sources file.

```
sudo cp /etc/apt/sources.list{,.bk}
```

Then will delete the lines.

```
sudo sed -i '/intrepid/d' /etc/apt/sources.list
```

Then update

```
sudo apt-get update
```

Kind regards

---

### Post by Fayaz427 on 2012-02-29
[http://ubuntuforums.org/showthread.php?t=1928387]("http://ubuntuforums.org/showthread.php?t=1928387")
try this
all the best

---

### Post by lechien73 on 2012-02-29
Hi folks,

The intrepid repos definitely need to be removed, as per Matt's post, but you there's also a key signing error for the main Oneiric repo.

To solve this, you could do:

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

Thanks for your comment on my membership thread as well :D

---

### Post by rcmfo on 2012-02-29
Thank you, everyone.  I will try that (as soon as my toddler goes down for a nap!) and let you know how it goes. - R

---

### Post by rcmfo on 2012-02-29
Well, it's a no-go.  I followed your directions but I'm still getting error messages.  Since I don't know what it is you've told me to do (just being honest), it's possible that I didn't do something right.  Working off the command line isn't something I do every day.  In any case, I may just reinstall and see how that goes.

Thanks again!
- R

---

### Post by oldos2er on 2012-03-01
Could we see the error messages please?

---

### Post by egalvan on 2012-03-01
Are we 100% certain of which release is actually installed?

I see both Oneiric and Intrepid referenced...

---

### Post by matt_symes on 2012-03-01
Hi

I missed in the in place edit switch from my sed command. Much apologies.

```
sudo sed **-i** '/intrepid/d' /etc/apt/sources.list
```

If you run the command again with -i, it will get rid of your intrepid references.

I will amend my previous post.

Kind regards

---

