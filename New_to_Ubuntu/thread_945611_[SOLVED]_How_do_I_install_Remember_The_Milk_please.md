---
title: "[SOLVED] How do I install Remember The Milk please?!"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by pariate on 2008-10-12
Hi all

I hope you've all had decent weekends :)

I can't figure out how to integrate Remember the Milk with Thunderbird in Ubuntu.  I downloaded the installation file, added it to Thunderbird by using Tools-> Add ons-> Extensions-> Install, and then restarted Thunderbird.  When Thunderbird was open again I followed the instructions listed here: [http://www.dailygyan.com/2008/05/remember-milk-provider-extension-for.html]("http://www.dailygyan.com/2008/05/remember-milk-provider-extension-for.html")

But now I'm stuck!  :confused: "Remember the Milk Provider" doesn't show up in the File-> New-> Calendar dialogue box.  I went back to the Thunderbird Add-ons and although RTM is listed, it says "Requires additional items".  Errr... what items?!  :lolflag:  I'm stumped!

Any help will be gratefully received. I'm on Ubuntu 8.04.  Have tried Googling and searching the forums, but to no avail.

Ta very much so.

Katie

---

### Post by jamesrl on 2008-10-12
Have you installed [lightning]("https://addons.mozilla.org/en-US/thunderbird/addon/2313") ([RTM Provider]("https://addons.mozilla.org/en-US/thunderbird/addon/7125") relies on it)?

---

### Post by pariate on 2008-10-13
Yes, I have Lightning.

---

### Post by pariate on 2008-10-13
Thought I should add - Lightning and TBird both working without any apparent problems.

---

### Post by MusicMastaMike on 2008-10-13
Add a new calendar, on the network, then select Remember The Milk and follow the prompts.  After you add it, go to the tasks pane and a confirmation link will show up.

---

### Post by pariate on 2008-10-14
Thank you, but please see my original post and the link contained therein.  I have tried that approach but RTM doesn't show up on the list of available calendars.  My only options are iCalendar or CalDAV.  

Please also the note in my original post about the RTM add-on needing "additional items".

---

### Post by pariate on 2008-10-15
Shameless *bump*...

---

### Post by jamesrl on 2008-10-15
I just tried to install it (I don't use thunderbird by default) and it worked beautifully.  First, installed lightning (have no other extensions/add-ons).  Then I restarted, and installed RTM provider (to download it I had to get thunderbird account, as its experimental with no support provided).  

Went to new calendar -> On my network -> RTM provivder (left location as is), named calendar rtm.  First task was Please Authenticate,
got a link to "http://www.rememberthemilk.com/services/auth/?api_key=3..." clicked the link, which told RTM I gave the thunderbird API permission to access.  Then right-clicked mark as completed and I had access.

More info: Using Thunderbird version 2.0.0.17 (20080925), Lightning 0.9, and RTM Provider 0.0.11

Hmm.   Have you tried running thunderbird starting it from a terminal (and see if you get any extra more detailed error messages in the terminal)?

---

### Post by pariate on 2008-10-15
Thanks for your feedback James :) 

I haven't tried the terminal thing... I am very new to Linux and I have yet to learn how to use the terminal effectively!  I've tried some of the simpler commands but all I can really do is copy instructions.  

I wonder if perhaps it's the version of Lightning that I'm using.  I'm on 0.7 because 0.9 doesn't work very well for me.  It installs but I can't actually view the calendar!  I feel silly for not having thought of this before.  Ah well, I might give 0.9 another go and then try again with RTM.

Thank you again!

---

### Post by jamesrl on 2008-10-15
To run thunderbird from the terminal, just start it the terminal up (e.g., [Alt-F2] gnome-terminal), and type thunderbird (and some messages get written to the terminal).  You actually only have to type a little bit e.g. like thun and then press tab and it auto completes if its the only option.  If you type

```
 thunderbird &
```
then it will still send messages to the terminal from the program, but you can type more commands (as its running in the background).

---

### Post by Ninj on 2009-12-09
Hi.

I may have missed something, but although this thread is marked as "solved", i can't figure out what the solution is... to me, the last tries were "updating to ligthning 0.9" (which i have, actually), and lauching from console.

No any feedback about these solutions, and I'm still having the same problem :(

Any idea ?

---

