---
title: "Who is familiar with *sfile* on Ubuntu 20.04?"
date: 2021-12-28
forum: New to Ubuntu
---

### Post by bhubunt on 2021-12-28
Hi there,
I recently was copying a LibreOffice file from a USB stick to the hard drive of my laptop (OS Ubuntu 20.04), when I thought that the file folder icon on the left-hand side of my screen, where my Ubuntu icons are lined up vertically, looked weird. There was a small horizontal bar at the bottom of that file folder icon that was moving from left to right, as if some downloading was going on. I had never seen such a moving bar on the file folder icon before.  I also briefly saw the word sfile pop up at the top of my screen and so I quickly ejected the USB stick, logged out of the laptop. I should add that my laptop is not connected to the internet and in fact has no wifi module so the laptop cannot accidentally connect to wifi. 

I am not sure what was going on and what sfile is. A quick google search indicated that there is an sfile trojan for ransomware but that is for Windows, I believe. Then there is sfile.mobi, but that's for if you are on the internet it seems.

My questions to you knowledgeable folks here on the forum:
-is such a horizontal little bar on the file folder icon normal and when does it show up? 
-how can I detect on my system logs if anything weird happened during that session?
-can I look for sfile on my system via a terminal search? What command would I need to type in?

Thanks for your suggestions!

---

### Post by grahammechanical on 2021-12-28
Question: What was on that USB memory stick? Libreoffice is a distant cousin of a product called Star writer and Star Office. The successor to StarOffice was OpenOffice which was forked by community developers to become Libreoffice.

[https://opensource.com/article/18/9/libreoffice-history](https://opensource.com/article/18/9/libreoffice-history)

If you go to /etc/libreoffice/ you will see two files - soffice.sh & sofficecerc. The developers of Libreoffice comply with the terms of the original open source licenses that Libreoffice is built upon.

This link shows that sFile is some sort of command used in a spreadsheet macro.

[https://ask.libreoffice.org/t/calc-how-to-reference-document-name-in-macro/46489](https://ask.libreoffice.org/t/calc-how-to-reference-document-name-in-macro/46489)

When you say "file folder icon" do you mean the file manager or the icon representing the USB stick? What you saw may simply be a graphical representation of the file transfer. I have seen such things in Ubuntu in the past but as I do not transfer files off of USB sticks I cannot confirm what you saw.

Regards

---

### Post by TheFu on 2021-12-28
The way that file copies work on Unix systems is different than on Windows.  Linux/Unix does lots of caching, so just because the program returns and seems to have completed a copy/move, that doesn't mean that all the bits were actually written to storage.

Files can be named anything, so naming a random file and saying "possible virus" isn't exactly helpful.
Being paranoid is fine, if you have lots of time to research and learn.  Over 99.9% of the time it will turn out to be nothing and if you aren't doing foolish things on the interent, then 99.9999999999% of the time, it will trace back to nothing important. This assumes some spy organization isn't after you.

Learn to use the **file** command. It will open your eyes.
Learn to use the **locate** command to find files.
Learn to use the **find** command to find files. Learn about the difference between locate and find.

---

### Post by bhubunt on 2021-12-29
> **grahammechanical said:**
> Question: What was on that USB memory stick?


This was an old USB stick that I used on a public computer. For all I know, it simply has LibreOffice docs and PDFs, but, as I said, I used it on a public computer.

 I have since stopped using USB sticks on public computers, but I stuck it in my laptop by mistake. I will definitely not use that USB stick  again.

 > **grahammechanical said:**
>  When you say "file folder icon" do you mean the file manager or the icon representing the USB stick? What you saw may simply be a graphical representation of the file transfer. I have seen such things in Ubuntu in the past but as I do not transfer files off of USB sticks I cannot confirm what you saw.

Regards

Sorry my original description of what I saw was not totally clear.  The file folder icon is the icon on the left of my screen and represents the files on my laptop, the file manager, not the USB stick. You can see what it looks like on this link which has the ribbon of typical Ubuntu 20.04 icons -- it looks like a pale yellow file folder (I am adding the link just to make things more visual, the problem discussed on the link is none of my concern.)

[https://discourse.ubuntu.com/t/yaru-folder-icon-doesnt-match-others-in-ubuntu-20-04/14943](https://discourse.ubuntu.com/t/yaru-folder-icon-doesnt-match-others-in-ubuntu-20-04/14943)

Let me try and describe more precisely what I saw and what I was doing:

 first, I should say that LibreOffice was not open on my laptop, but the file folder manager of my laptop was still open, as I had checked to see whether the LibreOffice file I wanted to get off the USB stick was  in the download file on my laptop.

 I then proceeded to simply copy this old LibreOffice doc on the old USB stick to the hard drive of my laptop by dragging the doc from the stick into the download files on my laptop. I have done this hundreds of times in the past, and there's nothing special to see. Yet, this time I noticed a tiny horizontal bar moving from left to right on the file folder icon (on the left hand side of my screen, as I keep the ribbon with icons visible at all times.) Then I saw the word sfile pop up at the top of my screen. It all went very fast and so not knowing what was going on, I ejected the USB stick and logged out of the laptop.

The most basic question I have is: what does the file transfer bar on the laptop file folder manager icon signify? Does it mean that files are being extracted *from* the laptop or are they being transferred *onto* the laptop? 

I am also still puzzled by the sudden appearance of "sfile" at the top of my screen. In googling sfile, I had come across the macro reference you cite, but LibreOffice was not open and I don't see why the term would pop up just because I am transferring a file from a USB stick to my laptop.

Hope I explained the issue clearly.

Regards


I

---

