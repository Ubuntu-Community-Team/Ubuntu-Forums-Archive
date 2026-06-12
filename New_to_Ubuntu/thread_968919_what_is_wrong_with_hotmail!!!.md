---
title: "what is wrong with hotmail!!!???"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by taekr on 2008-11-03
I'm getting a prompt that tells me to upgrade my browser. 

I have just installed ubuntu 8.10 and am using firefox 3.03. 

I googled it but can not find a solution.. 

What is happening here?

---

### Post by lisati on 2008-11-03
I haven't used Hotmail regularly for years, I dropped it when they started charging for access via OutlookExpress

---

### Post by peetbull on 2008-11-03
Managers in Microsoft don't like us to use a platform other than Windows and Internet Explorer, as it seems.

I keep a hotmail account working and faced the same problem;
Until I noticed a link under that warning that prompted me to go to my mail account.

So you can just read this whole warning and meet this link below the referred browsers.

Alternatively, when you login, you can just retype "hotmail.com" to visit your inbox.

Hope this one helps...

Be well!

---

### Post by kerry_s on 2008-11-03
> **taekr said:**
> I'm getting a prompt that tells me to upgrade my browser. 

I have just installed ubuntu 8.10 and am using firefox 3.03. 

I googled it but can not find a solution.. 

What is happening here?

it's the firefox user agent, ubuntu sets it to ubuntu.
the fix is to set it back to firefox.

---

### Post by Narshada on 2008-11-03
I'm not sure this is a Ubuntu problem, I got the same message when viewing Hotmail in Firefox 3 on Windows XP pro. I'm guessing it's M$ not recognising FF3 correctly.

---

### Post by skymera on 2008-11-03
It's Microshaft being themselves.

If you're not on Windows or IE it pops up.

My mum on Vista SP1 and Firefox, even the message pops up for her.

There is a "continue" button

---

### Post by justchange on 2008-11-03
I agree with you, *Skymera*.

I got the same message, today, and quickly figured out that it was just MS proselytizing for their products... especially after I noticed the "continue" button.

So, *taekr*, just continue peacefully on your way and ignore the **ranting man** on the street corner... there's nothing you can do for him.

:)

---

### Post by sanderella on 2008-11-03
I went through these hoops and hurdles, too. If you look for a tiny word at the top right of the screen that says M$N Hotmail you can click on that.

---

### Post by Paqman on 2008-11-03
Sounds like time to consider migrating to Gmail, folks.

---

### Post by roelpeeters on 2008-11-03
The solution to this problem lies in the useragent Firefox sends to the website when trying to login. You can (besides choosing another webmail provider like gmail or yahoo) change the useragent in Firefox as follows:

Type in the addressbar the following:
```
about:config
```

Confirm the warning, and in the filter bar, type **vendor**.

There you will see that the option *general.useragent.vendor* is set to Ubuntu. Change this value to **Firefox** and try again to access the website. In most cases it is not even necessary to reboot your browser. 

Warning: apparently this tag only exists for Firefox for Linux. On Windows you will not find this.

Roel.

---

### Post by kerry_s on 2008-11-03
i would like to add to this, i use debian and here it's "general.useragent.extra.firefox"

for mine i use the whole string:
```
Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.17) Gecko/20080827 Firefox/2.0.0.17

```
i changed the productsub to match and the firefox version.

you can check you user agent here:
[http://whatsmyuseragent.com/](http://whatsmyuseragent.com/)

mine has both a linux and windows agent string:
```
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.17) Gecko/20080827 Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.17) Gecko/20080827 Firefox/2.0.0.17 (Debian-2.0.0.17-0etch1)
```

---

### Post by vratnica on 2008-11-03
Thank ypu very much for the solution

I actually dont use the microsoft products, but my wife do, so this was very helpful =D>

---

### Post by Coreigh on 2008-11-03
I have changed my useragent setting back to Firefox and I still have problems with HoTMaiL.


EDIT:
I compared about:config FF 3.0.3 on Ubuntu 7.10 with FF 3.0.3 on Windows XP.

The XP machine has no problems or alerts with HoTMaiL however the Ubuntu machine gets the upgrade notice.

The two config files are nearly identical. On the XP setup the words Windows or Microsoft do NOT appear.

HoTMaiL has some other way of knowing it is not a M$ computer.

---

### Post by mingohills on 2008-11-03
> **roelpeeters said:**
> The solution to this problem lies in the useragent Firefox sends to the website when trying to login. You can (besides choosing another webmail provider like gmail or yahoo) change the useragent in Firefox as follows:

Type in the addressbar the following:
```
about:config
```

Confirm the warning, and in the filter bar, type **vendor**.

There you will see that the option *general.useragent.vendor* is set to Ubuntu. Change this value to **Firefox** and try again to access the website. In most cases it is not even necessary to reboot your browser. 

Warning: apparently this tag only exists for Firefox for Linux. On Windows you will not find this.

Roel.

This worked perfectly!!!!

---

### Post by mingohills on 2008-11-03
Ok. I guess perfectly was an overstatement.  It works perfectly with the session I was working in.  However, I rebooted earlier today and found that when I ran FF the config file had reverted to Ubuntu.  Is there any way to make this config change permanent?

---

### Post by rugbeeprop on 2008-11-03
I can access Hotmail, but not able to write or reply.

What a total coincident??? Ubuntu launched 8.10 on October 31...

I wonder...

Found a solution? [http://ubuntuforums.org/showthread.php?p=6101328#post6101328](http://ubuntuforums.org/showthread.php?p=6101328#post6101328)

It works right now for me, but we'll see tomorrow.

---

### Post by taekr on 2008-11-04
> **roelpeeters said:**
> The solution to this problem lies in the useragent Firefox sends to the website when trying to login. You can (besides choosing another webmail provider like gmail or yahoo) change the useragent in Firefox as follows:

Type in the addressbar the following:
```
about:config
```

Confirm the warning, and in the filter bar, type **vendor**.

There you will see that the option *general.useragent.vendor* is set to Ubuntu. Change this value to **Firefox** and try again to access the website. In most cases it is not even necessary to reboot your browser. 

Warning: apparently this tag only exists for Firefox for Linux. On Windows you will not find this.

Roel.

Thanks a lot. it works now!!!

---

### Post by ronnielsen1 on 2008-11-04
They changed their looks and I no longer get this error.

---

### Post by ronnielsen1 on 2008-11-06
It's back

---

