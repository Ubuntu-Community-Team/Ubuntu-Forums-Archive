---
title: "[SOLVED] HOW TO download books from Audible.com"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Commander_Bob on 2008-09-29
I just bought a book from Audible.com and was disappointed to find out I needed a windows program to download it. However I found a way to download it without their program! Here is how...

First purchase the book you want. Then go to "My Library".

Click on "Stream" under "Download It" Save the .pl file.

Open the .pl file in the text editor. You will find something like this
```
<ASX VERSION="3.0">
<Title>Brisingr (Unabridged) Part 4</TITLE>
<ENTRY>
<ref href="http://cdl.audible.com/cgi-bin/aw_assemble_title_dynamic.aa/BK_LILI_000762dmp332.aa?stuff about your account here fas;dlfilasddk" />
<MOREINFO href="http://www.audible.com" />
<TITLE>Brisingr (Unabridged) Part 4</TITLE>
<AUTHOR>Christopher Paolini</AUTHOR>
<COPYRIGHT>Audible, Inc.</COPYRIGHT>
</ENTRY>
</ASX>
```

Copy the URL,
```
http://cdl.audible.com/cgi-bin/aw_assemble_title_dynamic.aa/BK_LILI_000762dmp332.aa?stuff about your account here fas;dlfilasddk
```

Past it into FireFox and you will download the .aa file! It is that easy.

I don't think you can play the .aa files on Ubuntu but you should be able to play them on your mp3 player.

Good luck,
Justin

---

### Post by uberdonkey5 on 2008-09-30
well, if mp3 codecs are downloaded for ubuntu it should work!

Did you write to the company and tell them your fix? I think we need to pressure companies to make downloads linux compatible as many don't even think of it. This would be simple for them to do now you have the fix as well! Well done!

---

### Post by Commander_Bob on 2008-10-10
I think that they would be aware of the fix. The problem is you need to make your mp3 player authorized to play the files. I ended up just downloading the mp3 from a torrent. The .aa files have DRM and you can't just play them...

I believe people were able to run their program under wine and link up with it but not download the files, now they can.

---

### Post by azebuski on 2008-10-11
Thanks for this tip Commander Bob.  I just recently purchased a book from audible.com and was disappointed when I could not download it.  I wrote an e-mail to their help dept. but never got a response.  I followed your directions and the book playes perfectly on my mp3 player!!

---

### Post by Commander_Bob on 2008-10-11
That's great! Mine said I need to connect it to my computer. I too contacted the customer support and I got 
> **"Regina Audible Customer Support"]Dear Justin,

Thank you for contacting Audible.com. On its behalf, I would like to apologize for any inconvenience and I am most committed to satisfying and resolving your inquiry to the fullest of my abilities.

I have read your email inquiring how to install the Audible Software on a Unix computer.
Unfortunately the Unix Operating System is not supported by audible. There are no announced plans on if or when it will be supported. 

I would like to take some time to thank you for being a much valued customer of Audible.com. Thank you so much for your support!
I hope I have met all your needs and requests, as it has been a pleasure assisting you today. In addition if my assistance provided to you as a customer was a positive experience, please fill out an E-Survey that may possibly be sent to your email address.

Have a nice day!

Here at Audible, we truly value and appreciate your business said:**
> www.audible.com/contactus[/url]

Sincerely,
Regina
Audible Customer Support
I filled out the survey telling them how *happy* I was that they don't support Linux. :mad:
You would think something like downloading a book would be easy enough to support all systems... I download music from Amazon all the time with no problems, they even have a Linux downloader!

---

### Post by avalenc on 2008-10-12
I don't really know much about computers, so a couple of questions:
a) how do you open a file in the text editor?
and,
b) is the text editor Terminal? Or is it something else?

Thank you!

---

### Post by Abu_Dayya on 2008-10-12
Text editor is like notepad in windows. In linux we have 'gedit'

```

gedit file

```

---

### Post by Commander_Bob on 2008-10-12
You can usually just double click it or right click it go to Open With->Text Editor

Or you can use the terminal to start gedit like Abu_Dayya suggested.

---

### Post by avalenc on 2008-10-14
Hnm, so I opened it in text editor, and cut and pasted the URL into Firefox, and it gives me "Internal Error. Code: 5."

Has anyone else gotten this?

---

### Post by Commander_Bob on 2008-10-14
What gave you the error? Firefox or their site? If it is their site you probably did not copy the entire link, don't forget the stuff after the ? and don't copy the "

---

### Post by avalenc on 2008-10-14
Yes! It was the site. And you're correct; I was copying the quotes. I'm still at a very basic level with all of this and don't know how to properly form/format things.

Thank you!

---

### Post by Commander_Bob on 2008-10-14
Been there, done that :)

I still get things wrong a lot and I am not that familiar with linux, more than Windows though (all my Windows knowledge fell out of my head when Ubuntu came along). Just enough to get by, you pick up bits and pieces as you need them. I recently learned a lot about how USB devices are treated because I could not get my AVR programmer working correctly.

Glad it worked out for you,
Justin

---

### Post by milesje on 2008-10-18
Does the iPod support the Audible audio files out of the box or do you have to register it via the Audible software? I have installed their software in WINE but it tells me that my device is not connected. My player (Rio Carbon) is autodetected and is mounted, I can use banshee to transfer songs to it so I know it is connected, but the audible software does not find it and I have to use their software to register so I can listen to the file I have already paid for and downloaded. Man Audible SUCKS.

---

### Post by Charrlie on 2009-02-18
Thank you so much for posting that tip.  I also wrote to them and they said you could not play audible books on linux.  They need to hear from linux users and realize they are missing possible sales.

---

### Post by soan on 2009-06-12
Thanks BIG TIME, this worked for me. Seems like most companies don't do most forms of DRM on Linux.

---

### Post by shadowlands on 2009-06-24
Is this still good information or is it outdated?

---

### Post by shadowlands on 2009-06-24
Can some one give me step by step directions on how to get my books from this site on to my walkman?  Thanks a head of time.

---

### Post by olafura on 2009-07-03
There is a [petition for Amazon to remove DRM from Audible.com]("http://callanaudible.org/"). Please sign it, they will deliver it on 31 July 2009.

---

### Post by Don1500 on 2009-08-20
> **olafura said:**
> There is a [petition for Amazon to remove DRM from Audible.com]("http://callanaudible.org/"). Please sign it, they will deliver it on 31 July 2009.

SO, how did this work out?

---

### Post by humble_coffee on 2010-06-28
The solution still 'works' fine.

Although the resultant file is encrypted, so it still seems that you need to go via the Audible Windows software.

---

### Post by chelmite2 on 2010-07-12
The download file, aw_dhelper.pl now looks like:
(I've substituted <ALL_CAPS> for fields, account numbers, etc.)

user_id=<USER>&product_id=<PRODUCT_ID>&order_number=<ORDER_NUMBER>&agg_id=&awtype=&title=<TITLE>&assemble_url=http://cdl.audible.com/cgi-bin/aw_assemble_title.pl&cleanup_url=http://cdl.audible.com/cgi-bin/aw_cleanup_title.pl&size=<SIZE>&DownloadType=Now&domain=www.audible.com&codec=mp332&transfer_player=1&browser_type=

I'm not trying to bypass DRM or download anything that I haven't purchased.  I just don't want to have to run Windows just to download content that I've purchased!

---

### Post by kaligus on 2010-07-26
it may not hurt to visit this link

[http://audible.custhelp.com/app/answers/detail/a_id/3899/kw/linux/r_id/166](http://audible.custhelp.com/app/answers/detail/a_id/3899/kw/linux/r_id/166)

I have been sending them an email or feedback once a month since installing Ubuntu and this month did both after finding this link in another search.

---

### Post by Garudi on 2010-09-11
> **Don1500 said:**
> SO, how did this work out?

Obviously had no effect what so ever.

---

### Post by elixirsoo on 2010-10-18
Huge thank you to [Commander_Bob]("http://ubuntuforums.org/member.php?u=455135") for this tip - you're an absolute star! :KS

I cancelled my membership with Audible when I moved over to Linux about three years ago. It's their lost revenue, especially now Ubuntu is spreading like wildfire - I have even converted my computer illiterate eldest daughter over to a simplified Linux desktop!

I can now buy an occasional bargain - without a membership - and use an old windows machine to get it onto my iPod. So this is from me to Audible ):P bye for good (pun intended)

:lolflag:

---

### Post by TTGRULES on 2010-12-15
I just bought some audio books from audible, and it started directly downloading the .aa files. I think they might have taken linux into consideration now. That, or they supported chrome or something...

---

### Post by davegregg on 2011-05-25
**[SIZE="4"]NEW SOLUTION!!![/SIZE]** :guitar:

Okay, just figured this out. *This should work with all browsers and operating systems.*

Here's how to download an Audible file you've already purchased **without Audible Manager:**

1) Download the helper file. This is the file that is downloaded when you click the "Download" button in "My Library". The file name of that file will be "admhelper". Open it in a simple text editor, like gedit or Notepad. The contents will look like this:

> user_id=**[COLOR="red"]{YOUR USERNAME}[/COLOR]**&cust_id=**[COLOR="red"]{YOUR CUSTOMER ID}[/COLOR]**&product_id=**[COLOR="red"]{PRODUCT ID}[/COLOR]**&asin=&codec=LC_64_22050_stereo&awtype=AAX&source=audible_adm&title=**[COLOR="red"]{BOOK TITLE}[/COLOR]**&assemble_url=http://cds.audible.com/download&order_number=**[COLOR="Red"]{ORDER NUMBER}[/COLOR]**&size=&domain=www.audible.com&transfer_player=1&browser_type=

2) Go to the actual Audible.com bookstore page for the exact book you are trying to download. Look at the URL:

> http://www.audible.com/pd?asin=**[COLOR="Red"]{ASIN}[/COLOR]**

3) You now have the information you need. Specifically, you need the username you log in with (probably your email address), the Product ID, that ASIN (which is like an ISBN) from the bookstore page, and your Order Number. Now plug the above information EXACTLY into the correct places in the URL below:

> http://cds.audible.com/download/cgi-bin/aw_assemble_title_dynamic.aa/**[COLOR="Red"]{PRODUCT ID}[/COLOR]**dmp332.aa?asin=**[COLOR="red"]{ASIN}[/COLOR]**&user_id=**[COLOR="red"]{YOUR USERNAME}[/COLOR]**&codec=LC_64_22050_stereo&awtype=AAX&source=audible_adm&order_number=**[COLOR="Red"]{ORDER NUMBER}[/COLOR]**

[COLOR="Red"]**IMPORTANT!!**[/COLOR] Check your final URL thoroughly for random spaces. For some reason, the forums occasionally insert stray spaces where they shouldn't be. Your final download URL **should not contain any spaces.**

4) Once you have your new download link, **make sure you are logged in to Audible.com** and paste your download link into your browser's address bar and go! The download should commence immediately.

[SIZE="4"]***NOTE: This does not remove the DRM protection.***[/SIZE]

---

### Post by davegregg on 2011-05-25
Here's a quick Excel function I've created to partially automate the creation of the working download link. I realize this may not be that helpful to many of you (because you are looking for a Linux-only solution), but I don't have the time to work out a perl script, or HTML file with javascript, or something, to do this.

1) Drop the contents of the file "admhelper" into cell A1 of a new spreadsheet.
2) Drop the bookstore page link to the actual book you are trying to download into cell A2.
3) Paste the following function into cell A3: ```
=HYPERLINK(CONCATENATE("http://cds.audible.com/download/cgi-bin/aw_assemble_title_dynamic.aa/",MID(A1,SEARCH("product_id=",A1)+11,SEARCH("&",A1,SEARCH("product_id=",A1))-SEARCH("product_id=",A1)-11),"dmp332.aa?asin=",MID(B1,SEARCH("asin=",B1)+5,SEARCH("&",B1,SEARCH("asin=",B1))-SEARCH("asin=",B1)-5),"&user_id=",MID(A1,SEARCH("user_id=",A1)+8,SEARCH("&",A1,SEARCH("user_id=",A1))-(SEARCH("user_id=",A1)+8)),"&codec=LC_64_22050_stereo&awtype=AAX&source=audible_adm&order_number=",MID(A1,SEARCH("order_number=",A1)+13,SEARCH("&",A1,SEARCH("order_number=",A1))-SEARCH("order_number=",A1)-13)))
```
4) Be sure you are logged in to Audible.com, then click the new link in cell A3 or copy its new contents into your browser. The download should begin immediately.

---

### Post by kaligus on 2011-06-22
> **davegregg said:**
> **[SIZE=4]NEW SOLUTION!!![/SIZE]** :guitar:
{deletia}

[SIZE=4]***NOTE: This does not remove the DRM protection.***[/SIZE]

Is there any simple way to play these?

I do not desire to remove the DRM I would be content with a simple desktop player solution but would love to be able to take my already purchased books on my new mp3 device (not iJunk or MS-junk but a simple mp3/ogg/etc. player which talks to any USB connection or an addon micro SD card to play everything I have tried so far except audible).

---

### Post by EriktheAwful on 2011-07-29
I've been trying to listen to the Samuel L. Jackson recording of _Go the F*** to Sleep_ for a month now. I emailed their customer service and chided them, but I think it'll fall on deaf ears. I think it's about the perception that "If we make our codec available for an open source OS, then everybody will have the keys to our content and our DRM won't be worth anything any more". :(

---

### Post by Aessa on 2011-08-08
Well then we'll need to convince them that software running on open source ***can*** be closed source, so it's the same in the end in terms of security.

I use the BlackBerry app now, which means you buy online and  download and listen from the phone. Any Android and the iPhone should also have an app (which looks a bit nicer :( ). Otherwise, with audiobooks being a good couple of hours, having to boot windows to copy them to my mp3 player now and then is not too much hassle. Ultimately though, there's no excuse, we need a linux app.

---

### Post by druhu on 2012-05-03
Guys, you're all doing this the hard way. Just install a user agent changer on Firefox (User Agent RG 1.0) and set it to pretend to be a Kindle. Then all your download links on Audible's library will just take you straight to the audible file instead of sending you those download manager files instead.  Enjoy :-)

---

### Post by oldos2er on 2012-05-03
Old thread closed.

---

