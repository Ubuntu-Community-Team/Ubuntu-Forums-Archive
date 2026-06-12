---
title: "Firefox not remembering application preferences"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by browny254 on 2008-06-26
I was wondering if anyone knows how to get Firefox to automatically download things and open a certain program, ie when downloading a torrent automatically starts ktorrent. I have the box ticked to do this and when you select to do it it says if you want to change preferences in the future go to Edit -> Preferences -> Applications, but all I get there is a blank screen. So currently every time I download something I have to search for where the program is located (ie for torrents /usr/bin/ktorrent) which is a pain.

also once things have already downloaded and they stay in the firefox download manager, if i try to open it from there, it trys to open everything with Kpdf, meaning that I cant just select things to open and save in a temp file rather than select a download location because I cant open it later without having to navigate to wherever the temp file is.

i hope that made sense...its really starting to frustrate me and my thinking suffers then :P

---

### Post by aysiu on 2008-06-26
Well, there are potentially two problems here. One is that you may have somehow (particularly if you've ever run the command *sudo firefox*, which you should never run) changed ownership of your Firefox settings folder. The other is that your Firefox profile may have become corrupted for some strange reason or through conflicting extensions.

To make sure you have ownership of your Firefox settings, type this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username*:*username* /home/*username*/.mozilla
``` where *username* is your actual username. Then restart Firefox (close it completely, then start it again).

If that doesn't fix the problem, close Firefox completely and paste this command in the terminal: ```
firefox --profilemanager &
``` and create a new test profile and see if you still get the blank window.

---

### Post by browny254 on 2008-06-26
ok that first step fixed the remembering the program (for torrents at least) but the application tab still contains nothing and loading a .doc file from the download manager still tryed to do it in kpdf. after creating a new profile nothing changed.

i should also clear up, the window inst blank, it just contains nothing. I can see 2 columns, content type and action, but there is nothing listed there. I would expect it would contain any extensions or whatever I come accross and list them there with the application I choose to use, so just from the past 5 minutes doing this there should be .torrent and .doc listed there at least.

---

### Post by aysiu on 2008-06-27
I think it won't fill in unless you actually trying to open or download a file of that type, at which point Firefox should ask you what you want to do with the file. If you say "Always do this," then it should appear. Maybe I'm wrong.

---

### Post by browny254 on 2008-06-27
yeah thats what Im trying to say it isnt doing. So everytime I try to download something I have to select the program I want to use. I used that torrent example earlier but another one if for .doc files, firefox comes up with SOffice - which I dont even have, and I have to either download to a certain location and open the file from there, or browse through /usr/bin/ till i find openoffice...or whatever I am trying to do.

I have been using firefox 3 since one of the early gran paradiso versions and its always happened, its just now I decided to try and do something about it.

---

### Post by stek79 on 2008-06-27
Hi,

I have the same problem with Firefox 3. Firefox 2 also had this issue, at least I noticed it.

What happens is that I tell FF to remember the application association, for example Mplayer to open WMV files. Then I open some files, and it opes Mplayer correctly.

After a bit of web surfing, the association disappear and FF keeps asking me what application it should use. And, notice, in this popup the checkbox "remenber" is already turned on!

Any other with this problem???

---

### Post by 1/0 on 2008-08-22
Firefox would just download all torrent files for me. I solved this by removing all sections containing torrent in the file: .mozilla/firefox/12345678.default/mimeTypes.rdf (adjust the profilename). Also make sure you delete the whole section that contains torrent. Start at *<RDF:Description...* until either */>* or *</RDF:Description>*. Make a backup of the file just to be sure if you do anything wrong.

---

### Post by stek79 on 2008-08-22
> **1/0 said:**
> Firefox would just download all torrent files for me. I solved this by removing all sections containing torrent in the file: .mozilla/firefox/12345678.default/mimeTypes.rdf (adjust the profilename). Also make sure you delete the whole section that contains torrent. Start at *<RDF:Description...* until either */>* or *</RDF:Description>*. Make a backup of the file just to be sure if you do anything wrong.

Thanks! I'll certainly try your suggestion!

---

### Post by 1/0 on 2008-08-27
Hope it works for you!

---

### Post by algorhythm on 2008-08-28
I/O post #7: Thankyou for this -- so simple, yet because firefox normally works so well I forgot to try and hack it up... I would just add that depending on what you want firefox to do, the mimeTypes file is fairly self-explanatory and it may not be necessary to delete an entire section (in my case I found the pdf section and changed AlwaysAsk to "true", rather than changing the whole thing)

---

### Post by 1/0 on 2008-08-28
> **algorhythm said:**
> it may not be necessary to delete an entire section (in my case I found the pdf section and changed AlwaysAsk to "true", rather than changing the whole thing)

Glad I could help. Looks like I got something out of this too.

---

### Post by bartek on 2008-09-10
Any other suggestions? My FF never remembers ANY application preferences - Edit > Preferences > Applications is always blank, .mozilla/mimeTypes.rdf has proper apps listed. 

Build:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

---

### Post by stek79 on 2008-09-10
Please report your experience in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/243704](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/243704)

Currently it is still in undecided status, we need to keep our voice adding user reports there, so that the bug will gain importance.

Thanks

---

