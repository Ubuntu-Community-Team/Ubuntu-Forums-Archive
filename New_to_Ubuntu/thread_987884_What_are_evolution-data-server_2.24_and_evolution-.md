---
title: "What are evolution-data-server 2.24 and evolution-exchange-storage used for?"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by VitaminBB on 2008-11-20
What are **evolution-data-server 2.24** and **evolution-exchange-storage** used for?

I assumed they are used in conjunction with Evolution email client but I uninstalled Evolution and am wondering why these other files are still here?

I also cant delete these files from synaptic without synaptic wanting to remove a ton of files, including **ubuntu-desktop**.

Can someone just tell me what their purpose is and why I cant cleanly get rid of them?

Thanks ...

---

### Post by bscbrit on 2008-11-20
I think that these are both associated with Microsoft's Exchange Server and are necessary to interface with ES.  They do not take up any significant disk space on a modern computer so is there a particular reason why they must be removed?  I can understand a desire for neatness (I have exactly the same wish for my own computer) but are these packages causing any other problems that makes their removal a necessity?  Why they are so closely integrated with everything else is still a mystery - but I'm looking into it!

---

### Post by VitaminBB on 2008-11-20
They run constantly in memory, your right they arent taking up much memory or space but id like to remove them if possible.

I suppose my curiousity got the best of me too since the way its integrated with ubuntu struck me as odd ...

---

### Post by bscbrit on 2008-11-20
My guess is that you installed Evolution, upgraded your system, and subsequently removed Evolution.  The 2 ES packages depend upon several other packages which might have been kept after the upgrade simply to ensure that ES kept working.  Now that you want to remove ES the system knows that it can now remove the now unwanted versions of the other packages.  However, this is only a guess.  Without more information about your computer and the packages installed there would be a risk in simply trying to remove the packages.  It might break your system.  As the total size of the 2 packages is less than 5MB (and even with all the dependencies is unlikely to be a great deal bigger), I would suggest simply leaving them on your computer is the safest option.

I know that the package management in Ubuntu is not infallible, but it is still very good.  If it suggests that there is a dependency issue when you want to remove a package then I, personally, would let it have its own way.

It is still a little bit mysterious why it should be so deeply integrated if my guess above is wrong.

---

### Post by bscbrit on 2008-11-20
> **VitaminBB said:**
> They run constantly in memory, your right they arent taking up much memory or space but id like to remove them if possible.

I suppose my curiousity got the best of me too since the way its integrated with ubuntu struck me as odd ...

If you have a sense of adventure, have you tried stopping them and seeing what breaks?  Assuming that you have rebooted since you removed the other packages (otherwise they might simply be running because they haven't been told to stop yet!) then I do not expect a major catastrophe to occur.  But this is only my opinion - if you are not happy with the idea then DO NOT DO IT!

---

### Post by VitaminBB on 2008-11-20
> **bscbrit said:**
> My guess is that you installed Evolution, upgraded your system, and subsequently removed Evolution.  The 2 ES packages depend upon several other packages which might have been kept after the upgrade simply to ensure that ES kept working.  Now that you want to remove ES the system knows that it can now remove the now unwanted versions of the other packages.  However, this is only a guess.  Without more information about your computer and the packages installed there would be a risk in simply trying to remove the packages.  It might break your system.  As the total size of the 2 packages is less than 5MB (and even with all the dependencies is unlikely to be a great deal bigger), I would suggest simply leaving them on your computer is the safest option.

I know that the package management in Ubuntu is not infallible, but it is still very good.  If it suggests that there is a dependency issue when you want to remove a package then I, personally, would let it have its own way.

It is still a little bit mysterious why it should be so deeply integrated if my guess above is wrong.

To make the whole thing more confusing I did try to remove the two files mentioned and it did remove my ubuntu-desktop, ekiga, and a few other programs. I figured the damage was done but like your saying I was hoping that then reinstalling the missing programs would mean id be set and without those two evolution files. it didnt work that way.

When I went to reinstall ubuntu-desktop it fprced me to reinstall those two evolution files again, so I grudgingly did ...

If theres any other information youd like let me know, im fairly computer literate but im a linux retard at this point ...

---

### Post by VitaminBB on 2008-11-20
> **bscbrit said:**
> If you have a sense of adventure, have you tried stopping them and seeing what breaks?  Assuming that you have rebooted since you removed the other packages (otherwise they might simply be running because they haven't been told to stop yet!) then I do not expect a major catastrophe to occur.  But this is only my opinion - if you are not happy with the idea then DO NOT DO IT!

Negative, I can kill the processes apparently with no problems but trying then to uninstall the files doesnt work, this is the list of things it wants to uninstall when i go to remove evolution-data-server ...

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/pic2.jpg[/IMG]

---

### Post by bscbrit on 2008-11-20
Well, if you can kill them, they are not using memory nor CPU cycles.  So the only drawback would be about 4.5MB of hard drive storage.  I'd be tempted to live with it but I agree that they should be easily removable without taking half the system with them!

---

### Post by redseventyseven on 2008-11-20
Interesting! I use Linux Mint 5.0, which is based on Ubuntu 8.04, but with some key differences. In particular, the default mail client is Mozilla Thunderbird rather than Evolution.

However, I just had a look at my Synaptic and the two packages you mentioned are installed. Looking at the information on the packages reveals the following:
> The data server, called "Evolution Data Server" is responsible for managing
mail, calendar, addressbook, tasks and memo information.
Since gnome-panel depends on that, I would guess that the panel uses some of the features of the calendar from that package. After all, why shouldn't it? This is open-source, after all; source code from one package can quite happily be shared and used by another.

Final note (something which I learned only today), ubuntu-desktop is what's called a meta-package. This means it isn't a program in its own right, but is a collection of other packages. This makes it more convenient to install the large number of packages, but getting rid of just the meta-package won't do you any harm. Think of it like a sheet of wrapping paper: it contains lots and lots of items, but once you've opened the parcel and put all those items where you want them, you can quite happily throw away the wrapping paper and it won't affect your usage of the things that were once inside it.

---

