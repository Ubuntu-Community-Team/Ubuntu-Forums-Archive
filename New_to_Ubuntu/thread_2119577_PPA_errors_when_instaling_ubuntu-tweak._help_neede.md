---
title: "PPA errors when instaling ubuntu-tweak. help needed please!"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by brokeit on 2013-02-24
i unable to install ubuntu-tweak
 using the terminal. 

when i copy and paste these below commands into gnome-terminal.

 sudo add-apt-repository ppa:tualatrix/ppa
 sudo apt-get update 
sudo apt-get install ubuntu-tweak

i get this error message:

mark@mark-desktop:~$ sudo add-apt-repository ppa:tualatrix/ppa
You are about to add the following PPA to your system:
 The official Ubuntu Tweak stable repository
 More info: [https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)
Press [ENTER] to continue or ctrl-c to cancel adding it

Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 99, in run
    self.add_ppa_signing_key(self.ppa_path)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 132, in add_ppa_signing_key
    tmp_keyring_dir = tempfile.mkdtemp()
  File "/usr/lib/python2.7/tempfile.py", line 322, in mkdtemp
    name = names.next()
  File "/usr/lib/python2.7/tempfile.py", line 141, in next
    letters = [choose(c) for dummy in "123456"]
  File "/usr/lib/python2.7/random.py", line 274, in choice
    return seq[int(self.random() * len(seq))]  # raises IndexError if seq is empty
ValueError: cannot convert float NaN to integer

I can no longer update ubuntu using update-manager after trying to add the PPA for new updated ffmpeg you suggested.

i get this error message when i try to install the updates that appear in update-manager

Requires installation of untrusted packages

The action would require the installation of packages from unauthenticated sources.

ffmpeg libav-tools libavcodec-extra-53 libavdevice53 libavfilter2 libavformat-extra-53 libavformat53 libavutil-extra-51 libavutil51 libpostproc-extra-52 libpostproc52 libswresample0 libswscale-extra-2 libswscale2

im still learning about certain aspects of ubuntu. and i would really like to know what 
i can do to fix this problem i am having.

what do i need to do to fix this issue.
any help appreciated.

---

### Post by grahammechanical on 2013-02-24
> Requires installation of untrusted packages
The action would require the installation of packages from unauthenticated sources.

This is not an error message. It a verification message regarding something we have commanded Linux to do. Did you authentic the action by pressing Y?

This will help you understand what a PPA is

[https://help.launchpad.net/Packaging/PPA]("https://help.launchpad.net/Packaging/PPA")

This will explain why they are called "untrusted."

[https://help.ubuntu.com/10.04/add-applications/C/adding-repos.html]("https://help.ubuntu.com/10.04/add-applications/C/adding-repos.html")

> You download and install PPA packages at your own risk. Ubuntu, Launchpad and Canonical do not endorse these packages. You must be certain that you trust the PPA owner before you install their software.

You now have a choice. Remove the PPA or accept the download. Do one or the other and it may solve the issue of not being able to update Ubuntu.

Just in case you do not know you can add and remove a PPA in Software Sources or in Ubuntu Software Centre>Settings.

Regards.

---

