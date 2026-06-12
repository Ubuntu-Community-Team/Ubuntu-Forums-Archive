---
title: "Intrusive Chrome something..."
date: 2019-10-13
forum: New to Ubuntu
---

### Post by Innernet on 2019-10-13
Hi.
My laptop freezes out of recovery chance and needs power cycling for several minutes (a couple of seconds shutoff does not make it ! ),  happened about 6 times in a few months.
The message that a script "chrome//global/content/customelements.js" is causing the problem does not even allow force quit, closing, or ignoring the halted condition.  Mouse, keyboard or clicks unresponsive.

There is no Chrome nor Windows **anything** in my computer, I do not even know what a script is, what Chrome is and I do not want to know.

How do I forbid any Chrome, or ALL scripts from intruding ?

---

### Post by TheFu on 2019-10-13
"chrome" is a generic term for pretty window stuff.  Thunderbird has "chrome", any GUI program has "chrome" ... think of it like having chrome wheels or bumpers on your vehicle.

---

### Post by Frogs Hair on 2019-10-13
Are you using Google Chrome browser ?

---

### Post by guiverc on 2019-10-13
I don't use chrome|google-chrome|google-chrome-stable|etc browser, but do see "chrome://...." messages on occasion on my chromium-browser setup (for me a snap installed by deb package).

These usually relate to extensions that treat my browser as if it was 'google-chrome', but there's always a "chrome://"  (colon ':' after the 'chrome').  It could be you made a typo (missing the ':') and have an extension that is playing up (if you are using chromium-browser) that possibly you should remove.

---

### Post by Innernet on 2019-10-13
Thanks.
I did handwrite the prompted  " Script:chrome//global/content/customelements.js:504 " on a piece of paper as was unable to take a screenshot as all freezes.

I do not use nor have any chrome application, browser nor anything chrome. Never used Thunderbird.  My email is from a fully external provider that I log in manually, never 'remembered' at the site.  My computer has nothing outside Ubuntu/Firefox, never had, never will, and kept miles away from anything Windows.  Even the search engine I mostly use is duckduck;  not Google.   Paranoic?  Perhaps.

Shows up slightly different at 
----> [https://duckduckgo.com/?q=%3Achrome%2F%2Fglobal%2Fcontent%2Fcustomelements&t=canonical&ia=web](https://duckduckgo.com/?q=%3Achrome%2F%2Fglobal%2Fcontent%2Fcustomelements&t=canonical&ia=web)

---

### Post by TheFu on 2019-10-14
> **Innernet said:**
> Thanks.
I did handwrite the prompted  " Script:chrome//global/content/customelements.js:504 " on a piece of paper as was unable to take a screenshot as all freezes.

I do not use nor have any chrome application, browser nor anything chrome. Never used Thunderbird.  My email is from a fully external provider that I log in manually, never 'remembered' at the site.  My computer has nothing outside Ubuntu/Firefox, never had, never will, and kept miles away from anything Windows.  Even the search engine I mostly use is duckduck;  not Google.   Paranoic?  Perhaps.

Shows up slightly different at 
----> [https://duckduckgo.com/?q=%3Achrome%2F%2Fglobal%2Fcontent%2Fcustomelements&t=canonical&ia=web](https://duckduckgo.com/?q=%3Achrome%2F%2Fglobal%2Fcontent%2Fcustomelements&t=canonical&ia=web)

Sorry I wasn't clear.  "chrome" is a generic term for window dressings.  Any GUI program has "chrome" - that includes chromium-browser, **Firefox**, a music player, video player ... any GUI program that isn't extremely plain has "chrome".

Since it is a javascript issue, that cuts down the possible programs drastically. Lots of programs use javascript to control their "chrome" - customizations of the GUI.  Firefox is a likely candidate.

As for the original problem ... locks ups aren't always lock ups.  It could be just the Wayland or X11 programs that are locked up.  This can be caused by running out of RAM or a bad driver or bug in the program.  Often, the underlying OS isn't locked up, just the GUI is.  To troubleshoot, if you have ssh setup and another device you can ssh into the Ubuntu machine using, then you can ssh in and look at the driver situation, logs, memory use.

When this sort of thing happened to me previously, it was because I hadn't configured sufficient swap for modern browsers, which are hogs.
After you check the system logs to verify the issue isn't with hardware, looking at the memory situation would be my next step.  
Usually, the system starts slowing down before anything bad really happens. If we notice that soon enough, we can close the application eating all the RAM before it is all used up.

---

### Post by Innernet on 2019-10-14
Thanks.
No clue what is Wayland, X11, ssh.

This being a forum for 'beginners talk', would be good to see detailed instructions to reach the system logs and what to look in them for "looking at the memory situation" , or diagnostics.

The original point is how to stop these unsolicited scripts garbage from intruding, with plenty of spare swap ram or without it.  If "the underlying OS isn't locked up" ; how to recover control?

---

### Post by uRock on 2019-10-14
Please share with us your hardware specs. Are you using Firefox when this happens? Are you using any other app when this happens?

Wayland [https://wiki.ubuntu.com/Wayland](https://wiki.ubuntu.com/Wayland)
X11 [http://manpages.ubuntu.com/manpages/xenial/man1/Xorg.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/Xorg.1.html)
SSH [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by Innernet on 2019-10-14
Thanks for the links, uRock.  Now I just need a brain to understand them.

Plain Compaq CQ57 laptop, 160GB HD, 2GB RAM, 630MB swap, with only Ubuntu 18.04 and Firefox 68.0 in use when trouble shows up, and no other applications beyond simply surfing the web. Not a advanced user, just plain LibreOffice, check email, visit forums on the net.  Very light use. 
The link on post #5 shows similar behavior to other users.

---

### Post by TheFu on 2019-10-14
That is a system low on memory.  Increase the swap to 4G.  More isn't better, but 4G of swap is perfect for a system using a modern browser.
Firefox is huge.
Most email programs are huge too.
LibreOffice is a hog too.  You need to be very careful about over-committing RAM and swap on a system like that. Unix systems don't like it when all the memory is gone. The system will crash.

---

### Post by Innernet on 2019-10-14
Thanks again, TheFu.

Rarely have the browser and LibreOffice open at the same time.  The external email provider is just a website loggedout when done, never left idling on-line for hours.

"Low on memory" because the script that I did not request wants to load and I **should allow** it to load ?   Do you mean I should give up control of my computer to whoever develops, pushes and invades my system with unwanted unsolicited whoknowswhat scripts software ?

It is like buying more memory, upgrading my computer to acommodate receiving trendy garbage. The point is to block the crap I do not want from taking over the memory and halting the system.  Ideally, a way for  blacklisting scripts from loading,..  I wish I knew more about computing and be able to understand and manage these hurdles.

---

### Post by uRock on 2019-10-14
I'm not a browser expert by any means. I googled the error you're getting and though nothing came back matching it exactly, they all seemed to point back to Firefox. I completely understand your frustrations with this. I have a laptop with 4GB RAM and I get messages on it stating that certain webpages are slowing the computer.

On my current machine, I have three tabs open (Facebook, UbuntuForums, and GMail) and System Monitor is showing web content processes taking more than 1GB of RAM.

Do you see this error when on a certain page? If yes, then you might have to stop using the site. If no, then the following list of things may be helpful;

1) In Firefox, go to about:preferences#privacy and clear history and cookies. (This may log you out of some sites.)
If still seeing the error, then;
2) Close Firefox, then go into your home folder and rename the .mozilla folder to .mozilla_old and reopen Firefox. This will bring you back to a "new" Firefox. If then fixes the issue, then you can rename to mozilla folder back to .mozilla and then go into Preferences and export passwords and favorites, then swap the new folder back as being .mozilla and import those two files into the new profile. Let me know if you need more in depth steps, or a screen record, or screenshots on how to do those steps, because I know it can be a bit confusing the first time.

---

### Post by Holger_Gehrke on 2019-10-15
> **Innernet said:**
> 
"Low on memory" because the script that I did not request wants to load and I **should allow** it to load ?   Do you mean I should give up control of my computer to whoever develops, pushes and invades my system with unwanted unsolicited whoknowswhat scripts software ?


Actually, if it **is** Firefox which is the problem, then you **did** request it to run that script. The 'chrome://'-scheme is a way to access **local** resources so it's either a part of the Firefox UI (which is written in a mix of XUL (a markup-language to describe and place UI elements), CSS (to format the elements created through XUL) and JavaScript (to actually react to actions on the elements)) or it's a Firefox add-on. In both cases it was your decision to install and run it (except if it's some kind of stealth-install malware add-on ... don't laugh, I've seen one working a few years ago on a Ubuntu 12.04 machine in the office; it inserted links to ads on keywords in any loaded page ...).  If this happened on my machine I would go through the add-ons carefully and uninstall all non-essential ones and I'd limit the number of content-threads (default is 4, I've been running with 2 for several months now).

And as far as blocking script on websites from executing is concerned, there's an add-on named No-Script which will stop the execution of scripts on a per host basis. It's one my 'essential' add-ons (even though sites I haven't visited before often come up blank; have to allow some scripts on those - either temporarily for the session or permanently (rare ...) - to even see the text of the page). Another 'essential' is an Add-blocker (more than half of all the JavaScript trouble I've encountered was with ads).

Holger

---

### Post by Innernet on 2019-12-09
Hi.
Happening more often, with increased 'swap'
First a yellow strip telling that "a script is slowing down the browser, Do you want to stop it or wait ?" 
Unable to take an image of it, but later shows the following attachment:

[ATTACH=CONFIG]284589[/ATTACH]

Selecting the box "Don't ask me again" means that the dialog will not appear again and will have no warning of the anomaly,
or 
When I next select "stop script" will be remembered every time the anomaly occurs and the script will be stopped "without asking again" ?
or
Selecting "Continue" next will send me to continuing being stuck for the unknown anomaly ?

---

### Post by Frogs Hair on 2019-12-09
What if any extensions/add-ons are you using ?

[https://developer.mozilla.org/en-US/docs/Mozilla/Chrome_Registration](https://developer.mozilla.org/en-US/docs/Mozilla/Chrome_Registration)

---

### Post by Innernet on 2019-12-09
Thanks, Frogs Hair.
Am not conscious of using any.  Running a very lean system with light usage.  But could fetch information on what extensions may be running if you instruct me how to display such.

---

### Post by Frogs Hair on 2019-12-09
Look under addons as in the picture. The error can be caused by a theme, addon, or tool bar element , but there is little information on how to prevent or eliminate it.

---

### Post by Innernet on 2019-12-09
Hi. Thanks.
[ATTACH=CONFIG]284591[/ATTACH]

---

### Post by TheFu on 2019-12-09
if you want a very light browser, dillo is it.  No javascript at all.  It has terrible HTTPS security, so don't use it for buying anything, but if you use mobile versions of websites with dillo, you can usually access the stuff you want with minimal ads and minimal performance issues.

I had a few 2GB systems for a few years - an Asus Eee and an Acer C720. Both would crash after getting slow as the swap was used up.  I bumped the swap to 4G and it never crashed again.  I use ublock origin and NoScript addons in Firefox to limit the bad stuff.  I also block about 130K advertising and tracking websites with a DNS and /etc/hosts settings at the entire-host level.  It isn't perfect, but I find the trade offs worth it. YMMV.
How-to guide that I wrote: [https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279](https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279) in 2011.  Still relevant.

Moved to a 4G laptop which also started crashing due to low memory.    Bumped up my swap partition to 4.1G and the feedback before crashing (system would slow down) let me take action to close big programs using lots of RAM BEFORE any crash happened.  Modern browsers are RAM hogs.  Right now, firefox is using 3.1G of RAM on my current system according to **top**, to the system says only 520MB is actually in RAM.
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           7.7G        2.7G        2.3G        517M        2.7G        4.1G
Swap:          4.5G          0B        4.5G

```
tells a different story.  I'm going to believe the 'free' output.

I also use a few other firefox addons
* tab control on the left - cannot stand top tabs.
* Wallabag - a Read-it-Later clone.
* Play to Kodi ... handy to send video stuff to the TV for playback.
* Ghostery - tracking blocker.

Dillo is probably easier if you dislike javascript.  I use dillo on mass-media websites like cnn.com.

---

### Post by Frogs Hair on 2019-12-09
You could try disabling the gnome shell extension except when needed and see it the error still occurs. Just for your own protection from malicious links and tracking you may want add an adblock  extension of your choice.

---

### Post by Innernet on 2019-12-17
Hi again.
With the shell extension disabled and the swap increased, got the same misbehavior after a while.  Could be something different this time.  Can anyone please confirm this site responds properly ?  If does not, what is it happening ?

[ATTACH=CONFIG]284626[/ATTACH]

---

### Post by Frogs Hair on 2019-12-17
I don't get the same results because I don't know the exact search terms. I do find user manual.wiki
[https://usermanual.wiki/](https://usermanual.wiki/)

---

### Post by Autodave on 2019-12-18
This is probably not going to help, but seeing how that I just "fixed" a laptop with the same condition, give it a try.  This is the first thing that I do with most laptops that I get for repair:

Power down. Remove ALL cables including power cable.  Remove battery.  Let sit for 10 minutes.  Reinstall battery, plug in power cord, boot machine.  See what happens.

---

### Post by Innernet on 2019-12-19
Thanks.
The search terms were ----> mc13156dw data 1993
:(
Clicking on that result, all froze, every time.

---

### Post by Frogs Hair on 2019-12-19
The site did load, but it took forever. I was expecting it to time out . I think it's a web site problem or the data/document being 26 years old took time to load from the data base.

[https://usermanual.wiki/Document/1993MotorolaCommunicationsDeviceData.1891433337/help](https://usermanual.wiki/Document/1993MotorolaCommunicationsDeviceData.1891433337/help)

---

### Post by Innernet on 2020-02-07
After almost two months of good computer behavior, decided to **allow** software updating yesterday, as has proven in the past to obtain smoother/better performance when updates are disabled.
Well today, a GoogleChrome script halted Firefox again, unable to take screenshot as 'camera' froze at **that** moment.

Was unable to close tabs, the pictures show _incorrect prompts_ when the arrow pointer is clicked in both screenshot locations shown
One is supposed to open new tab, the other to restore the 'SanRemo' tab. Nothing responded, wrong prompts. "Show bookmarks ; close tab" at places clicked.

Could take screenshots :
[ATTACH=CONFIG]284983[/ATTACH]
[ATTACH=CONFIG]284984[/ATTACH]

---

### Post by him610 on 2020-02-08
> The search terms were ----> mc13156dw data 1993
I searched the term on both Chrome and Firefox using Google search engine on both. Chrome found it right away; it took a couple of seconds for the page to load. Firefox using Google search found it too, but not as quickly as Chrome; the page load using Firefox+Google search did take longer than than Chrome+Google.  The more often the search term, 'mc13156dw data 1993' is searched, the quicker it will turn up. How quickly that particular webpage loads in your browser depends on external factors - the capability of server and database where that particular page resides, the loading, routing, and speed of the external internet, the constraints of your own router, local network, and computer.
When is the last time you performed a speedtest, [https://www.speedtest.net/]("https://www.speedtest.net/")
I completed a speedtest just now - Download = 50.58 Mbps Upload = 17.90 Mbps. Most days my download speed runs around 90 Mbps.

---

