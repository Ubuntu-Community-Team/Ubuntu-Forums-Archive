---
title: "Red warning triangle; what does it mean?"
date: 2014-06-13
forum: New to Ubuntu
---

### Post by Mike_Walsh on 2014-06-13
Evening all.

I've been quite happily using Trusty Tahr for the last 3-4 weeks, and it's been behaving faultlessly.

Earlier on today, I noticed a red warning triangle on the taskbar, which upon clicking, declared that my "update information is out dated. Please update manually by selecting 'Show Updates' from the indicator menu, and watch for failing repositories..."

I've followed the instructions, and all my software is bang up to date. It disappeared for a couple of hours, but now it's back.

Can anyone enlighten me as to what may, or may not, be going on, please?

Mike Walsh.

---

### Post by Bucky Ball on 2014-06-13
You may have it set to alert you for updates once a day. Check in Software Sources (or you can open the Update Manager, click the Settings button) under the Updates tab. Down the bottom it should be set for weekly, not daily (or whatever suits you).

To get it completely up to date, open a terminal and issue these three commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... if you haven't already. This will NOT upgrade the release to a newer one. Post any errors.

---

### Post by kansasnoob on 2014-06-13
Open the terminal and run:

```
sudo apt-get update
```

Then look for any errors, or post the full output here.

---

### Post by Mike_Walsh on 2014-06-13
Hi, Bucky Ball.

Yes you're quite right; I did have the update checks set for daily, rather than weekly.

I've applied those three commands; this was at the end of the first one.

W: GPG error: [http://liveusb.info](http://liveusb.info) all Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4E940D7FDD7FB8CC
W: Failed to fetch [http://ppa.launchpad.net/faster3ck/converseen/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/faster3ck/converseen/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/faster3ck/converseen/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/faster3ck/converseen/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://liveusb.info/multisystem/depot/dists/all/hand/binary-amd64/Packages](http://liveusb.info/multisystem/depot/dists/all/hand/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://liveusb.info/multisystem/depot/dists/all/hand/binary-i386/Packages](http://liveusb.info/multisystem/depot/dists/all/hand/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 


Second one went through without any fuss.

Third one, just this little bit at the end:-


The following package was automatically installed and is no longer required:
  libsensors4:i386
Use 'apt-get autoremove' to remove it.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
paul@paul-EK335AA-ABU-SR1619UK-GB540:~$ 



And that's it. However, I think you've cracked it for me, guys; the triangle has GONE.

Easy to tell us noobs, ain't it? (And this from somebody who's been playing about with these things since the days of the Commodore 64 and the Sinclair ZX81; jeez, I am SO embarrassed!)

Fancy making a basic error like that...

Still, it took me years to refine and adapt Windows systems to my personal requirements; I feel like I'm back at school again!

Cheers, guys..!

Mike

ps By the way, what does the 'sudo apt-get dist-upgrade' command do?

---

### Post by Elfy on 2014-06-13
The error will come back.

I checked the first ppa - [http://ppa.launchpad.net/faster3ck/converseen/ubuntu/dists/](http://ppa.launchpad.net/faster3ck/converseen/ubuntu/dists/) if you go there you'll see that it's not actually available for trusty

The third - no [http://liveusb.info/multisystem/depot/dists/all/hand/](http://liveusb.info/multisystem/depot/dists/all/hand/) there 

You can remove these from Software Sources - or you can manually remove the files relating to them from /etc/apt/sources.list.d/ 

You shouldn't get any errors showing up when running apt-get update

---

### Post by Mike_Walsh on 2014-06-13
Yep, you're absolutely right. The triangle IS back.

The menu attached to it says it may be caused by 'network problems, or a repository that is no longer available'; sounds like just what you've told me. (I know for a fact there's nothing wrong with my network...)

So...

What would be the best way to go about removing them Software Sources? Remember, I'm VERY much a beginner with the terminal!

Mike.

---

### Post by monkeybrain20122 on 2014-06-13
For the third one (multisystem), replace 'hand' in the end with 'main'  (no quotes) and it will work.

---

### Post by Bucky Ball on 2014-06-13
As Elfy said, if you open your Software Sources (Software Updater>Settings>Other Software) and untick or remove the offending repositories (the ones showing the error at then end of the update command) it should go away permanently. 

You could edit the 'multisystem' one, as suggested by monkeybrain20122 (in same place as above by clicking 'Edit'), and see if that fixes that one, but if not, untick or remove.

---

### Post by monkeybrain20122 on 2014-06-13
Well here is an easy way to edit/remove ppa. Open Sofware & Updates (either search in the dash or find it in the menu, depending on the DE)  Go to "Other Software", find the ppas in question, right click and choose either "remove" or "edit".

---

### Post by Bucky Ball on 2014-06-13
> **monkeybrain20122 said:**
> Well here is an easy way to edit/remove ppa. Open Sofware & Updates (either search in the dash or find it in the menu, depending on the DE)  Go to "Other Software", find the ppas in question, right click and choose either "remove" or "edit".

Erm, I've said that two posts ago ... :-k

---

### Post by Mike_Walsh on 2014-06-14
Well, thanks for all your help, guys.

I've now edited the offending software sources from the list in the Software Updater (last night, in fact!), and the triangle has disappeared...and STAYED disappeared.

Thanks Bucky Ball, monkeybrain, Elfy, and others, for your suggestions and advice; taken in combination, we've sussed it.

I'll mark this as solved.

Cheers, guys!!

Mike.

---

