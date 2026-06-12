---
title: "Clock Issues"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by dolphin194 on 2011-11-04
I am having some issues with the clock in Ubuntu 11.10. When I set the time correctly in Windows, the time is way off in Ubuntu (By about 5 hours). Then, if I set it to the correct time in Ubuntu, the clock is 5 hours off in Windows! 

For example, if it's 10:30AM for reals and I set it in Ubuntu, Windows will tell me that it's 5:30AM.

I am in the USA and Canada Moutain timezone with Daylight Savings.

The clock worked fine in other Ubuntu versions.

By the way, This is not a double post. The other post i made was for a different clock problem.

---

### Post by Old_Grey_Wolf on 2011-11-04
Type these commands into the terminal
```
date
``` Will give you the date and time of your time zone

and ```
date -u
``` Will give you the Coordinated Universal Time.

There should be 6 hours difference where you live in Denver. If they are showing the same time or something other than 6 hours, you many need to use the command line to change them.

If you read this post on Sunday, there should be 7 hours difference.

---

### Post by dolphin194 on 2011-11-08
> **Old_Gray_Wolf said:**
> Type these commands into the terminal
```
date
``` Will give you the date and time of your time zone

and ```
date -u
``` Will give you the Coordinated Universal Time.

There should be 6 hours difference where you live in Denver. If they are showing the same time or something other than 6 hours, you many need to use the command line to change them.

If you read this post on Sunday, there should be 7 hours difference.

I'm sorry, but that didn't work. The time still is off in windows.

---

### Post by Redblade20XX on 2011-11-08
Take a look at this: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)
Specifically the section dealing with multiple boots!
:)

-Red

---

### Post by dolphin194 on 2011-11-10
> **Redblade20XX said:**
> Take a look at this: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)
Specifically the section dealing with multiple boots!
:)

-Red
This doen't help with my problem

---

### Post by Johnny3 on 2011-11-10
Is your clock right in your BIOS?

---

### Post by Ms. Daisy on 2011-11-10
> **dolphin194 said:**
> I am having some issues with the clock in Ubuntu 11.10. When I set the time correctly in Windows, the time is way off in Ubuntu (By about 5 hours). Then, if I set it to the correct time in Ubuntu, the clock is 5 hours off in Windows! 
 
For example, if it's 10:30AM for reals and I set it in Ubuntu, Windows will tell me that it's 5:30AM.
 
I am in the USA and Canada Moutain timezone with Daylight Savings.
 
The clock worked fine in other Ubuntu versions.
 
By the way, This is not a double post. The other post i made was for a different clock problem.
Computers lose time when the internal CMOS battery goes bad.  Have you tried replacing that?

---

### Post by dolphin194 on 2011-11-10
> **Johnny3 said:**
> Is your clock right in your BIOS?
Yes, the clock is correct in the BIOS.

> **Ms. Daisy said:**
> Computers lose time when the internal CMOS battery goes bad.  Have you tried replacing that?
I am using a laptop, and the computer keeps time.

In both Operating Systems, the Minutes and Seconds are *correct*, however the hours are *not correct*. Both Operating systems are using the same timezone.

---

### Post by Ms. Daisy on 2011-11-10
> **dolphin194 said:**
> I am using a laptop, and the computer keeps time.

In both Operating Systems, the Minutes and Seconds are *correct*, however the hours are *not correct*. Both Operating systems are using the same timezone.Laptops can have CMOS batteries, too.  It's a little watch-like battery that's in there somewhere. You didn't say what kind of laptop you've got, so I don't know exactly where it is.  When that little battery starts dying, your computer has a hard time keeping track of time after you power down.  You didn't say, but it sounds like you're dual booting windows & Ubuntu.  So if you set the clock in one system, restart and boot into the other OS, if your little CMOS battery is dying/dead, the machine can't remember what time it is.  It's a super simple fix to buy a $3 battery & change it out yourself.  Personally, based on what you've said in this post, the first thing I would do is change the battery & see if that takes care of it.

---

### Post by dolphin194 on 2011-11-10
> **Ms. Daisy said:**
> Laptops can have CMOS batteries, too.  It's a little watch-like battery that's in there somewhere. You didn't say what kind of laptop you've got, so I don't know exactly where it is.  When that little battery starts dying, your computer has a hard time keeping track of time after you power down.  You didn't say, but it sounds like you're dual booting windows & Ubuntu.  So if you set the clock in one system, restart and boot into the other OS, if your little CMOS battery is dying/dead, the machine can't remember what time it is.  It's a super simple fix to buy a $3 battery & change it out yourself.  Personally, based on what you've said in this post, the first thing I would do is change the battery & see if that takes care of it.

The system is keeping track of the time. I know this because the **minutes are correct** when i boot into the other system. The **hours are off** one operating system at all times.

My laptop is a Dell Latitude D620

---

### Post by llamabr on 2011-11-10
This is only kind of a work around, maybe, but you could try messing with the TZ command.  Put this in your ~/.profile or ~/.bashrc:

```
TZ='US/Mountain'
export TZ
```

And then, if that helps but doesn't get it right, you can adjust the timezone until it does.

It may be, actually, that you've got a TZ command working somewhere in there and that's messing it up.  Anyway, just a thought.  From here:

[http://www.tablespace.net/papers/unix_time.html](http://www.tablespace.net/papers/unix_time.html)

---

### Post by dolphin194 on 2011-11-10
Ok, I'll give that a shot later.

---

### Post by SeijiSensei on 2011-11-11
One or the other installation doesn't have the correct timezone data.  One option might be to set the CMOS clock to UTC rather than your local time zone, though I don't know how well that works with Windows.  It's also possible that Ubuntu thinks the CMOS clock is using UTC when it's really set to Mountain Time.  If so, llamabr's suggestion should work.

---

