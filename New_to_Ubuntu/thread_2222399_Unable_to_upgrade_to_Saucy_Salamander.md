---
title: "Unable to upgrade to Saucy Salamander"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by jan_jan_64 on 2014-05-06
Its been a while since I used my notebook, and I need to upgrade to 13.10. Problem is, via the Software Updater, during the process I finally come to the part where it asks me to confirm the upgrade...and the box is too big for my little notebook screen and I actually cant get to and click the confirm button. I tried adjusting my monitor settings but its already on the finest resolution, the others  make it worse. Could someone please help walk me through the process via the terminal? Thanks in advance ^^  EDIT: Yes I have tried minimising the box :p

---

### Post by grahammechanical on 2014-05-06
Yes I think we can use the Software Centre but what is wrong with using Software Updater/Manager? It has a much smaller application window. And is it not possible to re-size the application window or to drag the window to a more useful location on the screen?

```
sudo apt-get update && sudo apt-get dist-upgrade
```

That will fully update the existing installation

```
sudo do-release-upgrade
```

That will perform the upgrade to the next version. You may need to run again apt-get update and apt-get dist-upgrade.

Regards.

---

### Post by Thomas_Robert on 2014-05-06
[SIZE=2]Have you tried graphical upgrade method? because Command line upgrade is a bit challenge for you, because upgrade from Lts to normal release. Anyway hope you can do it.

If you are on LTS version probably you can't upgrade to latest normal release, To do this you need to edit release text file. So lets start.

Enter following command in terminal to install Core Update-Manager:
```
sudo apt-get install update-manager-core

```
Now enter following to open release file in text editor:

```
sudo gedit /etc/update-manager/release-upgrades
```


Now change lts to normal in opened text file

Prompt=normal

Now enter following commands in terminal to upgrade:

```
sudo apt-get update

sudo do-release-upgrade -d
```

or use this command to upgrade

```
sudo apt-get dist-upgrade -d

```


**Upgrade to LTS Release from Normal:**

If you are on normal version of Ubuntu and you want to upgrade to LTS version simple follow the guide.

Enter following command in terminal to install Core Update-Manager:

```
sudo apt-get install update-manager-core
```

Now enter following to open release file in text editor:

```
sudo gedit /etc/update-manager/release-upgrades
```

Now change normal to lts in opened text file

Prompt=lts

Now enter following commands in terminal to upgrade:

```
sudo apt-get update

sudo do-release-upgrade -d
```
or use this command to upgrade

```
sudo apt-get dist-upgrade -d
```
[/SIZE]

---

### Post by jan_jan_64 on 2014-05-06
**|Yes I think we can use the Software Centre but what is wrong with using Software Updater/Manager? It has a much smaller application window. And is it not possible to re-size the application window or to drag the window to a more useful location on the screen?**

Ack, sorry, my bad - I meant the Software Updater, not Software Centre. I can resize the window length-wise but not height-wise, unfortunately (the windowm Im talking about is the one that details how many packages will be installed/removed/upgraded etc).

Thanks for the help, I will give it a go!

---

### Post by jan_jan_64 on 2014-05-06
I tried the command line **sudo apt-get update && sudo apt-get dist-upgrade **- it listed several files, but after some of them were not found, the process just stopped.

Here are the 'failed' messages:
[B]
W: Failed to fetch [http://extras.ubunt.com/ubuntu/dists/raring/main/source/cources](http://extras.ubunt.com/ubuntu/dists/raring/main/source/cources) 404 not found

W: Failed to fetch [http://extras.ubunt.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://extras.ubunt.com/ubuntu/dists/raring/main/binary-amd64/Packages) 404 not found

W: Failed to fetch [http://extras.ubunt.com/ubuntu/dists/raring/main/binary-i386/Packages](http://extras.ubunt.com/ubuntu/dists/raring/main/binary-i386/Packages) 404 not found

E: some index files failed to download. They have been ignored, or old ones used instead[/B]

---

### Post by jan_jan_64 on 2014-05-06
@Thomas_Robert - Im sorry your explaination was a little confusing for me (I am 100% newb here). Im not even sure what LTS is??

---

### Post by Vladlenin5000 on 2014-05-06
Ubuntu 13.04 - raring ringtail" is EoL therefore its repositories might not work. Anyway, it should be safe to proceed with the other commands. However, a clean install of the the current LTS - Ubuntu 14.04 - is highly recommend but if you want to go the upgrade route anyway it's better to boot from a current version's installation media and select the upgrade option during the installation process. Online you'll need to upgrade to 13.10 and repeat the process for 14.04. Messy, to say the least, but usually works fine provided you have a pristine system, no PPAs, etc.

---

### Post by jan_jan_64 on 2014-05-06
Im not confident in my ability to do a clean installation, to be honest. Even if it may be a little more roundabout, upgrading from my current version is probably the easiest solution for me. But the previous solution given to me did not work?

---

### Post by Thomas_Robert on 2014-05-06
Too many problems, Why do not you try to install new OS, instead of upgrading .

---

### Post by jan_jan_64 on 2014-05-06
Well, Im not sure how to do it... How difficult is it? I really know very little about Linux so...

---

