---
title: "User account"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by APEKSWTX6R on 2012-05-11
Good morning...
                              I installed ubunto.precise pangolin.one minor problem.had to edit the"nomodeset" to get it to boot.great..then tried to add a user account.now the pinkish/orange background is up, without launcher,toolbar or any way to switch user
                                                thanks

---

### Post by APEKSWTX6R on 2012-05-11
Hello,again  as a windows bafoon, i tried ctr+alt+del...it showed my account name..the new one, and guest.when i entered my passwd. It said internal problem cannot be reported.some obsolete package versions installed gnome-settings-daemon, libtasn 1-3
                     for the record i have a seagate barracuda hard drive 120gb 7200rpm.that i wiped completely clean,ididn't want anything to interfere with my install..2.25 gb in dimm slots, amd sempron 34000+ ????????thanks

---

### Post by sadaruwan12 on 2012-05-11
If you don't mind friend I like to sujest to do a complete reinstall of your system and starrt fresh againe.

---

### Post by APEKSWTX6R on 2012-05-11
Hello.would you please send the steps to do just that??
                                        I'm an absolute rookie

---

### Post by sadaruwan12 on 2012-05-12
Ah, Found you ignore the PM.

OK so you're coming from a windows base I presume keeping that in mind lets get our hands dirty.

First you need to have a bootable media but you already have installed the system that means you have one we could use that or download a new and fresh image if you have a spare CD (Don't use rewritable CD / DVD tends to give trouble). Do you have 2 or 4 Gb thumb drive hand ? if you do that'll be a grate installation media with very less trouble. If you can make a bootable USB stick then here's the [guide to do it in Windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows").

Now we get to the more under the hood stuff.

Pop your CD or USB in hit the function key that you can the boot device selecting menu. From there select the boot device USB or CD.

After that just let it load and wait.

You'll get a purple background with a small dialog asking you want try it or install it just select install.

Now just press next until you get to the "Allocate drive space" the partitioning part. Here select "Something Else" else option and press continue.

You'll see your full hard disk select the /dev/<your HDD name> at the very top and press "New Partition Table" now you'll see an empty hard disk select that and create a new partition of the size of 600Mb and set the mount point as /boot. After that action you'll see a reduced free space select that and create another partition and give around 50Gb then set the mount point as /. Select rest of the free space and set the mount point as /home. Now press next.

Then press next until you get to the part where you have to set a user name and password create a good user name and a password and don't put it to auto log in or to encrypt the /home folder 'cos this some time screws things up.

Finish the installation and let us know is your issue solved or not.

P.S: Just in case if you get stuck refer [this]("http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/")

---

