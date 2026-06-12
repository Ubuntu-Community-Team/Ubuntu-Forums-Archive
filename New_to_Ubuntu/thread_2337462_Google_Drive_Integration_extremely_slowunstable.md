---
title: "Google Drive Integration extremely slow/unstable"
date: 2016-09-18
forum: New to Ubuntu
---

### Post by stumpie2 on 2016-09-18
Dear all,

When I open Files and click my Google Drive, it takes about 12 minutes for it to load. After that, as long as I keep Files open, it works just fine. However, if I close Files and re-open it, it takes again 12 minutes. All other applications I have used so far start quick enough. The whole system is nicely smooth and responsive. Sometimes, it will load real quick, but then it'll show only a fraction of the contents of my Google Drive.

I'm running 16.04 with plain vanilla Gnome, right out of the box, all updates installed as far as I'm aware. I'm on a stable ADSL connection with almost 70Mbps down and 11Mbps up. I'm using the Google public DNS as the DNS provided by my telco is horrible.

I've searched all over but can find a solution. I've seem some other people mentioning the problem, but no-one seems to have a solution at hand. It's really too bad, because I use my Google Drive a lot.

If anyone has any thoughts, I'd be really happy to hear them.

Thanks in advance,

Stumpie

---

### Post by mörgæs on 2016-09-21
Do you see extra CPU load or network traffic during the 12 minutes?

---

### Post by stumpie2 on 2016-09-21
[ATTACH=CONFIG]271300[/ATTACH]

Yes, now I look for it, I see a little CPU load but quite some network traffic. Please see the attached image.

---

### Post by #&amp;thj^% on 2016-09-21
Am I missing something here "Please see the attached image."
Ok Your attached image now shows.:)

---

### Post by stumpie2 on 2016-11-01
Bump

---

### Post by vasa1 on 2016-11-01
> **stumpie2 said:**
> ... However, if I close Files and re-open it, it takes again 12 minutes. .... 
The delayed loading is mentioned in [this article]("http://www.techrepublic.com/article/how-to-make-the-most-out-of-google-drive-on-gnome/") dated March 15, 2016:> Instead of the Google online account simply syncing with a local desktop folder, it allows you to mount the remote Google Drive folder to the local machine. This can be a painfully slow process depending upon your connection speed, as **every time the drive is unmounted and mounted, the folders have to be reconnected**. This means **you don't actually have a local copy of your Drive folders** ...As long as this state persists, using Google Drive this way won't be fun because there isn't true sync at all.

I haven't found a more recent article dealing with this topic :(

---

### Post by stumpie2 on 2016-11-01
Thank you, this is very clear. In GNOME we trust (to come up with a solution), and I simply have to be patient and use Drive though the browser.

---

### Post by mastablasta on 2016-11-02
grive2 and sync with chronjob might solve the sloweness issue or something like overgrive.

or your owncloud or nextcloud or seafile..

still i am not sure why it needs so long just to read the list of files.

---

### Post by buzzingrobot on 2016-11-02
FWIW, I set up a Win10 machine yesterday and installed the official Drive app.  Initial population -- the downloading -- of the local directory and contents  was terribly slow.  So slow, in fact, that I installed Chrome and used the web interface to grab the whole thing -- 15 gigs -- while the app was grinding away. 

I use the web interface in Linux.  There's no syncing to local drives going on, of course, but I don't need that.  Always very fast, probably because there's none of the constant mounting/remounting that Vasa mentioned needed to access it via Files.

---

