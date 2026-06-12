---
title: "not enough space for small image on dvd"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by mrtalkingbadger on 2011-09-25
hi,
I'm trying to burn an image onto an DVD-RAM 2~3x speed using my plextor px-l611u with brasero.
no matter how small the image is brasero keeps telling me there is not enough space on the dvd.
i never used dvd-ram before so maybe that is causing this. 
still my dvd-drive is should be able to support this format as far as i know.
any ideas?
don't tell me to buy another dvd please, since i'm broke at the moment :cry: ;)

---

### Post by MG&amp;TL on 2011-09-25
You used DVD for anything else?

Buy a CD or USB ;)

---

### Post by alegomaster on 2011-09-25
What is the size of the image?

---

### Post by mrtalkingbadger on 2011-09-25
@alegomaster:
one image i tried is 97mb, the other 1.9gb

@MG&TL:
as i already said, i'm broke at the moment so buying a new cd or usb will have to wait for somer days. i spent my last $ on the dvd-ram and some beer...
my usb drive needs some attention as well...u already answered my post regarding that one :D
if i'm not stupid as hell, i can't boot an image from an ntfs drive so i'll have to repartition it with gparted...wich does not work at the moment due to sector damages

---

### Post by alegomaster on 2011-09-25
Try to format the dvd to fat32 and then try again to burn.

---

### Post by Captain Smiley Pants on 2011-09-25
There is always the [Install Ubuntu From USB](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) method if your computer supports it. I do realize that link is pretty specific for Windows (I'm just assuming you are on it), but I think there is some software on the repository that basically does the same thing as this. Just a warning, you may need to format your USB stick so maybe backup that information to another device (since you may end up formatting the entire HD on your computer, wouldn't be a good idea to store info there at that point :p). I'll take a look around for that method if you are on Ubuntu.

---

### Post by alegomaster on 2011-09-25
> **Captain Smiley Pants said:**
> There is always the [Install Ubuntu From USB](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) method if your computer supports it. I do realize that link is pretty specific for Windows (I'm just assuming you are on it), but I think there is some software on the repository that basically does the same thing as this. Just a warning, you may need to format your USB stick so maybe backup that information to another device (since you may end up formatting the entire HD on your computer, wouldn't be a good idea to store info there at that point :p). I'll take a look around for that method if you are on Ubuntu.

I don't think his distro image is 97mb or 1.9gb;)

It is probably some other image.

---

### Post by Captain Smiley Pants on 2011-09-25
I have terrible reading comprehension :(

Your best bet would be to check the md5sum against the actual file on your hard drive vs. the sum produced from the website, if there is one.

---

### Post by mrtalkingbadger on 2011-09-25
> **alegomaster said:**
> Try to format the dvd to fat32 and then try again to burn.
i formated the dvd using disk utility to fat (there was no option whether 16 or 32).
now beasero tells me to replace the disc with a supported cd/dvd.
according to google product search my drive supports dvd-ram 5x.
is it possible that dvd-ram 3x is not supported?
maybe ubuntu is not compatible with my drive.
i'll try it on windows tomorrow and let u know if it did work.
any advice which burning tool i should use on windows?

---

### Post by alegomaster on 2011-09-25
Brasero does not currently support dvd-ram fully, so that could be the issue you are having with the burning.
If you have windows 7, you could use the built-in iso burner, I always use that to burn iso's on a dvd-r.

---

### Post by mrtalkingbadger on 2011-09-25
> **Captain Smiley Pants said:**
> I have terrible reading comprehension :(

Your best bet would be to check the md5sum against the actual file on your hard drive vs. the sum produced from the website, if there is one.
i'm not trying to install an linux distro image.

(also this could help me as well since i'm trying to install an image
of gparted which is included in ubuntu live cds.)

the startup disk creator can be used to do so in ubuntu.
the file should be okay since the problem persists with several different images
which i downloaded twice to make sure there was no dataloss.

i checked the md5sums on my harddisk and they are ok. 
i didn't check those produced from the website, because i don't know how.

---

### Post by mrtalkingbadger on 2011-09-25
> **alegomaster said:**
> Brasero does not currently support dvd-ram fully, so that could be the issue you are having with the burning.
If you have windows 7, you could use the built-in iso burner, I always use that to burn iso's on a dvd-r.
that should fix it...i'll try it out after my midnight snack

edit: didn't fix it. i tried the built in iso burner which told me there was no writeable medium and ejected the dvd.
then i tried a crappy trial version of a crappy iso burner i found using google which did't even recognize my dvd drive.
i'll try the "burn" tool from synaptic now and if this doesn't work either postpone my search for a burning tool i can use on tomorrow

thanks for the help so far

edit: did burn something, though it appearantly thought it was burning on a cd instead of dvd-ram. got some pretty weird output trying to boot from it.
i think it just bricked the  dvd. no big loss though...i think i'll just get myself an usb-stick and use the strartup disk creator

---

### Post by alegomaster on 2011-09-26
> **mrtalkingbadger said:**
> that should fix it...i'll try it out after my midnight snack
 
edit: didn't fix it. i tried the built in iso burner which told me there was no writeable medium and ejected the dvd.
then i tried a crappy trial version of a crappy iso burner i found using google which did't even recognize my dvd drive.
i'll try the "burn" tool from synaptic now and if this doesn't work either postpone my search for a burning tool i can use on tomorrow
 
thanks for the help so far
 
edit: did burn something, though it appearantly thought it was burning on a cd instead of dvd-ram. got some pretty weird output trying to boot from it.
i think it just bricked the dvd. no big loss though...i think i'll just get myself an usb-stick and use the strartup disk creator
 
Dvd-ram has finicky support, so It would't be the best choice for this. Google tells me nothing, so your best bet is to format the drive again and use it for data storage(probably some high priority files).

---

### Post by mrtalkingbadger on 2011-11-09
just used a usb-flash drive instead. though i had to buy one and didn't actually get to burn an image to dvd-ram i'll mark the thread as solved

---

