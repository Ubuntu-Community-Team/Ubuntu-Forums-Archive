---
title: "JRE Security"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by mlnease on 2012-04-04
Hello,

There's been a lot of news today reporting that ["Mozilla has made a change in Firefox that will block all of the older  versions of Java that contain a critical vulnerability that's being  actively exploited."]("https://threatpost.com/en_us/blogs/mozilla-adds-older-java-versions-firefox-blocklist-040312")

This article states that ""Affected versions of the Java plugin will be disabled unless a user  makes an explicit choice to keep it enabled at the time they are  notified of the block being applied," Needham said."

It also states, "Mozilla strongly encourages anyone who requires the JDK and JRE to  update to the current version as soon as possible on all platforms...", but it *doesn't* advise what the 'current version' is.

I received such an error message yesterday when I found that Java wasn't working on a site I visit daily.  I scratched my head and chose to keep it enabled in order to keep that page functional.

I gather that my system's Java is based on openjdk-6-jre/jdk.  Is this the current version?  Is it secure?

Thanks in advance.

mike

---

### Post by Cheesemill on 2012-04-04
For more info:
[https://bugzilla.mozilla.org/show_bug.cgi?id=739955#c65](https://bugzilla.mozilla.org/show_bug.cgi?id=739955#c65)

---

### Post by QIII on 2012-04-04
Although I want OpenJDK to succeed (it is the reference implementation of Java 7, after all), I recommend updating the the latest Oracle/Sun Java 6, update 31 for now:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by mlnease on 2012-04-04
> **QIII said:**
> Although I want OpenJDK to succeed (it is the reference implementation of Java 7, after all), I recommend updating the the latest Oracle/Sun Java 6, update 31 for now:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Thanks for this!  I found the tutorial at your link really useful.  It was a bit challenging for a mainly GUI user but it was good exercise and worked.  Wish it was in the repositories so I could do this via Synaptic (and get automatic security updates) but I suppose one can't have everything.  Still, was all this really necessary?  Are the Open alternatives presently in the repositories really a security risk?

Thanks again and also for the speedy response.

mike

---

### Post by mlnease on 2012-04-04
> **Cheesemill said:**
> For more info:
[https://bugzilla.mozilla.org/show_bug.cgi?id=739955#c65](https://bugzilla.mozilla.org/show_bug.cgi?id=739955#c65)
Bit over my head, but thanks for the quick response just the same.

---

### Post by Cheesemill on 2012-04-04
> **mlnease said:**
> Still, was all this really necessary?  Are the Open alternatives presently in the repositories really a security risk?

No. If you read the thread that I posted the open alternatives aren't a risk at all, the blackllisting of OpenJRE was a mistake.

---

### Post by mlnease on 2012-04-04
> **Cheesemill said:**
> No. If you read the thread that I posted the open alternatives aren't a risk at all, the blackllisting of OpenJRE was a mistake.
Thanks again.  The thread you posted contained around 42,000 characters, mostly in the fairly technical jargon of developers.  I scanned it and concluded that it would be best for me to wait for a simpler response.  Had you posted along with the link the caveat, "...the open alternatives aren't a risk at all, the blackllisting of OpenJRE was a mistake..."it would have been *most* useful--at the time.

Just the same, thanks again for your time and trouble.

mike

---

### Post by Cheesemill on 2012-04-04
> **mlnease said:**
> Thanks again.  The thread you posted contained around 42,000 characters, mostly in the fairly technical jargon of developers.  I scanned it and concluded that it would be best for me to wait for a simpler response.  Had you posted along with the link the caveat, "...the open alternatives aren't a risk at all, the blackllisting of OpenJRE was a mistake..."it would have been *most* useful--at the time.

Just the same, thanks again for your time and trouble.

mike

Sorry :)

All of the relevent information is in the post I linked to and the 2 comments underneath it. No need to read the entire page.

---

