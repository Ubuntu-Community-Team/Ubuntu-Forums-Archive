---
title: "Apparmor"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by grewolf on 2008-07-17
I was reading and it said that apparmor was only enabled for cups printing?  I'm not sure of this.  I went into synaptic and installed the apparmor doc and did ```
man apparmor
``` in the terminal but I didn't understand the manual

I wanted to enable apparmor but what I've read and I went to [HTML]http://www.beginlinux.com/index.php/desktop_training/ubuntu/ubsecure_m/Secure_ub/app_create_m[/HTML]

This looks much to complicated for me.  I would not be sure where to press "a" for "allow"  

Is there a layman's user guide for apparmor or do you need to be extremely familiar with Ubuntu and it's inner workings to use this tool properly?

I have also tried to read this [HTML]https://wiki.ubuntu.com/AppArmorGutsy[/HTML] 

I feel dumb... but a lot of what I'm reading doesn't make sense to me.  Not on the above page in particular, but when I travel to links, and my search in google left me frustrated.  I sometimes think it's a different language.

---

### Post by PmDematagoda on 2008-07-17
Apparmor administration is very easy, but it does take some getting used to the terminal and the CLI commands in general. About Apparmor, these are the commands you may need:-
```
sudo apparmor_status
```
gives you the current state of Apparmor which includes the profiles currently enforced, under complain mode and any processes currently under any profiles that are loaded.

```
sudo /etc/init.d/apparmor *action*
```
this allows you to control Apparmor, stop it, start it, reload it and the profiles and a few other things.

```
sudo aa-enforce *name-of-profile*
```
allows you to set a currently loaded Apparmor profile into enforce mode.

```
sudo aa-complain *name-of-profile*
```
allows you to set a currently loaded Apparmor profile into complain mode.

```
sudo apparmor_parser -a *name-of-profile*
```
allows you to add a new profile to the Apparmor framework.

```
sudo apparmor_parser -R *name-of-profile*
```
allows you to remove a profile from the Apparmor framework.

Basically the above commands are what you would need to administer Apparmor at the basic level, but there are more things that you could do with Apparmor, especially with the profiles which are usually located in /etc/apparmor.d. You can study the current profiles so as to give you a good idea on where to start with writing your own Apparmor profiles:).

---

### Post by grewolf on 2008-07-17
> **PmDematagoda said:**
> .

Basically the above commands are what you would need to administer Apparmor at the basic level, but there are more things that you could do with Apparmor, especially with the profiles which are usually located in /etc/apparmor.d. You can study the current profiles so as to give you a good idea on where to start with writing your own Apparmor profiles:).

Wow thank you for the quick response.  The info you give is easy to use and understand.  I used the command ```
sudo apparmor_status
``` and the problem I'm having is understanding the read out.  Is there a reliable resource that I can go to further understand the readout of it.  I had a very bad issue with security with windows which is the main reason why I moved to Ubuntu.  I have gone to the /etc/apparmor.d. and an example is sbin.klogd and I open it and have no idea what I'm reading.

---

### Post by PmDematagoda on 2008-07-17
Well, the only resource I can recommend is:-
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

---

### Post by grewolf on 2008-07-17
> **PmDematagoda said:**
> Well, the only resource I can recommend is:-
[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Thank you I have gone to this site and entered ```
sudo apparmor_status
``` and have 2 listings for /sbin/kloged one says that it is in complain mode and one says that ```
4 processes are unconfined but have a profile defined
```. The one that says it is unconfined but has a profile defined has (5412) beside it 

 ```
/sbin/klogd (5412)
```

I have read through the document on the link that you provided but don't understand this in particular

---

### Post by PmDematagoda on 2008-07-17
It means that 4 processes have a profile attached to them, but the profiles are only in complain mode and are therefore not confined.

Complain mode:- The processes are only confined "virtually" and not totally, Apparmor will report any incidents concerning improper access outside the profile, but will not stop them. This is good when you are testing a profile.

Enforce mode:- Apparmor reports any events outside the profile and also stops such actions.

---

### Post by KenF on 2008-09-12
Apparmor really messed up my printing.  I can not get printing to work at all with apparmor on.  The only thing that works is if I:

 sudo /etc/init.d/apparmor stop

before any attempted prints.  I would like to turn apparmor off permanently.  Please help!

Ken

---

