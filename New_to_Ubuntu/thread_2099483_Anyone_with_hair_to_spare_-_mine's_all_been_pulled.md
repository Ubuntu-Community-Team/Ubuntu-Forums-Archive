---
title: "Anyone with hair to spare - mine's all been pulled out"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by Langstracht on 2012-12-29
I hope someone can help me deal with this.

I have consecutively installed Mint, Fedora and ubuntu on a Toshiba Satellite C650.

The wireless connection created by Fedora is VERY fast ... and those of Mint and ubuntu are like molasses in February (connected - as in data is received - but measured in BYTES/sec).

I hope this "makes sense" to someone, for it sure doesn't to me.

I do NOT want to use Fedora ... but how can I overcome this "issue" and use one of the other distributions?


Thanks in advance for your help.

---

### Post by Pjotr123 on 2012-12-29
Try disabling power management for the wireless card:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-Disable-power-management-for-the-wireless-card)

---

### Post by Langstracht on 2012-12-29
Well maybe I REALLY don't know what I'm doing but "iwconfig" does not produce any output that I can see (this is in ubuntu 12.04).

So I continue to be stuck ...

---

### Post by daslinkard on 2012-12-30
> **Langstracht said:**
> Well maybe I REALLY don't know what I'm doing but "iwconfig" does not produce any output that I can see (this is in ubuntu 12.04).

So I continue to be stuck ...

I want to make sure that I understand this correctly....when in the terminal and you run ```
iwconfig
```....you are not getting any information in the CLI?

---

### Post by Langstracht on 2012-12-30
Well I was saying that, yes.  But in error.

Doing it again - properly this time I guess - revealed:

Power Management: Off.

In addition, in the hope that it'll help solve this problem/mystery, it reported:

Mode: Managed
Frequency: 2.412
Bit rate = 65 Mb/s
Tx-Power = 15 dBm
Link quality = 69/70
Signal Level = -41 dBm and some more stuff of 0 errors.

Look forward VERY MUCH to a diagnosis and remedy.

TIA

---

### Post by Pjotr123 on 2012-12-30
What wireless chipset is it? Please provide a hardware list in this fashion:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Make-automatically-a-nice-document-with-all-your-hardware-information)

---

### Post by Langstracht on 2012-12-30
Evidently it is:

AR9285 Wireless Network Adapter (PCI-Express)
Vendor Atheros

I'm afraid I didn't understand your reference to how to detail it.  Hopefully the above will suffice.

Thanks for taking this on.

---

### Post by Pjotr123 on 2012-12-30
Try this:
[http://ubuntuforums.org/showpost.php?p=10764872&postcount=4](http://ubuntuforums.org/showpost.php?p=10764872&postcount=4)

--Edit: I've clarified and explained it on my website:
[https://sites.google.com/site/easylinuxtipsproject/internet?pli=1#TOC-Driver-ath9k:-disable-hardware-encryption](https://sites.google.com/site/easylinuxtipsproject/internet?pli=1#TOC-Driver-ath9k:-disable-hardware-encryption)
(item 2.2, right column)

---

### Post by audiomick on 2012-12-30
> **Langstracht said:**
> Evidently it is:

AR9285 Wireless Network Adapter (PCI-Express)
Vendor Atheros

I'm afraid I didn't understand your reference to how to detail it.  Hopefully the above will suffice.

Just for future reference: you can generate a shorter lshw output by restricting it to the class of hardware you are interested in. You use the option -C . The man page says capital C, but lower case works too.

Do 
```
man lshw
```
to look at the man page.

In this instance, you would do
```
sudo lshw -c network
```

To post that sort of output here, use the # button at the top of the post window to generate code tags, and paste the output between them. If it is a lot of text, the code box will have a scroll bar at the side.

---

### Post by Langstracht on 2012-12-30
Re: Anyone with hair to spare - mine's all been pulled out

Try this:
[http://ubuntuforums.org/showpost.php...72&postcount=4](http://ubuntuforums.org/showpost.php...72&postcount=4)

Did so.  And it works perfectly!!!  Genius.

Thanks so much.

Also thanks to audiomick for the tips.  I'll endeavour to keep them in mind.

---

### Post by Pjotr123 on 2012-12-30
Great to hear that it works! :)

I've just added this tweak, clarified and with explanation, to my website:
[https://sites.google.com/site/easylinuxtipsproject/internet?pli=1#TOC-Driver-ath9k:-disable-hardware-encryption](https://sites.google.com/site/easylinuxtipsproject/internet?pli=1#TOC-Driver-ath9k:-disable-hardware-encryption)
(item 2.2, right column)

---

### Post by daslinkard on 2012-12-30
> **Pjotr123 said:**
> Great to hear that it works! :)

I've just added this tweak, clarified and with explanation, to my website:
[https://sites.google.com/site/easylinuxtipsproject/internet?pli=1#TOC-Driver-ath9k:-disable-hardware-encryption](https://sites.google.com/site/easylinuxtipsproject/internet?pli=1#TOC-Driver-ath9k:-disable-hardware-encryption)
(item 2.2, right column)

Pjotr123....just checked out your site....very informative...I could have used this about a year ago when I first came to Ubuntu.  Keep up the good work!

---

