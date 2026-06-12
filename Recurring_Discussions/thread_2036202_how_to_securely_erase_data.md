---
title: "how to securely erase data"
date: 2012-07-30
forum: Recurring Discussions
---

### Post by asmoore82 on 2012-07-30
> **Stonecold1995 said:**
> Peter Gutmann proved that simple deletion was NOT sufficient to remove data, and that actually overwriting it was necessary.

No, again, you are confusing "deletion" with "overwriting." Peter Gutmann's research had very little to do with "deletion" as everyone who's studied CSCI has known forever that "deletion" does almost nothing.

Peter Gutmann's position on this is always misrepresented and quotes from the man himself are in that bleachbit link I posted. Did I mention that that bleachbit link is really, really good stuff? Everyone should read it throughly or stop giving data "sanitation" advice altogether.

> **satimis said:**
> # dd if=/dev/urandom of=/dev/sdx bs=1M
even takes much longer time.

urandom is a complete waste of time. zero's are enough, sometimes I do 1's just for giggles. I recommend the `pv` (pipe viewer) command for a beautiful progress bar...
```
#1's instead of 0's :P
pv -s 40G </dev/zero | tr '\0' '\377' | sudo dd bs=$(( 16 * 1024 )) of=/dev/sdX
```

---

### Post by dcstar on 2012-07-30
> **asmoore82 said:**
> No, again, you are confusing "deletion" with "overwriting." Peter Gutmann's research had very little to do with "deletion" as everyone who's studied CSCI has known forever that "deletion" does almost nothing.

Peter Gutmann's position on this is always misrepresented and quotes from the man himself are in that bleachbit link I posted. Did I mention that that bleachbit link is really, really good stuff? Everyone should read it throughly or stop giving data "sanitation" advice altogether.
........

+1 The absolute rubbish **still** perpetuated on this issue is astounding.

Would some of you people please read the information offered to you rather than parroting the stuff that "you think" that has been proved to be next to useless over the last two decades?

---

### Post by dcstar on 2012-07-30
> **Stonecold1995 said:**
> With today's technology, but who's to say a method to recover data won't be discovered in the next 20 years?  Why take the chance?

Do you have any idea whatsoever on the characteristics of magnetic remenance and the chances of that sort of ancient technology being able to be accessed in 10 years time let alone 20?

---

### Post by kurt18947 on 2012-07-30
I don't know if this is of interest or not.

[http://tinyapps.org/docs/wipe_drives_hdparm.html](http://tinyapps.org/docs/wipe_drives_hdparm.html)

---

### Post by asmoore82 on 2012-07-30
> **Stonecold1995 said:**
> With today's technology, but who's to say a method to recover data won't be discovered in the next 20 years?  Why take the chance?

With today's technology, you can only write 1's and 0's to the disk. Who's to say that a million passes of your primitive 1's and 0's will ever successfully defeat yet-to-be-discovered recovery techniques of the future. Why take the chance? Better to go back to carbon paper and file cabinets instead.

:P

If you get the luxury of inventing a magical process in the future that can recover the data; then I get the joy of telling there is absolutely nothing you can do to stop it in the past or present. That's how magic works.

---

### Post by Stonecold1995 on 2012-07-30
I still say it's better to be safe than sorry, even if the chances that the data will be recovered in the near future are slim.

I'm not trying to spread this "myth", I just seriously worry how long we'll be safe with current security methods.  Scientists already have primitive mind-reading devices and god knows what the NSA has that they won't tell us. :shock:

---

### Post by Grenage on 2012-08-01
> **Stonecold1995 said:**
> I still say it's better to be safe than sorry, even if the chances that the data will be recovered in the near future are slim.

While I applaud 'better safe than sorry', in this case it unfortunately results in many, may people wasting many, many hours; there's no need for computers to sit there for days, thrashing random data pass after random data pass.

You could divide a drive and sending the pieces to the four corners for smelting, but there has to be a sane cut-off.

---

### Post by Stonecold1995 on 2012-08-01
> **Grenage said:**
> While I applaud 'better safe than sorry', in this case it unfortunately results in many, may people wasting many, many hours; there's no need for computers to sit there for days, thrashing random data pass after random data pass.

You could divide a drive and sending the pieces to the four corners for smelting, but there has to be a sane cut-off.

For a 40 GB drive it would take a matter of hours, not days.  If there isn't much sensitive data then of course it's best just to go for speed, but if you have very incriminating data on it then a few hours extra is fine IMO.

Also, wouldn't destroying the drive defeat the purpose of giving them away as OP indented?

---

### Post by Grenage on 2012-08-01
> **Stonecold1995 said:**
> Also, wouldn't destroying the drive defeat the purpose of giving them away as OP indented?

It's the only way to be sure, who knows what technology will be available in 20 years. ;)

---

### Post by HermanAB on 2012-08-01
Howdy,

The problem is not with data on the tracks, but rather with data in between the tracks and in remapped 'failed' sectors.  This data cannot be erased completely using the disk drive controller in its normal operating mode.

To address these problems, all disk drive controllers contain a utility that can be invoked to overwrite everything, including failed sectors and between tracks.  You can invoke this utility using hdparm - read the man page carefully.

On Windows, you can use this utility:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

Never underestimate the ability of a government employed intern with an electron microscope and nano sized iron filings...

---

### Post by Zill on 2012-08-01
> **HermanAB said:**
> The problem is not with data on the tracks, but rather with data in between the tracks and in remapped 'failed' sectors.  This data cannot be erased completely using the disk drive controller in its normal operating mode...
I would have thought that this particular problem could be overcome by the application of a large, AC-powered electromagnet, totally reversing the polarity of the magnetic fields on the disk numerous times.

How about this?  [AC Power Degausser Coil Wand Home Degauss]("http://www.ebay.co.uk/itm/AC-Power-Degausser-Coil-Wand-Home-Degauss-TV-Television-CRT-Clear-Display-Repair-/320937265548")

---

### Post by Grenage on 2012-08-01
You've got to figure that any magnet powerful enough to screw with the platter would also trash/misalign things like the actuator/arm, no?

---

### Post by KiwiNZ on 2012-08-01
Of course the key here is, there is a large team of forensic data recovery specialists just waiting for Joe Bloggs anywhere to throw a HDD in the landfill. Using CCTV to detect they then swoop recover the Disc and set to work for as many hours as need to get those pics of Ganny that didn't quite over write or the email to Mary Jane regarding Christmas diner.

Joe Bloggs should have zero'd the drive with at least 2,761 passes, then applied an industrial electro magnet, put the platter through an industrial shredder and then put the remain through a furnace. Then gather what dust etc is left hired a plane and scattered the remains over 1,000 square kilometres of ocean.

---

### Post by thatguruguy on 2012-08-01
Nuke it from orbit. It's the only way to be sure!

---

### Post by CharlesA on 2012-08-01
> **thatguruguy said:**
> Nuke it from orbit. It's the only way to be sure!
Beat me to it!

---

### Post by Stonecold1995 on 2012-08-01
> **HermanAB said:**
> Never underestimate the ability of a government employed intern with an electron microscope and nano sized iron filings...

And that's what I worry about, the government.  I wouldn't be surprised if the NSA already had the technology to do this and is just not telling us, but in 20 years it seems like a certainty.


> **thatguruguy said:**
> Nuke it from orbit. It's the only way to be sure!

That would work, but wouldn't launching it into the sun be a little more fun? :wink:

---

### Post by Paqman on 2012-08-02
> **Stonecold1995 said:**
> I wouldn't be surprised if the NSA already had the technology to do this and is just not telling us, but in 20 years it seems like a certainty.


They have the technology to extract any information you possess already. It's called a sack of doorknobs, a car battery and a locked room.

Just overwrite your disk with a single pass and you're good. For the really paranoid, take it out the back and blast it at point blank with a shotgun.

Personally I burn a lot more worry cycles making sure my data *never* gets erased. Losing data beyond recovery is laughably easy, keeping it secure is hard.

---

### Post by Eiji Takanaka on 2012-08-07
Take the cases off your harddrives and keep an extremely powerful magnet handy? Hoho. ;)

---

### Post by Eiji Takanaka on 2012-08-07
+1 for the aliens quote thatguruguy ;)

---

