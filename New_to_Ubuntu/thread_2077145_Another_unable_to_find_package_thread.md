---
title: "Another unable to find package thread"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by TRLOS on 2012-10-27
Hey all, running my first ubuntu system and so far has been working great. I am using it to replace my current streaming server which was on my laptop (this means it was down while i was traveling, defeating its purpose) so enter Ubuntu and as I said. Everythings working.

PROBLEM

My streaming server is Mediatomb >> LAN >> Bubble UpNp Server >> World(aka my phone) Problem is bubble isnt installing properly. I am hoping that this issue is me just being a noob and not a repository issue cause then its a pain to fix. here is a link to the full list of commands used for installation. [Ubuntu Bubble]("http://www.bubblesoftapps.com/bubbleupnpserver/#ubuntu_install")The error I get comes with the last command in the install process:

sudo apt-get install bubbleupnpserver

Error is, E: Unable to locate package bubbleupnpserver

I believe that the cause is coming from this command

sudo apt-get update

Because these are the last 3 lines:

W: Failed to fetch [http://ppa.launchpad.net/bubbleguuum/bubbleupnpserver/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/bubbleguuum/bubbleupnpserver/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bubbleguuum/bubbleupnpserver/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/bubbleguuum/bubbleupnpserver/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

I think this means that the main libraries are missing cause i recognize 404 anywhere.

So the main problem is the E: Unable to locate package bubbleupnpserver

Please help, 
Thanks in advance Trios

---

### Post by newb85 on 2012-10-27
Check this out: [https://launchpad.net/~bubbleguuum/+archive/bubbleupnpserver]("https://launchpad.net/~bubbleguuum/+archive/bubbleupnpserver")
If you click the "Published in" dropdown, you will notice Quantal is missing from the list.  The program hasn't yet been packaged for Quantal and published in this PPA yet.

The last update was only seven weeks ago (the PPA is by no means abandoned), and Quantal has been out less than two weeks.

You may want to contact the PPA maintainer, Michael Pujos, and find out if the PPA will be enabled for Quantal soon.

---

### Post by TRLOS on 2012-10-28
Thanks Mate;

Released update, new error lead me to post about disabling CD-ROM something or other in SSources so the command could get the correct files. Anyways all said and done and my server runs beautifully with BubbleUpNp streaming right to my phone when I am not at Home. Thanks a Bunch Newb!

---

