---
title: "Callto: Skype links for phone numbers with Ubuntu"
date: 2007-07-27
forum: Outdated Tutorials &amp; Tips
---

### Post by amoore on 2007-07-27
Looks for phone numbers in the page and hyperlinks them for calling with SkypeOut.

This script does not work by its self alone!! See the instructions below on how to use this script!!!
This script ** Tested on Ubuntu 7.04 ** ** Firefox 2.0.0.5 ** **Skype 1.3.0.53 **

If you are using the BETA version of Skype 1.4XXX See this post [http://forum.skype.com/index.php?showtopic=92761&st=0&gopid=424076&#entry424076](http://forum.skype.com/index.php?showtopic=92761&st=0&gopid=424076&#entry424076)... to use the new skype-action-handler

One of my biggest pet peeves is the closed source Skype VoIP client but, I use it because it just works. Development for the Linux version of Skype has always been slow and one of the greatest addition to Skype " The Skype Tool Bar" is not available for Linux. So I decided to implement my own version of it. What makes the The Skype Tool Bar so great is that it turns any 10 digit phone number on a web page into a Skype link. My own implantation looks for phone numbers in web pages and makes hyperlinks out of them. When clicking on the link, Skype will ring and be dialing the number / link you clicked on.


[IMG]http://photos1.blogger.com/blogger2/4312/3568/400/Callto%20Linkify%20%28for%20Skype%29.jpg[/IMG]

No more copying and pasting phone numbers to Skype. SkypeOut directly from your online contact list (say Gmail contacts) without any manual synchronization or addition to your Skype contact list.
My own implantation consists of a easy three step process and requires a Skype out account.
Step one:

Install the GreaseMonkey FireFox extension.

GreaseMonkey allows you to customize the way a webpage is display using small bits of JavaScript. This ability to customize the way a webpage display allows us to create the Skype link but, we need a script to do this.
Step two:

Install the skypelinkify for linux GreaseMonky script.
Step Three:

Configure FireFox to use Skype's network.protocol-handler.app.skype.

    * Open Mozilla (Firefox)
    * Type about:config in the address-bar to open the configuration editor.
    * Use the scroll bar to navigate to the network.protocol&#8230; section.
    * Check if the network protocol section includes a network.protocol-handler.app.skype key.
    * If a key exists, edit it. If no key exists, create a key by right-clicking on any key and selecting New -> String from the pull-down menu.
    * Enter network.protocol-handler.app.skype as the key name.
    * Enter /usr/bin/skype-action-handler as the key value.

Restart FireFox and lets give it a try!

The phone number below should now be a hyper link that will use Skype to call the number.

1-800-466-4411 This is the number to Google's FREE 411 phone service.

You will get a security warning in Firefox asking if its ok for Fire fox to allow Skype to dial out (this is normal).
Please comment to let me know you are using it.

---

### Post by komputes on 2008-11-24
Hi amoore,

:)

I read your blog post and thought this is a fantastic idea since the official skype extension is only for windows. I am having issues with installing this script on Ubuntu 8.10 Intrepid Ibex. I have started my own thread and would appreciate some help from you if possible. 

[http://ubuntuforums.org/showthread.php?p=6242569](http://ubuntuforums.org/showthread.php?p=6242569)

Thanks in advance! Also, is there any possibility of making this into a firefox xpi extension?

---

### Post by impresionist on 2010-08-30
Hi,
I'm not sure if this is up to date in Lucid, because I follow this manual, and after restarting it's true, I get firefox recognizing the callto-skype, but just when click in it, I get error, that firefox don't know how open this application...

Any update?
Regards,

---

