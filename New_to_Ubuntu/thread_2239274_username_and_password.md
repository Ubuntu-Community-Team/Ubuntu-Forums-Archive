---
title: "username and password"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by littlefoot2 on 2014-08-12
I'm New  to This System and a Guy Brought it to me to Fix!! The Web site tutorial Didn't Help Me. He Doesn't Know The Admin username or password Because it was Bought at a Flea Market. So My Question is How Do I Change Both?? Any Help would Be Appreciated, Thank You.

---

### Post by littlefoot2 on 2014-08-12
It's Saying: Authentication token manipulation error!!! This is on The Change username and password portion of the Site!! Any Help out Here???

---

### Post by mastablasta on 2014-08-13
are you trying to reset the password? if so then: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by coffeecat on 2014-08-13
> **littlefoot2 said:**
> Because it was Bought at a Flea Market.

If you don't know the person who installed and configured Kubuntu, then don't trust the installation. It could be corrupted, infected with rootkits, or simply be an obsolete and unsupported version. You would be far better off creating a new installation of one of the variants of Ubuntu on it. If you need help with that, you are welcome to start a thread in the [Installations & Upgrades forum]("http://ubuntuforums.org/forumdisplay.php?f=333"), or here in New to Ubuntu, detailing the make and model, plus specifications of the machine, so that people can advise.

If you don't know much about the differences between the members of the Ubuntu family, such as Ubuntu itself, and Kubuntu, Xubuntu, Lubuntu, etc, you will find plenty of threads in the chat areas discussing the pros and cons of the different desktops and flavours. If you want to know more about Ubuntu and its family of derivatives, you are welcome to start a thread in [Ubuntu, Linux & OS Chat]("http://ubuntuforums.org/forumdisplay.php?f=434").

---

### Post by littlefoot2 on 2014-08-13
Thank You But That's Where I was at and where I got The Message Then IT said Password Unchanged!!! I Haven't Done a Linux System since The Early 90's and This Version Has Me All Befuddled!!! I Live in a R.C.F. Residential Care Facility from a Work Accident and I am The Only Tech Person Here!!! Been Doing PC's since The Commodore 64, I Love a Challenge But This Thing is Pissing Me OFF!!! Any Help is Appreciated!!! Thank You.

---

### Post by steeldriver on 2014-08-13
The message "Authentication token manipulation error" probably means you missed the step of remounting the filesystem in read-write mode

```

mount -o remount,rw /

```

However, I agree with the other posters - better to nuke it and do a clean install

---

### Post by yancek on 2014-08-13
You haven't indicated which release of Ubuntu you are using, I guess we are all assuming you are using Ubuntu as you are here at these forums.  Also, information on your machines hardware would be relevant.  If it was purchased at a flea market, it probably isn't the latest/greatest hardware and a new Ubuntu might not run on it and the system installed might be outdated/unsupported.

---

### Post by littlefoot2 on 2014-08-13
I Only Have Access to The Guest Account, So I Can't Install a New Operating System without The Administrators Password!!! The Guy That Bought IT Knows NOTHING about THIS System!!! On The Site in The Change Username and Password it Says on Changing The Admin Password : Authentication Token Manipulation Error!!! And THAT'S Where I'm Stopped at!!! You Have Any Ideals or Help on THIS Matter/Problem??? I'd Appreciate Any Help at This Point!!! Thank You.

---

### Post by lisati on 2014-08-13
Were you able access the "recovery mode" recommended by the "reset password" link earlier in this thread?

---

### Post by steeldriver on 2014-08-13
You shouldn't need to access the **current** OS at all in order to install a **new** OS, you just need bootable media (CD or USB) and - possibly - access to BIOS to set the boot order

---

### Post by littlefoot2 on 2014-08-13
lunbuntu? it says on Start up and Software is up to date. I Vaguely remember How to Get around on a Linux System and Haven't Found The System Info Yet Because Yesterday was The first Time I've Seen IT and I'm Still Figuring Out How to Get Around on IT!!! I Told The Guy His Best Bet would Be to Change out The Hard Drive and Put a Windows System on IT!!! It's in a Old TOSHIBA Satellite Laptop!!! As Old as IT is IT probably Couldn't Run a Win 7 System??? I Have No Tools to Do Hardware Problems or Fixes So I Just Do Software Repairs!!!

---

### Post by littlefoot2 on 2014-08-13
Yes That's  Where I Started and I Followed The Directions But on The Change Password it Says: Authentication Token Manipulation error!! And The Link after That sent Me Here!! It's Been Many Many Years since I Owned or Worked on Any Variant's of The Linux System!!! So Please Bare with Me I'm a Re-Newbie to THIS System!!! IT Says it's a Lunbuntu on Start up and Ubuntu on The System. I STILL Haven't Found The System Info Yet!!! It's on a Old TOSHIBA Satellite Laptop!!! IT Also says System is up to Date!!! Any Help would Be Appreciated??? Thank You.

---

### Post by littlefoot2 on 2014-08-13
Thank You THAT'S What I was Looking For and IT WORKED!!! I Thought IT was mount Something But Like I said IT Has Been MANY YEARS Since I've Been on one of These Systems and IT/They Where Probably one of The FIRST Linux Systems!?!?!? THANK YOU AGAIN :D !!!!

---

### Post by littlefoot2 on 2014-08-13
Got it changed thank you

---

