---
title: "HOWTO: Firefox mailto w/ Thunderbird"
date: 2005-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by ming0 on 2005-03-27
Some people have problems using mailto links with Thunderbird. To fix the  "choose user profile" problem, follow this howto.
[b]
Method 1:[/b] [b]

THUNDERBIRD: Open with firefox an URL contained in an email
[/b] 
 1.) Open Nautilus and type this in the address bar:** ~/.thunderbird **(if that doesn't work, try **~/.mozilla-thunderbird**)

 2.) **Go your profile directory** (with a random-generated name, like this **Xbcgev.default**). To be sure you're in the correct directory check if a file named **prefs.js** exists.

 3.) **File > Create Document > Empty Document ** highlight it and press **F2** to rename the document **user.js** (If it already exists skip this passage).

 4.) Open **user.js** and write this line (if the file already exists append the line at the end): **user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");**
 /usr/bin/firefox is obviously the path to execute firefox
 
 5.) **That's all**
 
** FIREFOX: open thunderbird when clicking on a "mailto:" link**
 
 1.)  1.) Open Nautilus and type this in the address bar:** ~/.mozilla/firefox **(if that doesn't work, try **~/.mozilla-thunderbird**)

 2.) **Go your profile directory** (with a random-generated name, like this **Xbcgev.default**). To be sure you're in the correct directory check if a file named **prefs.js** exists.

 3.) **File > Create Document > Empty Document ** highlight it and press **F2** to rename the document **user.js** (If it already exists skip this passage).

 4.) Open **user.js** and write this line (if the file already exists append the line at the end):  **user_pref("network.protocol-handler.app.mailto","/usr/bin/mozilla-thunderbird");**
/usr/bin/mozilla-thunderbird is the path to execute thunderbird
  
  5.) [b]That's all

[/b][b]
Method 2: [/b](might be dangerous)

**(please back your original TB copy up--some people have had problems with this hack)**:
      
 1.) Type: **about:config** into the firefox  address bar (press ctrl + T for a new tab)
  
 2.) Right click and choose: **New>String**
 
 3.) In "new string value" box type:  **network.protocol-handler.app.mailto** click OK
  
  4.) In "enter string value" box enter: **/usr/bin/mozilla-thunderbird** click OK
 
5.) Open a terminal and use this command: **sudo cp /usr/bin/mozilla-thunderbird /usr/bin/mozilla-thunderbird.bak** (this is our backup in case anything goes haywire)

6.) Now use the following command: [b]sudo gedit /usr/bin/mozilla-thunderbird

[/b]7.) Press **Ctrl + R**. In the Search For box, type: **Mozilla-Thunderbird**. In the Replace with box type: **mozilla-thunderbird**. Press **Alt + M**, then **Alt + A**, then **Alt + C**, then **Ctrl + S**, then **Alt + F4**.
 
 7.) Reset Firefox and try the [email="test@test.com"]mailto[/email] link (it should work while TB is on or off)
[size=1]
Note: This is a dirty dirty hack--PM me if you have a more failsafe method, and I'll edit it in :)
Note 2: If you have problems w/ the script, post here, so I know what is going wrong.
[/size]

---

### Post by Technoviking on 2005-03-27
It does not seem to work for me? Hmmm....

---

### Post by ming0 on 2005-03-27
So you get everything done, and it still doesn't work? What happens? The one thing I would try is re-selecting the entire script, and making sure you didn't accidentally miss part of it--then re-copy it into the file w/ gedit. (maybe just try the entire process one more time to be sure)

I tried these steps on my laptop, and it worked just the same... I installed Warty during X-mas and immediately upgraded to Hoary. I think I'm using the firefox backport. 

You might try the [extension]("http://www.extensionsmirror.nl/index.php?showtopic=70&hl=mozex") instead of the about:config.

Let us know what works, and how it goes.

---

### Post by Silwenae on 2005-03-27
Worked perfectly for me, thank you!

---

### Post by Technoviking on 2005-03-27
I rebuilt the script again with gedit, and had no luck. I switch to emacs and it worked fine. Go figure.

Mike

---

### Post by Xeon3D on 2005-03-30
Worked Wonders!

5*****

---

### Post by ming0 on 2005-03-30
[QUOTE=Mike Basinger]I rebuilt the script again with gedit, and had no luck. I switch to emacs and it worked fine. Go figure.[/QUOTE]
Very strange indeed?? The only thing I can really think of is that maybe there needs to be an extra space down at the bottom of the page (I think that some languages and scripts complain when a file ends with no blank space), but I don't know if bash is one of them.

---

### Post by Georges on 2005-04-09
I just thought that the thunderbird scripts are braindead buggy!

I changed the following:

edit /usr/bin/mozilla-thunderbird

and replace every occurence of Mozilla-Thunderbird with mozilla-thunderbird
then it works much better, no need to create a separate script.

I have the following in about:config
network.protocol-handler.app.mailto   user-set   string    /usr/bin/mozilla-thunderbird

Yes, that's all!

Why I did that? Because some bugzilla entries gave me the idea that the script is wrong:
[https://bugzilla.mozilla.org/show_bug.cgi?id=259305](https://bugzilla.mozilla.org/show_bug.cgi?id=259305) 
[https://bugzilla.mozilla.org/show_bug.cgi?id=244060](https://bugzilla.mozilla.org/show_bug.cgi?id=244060)

Now how do we get that correction back into ubuntu, debian and even perhaps mozilla?

At least it's posted here, so ubuntu rules more :-)
Georges

---

### Post by Trickyphillips on 2005-04-09
Works in Mozilla too. 8-)

---

### Post by ming0 on 2005-04-09
[QUOTE=Georges]edit /usr/bin/mozilla-thunderbird

and replace every occurence of Mozilla-Thunderbird with mozilla-thunderbird[/QUOTE]

Good work! Thanks for sharing--I'll adjust the howto!

---

### Post by raid517 on 2005-04-17
Thanks, that worked - I had to reinstall Thunderbird though. But the question now is, how do I go the other way? If I click on a link in thunderbird, how do I get it to launch firefox and visit that address?

GJ

---

### Post by ming0 on 2005-04-17
it 'just works' for me... 

is firefox your default browser? (system>preferences>prefered app)

---

### Post by raid517 on 2005-04-17
Well it doesn't for me. But anyway I found a solution that should help complete your guide.

THUNDERBIRD: Open with firefox an URL contained in an email

1.Go to the .thunderbird directory in your home directory (it is usually an hidden directory like /home/user/.thunderbird)
2.Go your profile directory (with a random-generated name, like this Xbcgev.default). To be sure u're in the correct directory check if a file named "prefs.js" exists.
3. Create an empty file called "user.js". (If it already exists skip this passage)
4. Open "user.js" and write this line (if the file already exists append the line at the end):
Quote:
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox/firefox");


/usr/bin/firefox/firefox is obviously the path to execute firefox

5.That's all


FIREFOX: open thunderbird when clicking on a "mailto:" link

1.Go to the .mozilla directory in your home directory (it is usually a hidden directory like /home/user/.mozilla or /home/user/.mozilla/firefox)
2.Go your firefox profile directory (with a random-generated name, like this Xbcgev.default). To be sure u're in the correct directory check if a file named "prefs.js" exists.
3. Create an empty file called "user.js". (If it already exists skip this passage)
4. Open "user.js" and write this line (if the file already exists append the line at the end):

Quote:
user_pref("network.protocol-handler.app.mailto","/usr/bin/thunderbird/thunderbird");


/usr/bin/thunderird/thunderbird is the path to execute thunderbird

5.That's all

This is for those who find that the first method didn't work.

You may have to adjust the path of your executables for their real locations (e.g. Firefox for me can be found at /usr/lib/mozilla-firefox/firefox) but other than that you should be fine. Also this method should survive a firefox or thunderbird upgrade.

I hope this helps.

GJ

---

### Post by remmelt on 2005-04-18
this doesn't work for me.
I have set the network.protocol-handler.app.mailto to /usr/bin/mozilla-thunderbird in FF, and sed'd the original Thunderbird to the lowercase thunderbird.

Problem is, now I can't start up thunderbird anymore! It tells me it encounters an unexpected and of file, on line 275.

After looking in to it some more, the sed didn't seem to work just right... Thank god for backups, eh? Now I sedded the backup to the original name and all is well.

(edit)
On my other machine as well, same problem. The cat|sed cut the file at 8192 KB... Weird happenings.

---

### Post by raid517 on 2005-04-18
That is what happend to me, which is why I posted this alternative (and apparently safer) method. If for some strange reason it doesn't work, just delete the files you created. Nonetheless it is useful to have a choice.

GJ

---

### Post by marsopia on 2005-05-06
Worked for me Thanks!!

Mariano

---

### Post by crazybill on 2005-05-07
Thanks for this tutorial

---

### Post by KillerKiwi on 2005-06-04
A better fix (my opinion), seems like there are some typos in the mozilla-thunderbird script

edit the file 

```
sudo gedit /usr/bin/mozilla-thunderbird
```

Replace all '*Mozilla-Thunderbird*' with '*mozilla-thunderbird*'

Save

---

### Post by searles on 2006-03-13
Hi, I tried all, from prefs.js to KContol to preferred application in gnome, but the solution I did not think of is mentioned in this url: [http://gnuru.org/?node_id=941]("http://gnuru.org/?node_id=941"). 

Check what is your defaultbrowser using 

"$ update-alternatives --display x-www-browser"
and change it if it points to a different browser.

"$ sudo update-alternatives --config x-www-browser"

Worked perfectly for me.

Regards

---

### Post by henriquemaia on 2006-05-21
Very useful. I followed this guide since Evolution was refusing to start when I clicked a mailto link on Firefox. Now everything is working great.

Thanks.

---

### Post by vestgarden on 2007-05-23
Great how to :p , what baffles me though as a newbie is why this hasn't been fixed by the Firefox / Thunderbird teams yet. It's over two years since you started this thread :( . But anyways great fix.

Thanks John

---

### Post by Debord on 2007-08-23
**Opera **as a webrowser to open mailto (in a email writebox) in thunderbird:

In Opera, go to Tools -> Preferences -> Advanced ->
Programs, and select "Use specific e-mail client":

$PATH/thunderbird -compose mailto:"%t"

or only :
mozilla-thunderbird -compose mailto:"%t"

**Mozilla- thunderbird **as an email-client to open links (in a new page) in Opera:

In Mozilla-thunderbird go to  Tools ->  Advanced -> Configurationeditor
(you are now in *about:config* for mozilla-thunderbird)

**find for ftp:**
network.protocol-handler.app.ftp

click on it and change to:
*~/.mozilla-thunderbird/opera-thunderbird.sh*

**find for http:**
network.protocol-handler.app.http

click on it and change to:
*~/.mozilla-thunderbird/opera-thunderbird.sh*

**find for https:**
network.protocol-handler.app.https

click on it and change to:
*~/.mozilla-thunderbird/opera-thunderbird.sh*

Go to your home folder (have to show hidden files) and go then in to the folder:
 ** .**mozilla-thunderbird

Make a new textfile and name it:
opera-thunderbird.sh

Open the file and insert text:
*#!/bin/bash*
*exec opera -newpage "$@"*

Save the file. Change the file to bee exuteble (rightclick - > securitytab-> make file exutable box).

Done! 
:guitar:

That combination rocks!

(excuse my bad english, I am from sweden)

---

### Post by BigDoug on 2007-11-23
I'm a desktop Ubuntu user, an average Joe, learning Linux, not a guru, not a qualified hacker, so perhaps someone more experienced may be kind enough to correct any errors here. 
 
After installing Swiftweasel the browser would no longer open “mailto:” links by launching Thunderbird. Firefox developed the same problem. 
It may not be from installing Swiftweasel, because various forums report this problem with Firefox and Thunderbird not working together with mailto links in websites after updates. 
 
At some point my /usr/bin/mozilla-thunderbird was changed to /usr/bin/thunderbird (a link to a script in /usr/lib/thunderbird/thunderbird). So first check /usr/bin and if you only have thunderbird and mozilla (which links to the script /usr/local/bin/swiftweasel32 – hence my hunch that this problem developed when installing Swiftweasel)there, and not mozilla-thunderbird, this may help. The more complex solutions suggested in various forums may not be needed and did not work for me. 
 
I run Ubuntu 7.10 Gutsy Gibbon 64-bit with 32-bit Firefox, and now, joyfully, Swiftweasel, its soooo much faster. 
 
Here is the technique I used to make mailto links point from Swiftweasel and Firefox to Thunderbird – it is in part borrowed from fixes reported in various forums, including this one.
 
1) Launch Swiftweasel or Firefox and view the configuration strings using the URL 
about:config 
 
2) using the field at the top, search for 
mailto 
 
3) If you do NOT have network.protocol-handler.app.mailto (normally 
you don't), create it using these steps: 
a) right-click 
b) choose New --> String 
c) new string: network.protocol-handler.app.mailto 
d) new value: /usr/bin/thunderbird 
 
4) If you already see an entry for 
network.protocol-handler.app.mailto, verify the path to the mail 
client. Double click the string to set it if necessary. Also be sure 
network.protocol-handler.external.mailto is set to true 
 
5) Do the same in Firefox. Voila! website links mailto: now launch Thunderbird. 

Does anyone know if this was an update problem or a byproduct of the Swiftweasel installation? Or am I way off the mark?.

---

### Post by tsnj on 2008-01-20
Recently replaced 64 bit Ubuntu Feisty with 32 bit Kubuntu Gutsy.  Kept the same firefox and thunderbird profiles.  Mailto links stopped working in firefox, but links in thunderbird work fine.

In firefox, I opened about:config, searched for mailto: and changed the path to reflect my system.  WAS: /usr/bin/mozilla-thunderbird, NOW: /usr/bin/thunderbird.

Everything works ok now.

---

### Post by r0g on 2008-09-11
If anyone's wondering how to get Firefox 3 circa Hardy Heron (8.04) to recognise Thunderbird as the default mail client it's thankfully much simpler than it was back when this thread started! Just follow these 3 easy steps...

1. In Firefox go to Edit/Preferences/Applications/Mailto/Use Other
2. Enter the path to Thunderbird. For me this is /usr/bin/thunderbird
3. Profit!


Roger Heathcote - [http://movingtoubuntu.technicalbloke.com](http://movingtoubuntu.technicalbloke.com)

---

### Post by stevemds0210 on 2009-01-28
Thanks BigDoug. This is an awesome thread. I was a little hesitant to create a new config option in FF from a message more than 3 years old.

It's great that this thread has kept going to keep the info up to date.

Adding a new config option to FF in order for it to open a mail client is a little esoteric for such a common functionality.

---

### Post by buzzbo on 2009-04-28
> **r0g said:**
> If anyone's wondering how to get Firefox 3 circa Hardy Heron (8.04) to recognise Thunderbird as the default mail client it's thankfully much simpler than it was back when this thread started! Just follow these 3 easy steps...

1. In Firefox go to Edit/Preferences/Applications/Mailto/Use Other
2. Enter the path to Thunderbird. For me this is /usr/bin/thunderbird
3. Profit!


Roger Heathcote - [http://movingtoubuntu.technicalbloke.com](http://movingtoubuntu.technicalbloke.com)

This worked for me.  Thanks!
Buzz

---

### Post by eudemus on 2009-06-04
If you've upgraded from Firefox 2 to Firefox 3, the above may not work. But if so, the following might.

Check out this thread
[http://ubuntuforums.org/showthread.php?t=860010&page=2](http://ubuntuforums.org/showthread.php?t=860010&page=2)

Worked for me when nothing else did.
Basically Firefox 3 doesn't use this "network.protocol-handler.app.mailto" thing any more, but if you've upgraded from Firefox 2, you'll have a load of config data set up for it, which seems to confuse Firefox.

Anyway, that thread tells you how to sort it out.
Cheers,
Eudemus

---

### Post by fermulator on 2009-10-18
CORRECTION:
> 
FIREFOX: open thunderbird when clicking on a "mailto:" link

1.) 1.) Open Nautilus and type this in the address bar: ~/.mozilla/firefox (if that doesn't work, try ~/.mozilla-thunderbird)

Should read:
> 
FIREFOX: open thunderbird when clicking on a "mailto:" link

1.) 1.) Open Nautilus and type this in the address bar: ~/.mozilla/firefox

i.e. firefox is always in ".mozilla/firefox", and definitely not in mozilla-thunderbird.

---

### Post by gimmickless on 2010-04-11
Buzzbo's solution works for me.  I run Firefox 3.5.

---

