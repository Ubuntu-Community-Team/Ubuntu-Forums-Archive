---
title: "Avast anti virus?"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by Yezinki on 2012-10-03
Hi there,

How do I install Avast for Linux on Ubuntu......  [http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition) ?

Thanks.

---

### Post by hakermania on 2012-10-03
Hello. What problems have you experienced?

As it seems, you just go to the page you are linking to, click on the download button, then you choose the DEB package, you wait for it to download, you double-click on it. It will open with the Ubuntu Software Center and you click on the Install button on your right.

If you know all these steps but the error is elsewhere, please be more specific :)

---

### Post by zombifier25 on 2012-10-03
When you click download, you should be presented with 3 options. Choose to download the .deb file.

To install .deb files, double-click it to install it with Ubuntu Software Center. Or if you prefer command line,
```
sudo dpkg -i /path/to/file.deb
```

EDIT: Ninja'd

---

### Post by thatguruguy on 2012-10-03
> **Yezinki said:**
> Hi there,

How do I install Avast for Linux on Ubuntu......  [http://www.avast.com/linux-home-edition](http://www.avast.com/linux-home-edition) ?

Thanks.

Why would you? Why not use ClamAV?

If you insist on using Avast,

1. Click the "Download for Linux" button.
2. Choose the .deb package.
3. Open the package using the Ubuntu Software Center.

---

### Post by Yezinki on 2012-10-03
Thanks zombifier25 & thatguruguy for your replies.

Is Clam AV has a higher detection rates vs Avast?

Thought Avast was the no#1 rated AV on demand?

---

### Post by thatguruguy on 2012-10-03
> **Yezinki said:**
> Thanks zombifier25 & thatguruguy for your replies.

Is Clam AV has a higher detection rates vs Avast?

Thought Avast was the no#1 rated AV on demand?

Avast may be rated number 1 ***for Windows***. Generally speaking, Windows viruses don't run on Linux boxes. If you're going to use an anti-virus program, why not use one designed from the beginning for Unix-like systems?

---

### Post by daslinkard on 2012-10-03
> **thatguruguy said:**
> Avast may be rated number 1 ***for Windows***. Generally speaking, Windows viruses don't run on Linux boxes. If you're going to use an anti-virus program, why not use one designed from the beginning for Unix-like systems?

Amen!  Yezinki, I could not agree more with *thatguruguy*.  The great thing is that when you started using Linux you started using a system better than windows!

---

### Post by CharlesA on 2012-10-03
> **thatguruguy said:**
> Avast may be rated number 1 ***for Windows***. Generally speaking, Windows viruses don't run on Linux boxes. If you're going to use an anti-virus program, why not use one designed from the beginning for Unix-like systems?
What he said. I've been running BitDefender on my file server, but so far the only thing it has picked up are false positives. There really is no reason to run AV on a *nix box, unless you plan on sharing files with Windows, and even then, the Windows AV should be able to scan those files and detect any possible viruses.

---

### Post by Yezinki on 2012-10-03
Thanks all for posting your experienced views, shall go with Clam AV since it's only Ubuntu on the machine.

---

### Post by Yezinki on 2012-10-04
How do I update AV engine & GUI version of Clamav since it's not auto updating on startup?

AV definitions are current.

Thanks.

---

### Post by thatguruguy on 2012-10-04
> **Yezinki said:**
> How do I update AV engine & GUI version of Clamav since it's not auto updating on startup?

AV definitions are current.

Thanks.

You may want to read [this]("http://www.clamav.net/lang/en/faq/faq-upgrade/").

---

### Post by Yezinki on 2012-10-04
```
vaio@VGC-LS1:~$ $ whereis freshclam 
$: command not found
vaio@VGC-LS1:~$ whereis freshclam 
freshclam: /usr/bin/freshclam /usr/bin/X11/freshclam /usr/share/man/man1/freshclam.1.gz
vaio@VGC-LS1:~$ whereis clamscan
clamscan: /usr/bin/clamscan /usr/bin/X11/clamscan /usr/share/man/man1/clamscan.1.gz
vaio@VGC-LS1:~$  gpg --verify clamav-X.XX.tar.gz.sig
gpg: directory `/home/vaio/.gnupg' created
gpg: new configuration file `/home/vaio/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/vaio/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/vaio/.gnupg/pubring.gpg' created
gpg: can't open `clamav-X.XX.tar.gz.sig'
gpg: verify signatures failed: file open error
vaio@VGC-LS1:~$ 

```

Thanks but what does this signify?

---

### Post by zombifier25 on 2012-10-04
What are you trying to do anyway? From what I'm seeing you're verifying the downloaded ClamAV package, which is needed ONLY if you download ClamAV manually from the repository (also, you're not doing it right)

Also, to reply to your question, last time I checked ClamAV updates itself. If you want, you can set ClamAV to update from the GUI.

---

### Post by Yezinki on 2012-10-04
> **zombifier25 said:**
> What are you trying to do anyway? From what I'm seeing you're verifying the downloaded ClamAV package, which is needed ONLY if you download ClamAV manually from the repository (also, you're not doing it right)

Also, to reply to your question, last time I checked ClamAV updates itself. If you want, you can set ClamAV to update from the GUI.


Thanks zombifier25, correct I downloaded from repository & Ubuntu center....what should I do now?

---

### Post by Yezinki on 2012-10-04
Virus scanner startup preferences >  Check for AV engine updates, GUI Updates & Open DNS servers all 3 checked?

---

### Post by DuckHook on 2012-10-04
> **Yezinki said:**
> Thanks all for posting your experienced views, shall go with Clam AV since it's only Ubuntu on the machine.

One of the nicest things about Linux is how robust it is against viruses. I agree with CharlesA. Why install AV at all? It is a huge resource hog and is one of the reasons that Windows runs so poorly. When I moved to Linux, one of the best things about the move was not having to deal with AV any more. At first, you feel awfully exposed, until you realize that Windows has habituated us into feeling that its lousy security is the norm. In Linux, good security is the norm (as should be the case in Windows from the start), and AV is (in my opinion) a pointless layer of unnecessary sludge. Having said that, you may wish to install it simply to avoid passing on any Windows virus that you receive to Windows users further downstream. Clam does this by staying on the lookout for e-mails you receive that may contain *Windows* viruses. However, since such viruses cannot infect your computer, this is really just a public service and not a benefit to you.

---

### Post by Yezinki on 2012-10-05
Thanks I agree with your views.

What command should I type in terminal to get rid of Clam AV altogether?

---

### Post by CharlesA on 2012-10-05
> **Yezinki said:**
> Thanks I agree with your views.

What command should I type in terminal to get rid of Clam AV altogether?
It depends on how you installed it. If you installed it from the repos, it should be easy to remove via apt-get.

---

### Post by Paqman on 2012-10-05
> **thatguruguy said:**
> Why would you? Why not use ClamAV?


Because [ClamAV is rubbish]("http://en.wikipedia.org/wiki/Clamav#Effectiveness")?

You don't really need antivirus on a Linux desktop IMO, but if you did need one, you can do better than ropey old ClamAV.

---

### Post by Feyerbrand on 2012-10-05
I agree with Paqman, I never run antivirus on my linux machines and have never run into an issue.

---

### Post by Yezinki on 2012-10-05
Thanks.

---

