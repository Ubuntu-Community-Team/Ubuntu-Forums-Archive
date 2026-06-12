---
title: "Fiddler trace"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by heiowge on 2008-10-07
Fiddler trace - anyone know what one is, what it does, the risk factors and a linux equivalent?

I had a problem where every time I logged into hotmail it prompted me to upgrade my browser to the latest version.  It was forward enough to include firefox and opera, but it was prompting me to upgrade to firefox 3 - I was already using 3.0.2!

I queeried microsoft who (not entirely unexpectedly) suggested the fault was my browser or machine.  Since I managed to replicate the problem on 3 other machines running PC-BSD, XP / Ubuntu and Vista respectively, they were a bit stumped.  I am now on my 4th level techie.  The third suggested a Fiddler Trace with nice instructions on how to set it up in WinXP.

When I reminded him that I use Ubuntu, I got techie 4.0 who said:

"Thank you for patiently waiting for our reply.  My name is Lotis and I am a Subject Matter Expert for Windows Live Hotmail. I apologize for the delay in getting back to you.  I gather that you want to know the Linux equivalent of FiddlerCap.  I realize this is causing an inconvenience.  I know how important it is for you to have this issue resolved immediately.

I am sorry but we do not support Linux operating system.  You may need to contact the support team of Linux for assistance in getting the Fiddler trace.
 
We appreciate your continued support as we strive to provide you with the highest quality service available.  Thank you for using Windows Live Hotmail."

So back to my original question...

---

### Post by psylem on 2009-02-02
People seem to recommend wireshark as a linux substitute for fiddler. I've tried it and it captures a whole lot more than I needed, and for some reason I still haven't figured out how to just capture straight http(s) traffic in my environment, which is all fiddler does.

Maybe try installing the user agent switcher firefox add on. Perhaps fooling hotmail into thinking you are using firefox on windows will give the desired result.

---

### Post by edgar_knarretje on 2009-07-02
As you might have found out already: the plugin for Firefox is "tamper data". functionality is roughly the same, see tools->plugins in firefox for details. 

I use it al the time now...

regards, -- @gar --

---

### Post by a_flj_ on 2011-03-15
> **psylem said:**
> People seem to recommend wireshark as a linux substitute for fiddler. I've tried it and it captures a whole lot more than I needed, and for some reason I still haven't figured out how to just capture straight http(s) traffic in my environment, which is all fiddler does.

Maybe try installing the user agent switcher firefox add on. Perhaps fooling hotmail into thinking you are using firefox on windows will give the desired result.

Wireshark only captures whatever packets match a filter you set when starting the capture. Before you start a capture, you can configure the interface. For instance, "host localhost and tcp port 80" will only capture packets sent from or received on port 80 on localhost. Use 443 for https, or 8080 for application servers not listening on the default http port. However, be aware that wireshark doesn't interpret the stream data, so for https it is likely that you'll get gibberish, instead of the actual http traffic.

Data packets are usually displayed with a light green background in wireshark's trace log. Right-clicking on such a packet, and selecting "follow TCP stream" (IIRC - might be just "follow stream" or something alike) from the context menu filters out only the data traffic that happened on that particular TCP connection. If it's http, you get all posts/gets and the corresponding responses in the order they were exchanged. Which is quite a lot, I think, when you need to debug some web app.

What wireshark misses, compared to fiddler, is the ability to analyze and manipulate the streamed data - for instance like decoding https (does it?). That's how I landed here - I hoped to get a recommendation on a fiddler equivalent for linux.

---

