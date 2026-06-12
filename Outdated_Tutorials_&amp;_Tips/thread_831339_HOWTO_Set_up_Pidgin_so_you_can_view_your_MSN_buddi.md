---
title: "HOWTO: Set up Pidgin so you can view your MSN buddies' personal messages"
date: 2008-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by ezramorris on 2008-06-16
[COLOR="Red"]Update 2008-11-16: Most of the features of MSN Pecan are now included in the default 'MSN' option in Pidgin 2.5, which is included in Intrepid by default. If you no longer want MSN Pecan, you can remove the plugin by removing the "msn-pecan" and "pidgin-msn-pecan" packages from Synaptic Package Manager.[/COLOR]

----------------------------------------------------------

msn-pecan is an alternative MSN/Windows Live Messenger plugin for Pidgin. In the author's own words:
> Being the main author of the MSN plug-in in Pidgin I got tired of being neglected from the development. So I started a fork.
The project page is located at [http://code.google.com/p/msn-pecan/](http://code.google.com/p/msn-pecan/)

Please note: This is an unofficial plugin, so not supported by Pidgin's development team.

----------------------------------------------------------

[COLOR="Red"]**New: Use the Ubuntu repository:**

1. Click System>Adminitration>Software Sources, and enter your password if required.

2. Click on the "Third party software" tab, then click "Add..."

3. Type:
```
deb http://ppa.launchpad.net/msn-pecan/ubuntu hardy main
```
and click "Add Source". Replace gutsy for hardy if you are using 7.10 Gutsy Gibbon.

4. Click on "Add..." again, type:
```
deb-src http://ppa.launchpad.net/msn-pecan/ubuntu hardy main
```
and click "Add Source". Again replace gutsy for hardy if applicable.

5. Click "Close" then "Reload".

6. Once the Software Sources dialog box has closed, click System>Administration>Synaptic Package Manager, and enter your password if applicable.

7. Click Search, type ```
msn-pecan
``` then click Search.

8. **Important: **If you see a package named "**msn-pecan**" which has a green square next to it, right click it, then click "Mark for Removal".

9. Right click "**pidgin-msn-pecan**" and click "Mark for Installation". If a warning about authentication appears, click "Mark".

10. Finally, click "Apply" then "Apply" again. After this has finished, close Synaptic Package Manager, and follow step 4 below.

Although this method has a few more steps, it does mean that updates will happen automatically.[/COLOR]

-----------------------------------------------------

**The old (manual) method:**

I will do most things from the terminal, since it's easier to explain, but if you want, you can install the packages through synaptic. You can start the terminal from Applications>Accessories>Terminal.

Please close Pidgin before you start.

1. Install libpurple-dev and git-core:
```
sudo apt-get install libpurple-dev git-core
```

2. Download the plugin:
```
git clone git://github.com/felipec/msn-pecan.git
```

3. Compile and install the plugin:
```
cd msn-pecan

make

sudo make install
```

4. Setup Pidgin to use the new plugin:
- a. Start Pidgin and go to Accounts>Manage.
- b. Either disable your existing MSN account by unchecking the check box or delete it by selecting it and clicking Delete. I would recommend deleting it to keep things tidy, but it's up to you!
- c. Click add and set up an account as you normally would, except select WLM instead of MSN for Protocol.

5. Done!

Please let me know how you get on!

---

### Post by Hubi17 on 2008-06-20
Wow thanks. Works perfectly!!

I missed the status messages of some of my friends. Not any more.
Thanks again ;)

---

### Post by scotcella on 2008-06-20
Manged to download it ....

but for some reason number 3 doesn't work..  gives me error stuff..   the output being as long as my arm

and no WLM option anywhere that i can see
:(

---

### Post by ezramorris on 2008-06-20
> **scotcella said:**
> Manged to download it ....

but for some reason number 3 doesn't work..  gives me error stuff..   the output being as long as my arm

and no WLM option anywhere that i can see
:(

Any chance of posting the output (maybe just the end)?

Thanks.

---

### Post by scotcella on 2008-06-20
> /usr/include/libpurple/certificate.h:543: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;time_t&#8217;
/usr/include/libpurple/certificate.h:543: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;time_t&#8217;
In file included from /usr/include/libpurple/account.h:44,
                 from error.c:31:
/usr/include/libpurple/connection.h:254: error: expected specifier-qualifier-list before &#8216;time_t&#8217;
make: *** [error.o] Error 1

This is the last few lines...  the first two steps breezed through easily..

---

### Post by ezramorris on 2008-06-20
> **scotcella said:**
> This is the last few lines...  the first two steps breezed through easily..

Do you have the most up-to-date version of Pidgin?

I just compiled it now and it works fine.

---

### Post by scotcella on 2008-06-20
The version I have now was included in Hardy..

Just checked and the version is 2.4.1.

---

### Post by ezramorris on 2008-06-20
> **scotcella said:**
> The version I have now was included in Hardy..

Just checked and the version is 2.4.1.

Just found a pre-built deb here [http://ppa.launchpad.net/reda.ea/ubuntu/pool/main/m/msn-pecan/](http://ppa.launchpad.net/reda.ea/ubuntu/pool/main/m/msn-pecan/)

Try out msn-pecan_0.0.14-1ubuntu1~ppa1_i386.deb . If it works I'll update the tutorial.

---

### Post by durus on 2008-06-20
Thank you. This works perfectly for me!

---

### Post by scotcella on 2008-06-20
Hi ezramorris, 

Thanks,

I'm not really sure how to install it after downloading the package.

Usually I just copy and paste commands, or use the synoptics manager (point and click), so obviously I need to learn how to do this one. 

When I download the package on to the desktop you've just given me, how to I install it from there?

Thanks for your help so far!!

---

### Post by Hubi17 on 2008-06-20
Just double click it, and the package manager should open to install it ;)

---

### Post by scotcella on 2008-06-20
Thanks... 

Just worked it out..  hehe I couldn't wait so I figured I had nothing to lose if I clicked!

Whew!!!

Anyway thanks everyone for your help, everything works GREAT!!!

My only question now is..  is there a add on that will enable ME to put on personal messages? *hopes*

---

### Post by eldragon on 2008-06-20
i had a problem with this msn plugin, it suddenly showed everyone as being offline. even though they saw me online and i could chat with them...

did anyone suffer that?

had to revert to the msn plugin

---

### Post by HangukMiguk on 2008-06-20
Thanks, one problem I found:

Unable to connect multiple instances of MSN through this plugin.  I was able to connect my second account through the old plugin.

---

### Post by ezramorris on 2008-06-21
> **scotcella said:**
> My only question now is..  is there a add on that will enable ME to put on personal messages? *hopes*

Sort of. It is included by default. I haven't found it very good, but click on Available at the bottom of the screen, then select Available again from the pop up. A message box will now show underneath, and you can type a message in here.

The reason why it's so complicated is that pidgin doesn't actually support personal messages, but rather "status" messages.

[COLOR="Red"]Edit: [/COLOR]It works fine as long as you don't have the musictracker plugin installed.

---

### Post by Hubi17 on 2008-06-21
I also just realised that now my buddies dont have display pictures anymore :(
This normally works fine with normal msn plugin. Strange. Or am I missing a configuration?

---

### Post by ezramorris on 2008-06-21
> **eldragon said:**
> i had a problem with this msn plugin, it suddenly showed everyone as being offline. even though they saw me online and i could chat with them...

did anyone suffer that?

had to revert to the msn plugin

> Thanks, one problem I found:

Unable to connect multiple instances of MSN through this plugin. I was able to connect my second account through the old plugin.

I haven't tried either of these, but if you like you can post a bug report here: [http://code.google.com/p/msn-pecan/issues/list](http://code.google.com/p/msn-pecan/issues/list)

---

### Post by xen on 2008-07-01
Just tried this, works great so far! I'll report any bugs I encounter. Its a shame that the built-in Pidgin MSN protocol is so far behind.

---

### Post by FaberfoX on 2008-07-01
Wow, thanks a lot for this, is it safe to add:
deb [http://ppa.launchpad.net/reda.ea/ubuntu](http://ppa.launchpad.net/reda.ea/ubuntu) hardy main
to my software sources to keep up to date with your developments?
Also, any chance you can add offline messages support or does this need more plumbing fixes on the pidgin core?

---

### Post by ezramorris on 2008-07-02
> **xen]Its a shame that the built-in Pidgin MSN protocol is so far behind.[/QUOTE]

I asked about this on the Pidgin IRC, and they said there are plans to include this functionality in the future, but not through the msn-pecan code. It was due to msn-pecan not confirming to their code regulations or something.

[QUOTE=FaberfoX said:**
> Wow, thanks a lot for this, is it safe to add:
deb [http://ppa.launchpad.net/reda.ea/ubuntu](http://ppa.launchpad.net/reda.ea/ubuntu) hardy main
to my software sources to keep up to date with your developments?
Also, any chance you can add offline messages support or does this need more plumbing fixes on the pidgin core?

Hi,
Firstly I don't maintain/develop any of this stuff!

You could add that line, but it's up to you! If you want to test it an let me know if it works, then that could provide a much easier way for this tutorial.

---

### Post by magnus0 on 2008-08-15
But how do I set my own personal message?

---

### Post by ezramorris on 2008-08-15
> **magnus0 said:**
> But how do I set my own personal message?

See post #15.
Click on "Available" at the bottom of the buddy list, then from the menu , choose "Available" again. A message box appears. Type your personal message in here.

---

### Post by belh4wk on 2008-08-19
nice plugin
works like a charm
except for one thing

all the smiley-shortcuts are different...
not all of em but the hug shortcut doesn't appear to exist
(k) which should make for a kiss-emoticon has been replaced by :-*
can i alter these somewhere or is there a way to put the old ones back?

---

### Post by ezramorris on 2008-08-20
> **belh4wk said:**
> all the smiley-shortcuts are different...
not all of em but the hug shortcut doesn't appear to exist
(k) which should make for a kiss-emoticon has been replaced by :-*
can i alter these somewhere or is there a way to put the old ones back?

Not sure, but it might be to do with this:
[http://code.google.com/p/msn-pecan/wiki/FAQ#The_emoticons_are_different](http://code.google.com/p/msn-pecan/wiki/FAQ#The_emoticons_are_different)

---

### Post by ezramorris on 2008-08-20
Did anyone try using the repository? Shall I add it to the tutorial?

[COLOR="Red"]Edit: Stuff it. The guy who makes msn-pecan has set up his own repository. See the first post for an updated tutorial.[/COLOR]

---

