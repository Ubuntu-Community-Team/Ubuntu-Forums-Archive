---
title: "GPG error: http://ppa.launchpad.net hardy Release"
date: 2010-05-26
forum: Repositories &amp; Backports
---

### Post by mystika1 on 2010-05-26
Hi,
I am getting the following message  when I update. 
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6

Please advise.

Penny

---

### Post by bornagainpenguin on 2010-05-26
No advice, but I am also seeing this now, albeit with a different public key.

**EDIT--** The advice found [here](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/58435) was useful in fixing my problem, just substitute the missing key listed in the error message with the one in the advice in the post by pichet on 2009-01-22!

--bornagainpenguin

---

### Post by srk9 on 2011-03-09
**[SIZE=2]I had the same issue after I set up a PPA in launchpad for development and added it to my source list. The fix is simple, follow these instructions:[/SIZE]**

[SIZE=2][/SIZE][SIZE=2]YOU WANT to use:

sudo add-apt-repository ppa:<some_user>/<some_ppa_name>

[SIZE=2]You DON'T WANT TO use the url to the PPA:
sudo add-apt-repository[/SIZE][[SIZE=2] [/SIZE]http://ppa.launchpad.net/<some_user>/ppa-<some_ppa_name>/ubuntu)]("http://ppa.launchpad.net/srk9/ppa-srk9-open-source/ubuntu")

Now try:

sudo apt-get update
sudo apt-get upgrade

Hope this helps[/SIZE]

---

