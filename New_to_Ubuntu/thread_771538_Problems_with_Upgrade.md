---
title: "Problems with Upgrade"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by johngml on 2008-04-27
Yesterday I decided to upgrade from 7.10 to 8.04. Bad move. Download took five and a half hours on broadband and install has taken four and a quarter hours so far. The is an error for the network manager not working which asked if I wanted to send a report. Second bad move. Apport opened up and twenty minutes later was still going so I cancelled it as I wanted to go to bed. Install has been frozen for the last twenty five minutes with no time remaining left in the counter. Is this normal for it to take this long ? And is it normal for Ubuntu to screw up on installation as this is the third time I have installed/upgraded and everyone has had errors ?  Am I going to have to format the disc and start again like I have on a previous install ? Sorry to sound negative but I have installed Windows XP on over a hundred machines and I only ever had one error and that was due to a scratched disc so I am a bit concerned that Ubuntu cannot even install once without an error. If it wasn't for the fact that I like it so much I would have ditched it.

---

### Post by skrribble on 2008-04-27
When I upgraded from Feisty to Gutsy, I had similar problems and ended up having to reformat and reinstall.  So, when I wanted to upgrade to Hardy, I backed up everything and reformatted and reinstalled.  I think thats the best way to go.  I don't you the upgrade button in Update Manager, as that has only given me problems.  And honestly, if you back everything back before you reformat, its pretty easy and usually goes pretty fast.

---

### Post by hackle577 on 2008-04-27
I think the servers are way overloaded right now what with everyone trying to download and install all their applications at the same time. That would explain the length of time it's taking for you to install the system. I would wait until non-peak hours and try installing then.

---

### Post by PhoenixP3K on 2008-04-27
I'm sorry to hear you had a bad experience upgrading. However the servers have been hammered pretty seriously since Thursday. I figured it would trail during the week-end when more people have some free time to make an upgrade. 

The worse of the storm has passed. It's my first time upgrading but it's a known fact. Even amongst Microsoft Windows user is that a clean/fresh install is always better when possible. 

All that being said I did an upgrade myself and had to leave it running over night (Thursday night, bad move I know). Had a few errors and had to restart once, but since then it's been smooth sailing.

---

### Post by Zralou on 2008-04-27
I downloaded Ubuntu 8.04, Kubuntu 8.04 (KDE 3), and Kubuntu 8.04 (KDE 4) on saturday night and all of them downloaded at 350-400 kb/sec.  I suggest if the download is slow, switch to another mirror, i'm in Florida, and I downloaded KDE 4 from England at 400kb/sec.

Sara Lou

---

### Post by InfinityCircuit on 2008-04-27
Your machine should certainly be salvageable.  Check out /etc/apt/sources.list and make sure it points to the hardy sources, not the gutsy ones. (replace instances of gutsy with hardy).  Then, open up a terminal and try:

```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get dist-upgrade
```

---

### Post by johngml on 2008-04-27
I decided to stay up and found that the computer has not moved so I turned it off by the button. Having restarted it It appears that 8.04 is installed, the Firefox icon was blank but I replaced that (bit miffed that many of my favourite extensions don't work anymore) and it appears to be okay. Got a crash report showing which asked if I would like to send a report to which I said no because I don't know how many hours it might take.
I think the advice given is sound and IF I ever try and upgrade again I will back up, format then install. It must be quicker than the five hours it took before I turned off the computer. On a quick glance, with the exception of Firefox 3, I could not see any difference and am now wondering why I bothered. I will have a better look tomorrow but I would like to say thanks to everybody who replied so quickly.

---

### Post by PhoenixP3K on 2008-04-27
If you upgraded, the old Firefox should still be available by running firefox-2, this way all your extensions should be working again.

And yes, you wont notice much difference, but most of the work has been done in the back end.

---

### Post by frank002 on 2008-04-27
My upgrade from Gutsy to Hardy went terrible. I ended up making a clean install. Maybe that is the best thing.

---

### Post by mgmiller on 2008-04-27
I upgraded 2 machines, one last night and one this morning.  Total time to download and install was 1 hour.  I needed over 1.2 GB of data for one of the machines, but the mirror I used gave me over 2000k download speed, so not too bad.  The medibuntu servers on the other hand are very slow, I can only get about 56k out of them.

I Have upgraded the machine I am responding to this post on "a lot".  Take a look at my sig line. I haven't reinstalled my OS in 3 years.

There are a couple of things that make upgrading fairly painless.
1) Don't use automatix
2) Don't use easyubuntu
3) Don't use envy (if you can help it)
4) Don't use automatix
5) Don't use automatix.
  5A) Between the ubuntu-restricted-extras package and the medibuntu repository, you just don't need to mess with those system destroying scripts.
6) (This is the secret of getting good download speeds, so don't tell anyone)
Go to System > Administration > Software Sources
In the Download From: box, click the down arrow to open the choices dialog and then click "Other"

In the new dialog that opens, click "Select Best Server".

This will test all servers on earth and find the best one for you.

When it finds it, click select server.
The new one should appear in the "Download From" area in the first tab. 
Close the window.
Now you can do the Update Manager for the upgrade.

---

