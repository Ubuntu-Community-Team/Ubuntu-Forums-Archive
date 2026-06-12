---
title: "which debian?"
date: 2009-05-20
forum: Recurring Discussions
---

### Post by mamamia88 on 2009-05-20
i was just wondering which is better to install debian stable or debian testing?  i loved intrepid but had nothing but problems with jaunty.  i may end of reinstalling intrepid or even mint but i want to try the father of ubuntu first.

---

### Post by DLG102282 on 2009-05-20
If you are looking for stability Stable is the way to go.

---

### Post by mamamia88 on 2009-05-20
> **DLG102282 said:**
> If you are looking for stability Stable is the way to go.

lol nice but i'm looking to run newer packages.  would it be a good idea to install stable and if i want the newer version of a application install manually?

---

### Post by snowpine on 2009-05-20
If one was better, they would not both exist. :)

Do you want a rock-solid system whose packages will gradually become outdated over time (until the next stable is released in a couple of years), or do you want a fairly reliable system whose packages are constantly being upgraded (this is called "rolling release").

I personally recommend Debian stable for a corporate situation or important server, and Debian testing for the average desktop user. In Ubuntu terms, Debian stable is comparable 8.04 Hardy Heron LTS, while Testing is closer to Intrepid or Jaunty (but rolling release, as I mentioned).

Good luck, post back if you have any questions.

---

### Post by snowpine on 2009-05-20
> **mamamia88 said:**
> lol nice but i'm looking to run newer packages.  would it be a good idea to install stable and if i want the newer version of a application install manually?

It all depends on your definition of "new packages" but if you still want to be running Openoffice 2.4 in two years, Debian stable is the OS for you. :) (It does have a backports repository though.)

Debian testing is "unstable" in the sense that it is a rolling release, but it is not "unstable" in a buggy, likely to crash sense of the word. It is more stable in that sense than any Ubuntu release, for example. Before a package enters testing, it is thoroughly tested in unstable (Sid).

---

### Post by DLG102282 on 2009-05-20
> **mamamia88 said:**
> lol nice but i'm looking to run newer packages.  would it be a good idea to install stable and if i want the newer version of a application install manually?
Yes you could do that or you could use testing it is pretty stable and as long as you look what it wants to install and remove when upgrading you should have no problems.

---

### Post by mamamia88 on 2009-05-20
> **snowpine said:**
> It all depends on your definition of "new packages" but if you still want to be running Openoffice 2.4 in two years, Debian stable is the OS for you. :) (It does have a backports repository though.)

Debian testing is "unstable" in the sense that it is a rolling release, but it is not "unstable" in a buggy, likely to crash sense of the word. It is more stable in that sense than any Ubuntu release, for example.

so it will just keep updating testing until they finally release the next version and you'll have the final build?  then you can upgrade to testing of the next version once you feel it's stable enough?  well i've decided to give testing a go.  it's a 4gb file hopefully i only need the first dvd

---

### Post by snowpine on 2009-05-20
> **mamamia88 said:**
> so it will just keep updating testing until they finally release the next version and you'll have the final build?  then you can upgrade to testing of the next version once you feel it's stable enough?

It depends. If your software sources are set to "squeeze" then your system will transition from testing to stable in a couple of years, but if your software sources are set to "testing" then your system will always be testing forever.

---

### Post by albinootje on 2009-05-20
> **mamamia88 said:**
> would it be a good idea to install stable and if i want the newer version of a application install manually?

Look into apt-pinning.
[http://www.besy.co.uk/debian/howto_setup_apt-pinning_so_you_can_install_specific_packages_from_unstable](http://www.besy.co.uk/debian/howto_setup_apt-pinning_so_you_can_install_specific_packages_from_unstable)
[http://www.howtoforge.com/a-short-introduction-to-apt-pinning](http://www.howtoforge.com/a-short-introduction-to-apt-pinning)

---

### Post by mamamia88 on 2009-05-20
> **snowpine said:**
> It depends. If your software sources are set to "squeeze" then your system will transition from testing to stable in a couple of years, but if your software sources are set to "testing" then your system will always be testing forever.

that sounds great.  single install and then just update forever no reinstalling os every 6 months.

---

### Post by mamamia88 on 2009-05-20
last thing.  will the first cd just give me a straight gnome-desktop that i'm free to modify anyway i want?  or do i need more than 1 cd?

---

### Post by DLG102282 on 2009-05-20
The first CD has eferything you need to get a gnome desktop.

---

### Post by albinootje on 2009-05-20
> **mamamia88 said:**
> that sounds great.  single install and then just update forever no reinstalling os every 6 months.

Try it first before drawing such a conclusion :)

---

### Post by mamamia88 on 2009-05-20
> **DLG102282 said:**
> The first CD has eferything you need to get a gnome desktop.

thanks so much downloading now

---

### Post by forrestcupp on 2009-05-20
If you want bleeding edge, definitely do not install stable.  It will feel ancient.  You'll do all the manual work to update everything just to end up having the same thing as testing.

---

### Post by Wiebelhaus on 2009-05-20
Get the stable net install. Small quick installation with downloading the packages rather then burning an entire DVD or many CD's , this is of course if you have high speed internet.

Here:

[32bit]("http://cdimage.debian.org/debian-cd/5.0.1/i386/iso-cd/debian-501-i386-netinst.iso")

[64bit]("http://cdimage.debian.org/debian-cd/5.0.1/ia64/iso-cd/debian-501-ia64-netinst.iso")

---

### Post by mamamia88 on 2009-05-20
yeah but my internet is only about 1.5mbps dsl and if it doesn't detect my broadcom card i'm sol i don't want to connect my laptop to modem

---

### Post by snowpine on 2009-05-20
> **mamamia88 said:**
> yeah but my internet is only about 1.5mbps dsl and if it doesn't detect my broadcom card i'm sol i don't want to connect my laptop to modem

Debian probably will not detect your broadcom card, as broadcom uses proprietary (i.e. "non-free") drivers. Don't expect Debian to be "plug and play" with your hardware like Ubuntu is.

I have a BCM4312 chipset and used this guide to get wireless working (your mileage may vary depending on your specific chipset): [http://forums.debian.net/viewtopic.php?f=16&t=30648](http://forums.debian.net/viewtopic.php?f=16&t=30648)

---

### Post by mamamia88 on 2009-05-20
i am pretty sure i will find a way to install it via google. i know they have a broadcom linux and nvidia driver which is all i really need

---

### Post by init1 on 2009-05-20
> **mamamia88 said:**
> lol nice but i'm looking to run newer packages.  would it be a good idea to install stable and if i want the newer version of a application install manually?
If your main focus is newer packages, I'd just do testing. Stable is more for those who want an extremely reliable system.

---

### Post by mamamia88 on 2009-05-20
cool i installed it but removed it right away when i found out synaptic was missing from single cd and didn't want to be downloading all day for dvd with everything included and immediately installed mint 6 which i must say i'm enjoying

---

