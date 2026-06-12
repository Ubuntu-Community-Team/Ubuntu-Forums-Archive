---
title: "Internet, YES. Browser, NO!"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by fotoflex on 2014-02-26
Two days ago, my browsers suddenly could not access the internet.
The internet is active and my tablet has no problem.
I am now running Xubuntu off the LiveCD, so I could search for a solution.
Did not find one.
A friend found something, instructions to change the IPV6 settings in Firefox, but that made no change.
Anyhow, how could those settings have changed mid session???
Does anyone have any suggestions?
In Windows, which I used before, I would have used the option to go back to the last working system.
Is there something like that in Xubuntu 12.04?

---

### Post by buzzingrobot on 2014-02-26
Are any other internet apps working correctly?  Email, for example. Can you play streaming music?

If you open a terminal and execute this:
```
ping -c 4 google.com 
```

...do you see 4 lines displayed, each with the same IP number?


A 'System Restore' is not a standard Ubuntu feature.

---

### Post by fotoflex on 2014-02-26
Thank you, buzzingrobot.

Yes, I see 4 lines displayed, each with the same IP number.

Pity about the system restore.... :(

---

### Post by fotoflex on 2014-02-26
Oh, sorry, missed the questions on top.
For streaming music I need to go to a website with music, right?
All pages give the same message, that the server cannot be found.
No email, either.

---

### Post by buzzingrobot on 2014-02-26
The "ping google.com" was to check that name resolution was working, (Names like "google.com" need to be resolved to their IP address.) It appears to be working, since the ping completed successfully.  Broken name resolution is the first place to look if sites suddenly cannot be accessed.

You  might check that the contents of your /etc/hosts file hasn't been altered.  It should look more or less like this:
```

#
# /etc/hosts: static lookup table for host names
#

#<ip-address>    <hostname.domain.org>    <hostname>
127.0.0.1    localhost.localdomain    localhost
::1        localhost.localdomain    localhost
```

You could also try closing the browser, deleting the browser configuration directory (Firefox's is ~/.mozilla/Firefox) and restarting the browser.  You will lose bookmarks, etc, unless you back them up.  This will have the affect of using a freshly installed browser, eliminating any accidental or deliberate tampering with the previous configuration.

---

### Post by fotoflex on 2014-02-26
Thanks.

Where do I find te host file?

And reinstalling the browser, after remving it with an uninstaller do the trick?

---

### Post by buzzingrobot on 2014-02-26
To view /etc/hosts, either open a terminal and execute "cat /etc/hosts" or use the file manager to navigate to /etc and view the hosts file.

Deleting the browser's configuration files, e.g., deleting ~/.mozilla/Firefox, does not delete the browser,  It deletes the browser's configuration files, which is where a malevolent web page *might* have entered or edited some code that *might* be causing your problem. 

If you use the apt-get command with the purge option to remove a package, it's configuration files will also be removed, and you can reinstall it.  I don't think that is necessary in this case.  Just remove the configuration directory and relaunch the browser.  If that does not work, then purge the browser.

---

### Post by pqwoerituytrueiwoq on 2014-02-26
make sure networking in enabled, you should have a network icon near your clock

---

### Post by r.stiltskin on 2014-02-26
Are you on your own home network or somewhere else?

If it's your own:
reboot your cable/dsl modem (just disconnect the power for a few seconds then reconnect)
if you're using a separate router or access point, reboot that the same way

Either way (home or school, etc.)
try renewing your dhcp lease by running these commands (in a terminal window):
```

sudo dhclient -r
sudo dhclient

```

And by the way, is this a wireless or ethernet connection?

---

### Post by tripp98 on 2014-02-26
it sounds like your browers settings are messed up.   open nautilus(file browser)
in your home folder to a ctrl H to show hidden files.  rename the .mozilla folder to .mozille-old
then start firefox.  that will clear out all your setting within firefox

---

### Post by fotoflex on 2014-02-26
Thanks all!
My network is enabled, I have restarted the router.     
I don't really use firefox, it just comes with the xubuntu installation.
I have no problems with removing it, so I did that and am now re-installing it, but that takes an extraordinary long time.
Once that is finished, we'll see if it works.
If not, I will rename. mozilla.

---

### Post by fotoflex on 2014-02-27
Oh gosh!
I left the re-install running while I was away.
It failed.(see screenshot)
Reading the message, I decided to estabish a wired connection.
I have used that before, when re-installing Vista, to download the enormous service packs.
The access point is not readily available, I use it only when I have no other option.
Before, I just stuck the wire in, that was it.
But now that doen't work, the little lights are blinking away, but the laptop remains disconnected.
However, this complicates matters and distracts from the original problem.

I uninstalled Firefox via the Ubuntu Software Center.
I could see and search everything there, so I assumed the USC was using the internet.
But while reinstalling, I get a choice 'OK' or 'Repair'.
'OK' does nothing, 'Repair' leads to an hours long install.
[ATTACH=CONFIG]250726[/ATTACH]

So far, so good. :rolleyes:

---

### Post by fotoflex on 2014-02-27
Oh gosh!

---

### Post by buzzingrobot on 2014-02-27
Much of the info in that screen capture is cut off.  But, if you were seeing 404 errors, then the archive at nl.archive.ubuntu.com was simply offline. (It happens.)  When a mirror is offline, the program trying to do the install will wait for some time before moving on to try another mirror. That can add up when a number of packages are queued for download because each attempt to download another package restarts the timeout period. If a number of mirrors are offline simultaneously, things can really bog down.
 
On the other hand, this could be down to the same problem you have with browsers.  

Try again. Also, use the gizmo in the Update tool to identify the fastest mirror for your location.

---

### Post by fotoflex on 2014-02-27
Yes, I cropped the window with information about my internet connection, because I'm not sure what information to give out on the internet.
I'm using the computer with either the LiveCD to use the internet, or the harddisc to access my installation without internet.
Supposedly, the archive was offline for more then six hours?
That seems a lot, I have not encountered that before.
Maybe just lucky.
I will have a look at the gizmo in the Update tool, if I can find that.
Absolute beginner, I chose this thread carefully. :)

---

### Post by buzzingrobot on 2014-02-27
> **fotoflex said:**
> 
I will have a look at the gizmo in the Update tool, if I can find that.
  :)

Not sure what it is called in Xubuntu, but in straight Ubuntu it is in the Update tool where you set up your repos, aka software sources. The current mirror will be shown. By default it's a national mirror, like nl.archive.ubuntu.com. Clicking on it triggers a routine that tests response time from each mirror, shuffling the fastest to the top of the list.  It might take several minutes, but when it seems to havee concluded you can select the fastest mirror as your default.

Your problem still smells much like a DNS/name resolution problem, especially if you didn't run into mirrors being offline. But, if your DNS was not working, that ping of google.com would not have worked. It's further complicated because you say other web apps can't reach their servers, either. That rules out a browser-specific problem, or solution.

 I use Google's public nameservers (8.8.8.8,8.8.4.4).  On a very long shot (premised on the possibility that your ISP's nameservers are flakey), you might try those, replacing your current nameservers (presumably provided by your ISP).  Right click on the network icon, select "edit connections". Highlight the connection and click "Edit".  Select the "IPv4 Settings" tab. At the top, click the dropdown arrow at the "Method: Automatic(DHCP)" line. Select "Automatic (DHCP) addresses only". Then, in the "DNS servers:" field, enter "8.8.8.8,8.8.4.4" (no quotes).  Click 'Save" and close it out.  The switch to the new nameservers should take a second or two; you'll probably see a popup. 

If that doesn't change anything, I'm pretty much at a loss.

---

### Post by fotoflex on 2014-02-27
That would enable Chrome as well, I hope?
Because I fear for the return of firefox.

---

### Post by buzzingrobot on 2014-02-27
> **fotoflex said:**
> That would enable Chrome as well, I hope?


If the problem is, in fact, related to your ISP's nameservers, then it will change that across the board, for everything.

If that turns out to be the fix, it means Firefox was not the problem.

Again, though, I think it's a long shot, but worth trying.

Re: nameservers -- Every server on the web has a unique IP address assigned to it. That's how software finds it. People can't remember numbers, so we use domain names and assign those to servers. To make the net work, those domain names need to be translated into their corresponding unique IP numbers.  That's what nameservers do.  They are basically giant lookup tables that map unique server names to the right unique IP addresses. Most users default to using nameservers provided by their ISP. That's usually fine, but it is possible -- though not common -- that they miss an update, become unreliable, etc.  And, since you need a nameserver to find servers by domain name, you cannot find your nameserver by domain name.  Hence, the need to plug in actual IP addresses for those.  Everytime you point a browser at a site, check email, etc., the name of the server you are accessing goes to your nameserver, gets translated into the IP address, and that's sent back to your browser/mail client/etc. which only then can find that server and make the connection.

---

### Post by fotoflex on 2014-02-27
The window does not allow me to save. Should there be a , in between the numbers, not a .?

---

### Post by fotoflex on 2014-02-27
Okay, just like telephone book then. I look for the name, the book gives me the number. Out-of-date book, names and numbers don't match.

---

### Post by buzzingrobot on 2014-02-27
> **fotoflex said:**
> The window does not allow me to save. Should there be a , in between the numbers, not a .?

Yep, it's a comma between two numbers.

---

### Post by fotoflex on 2014-02-27
Just asking, because it'shard to read on the tablet an typing it in on the laptop.
Lots of room for mistakes.
Okay, I'll just try again the next time I restart without the LiveCD.
Sometimes things work in one session when they don't in another.

---

### Post by r.stiltskin on 2014-02-27
Just to be sure that we understand each other exactly:

Is it true that when you boot your laptop using the LiveCD you can connect to your wireless router and access this forum, but when you boot Xubuntu installed on that same laptop it cannot access the internet through that same wireless router?

Also, is it true that you are using DHCP to let your laptop get its IP address automatically from the router?

If so, then it's HIGHLY unlikely if not impossible that the problem is caused by your ISP's nameservers, since those same nameservers are working correctly for your LiveCD.

I also doubt that Firefox is the culprit.  Since you were unable to connect to the repository, your network connection was either down or damaged in some way.

When you boot the installed system:
On your top panel (assuming you haven't altered it) you should see a network connections applet - the icon may be a pair of arrows, one up and one down, or a wifi-signal-strength icon.  Do you see that?

When you click on it, can you confirm that both "enable networking" and "enable wireless" are checked?

Then click on "edit connections".  You should see, under the wireless tab, the name of your router or access point.  Click to highlight it, then click delete. Click again for "are you sure ...".
Next click "+Add".   This will bring up the dialog for "editing wireless connection 1". 

You probably already know what to do here, since you have done it to connect with your LiveCD, right?
(I assume that you are using DHCP.  These instructions don't apply if you are configuring the connection manually.)

But if you're not sure:
At the top, "Connect automatically" should already be checked.  If not, check it.
At the bottom, "Available to all users" should be checked.  If not, check it.
Connection name is unimportant; you can leave "wireless connection 1" or put in your router's name or whatever...
Next to SSID, type in the EXACT name of your router/access point.  (Case sensitive!)
Mode should say "Infrastructure"
MTU should say "automatic"
Leave the BSSID and the two MAC address fields blank.

On the IPV4 settings tab:
Method should say "Automatic (DHCP)"
leave the rest of this tab blank

On the IPV6 settings tab:
Method should say "Automatic (DHCP)"
leave the rest of this tab blank

On the Wireless Security tab:
select the appropriate security protocol for your router (WEP, WPA, etc)
enter the appropriate credentials (WPA password, WEP key, etc)

Click save, then close the Network Connections dialog and it should establish a connection.

If it still doesn't work, open a console and run:
```
dmesg
```
The last few lines of output should give some clues about what's causing the problem.

If the panel indicator says you are connected, do you have a browser to try?  Otherwise, you should be able to install one from the repository.  To eliminate any doubts about firefox, why not try chromium-browser (unbranded version of Google Chrome).  Run:
```
sudo apt-get install chromium-browser
```
and see if that works.

---

### Post by fotoflex on 2014-02-27
Thanks.
I really only use the Iron browser.
Now I use firefox because it comes with the liveCD.
But neither of them contact the network when I boot Xubuntu installed.
I will copy your suggestions and send them to the tablet, so I can check the settings.
I'll do that later, as I'm now on the LiveCD again.
Losing the internet is annoying, hard to check things.
The tablet is nice, but not a real substitute for a computer.

---

### Post by fotoflex on 2014-02-27
WOW!
That is... just wow!

I thought every time you log in to your router with the 26 digit code, you establish a fresh connection.
(I thought that was the point of the wpa 2.)
But you don't.

Well, so many thanks, I was already adjusting myself to the idea I would need to re-install Xubuntu and lose everything.
So I'm very happy now.
Also many thanks to the others offering suggestions.

Something occurred to me when the browser opened its 4 standard pages,
the first being Hotmail, that one didn't open.
I remember now that has been the case for a long time before.
I just clicked the reload button and everything went fine, but now I think it's somehow related to the problem.
What do you think?

---

### Post by r.stiltskin on 2014-02-28
Which browser are you referring to?  And what do you mean by "4 standard pages"?  A browser opens whichever page or pages you want.  You choose (in Settings/"on startup") which page(s) open when you start Chromium or its derivatives Chrome and Iron.  In Firefox you choose in the Edit/Preferences/General/Startup section.

I can't tell you why a particular page didn't open.  If you had the browser configured to open that page and it didn't, maybe the URL of that website has changed and you didn't change your setting.  I don't think a malformed URL is likely to mess up your network configuration, but I can't say that it's impossible.

---

### Post by fotoflex on 2014-02-28
[http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)
Ah, I should have said **my **standard pages, the ones I chose as you describe.
Hotmail, Giveawayoftheday, Gmail & startpage.
When Hotmail didn't open, I just hit the reload button and later clicked 'use current pages' in Settings.
In fact the same mistake as with the internet connection, I didn't replace it with a fresh URL (which I will do now).

Thanks again!

---

### Post by buzzingrobot on 2014-02-28
I'm at a bit of a loss to explain how the ping of google.com was successful if the connection wasn't active and/or the router was misconfigured.  I'd considered the router until the ping worked. Hence, the look at the admittedly very slim possibility that the ISP's nameservers were periodically unreliable. Anyway, glad it's fixed.

---

### Post by fotoflex on 2014-02-28
The screenshot also shows there was an active connection. How to know that's wrong?
Many lessons have been learned by all! :)

Thanks again.

---

