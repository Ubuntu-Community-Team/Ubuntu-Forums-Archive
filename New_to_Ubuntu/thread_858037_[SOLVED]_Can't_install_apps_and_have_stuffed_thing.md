---
title: "[SOLVED] Can't install apps and have stuffed things up royally"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by jmacg on 2008-07-13
After finally getting Ubuntu 8.04 installed, I wanted to install two applications that weren’t mong the Ubuntu set: Skype and XMMS. I started with Synaptic. It found quite a few different files with XMMS in their name. Which to choose? I chose one that looked most like the main program, though it certainkly wasn't obvious. It then gave me names of other files to download and install with the first one I chose. A pretty stupid system, I thought at the time. Why not have a single obvious install file like Windows does?

Anyway, it roared off and installed XMMS - and said it had done so. Great! Trouble was, I couldn't see XMMS in any of the software categories, so I couldn't run it. I still haven't found it.

In order to install Skype, I read that a special repository had to be added to Synaptic’s list of repositories. I thought I’d correctly followed the instructions I read, but unfortunately I really upset Synaptic and get this message whenever I try to do anything with it: "This is a major failure of your software management system. Please check for broken packages with Synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

What is a simple Windows soul supposed to make of that gibberish? This issue remains unresolved, at least until next weekend, when I can get at the offending computer again.

I thought I'd try some daring command line stuff, with this result: 
jmacg@ubuntu:~$ sudo apt-get install skype
[sudo] password for jmacg: [I entered it]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[I couldn’t see any other process that could be using the admin direcory.
Gibberish again.

Any help gratefully received: 

(a) To fix the Synaptic situation (like how can I do any checking with Synaptic when Synaptic won’t even run), and what does all the other stuff mean?
(b) Why is the command-line installation not working?

---

### Post by powerpleb on 2008-07-13
You need to close Synaptic before you can run apt-get on the command line. You cannot run two package managers at once.

---

### Post by ChameleonDave on 2008-07-13
> **jmacg said:**
> 

(a) To fix the Synaptic situation (like how can I do any checking with Synaptic when Synaptic won’t even run), and what does all the other stuff mean?
(b) Why is the command-line installation not working?
You normally get that message when you try to modify software with two programs at the same time (e.g. Synaptic and apt-get).

If you log out, then log back in again, then open a terminal and do "sudo -apt-get install -f", do you get an error?

---

### Post by ChameleonDave on 2008-07-13
We ought to make sure that you haven't inadvertently messed up your list of repositories.

Do the following command on to terminal and tell us the output:

```

cat /etc/apt/sources.list

```

---

### Post by jmacg on 2008-07-13
Thanks for yours and the other suggestions. Unfortunately I can't check this until next weekend - the Ubuntu computer is in another town.

---

### Post by zipperback on 2008-07-13
It appears your installation has somehow broken something.

Open a terminal window and issue the following commands:

**sudo apt-get update**
**sudo apt-get install -f**

That should resolve the problem with apt-get not working.

If it does not work, please let me know.



To install Skype, just click this link.
[http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)

That will download the currently released version of Skype for Ubuntu.
The name of the file currently is: **skype-debian_2.0.0.72-1_i386.deb**

After it downloadeds you then just need to issue the following command in a terminal window.

**sudo dpkg -i skype-debian_2.0.0.72-1_i386.deb**


You should then see some output that looks similar to:

[B]Selecting previously deselected package skype.
(Reading database ... 171452 files and directories currently installed.)
Unpacking skype (from skype-debian_2.0.0.72-1_i386.deb) ...
Setting up skype (2.0.0.72-1) ...[/B]

Skype should now be installed.

Click Applications -> Internet -> Skype


Hope that helps you.
- zipperback
:popcorn:

---

### Post by jmacg on 2008-07-13
Thanks - that looks very helpful. Unfortunately I can't check it until next weekend.

Incidentally, the "This is a major failure of your software management system..." error message still came back when I closed down and restarted Ubuntu.

John

---

### Post by jmacg on 2008-07-17
Zipperback - unfortunately your suggestion won't work because the system seems to be looking for a password I don't know, Specifically it tells me:

jmacg@ubuntu:~$ sudo apt-get update
[sudo] password for jmacg: 
E: Type '--15:24:24--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list


I just used the password associate with jmacg that lets me start up Ubuntu on this machine - i.e. the password I ghave when I installed Ubuntu. I've never been asked for, or have given, any other password. Not that I can recall, anyway.

What should I do now?

Regards
John

---

### Post by plucky on 2008-07-17
> jmacg@ubuntu:~$ sudo apt-get update
[sudo] password for jmacg:
E: Type '--15:24:24--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

Your medibuntu.list file is corrupt.Open a terminal and ```
sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.old
```

It will ask for your password and you use the password you login with.It will not echo what you type.
All you are doing is giving the command super user privileges.

Then still in the terminal ```
sudo apt-get update
```

If that works and you get no errors,then you have to install the Medibuntu repositories again.Still in the terminal copy and paste this command ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

And then add the key ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

If that is ok the you can install **skype** which was the whole exercise.

Good Luck

---

### Post by jmacg on 2008-07-17
That was a quick amswer - greeat!

Unfortunately it's still not working. Here is the result:

jmacg@ubuntu:~$ sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.old
[sudo] password for jmacg: 
jmacg@ubuntu:~$ sudo apt-get update
E: Type '--15:24:24--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

---

### Post by plucky on 2008-07-17
Whoops just realized you copied the file but didn't delete it.
Try ```
sudo rm /etc/apt/sources.list.d/medibuntu.list
``` to delete the file and then ```
sudo apt-get update
```

---

### Post by jmacg on 2008-07-20
Thanks Plucky - your suggestion fixed my problem. I now have Skype running. Yay!

Sorry this is a few days after your post - I haven't been able to get the the computer for a couple of days - helping a friend build a greenhouse.

Rgds
John

---

