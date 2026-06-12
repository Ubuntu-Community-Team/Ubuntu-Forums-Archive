---
title: "Help finding ubuntu documentation"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by RWells on 2008-05-14
Hi all,

I have what I think is a really really stupid question!!

Is there any Ubuntu documentation.

Now before someone points me to [https://help.ubuntu.com/](https://help.ubuntu.com/). this is not quite what I am asking for.
I am looking for Ubuntu specific not debian general.

I know I am just missing something, or being thick headed.

For instance where is the official Ubuntu specific bash commands documentation?

Where is the official Ubuntu specific documentation on xserver? 




Rusty

---

### Post by Cypher on 2008-05-14
There is no reason you can't look at the official Bash documentation to do what you want in Ubuntu, there is no specific Ubuntu version of Bash. The same goes for the rest of the applications..

---

### Post by tjwoosta on 2008-05-14
> 
For instance where is the official Ubuntu specific bash commands documentation?

Where is the official Ubuntu specific documentation on xserver? 


the reason you dont find much ubutnu specific documentaion on this stuff is because ,its not ubuntu specific

ubuntu specific bash? bash is going to be the same across most linux distros

as for xserver, ubuntu uses xorg and so do many other linux distros

so if you really want to learn this stuff then stop looking for ubuntu specifics because its simply not specific to ubuntu

---

### Post by t0p on 2008-05-14
Documentation for installed apps can generally be found under **/usr/share/doc**.  As for bash documentation: bash is bash, as far as I know, so googling for bash stuff will turn up relevant material.  At least, that approach has worked okay for me so far.

---

### Post by RWells on 2008-05-14
Weeell I am starting to feel like I am chasing my tail here.:lolflag:

I read the debian general info I can find on the web and it says it is critical to read the distro specific documentation because all distros  are different?

Why cant I edit my xorg.conf file in ubuntu 8.04 but I can in 7.10?

---

### Post by t0p on 2008-05-14
I'm not going to try and answer your xorg.conf question here - really you should start a new thread for that - but I will address the matter of ubuntu documentation.

You said you're not interested in [https://help.ubuntu.com](https://help.ubuntu.com), but I would have thought that's just the place to look for info on the xorg.conf issue.  Plus, of course, [https://help.ubuntu.com/community](https://help.ubuntu.com/community), [https://wiki.ubuntu.com](https://wiki.ubuntu.com), and [http://ubuntuguide.org/wiki/Hardy](http://ubuntuguide.org/wiki/Hardy) (when that last one eventually gets some content!).  The sites I've listed are where you'll find "official" and "community" documentation for ubuntu.  Maybe you can't find an answer to your xorg.conf question there... yet.  But Hardy *is* a new release, you know?

Anyway, I can't think of anywhere else to find the "ubuntu-specific" documentation you crave.

---

### Post by RWells on 2008-05-14
> **t0p said:**
> I'm not going to try and answer your xorg.conf question here - really you should start a new thread for that - but I will address the matter of ubuntu documentation.

You said you're not interested in [https://help.ubuntu.com](https://help.ubuntu.com), but I would have thought that's just the place to look for info on the xorg.conf issue.  Plus, of course, [https://help.ubuntu.com/community](https://help.ubuntu.com/community), [https://wiki.ubuntu.com](https://wiki.ubuntu.com), and [http://ubuntuguide.org/wiki/Hardy](http://ubuntuguide.org/wiki/Hardy) (when that last one eventually gets some content!).  The sites I've listed are where you'll find "official" and "community" documentation for ubuntu.  Maybe you can't find an answer to your xorg.conf question there... yet.  But Hardy *is* a new release, you know?

Anyway, I can't think of anywhere else to find the "ubuntu-specific" documentation you crave.

Yes I agree that it seems like those should be the places to look.

Like I said I think I am being thick headed about this or something.

I think this link is the answer to my question

ubuntuguide.org/wiki/Hardy

Its like a treasure hunt!! :lolflag:

Rusty

---

### Post by RWells on 2008-05-14
> **tjwoosta said:**
> the reason you dont find much ubutnu specific documentaion on this stuff is because ,its not ubuntu specific

ubuntu specific bash? bash is going to be the same across most linux distros

as for xserver, ubuntu uses xorg and so do many other linux distros

so if you really want to learn this stuff then stop looking for ubuntu specifics because its simply not specific to ubuntu

Ok Im going to ask for allittle specific help here then and see if I can learn what Im doing wrong

I copied this from [http://www.linuxcommand.org/wss0010.php#path](http://www.linuxcommand.org/wss0010.php#path)



"You can add directories to your path with the following command, where directory is the name of the directory you want to add:

[me@linuxbox me]$ export PATH=$PATH:directory

A better way would be to edit your .bash_profile file to include the above command. That way, it would be done automatically every time you log in."




Having dug around for the past hour now I cant for the life of me find .bash_profile .

I tried this acouple days ago and gave up and used the .bashrc file, but obviously thats not the right way of doing it.

Rusty

---

### Post by Monicker on 2008-05-14
Ubuntu does not give you a .bash_profile by default for some reason.  One of its differences from other distros.

---

### Post by Tatty on 2008-05-14
> **RWells said:**
> Why cant I edit my xorg.conf file in ubuntu 8.04 but I can in 7.10?

What do you mean by cant edit it?  It still exists in hardy in the same place as before "/etc/X11/xorg.conf"

If you mean why is it shorter than in gutsy, then help.ubuntu.com has your answer [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

---

### Post by RWells on 2008-05-14
> **Tatty said:**
> What do you mean by cant edit it?  It still exists in hardy in the same place as before "/etc/X11/xorg.conf"

If you mean why is it shorter than in gutsy, then help.ubuntu.com has your answer [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

When I eddit the xorg.conf file I get 

"This file was generated by failsafeDexcon....
Youshould use dexconf or another such too for creating a "real" xorg.conf
For example
"sudo dpkg-reconfigure -phigh xserver-xorg"

when I use "sudo dpkg-reconfigure -phigh xserver-xorg"
it changes the xorg.conf file back to what it thinks I need which leaves me with a black screen.

---

### Post by RWells on 2008-05-14
> **Monicker said:**
> Ubuntu does not give you a .bash_profile by default for some reason.  One of its differences from other distros.

Yeah thats kinda what Im getting at, there are a lott of diferences,
I can find tons of good info but it all seems to not be related to Ubuntu.
I have absoloutly no idea what Im doing here and I would like to not spend another week studying a site like linux.org if its not relivant to ubuntu, and I dont know how to tell beforehand.

---

