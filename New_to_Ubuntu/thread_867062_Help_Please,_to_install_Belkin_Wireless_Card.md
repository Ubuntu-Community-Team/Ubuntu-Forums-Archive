---
title: "Help Please, to install Belkin Wireless Card"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by warren100uk on 2008-07-22
Hi All,

First Ubuntu, is great, saved me from having to pay for XP to be re-installed on my PC.

Am having some trouble getting it on the internet, i have a Belkin Wireless g card and cant get it working.

I have looked in the Ubuntu help docs, and it makes it sound really easy, it says to download ndisgtk, which i have, from my laptop, this is where iam having the most trouble,it then says to install it,how do i do that????

I have looked at loads of sites and they are very hard to understand, am a novice when it comes to software. 

Any help would be great and make my kids day.

Thanks

Warren

---

### Post by northern lights on 2008-07-22
Apart from the fact, that there's a better way to install "ndisgtk", it'd be good to know, what kind of file the downloaded one is. I am assuming it's a .deb?!

If so, it can be installed via the "GDebi Package Installer". If that itsself is installed, a simple double-click on the .deb will do. I'd assume it isn't, since I'm certain you tried double-clicking it. In that case run ```
sudo apt-get install gdebi
``` from a terminal window first.


However, as for "ndisgtk", you can also, as done above for the package installer, run ```
sudo apt-get install ndisgtk
``` since it is in the Hardy repositories.

[EDIT]
This obviously has to be done while on a wired connection.
[/EDIT]

---

### Post by warren100uk on 2008-07-22
Hi,

Must i have the PC connected to the internet to sort this?, i have no ethernet card only the wireless card.

I do have a laptop so thats where i got the drive for the wireless card.

To be honest, all this is confusing me. Is there no way i can get what i need from my laptop and put them onto the pc?

Thanks ( Sorry am very thick with all this.

---

### Post by northern lights on 2008-07-22
In order for my above post to work, you'd have to be connected to the net. Thought you might have an ethernet adapter.

Two questions, yet again:
GDebi is not installed?
And, what file extension does your downloaded "ndisgtk" have?

Theoretically, it's possible to download the source with your laptop and compile it on your desktop:

You'd have to extract the source and then run ```
./configure
make
make install
``` from the terminal in the source folder.

But, then it might turn out that that package has uninstalled dependencies - now you'd have to download those packages and compile. Maybe one or more of those again have uinstalled dependencies...

---

