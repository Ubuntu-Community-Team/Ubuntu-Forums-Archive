---
title: "Playing DVD's"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by ajp2 on 2014-07-09
Hello I'm new to ubuntu and I'm not very computer minded so any help would be very much appreciated.I have installed 14.04 version, I tried a DVD but it wouldn't play, Can someone explain to me how to solve this problem. Thank you. ajp2.

---

### Post by kc1di on 2014-07-09
The reason it won't play is because you need to install some addition Proprietory codecs.  
They can not ship with Ubuntu because of Legal problems in some countries - U.S. for one. 
However you can install them by installing the pacakage and running the script on[ this page. ]("https://help.ubuntu.com/community/RestrictedFormats")
Good Luck and welcome to Linux & Ubuntu :)

---

### Post by ajp2 on 2014-07-09
Hello Dave, Thank you for the help and welcome, everything working now. Alan

---

### Post by ajp2 on 2014-08-04
Good morning, Can anyone help me please? I thought that I had solved my problem with not being able to play DVD's. I haven't, my computer crashed and I had to re-install everything I have tried to install handbrake,VLC media player and still no joy. I'm a total novice when it comes to computers so my wife had a go at installing and still not working. I told a forum member who helped me before that everything was now working ok because it would work on copies of DVD but now it won't play these either. Any help is much appreciated. Alan.

---

### Post by coffeecat on 2014-08-04
Did you follow the link kc1di posted in post #2 this time around? Did you install ubuntu-restricted-extras and run "sudo /usr/share/doc/libdvdread4/install-css.sh" ?

---

### Post by kc1di on 2014-08-04
you'll have to reinstall the codec in post # 2 and run the command again.  
I keep a little note book handy and keep a list of things I need to do after a new install. 
that way I don't forget something just a suggestion :)

---

### Post by Rob Sayer on 2014-08-04
> **kc1di said:**
> you'll have to reinstall the codec in post # 2 and run the command again.  
I keep a little note book handy and keep a list of things I need to do after a new install. 
that way I don't forget something just a suggestion :)

A list like that is a great idea ... I've DE/distro hopped on my netbook before the hardware support issues were fixed in 14.04.  I always have a list now.

Also, I do updates and most app software installs from the terminal and if something looks weird, or it's really huge, I'll copy and paste everything from the terminal and save it to a text file in a dedicated folder.  Very handy for debugging possible problems.

---

### Post by ajp2 on 2014-08-04
This keeps coming up when I try to follow your (kc1di) instructions,  can't understand why.   Firefox can't find the file at apt://ubuntu-restricted-extras.  Thanks to everybody for trying to help me. Alan

---

### Post by coffeecat on 2014-08-04
> **ajp2 said:**
> This keeps coming up when I try to follow your (kc1di) instructions,  can't understand why.   Firefox can't find the file at apt://ubuntu-restricted-extras.  Thanks to everybody for trying to help me. Alan

Firefox should be prompting you to open it with Software Centre. Rather than troubleshoot that, simply open Software Centre, search for ubuntu-restricted-extras and install it from the software centre. You need to keep an eye on the installation of restricted extras. You will be prompted to agree to a EULA for the installation of the Microsoft core fonts. They won't help you play DVDs, but they are part of the bunch of things that come with restricted extras and they are useful to have.

---

### Post by ajp2 on 2014-08-04
I have installed ubuntu-restricted-extras, It didn't ask me to agree to EULA, It now plays copies of DVD's again but still not play normal DVD's.Thanks again will keep trying to solve my problem.

---

### Post by coffeecat on 2014-08-04
> **ajp2 said:**
> It didn't ask me to agree to EULA,

In which case you won't have the Microsoft core fonts installed, but that's off-topic for this thread. If you need help with that you are welcome to start another thread.

> **ajp2 said:**
>  It now plays copies of DVD's again but still not play normal DVD's.

What do you mean by "normal" DVDs? If you mean proprietary encrypted DVDS, then you need to run the install-css.sh script as mentioned before.

---

