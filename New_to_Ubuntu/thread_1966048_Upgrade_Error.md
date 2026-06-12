---
title: "Upgrade Error"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-04-26
Tried to upgrade to 12.04 through upgrade manager.
At, 'Setting new software channels' stage, received a few errors of the following type :

W:Failed to fetch bzip2:/var/lib/apt/lists/partial/. . . . . _ubuntu_dists_precise_main_source_Sources  Hash Sum mismatch

After that the upgrade process stopped.
How can i get my OS upgraded ?
I have also downloaded the iso, can that be used to upgrade my OS ?

---

### Post by Jocklad on 2012-04-26
Had exactly the same problem today.

Think I will just wait for the CD .

Jocklad

---

### Post by 3dmatrix on 2012-04-27
I tried using the CD to upgrade my OS but it gave the following error

E: Sub-process gpgv returned an error code (2)

W: Signature verification failed for: /media/Ubuntu 12.04 LTS i386/dists/precise/Release.gpg

What is going wrong ?

---

### Post by 3dmatrix on 2012-04-28
Seems it is not a right time to upgrade to 12.04. There are a lot of people on this forum who are comming up with a lot of problem while upgrading and there are not enough solution being given so may be i would wait for some time till things get better.
Thanx anyway !

---

### Post by v_2e on 2012-05-18
Hello!
Is this problem solved in some way already?

---

### Post by 3dmatrix on 2012-05-18
> **v_2e said:**
> Hello!
Is this problem solved in some way already?

I did not receive any reply or suggestion to such problem so i consider it is a bug that is without proper solution so i wud not like to upgrade till then !

---

### Post by 3dmatrix on 2012-06-25
I am still geting the following error :

Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Plz can any one help.

---

### Post by NikTh on 2012-06-25
2 suggestions 

1) Open a terminal and run 
```
sudo rm -rf /var/lib/apt/lists/*
```

2)Go to update manager > ubuntu software > and Download From : change server to Main. 

Try again..
```
sudo apt-get update
```

---

### Post by 3dmatrix on 2012-06-25
> **NikTh said:**
> 

2)Go to update manager > ubuntu software > and Download From : change server to Main. 

Try again..
```
sudo apt-get update
```

I tried the 2nd option and got the following ERROR !

W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by jmfal on 2012-06-25
Try this:

```
  sudo rm /var/lib/dpkg/lock   
```

Then run:

```
  
sudo rm -rf /var/lib/apt/lists/*      
```
Then do the update

---

### Post by 3dmatrix on 2012-06-26
After using these codes i got the following result :

sudo rm /var/lib/dpkg/lock
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update


W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by jmfal on 2012-06-26
try the first  commmand  then update

---

### Post by 3dmatrix on 2012-06-26
Used these codes and got the following result :

sudo rm /var/lib/dpkg/lock
sudo apt-get update

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

-----------------------------------------
Then started the Upgrade process and received the following error.

Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.


I am trying to Upgrade since more than two months but still am not able to do that.

.

---

### Post by jmfal on 2012-06-26
I t looks like you have some ppa's or added some repos?  Yes

Open up "Update Manager"  and click on settings>> Other Sources >>uncheck the sources that are giving you errors.

You might end up unchecking all of them , they might give you problem when you try todo the version upgrade.

I'm surprised nobody thought of that.

---

### Post by 3dmatrix on 2012-06-26
I have not made any changes before posting this message.
So kindly have a look at the attachment and tell me what might be going wrong.

---

### Post by jmfal on 2012-06-26
OK  in the other sources section uncheck the top one CD,  then  right below that there are two for canonical partners , put a check in the second one (sources), and try to update, if you have any errors post them

---

### Post by nipunshakya on 2012-06-26
Please take a look at this and follow the instructions if u have similar problem:
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/194077](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/194077)
Goodluck

---

### Post by 3dmatrix on 2012-06-26
After doing those changes i get the following error :

Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.


W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Just to inform you, I am behind a proxy.
And do i need to check off Opera ?

.

---

### Post by jmfal on 2012-06-26
Yes uncheck opera then run
```
sudo apt-get update
```

and
```
  sudo apt-get upgrade    
```

If there are no errors and you feel confident that every thing is good, go back into the update center and in the other sources tab remove all the checks and do your version upgrade to 12.04

You can put a check back for those after you go to 12.04 
I would do one at a time, actually its two,, example:
canonical and canonical source
opera and opera source

---

### Post by 3dmatrix on 2012-06-26
Ok ! i will try :)

---

### Post by jmfal on 2012-06-27
Before you do download  and burn a iso of 12.04 just in case.

Did you backup all your important files???

Good Luck , I'm going to bed.

---

### Post by nipunshakya on 2012-06-27
Just in case, if the upgrades won't work out, there is a better option of a clean installation as well...

---

### Post by 3dmatrix on 2012-06-27
sudo apt-get update

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-i386_Packages  Hash Sum mismatch
E: Some index files failed to download. They have been ignored, or old ones used instead.

sudo apt-get upgrade

No error

So what next ? Should i upgrade ?

---

