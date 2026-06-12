---
title: "Manual Install Firefox Updates?"
date: 2015-05-04
forum: New to Ubuntu
---

### Post by ken0069 on 2015-05-04
I posted this in the newbie section as it’s something I probably should have learned myself 6 years ago when I first ran Ubuntu 9.04.  I thought maybe others might want to learn this also.  If this thread needs to be somewhere else, then please move it to the correct forum.

Anyway, I’ve got a problem with my internet connection that’s been going on now since August of 2013.  There is a thread or two on here where I’ve mentioned this in the past.  I go though spells where it won’t complete an http: download no matter how many time I try it and since I’m on a mobile broadband data plan my bytes are limited and not to be wasted on half a download that will never complete.  I’ve done work arounds on other downloads by doing them via FTP where possible and also I have a friend that allows me to do some large downloads on his DSL connection from time to time.  

That brings me to Ubuntu/Mate and Mint/Mate as I have the same problems with those as well but more specifically with updates to Firefox, which seems to come out about twice a month.  Upgrading Firefox results in the same incomplete downloads and more often than not they pretty much all stop at the same % even though I’ve tried using different update servers for that download?

So all this brings me to a need to be able to do those updates via a Firefox update file I’ve downloaded via FTP from Mozilla.  And yes, those downloads usually fail at some point also but Filezilla will reconnect and resume so I don’t loose what’s already been downloaded and it will complete it.  

Is there some kind soul on here that can walk me through the steps of doing a manual install of Firefox in Terminal or point me to a thread that will show me how to do this, and keep in mind that I’m somewhat command line challenged?  I’ve got 3 systems here that I need to do that on and probably should have learned this a long time ago, but I didn’t.

Any help?

Thanks,

Ken

---

### Post by haplorrhine on 2015-05-04
If it's 4G, a 4G antenna might help.

---

### Post by Keith_Helms on 2015-05-04
If you've downloaded the tar.bz file containing Firefox from mozilla, then installing it is just a matter of extracting the archived files into a directory somewhere.  Start archive manager and open the downloading file with it.  You should see a single directory named firefox.   Have archive manager extract that directory somewhere, such as into your home directory.  Once that's done, you can open a terminal window, change into that firefox directory, and just type ./firefox to run it.  I'd recommend setting up a launcher instead of doing that manually, but if you're on plain vanilla unity that is a little difficult.  Search for "create launcher unity" and you'll find instructions under some thread.

Verify you're actually running the version you downloaded by selecting help, then about firefox.   If it says mozilla firefox for ubuntu canonical, you're still running the repository version.  If not, you're running your downloaded version.  Once you've verified that, I'd uninstall the version from the repository using apt or synaptic so that ubuntu no longer tries to update it.

At that point it's up to you to track new firefox releases and install them.  You could just run the version you have and ignore new releases, but that would increase your risk from any new security threats.

I agree with you that updates to Firefox (and Thunderbird) are both huge and often.  I don't know why they can't just update pieces of it, like a library, instead of the whole thing.   Maybe it's because they increase the version number everytime they do anything.

---

### Post by ken0069 on 2015-05-05
[COLOR=#000000]Just found out that FF v38 will be released on May 12th so I'm going to just wait to do this with that version. 

To be continued:
[/COLOR]
Thanks

Ken

---

