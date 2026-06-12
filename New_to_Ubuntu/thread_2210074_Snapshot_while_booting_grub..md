---
title: "Snapshot while booting grub."
date: 2014-03-08
forum: New to Ubuntu
---

### Post by panorain on 2014-03-08
I am wondering the best way to take a snapshot or pause my computer when booting before I get to the splash window or at least slow it way down so I can clearly read the output messages. or system boot check data. I do not know what to call that exactly please excuse my wording.

I currently am using Ubuntu 10.04.

Thank you,

---

### Post by Bashing-om on 2014-03-08
panorain; Hi !


On my box I can pause the boot process, and see the boot messages on screen with the key combo ctl+o;
and resume with key combo ctl+s. On some bioses the key "scroll lock" may also work.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by panorain on 2014-03-08
Thanks for your reply but none of the key combinations ctl+o , ctl+s , scroll lock or pause seem to pause anything during boot. I am looking into this because there is a message 'operation timed out' line that always shows up and it flashes by so fast I can't read it. Is there an easy way I could modify /etc/default/grub I have been reading on that a little bit. Perhaps give all the loadup screens like 5 seconds pause. 

Thank you,

---

### Post by Bashing-om on 2014-03-08
panorain; Sorry,

No other way That I am aware of, nor do  I know of any way from grub to affect the boot messages.

my regards, maybe some one else knows something else.

[INDENT]it is a ill wind
[/INDENT]

---

### Post by panorain on 2014-03-08
Thanks for your help though. Possibly I should be looking into pausing the plymouth daemon. 

Thank you,

---

### Post by Bashing-om on 2014-03-08
panorain; Hey !

As an after thought, you do have text enabled when booting (that can be a grub edit) to see the boot messages ?
Then maybe the ctl-o and clt-s will function ?

[INDENT][INDENT]maybe yes
[INDENT][INDENT]maybe not so yes 
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DogMatix on 2014-03-09
This may not be ideally what you want, but, I once solved a similar issue by recording the boot up screens on a digital camera as a movie then playing the movie back and pausing it at the point the message I wanted to read was showing.

A low tech approach - I know. However, it worked for me.

---

### Post by panorain on 2014-03-23
Do you know exactly the screen I am trying to pause is called? I know it's not the splash screen because that is basically the same as the login screen correct? So I was thinking to either look more into pausing 'plymouth' somehow or now pausing 'grub'. Which I did so it's getting a bit confusing for me at this point.

Thank you,

---

### Post by sandyd on 2014-03-23
Some, if not most of the boot process is logged in /var/log/kern.log (kernel)

---

### Post by oldfred on 2014-03-24
If still running 10.04, only the server version is still supported.

If you want to see messages before grub the camera solution is probably about it.
After grub all messages are in log files, I usually look at /var/log/dmesg. That is the same info as when you remove quiet splash from boot stanza in grub.

---

### Post by panorain on 2014-03-26
I think it's not an issue with 'Grub' then it must be an issue within 'plymouth'. Could you reference on 'plymouth' what is the part 'plymouth' plays during boot on Ubuntu <----thanks.

---

### Post by panorain on 2014-04-02
I figure to look deeper into the problem. At some point things will come together.

Thank you,

---

