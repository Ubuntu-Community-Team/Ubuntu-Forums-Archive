---
title: "Browser Suggestion"
date: 2024-04-17
forum: New to Ubuntu
---

### Post by spinnekop1962 on 2024-04-17
Can anyone recommend a decent browser that doesn't force installation of snapd? This would seem to exclude firefox and chromium.....

---

### Post by Holger_Gehrke on 2024-04-17
There's an official repository by Mozilla for Firefox as a Debian package. You need to set some preferences to stop it from 'updating' to snap but once that's done everything works as expected. See [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) for the details.

Holger

---

### Post by spinnekop1962 on 2024-04-17
Thank you - have done that!

---

### Post by ActionParsnip on 2024-04-17
Google Chrome is what I use

---

### Post by #&amp;thj^% on 2024-04-17
Just a little early heads up, 24.04 will still try to install firefox and thunderbird as a snap, unless you rid yourself of all snap processes.
```
systemctl status snapd
&#9675; snapd.service
     Loaded: masked (Reason: Unit snapd.service is masked.)
     Active: inactive (dead)

```
I won't go into detail on that here and now, as Holger_Gehrke post and link will still work for Jammy 22.04 
Not very nice of Canonical to second guess or force my choices. :P
Time to hop around again I guess. :(

---

### Post by Rubi1200 on 2024-04-17
I may be mistaken but I think Vivaldi and LibreWolf have snap free versions. Never tried installing them though so cannot say for sure.

---

### Post by #&amp;thj^% on 2024-04-17
> **Rubi1200 said:**
> I may be mistaken but I think Vivaldi and LibreWolf have snap free versions. Never tried installing them though so cannot say for sure.

I'm also unsure on LibreWolf, but yes on Vivaldi
```
apt policy vivaldi-stable
vivaldi-stable:
  Installed: 6.6.3271.61-1
  Candidate: 6.6.3271.61-1
  Version table:
 *** 6.6.3271.61-1 500
        500 https://repo.vivaldi.com/stable/deb stable/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by TheFu on 2024-04-17
I use _firefox ESR_ (not a snap package) and _brave browser_ and _dillo_ and _lynx_.  Each for specific purposes, based on my needs, the dangers, and what is required to protect my system.

No browser is always "the best".

I remove the idea of using Google Chrome for privacy concerns.  

Prior to using Brave, I was using a non-snap version of Chromium with 18.04 when that OS still had support.  When that ended a year ago, I stopped using Chromium.  Brave was odd initially and it broke some of the locations I specifically used chromium to visit. This was due to extra tight anti-tracking, anti-spam, non-secure stuff that was fine in Chromium, I think.  For example, my microphone and webcam didn't work for a few weeks in a restricted environment.

Lynx is a text-only browser.  There are times when I only want text, nothing else.

Dillo is a minimal browser that supports images, but not javascript. There are times when I specifically don't want any javascript at all.  Dillo's HTTPS certificate handling has been badly broken for a long time, so don't use it if you want to ensure no packets are unmolested between your browser and the remote server.  I think there is a newer replacement similar to Dillo with similar restrictions, but I cannot think of the name right now. Sorry.  Net-something?  I don't remember.

When I use Brave, I always run it inside some sort of firejail constrained environment.  Sometimes that's restricted just to my HOME directory and sometimes it isn't allowed to see or touch any files on the computer.  Just depends on the needs.  Snap packages have constraints like that, but without any local control and with some other mandates that don't work for my systems.  Snap packages don't work with firejail because they both use similar OS capabilities to accomplish their constraints.  I just need more fine control than snaps allow.  Plus, snaps hate NFS storage, which I use a bunch.

Firefox is my I-know-this-is-usually-safe browser.  I run it inside a minimally restricted firejail just for some slight protection, while having access to storage anywhere on my computer or on the network.

Whenever picking a browser, I try to understand who is behind it and their core values.  Sometimes that means going 3-5 levels above the current company/owner to determine the true ownership and what the laws of that jurisdiction might be at odds with my desires.  Every few years, some slightly popular browsers get bought by organizations that I've decided are undesirable.  Each of us needs to decide what that line is.

---

### Post by alexwisha on 2024-04-17
I use Mozilla and its very good.

---

### Post by ajgreeny on 2024-04-17
> **alexwisha said:**
> I use Mozilla and its very good.
Not quite sure what you mean by that but perhaps you download the .tar.bz from Mozilla [https://download.mozilla.org/?product=firefox-latest-ssl&os=linux64&lang=en-GB](https://download.mozilla.org/?product=firefox-latest-ssl&os=linux64&lang=en-GB) as I do, extract it and then run Firefox direct from the executable file in the extracted archive.
You can also do the same for Thunderbird, which I've also done in my installs of the upcoming new LTS 24.04.

In the settings of both you can choose to either let them update automatically or to inform you when a new version is available

No snaps for me, or not yet anyway.  It may become essential eventually in Ubuntu but if so I shall undoubtedly move elsewhere, possibly Mint or Debian-Testing, both of which I run as VMs in KVM/QEMU to see which I prefer.

PS:
I also have chromium from a ppa at [https://ppa.launchpadcontent.net/savoury1/chromium/ubuntu/](https://ppa.launchpadcontent.net/savoury1/chromium/ubuntu/) (but seldom use it), and also occasionally use Brave but Firefox is undoubtedly my most used and definitely my favourite.

---

### Post by fyfe54 on 2024-04-17
Definitely Vivaldi. Basically Chrome without the surveillance baggage. And it comes with all kinds of cool and useful features.

---

### Post by spinnekop1962 on 2024-04-18
Thanks for the suggestions everyone!

---

