---
title: "Dumb question about browser pages"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by anewguy on 2011-09-16
I've noticed in Firefox (haven't ever checked my Windows laptop) that if the mouse goes over certain parts of text a little box pops up with either a definition of what I'm on or suggestions on what to do - like click here to see a map for this address.

I've looked in the normal tools for Firefox and can't find an option for this.  Is there an advanced option somewhere to turn this off, or is this a function of the actual web page coding?

Thanks in advance!
Dave ;)

---

### Post by mocoloco on 2011-09-16
What website are you seeing it on?  Most likely it's the site, and not anything to do with the browser.  Pull up the same site in Chrome or another browser and you should be able to confirm this.

---

### Post by anewguy on 2011-09-16
I did some more searching on the web and turned up a couple of pages with the exact problem - Firefox or Internet Explorer.

Apparently it's ads from something called IntelliTXT.  See [this link]("http://forums.mozillazine.org/viewtopic.php?f=38&t=1514205&start=15") for more information and sample pictures of the boxes.

It would seem from that thread that the solution is:

Terraspeed
    Guest
     

Post Posted October 9th, 2009, 11:35 am
I finally found out how to make it stop LARC; ***_when the window pops up, click on the question mark and follow the instructions for disabling it._*** Here is the text that is displayed: What’s this?

These are advertiser links running on FOXNews.com through Vibrant Media, a third-party media group.

FOXNews.com is working with Vibrant Media to run an InteliTXT, In-Text Media Campaign.

Vibrant Media delivers this advertising in real-time and only after the FOXNews.com article has been posted online. These links in no way reflect the views or opinions of the FOXNews.com editorial team and all in-text media placements are fully disclosed and identified with the words "sponsored link".

If you would prefer not to see any double-underlined words and corresponding advertisements, please click here. Please note: deactivation requires the use of cookie technology. If you should delete or refresh your cookies the service will be re-activated automatically.

Problem solved. Hope this helps, they were driving me crazy too.



Now, of course, I can't get one of the dang things to pop up so I can disable it!

Hope this helps anyone else who finds this annoying!

Dave ;)

---

### Post by vasa1 on 2011-09-16
> **anewguy said:**
> ...
Apparently it's ads from something called IntelliTXT...

Hi Dave,

There's another way of killing these things.
**For example**, you could put these urls in your AdBlock Plus filter (if you use ABP):
conceivablytech.us.intellitxt.com/intellitxt/
neowin.us.intellitxt.com/intellitxt/
if you don't want to see them on sites such as [http://www.conceivablytech.com/](http://www.conceivablytech.com/) and
[http://www.neowin.net/](http://www.neowin.net/)

Of course, intellitext isn't the only one. There's also kontera:
[http://www.wilderssecurity.com/showthread.php?t=301286&highlight=kontera](http://www.wilderssecurity.com/showthread.php?t=301286&highlight=kontera)
and
[http://www.wilderssecurity.com/showthread.php?t=146499&highlight=kontera](http://www.wilderssecurity.com/showthread.php?t=146499&highlight=kontera)

I just have things like:
.*intellitxt.com
and
.*kona.kontera.com
in my Privoxy user.action file and that takes care of them.
(I prefer Privoxy over AdBlock Plus since it can work for a variety of browsers)

---

### Post by anewguy on 2011-09-16
Hey - thanks for that!  I'm going to have to try installing one of those and trying it out.  So far I don't have anything like that installed, so I guess it's timed I learned, eh?

Thanks again!

Dave ;)

---

### Post by vasa1 on 2011-09-16
> **anewguy said:**
> Hey - thanks for that!  I'm going to have to try installing one of those and trying it out.  So far I don't have anything like that installed, so I guess it's timed I learned, eh?

Thanks again!

Dave ;)

You're welcome! The Privoxy devs are helpful but I'm not comfortable with their help system ... sort of like a mailing list thing and not as friendly as a forum format.

The AdBlock Plus forum is quite accessible:
[https://adblockplus.org/forum/](https://adblockplus.org/forum/)
Palant and the list maintainers are quite prompt in helping people. As of now, AdBlock Plus is available for Firefox and Chrome but the Firefox one is set up much better.

---

