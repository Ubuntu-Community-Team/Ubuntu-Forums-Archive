---
title: "Fresh install.....no wireless"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by jakewc2 on 2012-06-10
I have an Acer Aspire that works ok but is a bit slow, and I just installed lubuntu with a cd, everything went ok, but hen I went to use the wireless connection, its not there, and I get a message saying when I click on the connections icon, that 'wireless is disabled by hardware switch'. What does that mean......can I get my wireless back. It worked perfectly on Ubuntu 12.04.....

thanks

---

### Post by jakewc2 on 2012-06-10
Hi, well I ran 'rfkill list all' and got this result

>  0 :phy0: Wireless LAN
Soft blocked: no
Hard blocked: Yes

ran sudo rfkill unblock all and nothing happened. still have Hard block: Yes.

How can I unblock it

Thanks

(sorry cant get rid of smillie face)

---

### Post by fslezak on 2012-06-10
> **jakewc2 said:**
> Hi, well I ran 'rfkill list all' and got this result



ran sudo rfkill unblock all and nothing happened. still have Hard block: Yes.

How can I unblock it

Thanks

(sorry cant get rid of smillie face)

You have a hardware wifi switch (I think it is a switch on the side). Press that.

Also, you can disable smilies by checking Disable Smilies in Text in the Additional Options of Ubuntu Forums

---

### Post by jakewc2 on 2012-06-10
Well, got it fixed...I found out that somebody else got theirs fixed by taking the battery out, then rebooting, and it worked......yippee

---

### Post by westie457 on 2012-06-10
> **jakewc2 said:**
> Well, got it fixed...I found out that somebody else got theirs fixed by taking the battery out, then rebooting, and it worked......yippee

That is a novel way of fixing something. Not the usual way though.

---

### Post by jakewc2 on 2012-06-11
> **fslezak said:**
> You have a hardware wifi switch (I think it is a switch on the side). Press that.

Also, you can disable smilies by checking Disable Smilies in Text in the Additional Options of Ubuntu Forums

I tried that, it did nothing.....v

very frustrating :(

---

### Post by jakewc2 on 2012-06-11
> **westie457 said:**
> That is a novel way of fixing something. Not the usual way though.

It is, but its worked for me on other things as well, when I have been in the same situation.....dont know what it is about removing the battery sometimes but it must set off a really hard reboot, like when you remove the battery from your mobile......and its now working perfectly......I do like lubuntu......nice and simple....:P

---

