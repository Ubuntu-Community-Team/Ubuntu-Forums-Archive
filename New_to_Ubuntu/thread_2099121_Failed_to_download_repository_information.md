---
title: "Failed to download repository information"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by Nozza1990 on 2012-12-28
Hi,

After not turning my laptop on over Christmas I turned it on yesterday and tried to update it however when i click "Check" I get this message:

"Failed to download repository information

Check your Internet connection.

W:Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.200 80]
, W:Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.200 80]
, W:Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.200 80]
, W:Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.200 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead."

I'm presuming the internet connection is fine as the internet is running quite happily at the same time I try to update.

I've read the various other posts regarding this but i can't find this in the software sources to turn off and would rather not doing anything with it in case I screw up my laptop (the archive seeming to be from GB ubuntu has me worried).

Any help would be appreciated, thanks

---

### Post by bodhi.zazen on 2012-12-28
Edit - I see you are on an old release

You need to update your sources to point to old-release

[http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

In your case, 

[http://old-releases.ubuntu.com/ubuntu/dists/maverick-backports/](http://old-releases.ubuntu.com/ubuntu/dists/maverick-backports/)
[http://old-releases.ubuntu.com/ubuntu/dists/maverick-proposed/](http://old-releases.ubuntu.com/ubuntu/dists/maverick-proposed/)
[http://old-releases.ubuntu.com/ubuntu/dists/maverick-security/](http://old-releases.ubuntu.com/ubuntu/dists/maverick-security/)
[http://old-releases.ubuntu.com/ubuntu/dists/maverick-updates/](http://old-releases.ubuntu.com/ubuntu/dists/maverick-updates/)
[http://old-releases.ubuntu.com/ubuntu/dists/maverick/](http://old-releases.ubuntu.com/ubuntu/dists/maverick/)

See also

[http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/](http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/)

Of course, maverick is beyond end of life, so no longer supported, and no further updates are anticipated. I would highly suggest running a newer supported version of Ubuntu if at all possible.

---

### Post by Nozza1990 on 2012-12-28
Thank you for your help so far especially finding the specific updates, however I'm afraid I'm still lost at sea! I'm afraid I don't have a great deal of understanding for all this typing into command lines etc I've read about for instance.

When I open the links I get a list of stuff what am I supposed to do then? I've tried opening them and it's a long list of random text or more files so I'm confused again!

Also I thought I was on the newest version of Ubuntu? Does it not automatically update through update manager?

Sorry to be such a dunce!

---

### Post by Bucky Ball on 2012-12-28
Nope. Update updates apps and everything else, but not the release. That would be not good. An upgrade command in the terminal upgrades any packages that need to be upgraded, not the release. 

If you want to upgrade to another release you need to do that manually or reinstall. 10.04 LTS is supported until April 2013, 12.04 LTS until 2017. Support for Maverick ended in April this year and, personally, I would move on ...

Out of support releases do not receive security updates and can leave your system vulnerable to compromise.

---

### Post by ibjsb4 on 2012-12-28
Hi Nozza1990

Looks to me that your in a bit of a fix.  You can do what bodhi.zazen suggested, but your still on an outdated release and the next release (Natty 11.04) after yours also reached its end of life in October of this year, so you cannot easily upgrade.

I would suggest a fresh install of 12.04.  I has support for five years if you do not wish to upgrade for a while.  However there may be a few problems with this.  Ubuntu has changed quite a bit and looks nothing like what your running right now and requires more resources which your box may not have.

So what are your computer specs?  You may need to switch to Xubuntu which is similar in looks to what your now running and does not require as much resources as Ubuntu.

You could download both live CD's and try them out before installing.

If you decide to do this you will need to backup all your personal data so it can be reinstalled on the new release.

Just my thoughts  :)

[http://www.ubuntu.com/](http://www.ubuntu.com/)

[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by Nozza1990 on 2012-12-29
Ok thanks for all your help here. I'll try putting on the latest version of Ubuntu after backing up everything and see how I get on.

I did notice when I logged on this morning however that when asked for my password my laptop currently says Ubuntu 12.04 LTS in the bottom left corner so I don't know if it will work.

Wish me luck

---

### Post by Nozza1990 on 2012-12-29
Just changed to Ubuntu 12.10 and updated everything fine :-) Thanks

---

### Post by ibjsb4 on 2012-12-29
Congrads and welcome to the forums  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Bucky Ball on 2012-12-30
Please mark as Solved (if it is) from Thread Tools to help others ...

Good luck. ;)

---

### Post by chaalzz on 2012-12-30
Thanks a ton. This helped me as well.

I was really confused why it wasnt allowng me to install anything. I didnt realise that Maverick meerkat is already EOL .

---

### Post by radiostar on 2013-04-23
My settings info says I am using Ubuntu 12.10, But I also get the same error message about my internet connection.

Any thoughts would be appreciated.

---

### Post by radiostar on 2013-04-23
Screen shows:
W:Failed to fetch [http://ppa.launchpad.net/dpm/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/dpm/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/dpm/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/dpm/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by claracc on 2013-04-23
Instead of using a solved thread, better you have to open your own support thread for your problem.

The errors you obtain, say that the software addressed is not in the address given ( I obtain the same error on click on the addresses, so it is true there is not such software package in this server), so you have to unmark or disable these ppa repositories (dpm/ppa) in software sources (settings in update software manager), in tab other software, then close.

Then you try again to update your system .

---

### Post by Bucky Ball on 2013-04-23
> **radiostar said:**
> Any thoughts would be appreciated.

As mentioned, start a new thread with a descriptive title and outlining your problems rather than hijack this one. You will greatly improve your chances of help as this thread has been inactive for quite awhile.

***Thread Closed***

---

