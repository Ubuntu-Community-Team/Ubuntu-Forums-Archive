---
title: "HOWTO: Fix Broken &quot;mail-to&quot; and Linking Between Mozilla Firefox &amp; Thunderbird"
date: 2005-07-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Loungefly on 2005-07-22
This is something that was driving me NUTS ](*,) 

Not too long after I set up Thunderbird and Firefox in my Kubuntu I noticed that whenever I clicked on any sort of link in Thunderbird  (whether it be "Get New Themes" in the theme manager or regular web links in emails) that was supposed to open up a page in Firefox, nothing would happen. It was broken.

 I also noticed in Firefox that I couldn't get any email ("mail-to") links to open a "compose" page in Thunderbird.

I finally managed to stumble across the fix for this and I thought I'd share. It works like a charm :) 

TO FIX "MAIL-TO" LINKING BETWEEN FIREFOX AND THUNDERBIRD:

1.  In Firefox, open the url "about:config"
2.  Right click --> new --> string
3.  enter 'network.protocol-handler.app.mailto' for preference name.
4. enter 'path/to/Thunderbird' (wherever your Thunderbird executable is located)       for the string value
5. Restart Firefox 

That's it! When you click on an email link in Firefox, you should see Thunderbird open up properly.

TO OPEN PAGE IN FIREFOX WHEN CLICKING ON WEB LINKS IN THUNDERBIRD:

1.  Go to [addons.mozilla.org](https://addons.mozilla.org/extensions/showlist.php?application=thunderbird&category=All) and download the "about:config" extension for Thunderbird. Install the extension and restart Thunderbird.

2. Now that About:config is installed we have easy access to some of Thunderbird's hidden preferences. So, from the menu go to Tools --> About:config

3. This will open up the about:config window.  From here create the entries listed below, and add the paths as the values listed.
         1. Right click --> new --> string
         2. Type 'network.protocol-handler.app.http' for preference name.
         3. Enter your path to the Firefox executable for the string value ( example- ust/local/bin/firefox/firefox) for the string value
         4. add 'network.protocol-handler.app.https' with the same path to Firefox for the string value. 
5. add 'network.protocol-handler.app.ftp' and your path to Firefox once again for the string value

When you click on a link in Thunderbird from now on, you'll see that Firefox opens the way it's supposed to  :wink: 

Hope this helps any of y'all who've had these problems

Cheers  \\:D/

---

### Post by Loungefly on 2005-07-23
Doh... Just noticed some major typos and stuff ups in my initial post. All fixed now :)

---

### Post by Michael Matthews on 2005-12-31
Thunderbird starts firefox but url does not come up, instead default home page comes up. about:config solution no love.

When I bring up thunderbird > about:config I see entries as 'user set'
network.protocol-handler.app.http ... make s no difference.

thanks

---

### Post by acope on 2006-09-05
Now it's even easier, with [XK]ubuntu v6.06.

network.protocol-handler.app.http (and network.protocol-handler.app.https) is set to use x-www-browser.

/usr/bin/x-www-browser is a symbolic link to /etc/alternatives/x-www-browser

and

/etc/alternatives/x-www-browser is a symbolic link to whatever browser you want to use.

This is what I did:

$ sudo rm /etc/alternatives/x-www-browser
$ sudo ln -s /usr/bin/firefox /etc/alternatives/x-www-browser

and all is sweet. ;) 

Cheers
Andrew
-- 
DIRECTOR
Evergreen Computing Ltd
Websites - Excellent Quality, Excellent Value

Email:    [email]andrew@evergreencomputing.com[/email]
Website:  [http://evergreencomputing.com](http://evergreencomputing.com)
Phone:    +44 (0)1454 269 087 
Fax:      +44 (0)8707 515 596

---

### Post by Jorge hermosillo on 2006-10-27
I tried this and worked perfectly:

To Make [COLOR="Red"]Firefox[/COLOR] your [COLOR="Red"]default browser[/COLOR]: 
1. Open Firefox
2. Menu->Edit->Preferences
3. ->General->"Default Browser"->"Check Now"

To Make [COLOR="Red"]Thunderbird[/COLOR] your [COLOR="Red"]default mail-to application[/COLOR]: 
1. Go to [http://www.mozilla.com/en-US/support/](http://www.mozilla.com/en-US/support/)
2. Click Thunderbird-Help->Frequently Asked Questions
3. Follow "How do I make Thunderbird my default mail program?" link

Cheers,
Jorge

---

### Post by killa1976 on 2008-09-03
None of the fixes or steps listed above work for me, I tried them all and double checked, Thunderbird will not open a html link in a email after doing them! Please help!:confused::confused:

---

### Post by JackW60 on 2010-03-08
Thanks. 

Not being able to open the browser from within Thunderbird was driving me nuts also. 
about:config fixed it for me on my new Kubuntu 9.10 install. I haven't tried mailto: yet.

Cheers,
  Jack.

---

### Post by braincookie on 2010-07-11
I had a problem with "mailto" links after downgrading from FF 3.6 to 3.0.19. Here's what I did to fix it:

[LIST]
[*]In FF, go to "Edit -> Preferences -> Applications"
[*]Search for "mailto"
[*]Choose "Always Ask"
[*]When you click any mailto link now, FF will ask for which application to use
[*]Choose "Other", which will open a file selector
[*]Go to /usr/bin/ and choose thunderbird
[*]Check "Always use this application" (or something similar, I'm on a different locale)
[/LIST]
This should be working fine now.

Note: When I look at the preferred applications for "mailto", I have now two entries

[LIST]
[*]Thunderbird (default)
[*]Thunderbird
[/LIST]
The first one is the broken one, but the second one works fine

---

### Post by tjwilli on 2010-07-17
I got this to work with this:

1. System->Preferences->Preferred Applications
2. On Internet tab, select 'Firefox' as default web browser, select 'Open link with web browser default' checkbox.

---

### Post by wheezer on 2010-07-29
I have tried all of these fixes, but since installing firefox 3.6.8 and Thunderbird 3.1 (from Tbird sitel (not available from repository yet), I still get nada.  

The only SEND TO link i can make work is the gmail option.   I MUST get tbird working for a number of reasons. Can anyone suggest a fix that might work?

---

### Post by carlita on 2010-07-30
Just because someone doesn‘t love you the way you want them to, doesn‘t mean they don‘t love you with all they have.&#12288;

---

