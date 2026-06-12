---
title: "cannot update clamav"
date: 2010-12-04
forum: Recurring Discussions
---

### Post by toolmania1 on 2010-12-04
I am told my clamav engine is outdated.  I ran this:

sudo apt-get install clamav

I am told clamav is already the newest.

But, when I run this:

I am told the clamav engine is outdated.

I have version 96.3.  I am told I need 96.5 when I run:

sudo freshclam

How do I update clamav to the newest?

---

### Post by susema on 2010-12-04
Try this;

```
sudo apt-get install aptitude && sudo aptitude install clamav &&  sudo aptitude update && sudo aptitude upgrade
```

---

### Post by kgarbutt on 2010-12-04
This is how I update my clamav:

>If using Ubuntu (sudo gedit /etc/apt/sources.list), add (cut & paste) this to your sources.list (Note: charge karmic to your distro (ie lucid, maverick):

deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) karmic main

>Add the key (cut & paste) using the terminal):

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5ADC2037

>then run:
sudo apt-get update
sudo apt-get upgrade

Now, as for clamtk, I usually have to download the most recent deb file from the web site. From the terminal do: sudo apt-get remove clamtk. Then, install the recent clamtk deb file, and you will have the most recent clam files. I know this works because this is how I do it, and mine are all up to date.

Good luck.

---

### Post by uRock on 2010-12-05
I get the latest clamtk front end from their website whenever a new version comes out, but it is not needed as long as the signatures are up to date.

---

### Post by toolmania1 on 2010-12-06
Ok, I am going to try this later.  This looks like a more advanced way to do this, but hey, I am up for the challenge.  Through our struggles we learn things, right?




> **kgarbutt said:**
> This is how I update my clamav:
 
>If using Ubuntu (sudo gedit /etc/apt/sources.list), add (cut & paste) this to your sources.list (Note: charge karmic to your distro (ie lucid, maverick):
 
deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) karmic main
 
>Add the key (cut & paste) using the terminal):
 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5ADC2037
 
>then run:
sudo apt-get update
sudo apt-get upgrade
 
Now, as for clamtk, I usually have to download the most recent deb file from the web site. From the terminal do: sudo apt-get remove clamtk. Then, install the recent clamtk deb file, and you will have the most recent clam files. I know this works because this is how I do it, and mine are all up to date.
 
Good luck.

---

### Post by toolmania1 on 2010-12-06
I will try this also and see if it works


> **susema said:**
> Try this;
 
```
sudo apt-get install aptitude && sudo aptitude install clamav &&  sudo aptitude update && sudo aptitude upgrade
```

---

### Post by uRock on 2010-12-06
> **toolmania1 said:**
> I will try this also and see if it works
That will only install the same clamav that you already have.

---

### Post by toolmania1 on 2010-12-06
As I learn of this, I am starting to realize that maybe this is a lot more complicated than this process should be.  Although, I know that once I do it once, it will be fine each time ( Or I would think ).  But, shouldn't this process in general just be a little easier.  

For example, we should just be able to click on an update button or something to update instead of going through some hoops like this.  I know they are not really hoops, but you understand what I am trying to say.

I will figure it out and am not complaining.  I am just wondering if this process could not be made a little easier.

---

### Post by rburkartjo on 2010-12-19
tool i know that it can be a pain to update the virus scanner but as long as the defs are currently sudo freshclam i wouldnt worry about it.

---

### Post by toolmania1 on 2011-01-06
I believe after I ran the purge command and purged all the clamav stuff, I could just install the new clamav.  Installing a new version after removing the old version seems 1000 times easier than trying to update.  Updating is very difficult unless you have it down like some other users on here do.  I obviously did not.  But, after purging, it was super easy.  You have to go to the clamav page to find where it talks about removing the old version.  I don't have the link right now.  If I remember, I will post that link later.  The link to the clamav site is on one of my other posts though.  I had to click another link from that page, but it can be found.

---

