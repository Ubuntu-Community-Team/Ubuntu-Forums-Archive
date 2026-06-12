---
title: "Reverting to olderversion of Thunderbird ?"
date: 2017-05-19
forum: New to Ubuntu
---

### Post by Greg Mueller on 2017-05-19
I just installed Kubuntu 16.04 and with it came Thunderbird 52.1.1 .

Mozilla admits that it has bugs.
I'd like to go back to 45.7.0.
Is there a way to do this?

Thanks
Greg

---

### Post by &amp;KyT$0P# on 2017-05-19
[https://ftp.mozilla.org/pub/thunderbird/releases/]("https://ftp.mozilla.org/pub/thunderbird/releases/")

But keep in mind that old versions of Thunderbird have [publicly known vulnerabilities]("https://www.mozilla.org/security/known-vulnerabilities/thunderbird/").

---

### Post by Greg Mueller on 2017-05-19
forgive my ignorance but how do I install from this list?

---

### Post by &amp;KyT$0P# on 2017-05-19
First remove the system Thunderbird -
```
sudo apt-get purge thunderbird*
```

Then go to that link and click the Thunderbird version you want.  You will get a list of different OS versions.  If you're running 64-bit Kubuntu, select "linux-x86_64".  If 32-bit, select "linux-i686".

You will then have a list of locales, select yours among them.  Then you should be presented with a download link for the Thunderbird version you want.

Once downloaded, extract into your home directory.  Then you should be able to run Thunderbird with this command -
```
~/thunderbird/thunderbird
```

---

### Post by walts48 on 2017-05-20
> **Greg Mueller said:**
> I just installed Kubuntu 16.04 and with it came Thunderbird 52.1.1 .

Mozilla admits that it has bugs.
I'd like to go back to 45.7.0.
Is there a way to do this?

Thanks
Greg

All software has bugs.

The bugs in 45.7.0 were fixed with the release of 45.8.0, 52.0.0, 52..0.1, 52.1.0 and 52.1.1.

What problems are you having?

---

