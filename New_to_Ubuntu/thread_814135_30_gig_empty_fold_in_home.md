---
title: "30 gig empty fold in /home?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by TooDamFast on 2008-05-31
After a fresh install, I notice my home directory was about 30 gig smaller than it should have been.  When I check my file system is shows a mount point that I have no clue what it is   /home/andrew/.gvfs   and its 30 gig.

It appears empty.  I want to get rid of it and add the 30 gig back to my /home directory.  Does anyone know how to do this?

when I try to delete it, it says it is in use.

---

### Post by Maestro23 on 2008-05-31
[http://ubuntuforums.org/showthread.php?t=809306&highlight=%2F.gvfs](http://ubuntuforums.org/showthread.php?t=809306&highlight=%2F.gvfs)

---

### Post by TooDamFast on 2008-05-31
ok...   Now I kind of understand what it may be used for but how do I remove it or make it smaller...  I don't use network shares from other systems.  It must have shown up when I was attempting to connect to a server at work.

It is a 37 gig file with 33 gig free...

---

### Post by chrisccoulson on 2008-05-31
~/.gvfs doesn't actually take up any real space, so just ignore what it is telling you. If you have a look at the output of 'df -h', you will notice that ~/.gvfs is the same size as your root partition

---

### Post by mdpalow on 2008-06-03
> **chrisccoulson said:**
> ~/.gvfs doesn't actually take up any real space, so just ignore what it is telling you. If you have a look at the output of 'df -h', you will notice that ~/.gvfs is the same size as your root partition

I've seen a few posts where you casually dismiss this questioning on our part, but I have to tell you... when I install 8.04 and then start having this problem, my / partition does fill up and I can no longer run the computer because there is no space left on the / partition to do anything. 

And, I have two partitions (/ and /home) where all my files are loaded to /home. There is some connection there and it's more than just something displayed wrong.

---

### Post by brunolaborde on 2008-06-03
The launch of BelleEscape.com means it just got easier for homeowners and decorators to find cottage-style accent pieces, décor and furniture ideal for creating a coastal escape, country cottage or shabby chic room in any home that will stand out from the rest.

(PRWeb) June 2, 2008, Shabby chic décor, hand-painted and distressed furniture and cottage style home accents are among the most sought after by homeowners decorating an escape home.  But finding accent pieces that add the perfect splash of color and charm to differentiate a home can be somewhat difficult even in vacation home bastions such as Southern California, Florida, the Carolinas and The Hamptons.

“After spending an enormous amount of time looking for just the right accent pieces for our vacation properties over the years, I knew that an online boutique featuring hard-to-find cottage-style décor in one convenient place would really fill a need,” said Belle Escape founder and president, Donna Jensen-Madier, a serial entrepreneur and licensed real estate broker. “The process of finding decorative pieces that can transform a home into an escape is challenging because you want décor that is not only unique, but also durable, comfortable and relatively affordable. And that’s what BelleEscape.com offers,” Jensen-Madier states.

With vacation home rental listings increasing in light of the depressed home sales market, many homeowners are seeking to set their home apart from the competition.  "Savvy homeowners have come to realize that they need their listing to stand out online or in publications and the most effective listings include colorful, stylish decor," advises Christine Van Buskirk, founder and co-owner of SeeVacationRentals.com.  "The right pictures that show style and warmth can make a home rent far more frequently than other homes in the same area and ultimately increase a home’s sales valuation." Van Buskirk concludes.

BelleEscape.com has just launched to fill a need in the market for an efficient way to access hard-to-find cottage-style décor, furniture and gifts. One or two pieces can completely transform a room making it a more desirable escape for homeowners and renters alike.  

"Distressed painted furniture, French country décor, beach cottage décor and shabby chic furniture and décor are perfect for a vacation home, cottage or even a retreat room in urban homes," says interior designer Dana McMahan. “BelleEscape.com features gorgeous designer pieces and makes it easy for the more discriminating buyer to differentiate their escape home," states McMahan.

With a wide variety of products from painted furniture to designer throw pillows and décor to fun guest room accessories, BelleEscape.com can provide all the décor needed to transform any home into a sanctuary.

ABOUT BELLEESCAPE.COM
Belle Escape is a new online boutique that brings together a unique collection of colorful and artistic cottage-style home décor and furniture for vacation homes and cottage-style rooms. The Belle Escape team visited designers and manufacturers from around the world to bring together a unique collection of beautiful furniture and décor. Featured items are segmented by style, including Coastal Escape, Cottage Couture, French Country and European Manor. Belle Escape also offers housewarming gifts and gift cards, making it easy to give the gift of an escape anytime.

---

### Post by ByteJuggler on 2008-06-03
> **mdpalow said:**
> I've seen a few posts where you casually dismiss this questioning on our part, but I have to tell you... when I install 8.04 and then start having this problem, my / partition does fill up and I can no longer run the computer because there is no space left on the / partition to do anything. 

And, I have two partitions (/ and /home) where all my files are loaded to /home. There is some connection there and it's more than just something displayed wrong.

How big is your / partition?  This all by itself can fill up for a variety of reasons and cause your problems, quite without involving .gvfs

---

### Post by mdpalow on 2008-06-06
> **ByteJuggler said:**
> How big is your / partition?  This all by itself can fill up for a variety of reasons and cause your problems, quite without involving .gvfs

My / partition was 10 gigs to start. When done installing EVERYTHING I wanted it was like 2-3 gigs full. Then I went to copy my back-up folders from another drive to /home; not /. When finished, my / partition was at about 95% full. Then on the first scheduled sync, my / went 100% full.

That shouldn't happen.

---

