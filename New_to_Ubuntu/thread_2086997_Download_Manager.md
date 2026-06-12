---
title: "Download Manager?"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by Yezinki on 2012-11-22
Which is the ideal download manager for Ubuntu that won't break a large file (size 5 GiB), even if paused?

Thanks.

---

### Post by slickymaster on 2012-11-22
**Uget**
Uget (formerly urlgfe) is a Free and Open Source download manager written in GTK+ , support pause and resume , classify download , every category has an independent configuration, can be used from command line.

---

### Post by Yezinki on 2012-11-22
Thanks, how do I install it?

---

### Post by slickymaster on 2012-11-22
Install it from GetDeb. GetDeb provides downloadable DEB packages and also Ubuntu repository for these applications.

---

### Post by Yezinki on 2012-11-22
Thanks lastly are the downloads using it reliable, like no broken packages, correct md5 etc?

---

### Post by slickymaster on 2012-11-22
You can always take a look at these ones:

**_Wget:_**
Wget is the default download manager that ships with Ubuntu. It’s a network utility designed for retrieving files from the web using the http(s) and ftp (s|es) protocols. Apart from the initial invoking, it doesn’t require any more interactions from the user.
The program also supports mirroring of entire web directories making it extremely useful for someone with limited access to the internet.
As wget ships natively with most Linux versions, chances are that you already have it installed. Run the following to get a basic idea of the options
```
wget –help
```

_**Gwget:**_
Gwget is a GNOME front end for the ever so popular wget application. Ideally recommended to people who are not comfortable working with the command line. It features a system tray icon, multiple downloads at the same time and a lot of customizable options.
To install it on Ubuntu, simply run the following:
```
sudo apt-get install gwget
```

_**Curl:**_
Curl may be considered a nice alternative to wget. It’s extremely versatile and supports an extensive number of protocols. Thanks to it not needing any user interaction after the invoke step as well, it’s idea for use in the background.
Installing curl is relatively simple as well, just run the following:
```
sudo apt-get install curl
```

---

### Post by slickymaster on 2012-11-22
> **Yezinki said:**
> Thanks lastly are the downloads using it reliable, like no broken packages, correct md5 etc?

Why don't you take a look at [Uget FAQ webpage]("http://uget.visuex.com/faqs")? I think you'll find easily the answers for all your questions.

---

### Post by Yezinki on 2012-11-22
It won't start with the downlaod using G Chrome browser?

---

### Post by slickymaster on 2012-11-22
With Chrome I don't know. What I do know is that it can be integrated with Firefox through Flashgot plugin.

---

