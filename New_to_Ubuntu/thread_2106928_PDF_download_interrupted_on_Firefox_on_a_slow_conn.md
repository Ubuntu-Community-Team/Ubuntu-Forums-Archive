---
title: "PDF download interrupted on Firefox on a slow connection"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by al.adab on 2013-01-20
currently in the middle of nowhere and relying exclusively on an internet dongle - I don't know exactly how slow the connection is, but it extremely slow (I can't load more than one page at a time). 

other than this, the connection works all right (it never disconnects itself) and has just handled a forty-MB download (it did take forever). 

on the other hand, any PDF document that's bigger than half a megabyte can't be downloaded: the download gets interrupted, and an empty document viewer pops up. I tried different sites, same result. 

it feels funny - have been on Xubuntu 12.04 for a quite a while now and often on slow/unreliable connections, and never had this issue. Firefox version: 18.0. 

any idea?

---

### Post by motorcity909 on 2013-01-20
Can you post a link to one of the PDFs you've tried?

---

### Post by al.adab on 2013-01-20
it's mostly Jstor and the like - passworded articles, average 1.5 MB - so thought it might have something to do with their server. I don't think it does, though. Just tried 

[http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDQQFjAA&url=http%3A%2F%2Fwww.digital-photography-tips.net%2Fsupport-files%2Fdigital-photography-free-guide.pdf&ei=9T_8UIzPELH14QS6joGYCQ&usg=AFQjCNF9t3tmyym1NPfspv7pt_WxElzWvA&sig2=Uie74dz8-9WOjSxjjDGOUg&bvm=bv.41248874,d.bGE](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDQQFjAA&url=http%3A%2F%2Fwww.digital-photography-tips.net%2Fsupport-files%2Fdigital-photography-free-guide.pdf&ei=9T_8UIzPELH14QS6joGYCQ&usg=AFQjCNF9t3tmyym1NPfspv7pt_WxElzWvA&sig2=Uie74dz8-9WOjSxjjDGOUg&bvm=bv.41248874,d.bGE)

please see outcome as on screenshot in attachment - same as with the articles above: the Firefox download window indicates a speed of about 6kb/sec and the download gets interrupted as soon as 4/5% of the PDF has been downloaded.

---

### Post by ciscoboy on 2013-01-20
Have you always used the 12.04 distro of Xubuntu? And if not, have you always had this problem? Maybe downgrading may help.

CiscoBoy


A simple solution that may just do the trick

---

### Post by motorcity909 on 2013-01-20
As you can see I'm on Xubuntu 12.04 as well and I was able to download that PDF and it opened no problem.

I've put it in my Ubuntu One folder and shared it so see if you have any more luck with this link - 

[http://ubuntuone.com/4Mbkluh0PMoMqoDPPSnvbo](http://ubuntuone.com/4Mbkluh0PMoMqoDPPSnvbo)

---

### Post by al.adab on 2013-01-20
if i'm not mistaken I've been on Xubuntu 12.04 for the past 10 months and never experienced this kind of problem. Usually I download average 15 to 20 pdf articles a week, and as I said it's not the first time I'm on a slow connection. It happened today for the first time.

---

### Post by al.adab on 2013-01-20
thanks motorcity909 for helping me with this - tried your link with no success: same as before. On the other hand, I've just installed Chrome and can download PDF docs no problem now. 

can it be concluded that it's got something to do with Firefox? if I'm not mistaken, Firefox was very recently updated on this distro. 

i'll be trying the Firefox extension "PDF download" to see it makes any difference. Will report back on it shortly.

---

### Post by al.adab on 2013-01-20
PDF Download in Firefox (on my machine) only work with the option "open as HTML" (which now that I think about it it's probably what Chrome does by default with PDFs). "open as PDF" doesn't work, though. 

...this is annoying. Any idea?

---

### Post by motorcity909 on 2013-01-20
What is Firefox set to do with PDFs?

Screenshot attached of my settings - two entries for Adobe Acrobat documents, both set to 'Save File'.

---

### Post by al.adab on 2013-01-20
*What is Firefox set to do with PDFs?*
I don't know exactly. I suppose it downloads/lets you download them?

my settings are like yours.

---

### Post by monkeybrain2012 on 2013-01-20
I have no problem downloading pdf with Firefox. In fact I downloaded quite a few Jstor articles myself. However my internet connection is decent.

Try install the downthemall addon to Firefox, it is a download manager and can resume when connection is interrupted due to slow connection or even if computers shut down and restarts a day later. To resume a download in Firefox go to Tools > DownthemallTools and click "Manager".

[https://addons.mozilla.org/en-US/firefox/addon/downthemall/](https://addons.mozilla.org/en-US/firefox/addon/downthemall/)

---

### Post by al.adab on 2013-01-21
tested DownthemallTools and it failed - msg given: *size mismatch* (though i understand from elsewhere it might be a bug?). 

made it back into town and on a good connection both Firefox and Chrome download PDF files all right with no extension aid. Both are still completely unreliable on a dongle connection. 

so it's got to be the very slow connection i'm on. and now i'm heading back to the desert - any solution? this is an emergency: the nearest town is three hours away...

---

### Post by audiomick on 2013-01-21
What are you trying to do exactly: save the file to your computer, or open it directly with the viewer? If you are trying to open directly, I would suggest trying to save it to the drive first. As I understand it, the download manager should keep track of whether it is finished or not that way. If you try and open directly, I don't know if it does.

There is a bit of guesswork there, though.

---

### Post by al.adab on 2013-01-21
i usually save articles first things first - but at the moment I can neither save nor open them directly: (*size mismatch* message with extension or download interrupted without extension...

---

### Post by WanderingAlbatross on 2013-01-21
I also suffer from a slow connection, and for larger files I use: > wget -c (url-to-file)

This will not give up on the file for 20 tries.  It will also resume later just by being in the same directory you were in last time, where the file was being saved.

---

### Post by al.adab on 2013-01-22
thanx WA.

here is is - it's been sitting there for a while now. sorry I'm not familiar with wget: shall i just leave it to it? is there any chance it might also save what's being downloaded if there's a power cut and the laptop battery dies? 

[I]@T42:~$ wget -c [http://booksandjournals.brillonline.com/deliver/1570064x/43/2-3/1570064x_043_02-03_S03_text.pdf?itemId=/content/10.1163/1570064x-12341234&mimeType=pdf-to-desktop](http://booksandjournals.brillonline.com/deliver/1570064x/43/2-3/1570064x_043_02-03_S03_text.pdf?itemId=/content/10.1163/1570064x-12341234&mimeType=pdf-to-desktop)
[1] 2684
@T42:~$ --2013-01-22 11:05:33--  [http://booksandjournals.brillonline.com/deliver/1570064x/43/2-3/1570064x_043_02-03_S03_text.pdf?itemId=/content/10.1163/1570064x-12341234](http://booksandjournals.brillonline.com/deliver/1570064x/43/2-3/1570064x_043_02-03_S03_text.pdf?itemId=/content/10.1163/1570064x-12341234)
Resolving booksandjournals.brillonline.com (booksandjournals.brillonline.com)... 93.91.26.126
Connecting to booksandjournals.brillonline.com (booksandjournals.brillonline.com)|93.91.26.126|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `1570064x_043_02-03_S03_text.pdf?itemId=%2Fcontent%2F10.1163%2F1570064x-12341234'

    [  <=>                                  ] 20,174      8.04K/s   in 2.4s    

2013-01-22 11:05:39 (8.04 KB/s) - `1570064x_043_02-03_S03_text.pdf?itemId=%2Fcontent%2F10.1163%2F1570064x-12341234' saved [20174][/I]

---

