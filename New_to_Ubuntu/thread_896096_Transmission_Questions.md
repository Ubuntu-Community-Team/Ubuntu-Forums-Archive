---
title: "Transmission Questions"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-08-20
I am a Bit Torrent N00B, and I have some questions about transmission.

- The progress bar has two components, a fast moving yellow bar and a slower moving blue bar.  What is the difference?

- This should be obvious, but what *exactly* happens when I click on "Ask tracker for more peers"?

- Lets say that I have a complete file, and I want to reseed it without having to re-download it.  How would I go about doing this?

- This should also be obvious, but what are the "private to this tracker" and "announce URL" fields for in the create new torrent dialog.

Thanks, I am a total N00b. . .

EDIT: One more

- In the details dialog, in the peers tab, what does the little lock icon next to some peers mean?

---

### Post by sam_delta on 2008-08-20
well, about the yellow bar and the blue bar
the yellow bar represents the downloaded percent and the blue bar represents how much of the downloaded content has been verified/checked. thats why the blue bar will never pass the yellow one, because you cannot verify the content you havnt download. once the yellow line is aproaching the end, transmission will start verifying faster, so you do not loose any time verifying when the download has  ended.

sam

---

### Post by pi.boy.travis on 2008-08-20
Anyone else BUMP?

---

### Post by Rolcol on 2008-08-20
The lock icon means the connection is encrypted.  "Ask tracker for more peers" updates the tracker (announce and scrape?) and asks for more peers to download from.  The version of Transmission I use is the nightly build from svn which is 1.32 as compared to the one in the Ubuntu repositories which is 1.06

---

### Post by pi.boy.travis on 2008-08-20
Excellent!  Thanks!  

Two left. . .

---

### Post by tuxxy on 2008-08-20
Also Deluge is an excellent client, more advanced than transmission :)

---

### Post by pi.boy.travis on 2008-08-21
Anyone else?

---

### Post by pi.boy.travis on 2008-08-21
OK, to reseed I opened a torrent with the complete file in my download directory.  Transmission checked the integrity and began seeding.  

If I can get the create new torrent thing figured out, I'll be all set!

---

### Post by alanwalterthomas on 2009-01-20
I've another noob question about transmission:
When I'm in the middle of a download & restart transmission it first verifies the files. Fine, but it goes so slowly for a big file! I have a 2.5 GHz dual core athlon system but not making use of it! The verification process only takes a few percent of my processor's resources & for a ~3 GB file verifies at about 0.5% per second. So I'm curious, why isn't transmission working through that faster so that it can start downloading again right away?
Thanks,

---

### Post by pi.boy.travis on 2009-01-21
> **alanwalterthomas said:**
> I've another noob question about transmission:
When I'm in the middle of a download & restart transmission it first verifies the files. Fine, but it goes so slowly for a big file! I have a 2.5 GHz dual core athlon system but not making use of it! The verification process only takes a few percent of my processor's resources & for a ~3 GB file verifies at about 0.5% per second. So I'm curious, why isn't transmission working through that faster so that it can start downloading again right away?
Thanks,

Ubuntu tries to keep processes that aren't critical from eating up too many resources.  The priority is measured by the "nice" value.  If you open System Monitor, you can decrease Transmission's nice value to allow it to use up more resources.

Also, not all programs are designed to take advantage of multi-core/multi-threaded computing.

Hope this helps!!

---

### Post by alanwalterthomas on 2009-02-25
Ok, about renicing transmission.

I open up system monitor, find transmission's process, & set it's nice value to -10, but when I click change priority, system monitor closes, & a little bar with the administration gear image that says starting administrative application appears that disappears if I click on it. Transmission keeps working slowly & is back to nice 0 if I reopen system monitor.

Is that a bug?

---

### Post by NearlyALaugh on 2009-07-16
> **pi.boy.travis said:**
> - Lets say that I have a complete file, and I want to reseed it without having to re-download it.  How would I go about doing this?From the Transmission forums:

[http://forum.transmissionbt.com/viewtopic.php?f=2&t=6869](http://forum.transmissionbt.com/viewtopic.php?f=2&t=6869)

---

### Post by servicetech on 2009-07-16
> **tuxxy said:**
> Also Deluge is an excellent client, more advanced than transmission :)

+1 for Deluge, it's more advanced while remaining easy to use. Once you use it you will abandon Transmission.

---

