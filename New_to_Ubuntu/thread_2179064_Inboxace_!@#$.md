---
title: "Inboxace !@#$"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by carusoswi on 2013-10-06
Just this morning installed Ubuntu 31.04.  All went well until I tried to check my gmail.  I get this pop-up (guess that's what it is) informing me that a download of InboxAce is required.  I have found no way to dismiss this box, and (probably fortuantely), clicking to download doesn't seem to do anything, either.

I have no interest in this InboxAce, and, all I want to do is access my gmail.

How do I get rid of this goofy pop-up thing??

Thanks.

Caruso

---

### Post by carusoswi on 2013-10-06
I have uninstalled Firefox until I get some info that helps me to sort this out.
When I search online, the preponderance of links purport to promote this nuisance as an enhancement tool.
I guess it is designed to infect windows machines, since it seems not to install on my Ubuntu machine.  Even so, it blocks my efforts to sign on to my gmail account.

I have installed Chrome in the interim, and, although browsing online indicates that there is a version of this thing for Chrome, so far, my Chrome is not affected.

More info would be appreciated.

Thanks in advance.

Caruso

---

### Post by ajgreeny on 2013-10-06
As far as I can see from a quick search, this is an add-on toolbar, so I suggest you have a look in Firefox ->Tools ->Add-ons ->Extensions to see if you can find it there and either disable it or remove it completely.

If that is no help try renaming the hidden .mozilla folder in your home by right clicking it.  You will lose all your extensions/add-ons and bookmarks etc etc, when you start up FF next, but they will all still be there in the old .mozilla folder and if that works for you we can show you how to copy the needed files from the old profile to the new

---

### Post by DuckHook on 2013-10-06
Call me paranoid, but this doesn't sound right. You said that you installed 13.04. Was this a pristine install? Not an upgrade? If so, then there is no way it should have come with some goofy FF add-on already installed. From where did you download the image? Did you torrent or download directly from Ubuntu's official site?

Of course, if this is an upgrade, then all bets are off. I have no idea what you did to your prior install, and FF would have inherited all of your old plugins, extensions, etc.

---

### Post by carusoswi on 2013-10-06
> **DuckHook said:**
> Call me paranoid, but this doesn't sound right. You said that you installed 13.04. Was this a pristine install? Not an upgrade? If so, then there is no way it should have come with some goofy FF add-on already installed. From where did you download the image? Did you torrent or download directly from Ubuntu's official site?

Of course, if this is an upgrade, then all bets are off. I have no idea what you did to your prior install, and FF would have inherited all of your old plugins, extensions, etc.

I downloaded (not torrented) from the Ubuntu site.
It was a fresh install.  I formatted my 12.10 partitions and installed 13.04 to them.

This was not an upgrade, and the version of Firefox that I opened is the one that is integrated into 13.04.

The install was but 15 minutes or so old, and this was my first attempt to access gmail using Firefox.

I am a long time user of Ubuntu (from the days of version 6.xx).  I have absolutely no incentive to make anything up, and had never heard about this goofy Inboxace before encountering it.  It really makes me wonder what we are coming to when I search the topic online and find so many pieces that seem to give it credulity.  What really frustrates me is that once the thing pops up, I find no way to dismiss it other than to exit Firefox and start over.  As soon as I navigate to the Gmail login screen, it pops up again.

As mentioned above, I solved the problem by removing Firefox and going with another browser.

Fortunately, this insidious little varmint has yet to infect any of my Windows browsers or the Chrome browser that I installed to replace Firefox on my Ubuntu OS.

This much I assure you, the thing popped up on my Firefox, it did not ask permission, and it would not go away.  When I reinstalled Firefox and tried to log onto Gmail, it popped right up again.

So, until someone enlightens me as to how to ban this thing, I will make do with alternate browsers.

Caruso

---

### Post by DuckHook on 2013-10-06
I was not implying whatsoever that you were making anything up. On the contrary, my reference to "not sounding right" was targetted at the install itself. My paranoia stems from a concern that the Ubuntu install image may be compromised.

A Google search of "inboxace" turns up a whole lot of nasties. Apparently, it is malware, more specifically, a browser hijacker. According to [this]("http://malwaretips.com/blogs/inboxace-toolbar-removal/") site, it will infect numerous browsers. Your instincts are absolutely spot on to be rid of it. As per the same above link, it may have installed when you visited a particular site. If so, then this is actually less worrisome than if it has somehow infected the install image, though it doesn't address your particlar problem.

This is the reason that I harden my browser to the point of lock-down with NoScript, AdBlockPlus, Better Privacy, WOT and Cookie Manager. If youhave not done so, then these tools are highly recommended once you get rid of this malware. Instructions for removing are in link above.

---

### Post by heir4c on 2013-10-06
Like ajgreeny say, rename the .mozilla file (keep it but rename it to .mozilla.original) and start FF again. If it is popping up again there is something wrong with FF itself. So, if pops up than is it better to contact Mozilla.

---

