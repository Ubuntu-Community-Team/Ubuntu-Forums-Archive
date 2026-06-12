---
title: "Update errors"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by RedTornado5252 on 2012-04-10
When attempting to install newest security updates my computer hangs at "applying changes" keep getting this error, "/tmp/tmpQPLfrD (END) (END)Error in function:  "
I believe the same error would occur when I would attempt to update google chrome..

Also every time i run apt-get update i get this error, "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0"
Should I just remove the entry from my sources list? 
Is it wise for a noob to have "prereleased,multiverse,and unsupported updates enabled?

---

### Post by RedTornado5252 on 2012-04-10
if Ive posted in the wrong forum or anything please let me know. totally new to the community. thanks

---

### Post by daslinkard on 2012-04-10
From looking at another [post]("http://askubuntu.com/questions/67594/unable-to-repair-packages-in-ubuntu-software-center"), you should be able to fix this with the following sudo commands:

> sudo gpg --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
> sudo gpg --export --armor 5A9A06AEF9CB8DB0 | sudo apt-key add -

---

### Post by RedTornado5252 on 2012-04-10
hmm.. after the first one i get this:

ubuntu@ubuntu-desktop:~$ sudo gpg --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
[sudo] password for ubuntu: 
gpg: WARNING: unsafe ownership on configuration file `/home/ubuntu/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
ubuntu@ubuntu-desktop:~$ 

and after the 2nd command:

ubuntu@ubuntu-desktop:~$ sudo gpg --export --armor 5A9A06AEF9CB8DB0 | sudo apt-key add -
gpg: WARNING: unsafe ownership on configuration file `/home/ubuntu/.gnupg/gpg.conf'
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

---

### Post by daslinkard on 2012-04-10
Hit Ctrl+Alt+T to open Terminal and then run following commands one after another:
     Code:
$ sudo -i  
# apt-get clean  
# cd /var/lib/apt  
# mv lists lists.old  
# mkdir -p lists/partial  
# apt-get clean
# apt-get update

---

### Post by critin on 2012-04-10
Are you trying to install updates on a live cd?

---

### Post by RedTornado5252 on 2012-04-10
"Are you trying to install updates on a live cd?" 
nope, ubuntu 11.10 gnome only OS on the computer.


"Hit Ctrl+Alt+T to open Terminal and then run following commands one after another:
     Code:
$ sudo -i  
# apt-get clean  
# cd /var/lib/apt  
# mv lists lists.old  
# mkdir -p lists/partial  
# apt-get clean
# apt-get update 	"

 Thanks for the help, unfortunetly im getting the same error. when I try to update from the update manager I get this error everytime. 

"* SECURITY UPDATE: Update to 5.1.62 to fix security issues (LP: #965523) 
    - [http://dev.mysql.com/doc/refman/5.1/en/news-5-1-62.html](http://dev.mysql.com/doc/refman/5.1/en/news-5-1-62.html) 
 
 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Mon, 26 Mar 2012 13:26:05 -0 400 
 
/tmp/tmpX8yKg0 (END) (END)Error in function:  "

---

### Post by RedTornado5252 on 2012-04-10
Although, if i never cancel it just hangs at applying changes forever.. when i click details i can see "/tmp/tmpX8yKg0 (END) (END)Error in function:  "

---

### Post by critin on 2012-04-10
> nope, ubuntu 11.10 gnome only OS on the computer.

Okay, I asked because this looks like a live cd terminal.  Is your user name ubuntu?  That's clever.  lol
  
> ubuntu@ubuntu-desktop:~

---

### Post by RedTornado5252 on 2012-04-10
lol, yep.

---

### Post by daslinkard on 2012-04-10
I brought this question up to a solid Ubuntu user and he suggesting dumping and re-adding the PPA.  

Documentation on how to do this can be found [here]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by RedTornado5252 on 2012-04-10
"I brought this question up to a solid Ubuntu user and he suggesting dumping and re-adding the PPA.  

Documentation on how to do this can be found [here]("https://help.ubuntu.com/community/Repositories/Ubuntu")."

unfortunately none of the ideas suggested seem to work. Update manager says the update have been downloaded, but not installed. Its still freezing and giving me this "/tmp/tmpX8yKg0 (END) (END)Error in function:"

---

### Post by daslinkard on 2012-04-10
Did you remove the ppa like in the removing sources section? Then add it again so the key refreshes?

---

### Post by RedTornado5252 on 2012-04-10
yep, no luck :[

---

### Post by daslinkard on 2012-04-10
Alrighty then....I'm going to try and do some more research and see if I might be able to find a possible solution for you.

---

### Post by RedTornado5252 on 2012-04-10
thanks!

---

### Post by daslinkard on 2012-04-11
I wonder about trying this: 
```

gpg --keyserver pgpkeys.mit.edu --recv-key  5A9A06AEF9CB8DB0

```Then try
```
 gpg -a --export 5A9A06AEF9CB8DB0    | sudo apt-key add -
```

---

### Post by RedTornado5252 on 2012-04-11
I wonder about trying this: 
 	Code:
 	gpg --keyserver pgpkeys.mit.edu --recv-key  5A9A06AEF9CB8DB



^^this seems to work

but im a little confused about the next command. 
do i run 
gpg -a --export 5A9A06AEF9CB8DB0 followed by sudo apt-key add? or all one line? right now my terminal is hanging after key-add.. about 20min now.

thanks for the help

---

### Post by RedTornado5252 on 2012-04-11
just to clarify first code works
2nd code works when i run "export" command seperate from "apt-key add" 
apt-key command goes through, but leaves me w/ a blinking prompt and no term output

---

### Post by RedTornado5252 on 2012-04-11
Success! ;)

Thanks daslinkard! For some reason (error on my part im sure), the gpg codes you suggested weren't working with my ubuntu 11.10 setup. I Decided to updrade to 12.04beta2 earlier today. After the install I was getting the same errors, so I tried those codes and it worked right away. I think (THINK) I may have done a sloppy removal of KDE.. the culprit was a 35kb kde config. :]  
Thanks guys. 

** by the way, the ubuntu community has been outstanding! everyone has been very helpful and patient. the complete opposite of the linux user stereotypes you always hear about..... except that one guy on #IRC :] **

---

### Post by daslinkard on 2012-04-11
Awesome, I'm glad I was able to help.  If at any time in the future you have a question that I might be able to help you with....I'm here for you.  Good luck moving forward!  Also can you mark this topic as solved please.

---

