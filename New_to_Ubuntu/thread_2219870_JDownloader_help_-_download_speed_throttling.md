---
title: "JDownloader help - download speed throttling"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by jan_jan_64 on 2014-04-25
I have had JDownlaoder for a little while now, and I think I have gotten to grips with it for the most part. However, Im having a problem whenever I try to download large files. Even if I set my download speed to 500 or 1000 kb.s, a lot of the time a connection will max out at 75 or 100kb/s and take hours for something to download. I know that I *can* achieve fast speeds, as with a meagre few hosters I have done, and my internet connection isnt too bad (wired, I should be getting around 5mb/s). I read on the JDownloader forums that not having Java running, or having an entivirus etc that blocks it, can affect this - I have very little knowledge of Linux and everything was installed for me by an ex boyf, but I DO know I have a lot of browser plugins for internet security that pretty much blocks the crap out of everything or modifies my IP in some form or another. I have trawled through various settings of NoScript and such until I have been able to allow JDownloader to run unhindered for the most part, but I am unsure if perhaps one of these programs is still affecting it (though thus far this has only hindered me from connecting to the host sites via the browser and accepting packets, I didnt really think said things may affect my download speed...).

There was a brief moment, for example, when, after reconnecting to the internet after having to take out the wire (irrelevant story), it reconnected at 1.5mb/s and my packet was going to be downloaded in 15 seconds. Then it instantly switched back to 99 kb/s, taking over an hour to download 512mb. And when thats one packet out of 9, and I have to be in front of the PC to put in the captcha for each packet... yeah, this is getting very frustrating.

Im not sure what additional information to give you which will be helpful in figuring out the problem, but if anyone has any ideas or thinks they can help just let me know what info you need and I will do my best to get it to you! Thanks a lot :)

---

### Post by jan_jan_64 on 2014-04-26
Bump?

---

### Post by LastDino on 2014-04-26
>Try downloading with something that's not JD, even firefox default downloader will do.
>Compare the speeds
>If possible check the same connection on different PC
>If speed is still less, contact your ISP. 

I highly doubt its anything other than that but if it is, you can also check what other applications are using your net bandwidth, maybe torrent, maybe something else? You can try tracking packages over Wireshark or something, but it would be easier to just call someone to have a look at this physically.

---

### Post by stinger30au on 2014-04-27
in jdownloader in bototm right corner, set speed to 0 make it run fastest

---

### Post by jan_jan_64 on 2014-04-28
Thanks for your comments/responses. After setting the download speed to 0, I got a very slight increase in download speed, but not much. After doing some experimenting, it would appear (at least from what I understand) that its not JDownloader, but the hosting sites themselves. Before, I was automatically selecting files with a one-click option to load them into JDownloader - after actually clicking through manually to the hoster pages (to try a download in just my browser itself) I see that non-members of these sites have a much more severe restriction on their download speeds. Which sucks. Im trying to find some different sites which may not be as bad but its proving difficult to find anything thats legit/safe for me to download from (torrenting laws are stricter/enforced more here in Germany, so I am told). Much appreciate teh iput, if anyone has any other info which may be of use to me it would be very much appreciated.

---

