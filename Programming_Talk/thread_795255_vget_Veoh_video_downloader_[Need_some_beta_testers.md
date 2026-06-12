---
title: "vget Veoh video downloader [Need some beta testers]"
date: 2008-05-15
forum: Programming Talk
---

### Post by Zapotek on 2008-05-15
Hi everybody,

This is my first post.
I just published a C application that downloads full-time high-resolution videos from Veoh without registration etc.

You can find details here: [http://segfault.gr/projects/lang/en/projects_id/15/secid/28/](http://segfault.gr/projects/lang/en/projects_id/15/secid/28/)

I've tested it as much as I could and fixed as many bugs as possible
but one machine isn't enough.

I need testers for both the source and binaries.

Thanks in advance,
Zapotek.

---

### Post by sektor242 on 2008-05-28
Nice work.

When I tried your precompiled binarys I had some Problems with the ncurses output. But after I compiled the source code on my own everything went fine. Therefore I had to install the following Packages:

libcurl4-gnutls-dev
libncurses5-dev
libxml++2.6-dev

One suggestion:
An option or configfile to specifie the download directory would be fine. 

greets
sektor242

---

### Post by secretspicy15 on 2008-05-28
the vget-i686 binary worked fine for me. Fantastic! Thank you!

---

### Post by sektor242 on 2008-05-29
> **secretspicy15 said:**
> the vget-i686 binary worked fine for me.

I just tried these binarys again and this time it worked for me too.

But I have another suggestion. If possible it would be nice to have a pause/resume funktion or maybe an automatic resume funktion after the internet connection broke down.

greets 
sektor242

---

### Post by Zapotek on 2008-06-07
> **sektor242 said:**
> Nice work.
One suggestion:
An option or configfile to specifie the download directory would be fine. 

That's very reasonable and I'm surprised I didn't think of it myself.
I'll reply when I implement it. :)

> **sektor242 said:**
> 
But I have another suggestion. If possible it would be nice to have a pause/resume funktion or maybe an automatic resume funktion after the internet connection broke down.

That's a painfull story my friend, I wanted the main feature of vget to be what you proposed.
Unfortunately, it's not easy to implement because of the way Veoh's service is designed.
I'll try to figure it out though.

Thanks guys for your support and feedback.

Regards,
Zapotek.

---

### Post by bobbocanfly on 2008-06-07
Great little app. Worked perfcetly downloading a couple of videos. Thanks alot.

---

### Post by mwmbqglib on 2008-06-11
i have some problem to compile vget...


michele@desktop-casa:~/Desktop/vget/trunk$ sudo make
gcc -O3 -Wall \
                `curl-config --cflags` \
                `xml2-config --cflags` \
                -lm  \
                -lncurses \
                `xml2-config --libs` \
                `curl-config --libs` \
                includes/*.c vget.c -o bin/vget-i686
vget.c: In function ‘main’:
vget.c:179: error: ‘CURLPROXY_SOCKS4A’ undeclared (first use in this function)
vget.c:179: error: (Each undeclared identifier is reported only once
vget.c:179: error: for each function it appears in.)
make: *** [all] Error 1



problem seems to be curl ,cause in the 7.18.1 ver, curl.h doesn't have CURLPROXY_SOCKS4A definition 
i have tried to install other versions but it return always same message...

also i have tried to produce a deb pack from tarball ver but when i install it nothing happen and when i call vget from terminal it says that vget not exist...

any suggest?

---

### Post by Zapotek on 2008-06-11
vget v0.2 is out and updated to work with the change Veoh made to it's network.
Also, as suggested, I added a "save-dir" parameter. :)

Michele I'm sorry but if my e-mail replies didn't help you I don't think I can further assist you.

---

### Post by lastcameleon on 2008-06-16
I don't know about libcurl, but I am already downloading from Veoh , and I can resume my download at any time (Unlike with Youtube). I am using my own library to comunicate with the site, and what I do is add this 'Range: bytes=%d-\r\n' to my Request header (HTTP header), and when I got the result, I just check for the 'content-range: bytes %d-%d/%d\r\n' in the Response Header, if it is present; I can resume, If not I just redo the request (Step 1) without 'Range:'. I hope that this will help you.

 Good luck :guitar:

---

### Post by Zapotek on 2008-06-17
Are you by any chance downloading the FLV file?
I plan on implementing that functionality on vget anyways, I just haven't found the time to do it.

When I do I'll let you guys know. :)

---

### Post by lastcameleon on 2008-06-17
Yes, sorry for that, I just look at the source of your soft. I am just getting the FLV file from 'fullPreviewHashPath=', and downloading by using 'Flash Player' as user-agent to keep out from any checking from them (from Veoh I mean).

---

### Post by Quzart on 2008-06-30
Thanks Zapotek, this is a great tool if you ask me! Works just fine, I've already downloaded 20 video's or something :D and no problems at all.


Looking through the posts:
I fixed the output-directory thing by adding this line to ~/.bashrc:

```
alias vget='vget --save-dir ~/Videos/'
```

Although a config file would be nice :P

---

### Post by Zapotek on 2008-07-01
Hehehe, no worries man, I'm just happy people find it useful. :)

Tbh I added the "save-dir" parameter to avoid a config file.
Adding a config file parser for just one parameter is a bit of an overhead if you ask me.

Using "alias", as you did, is much more appropriate[1] in my opinion. :)

[1] That's the reason "alias" was written i the first place.

---

### Post by Quzart on 2008-07-01
Emmm, perhaps it would be a nice idea to put hashFile.xml and MediaInfo.xml in the /tmp dir, it's spamming my homedir a bit :P. Or if you could add a parameter for it, that would be nice too.

I didn't really lookin the code (and haven't tested it), but it could be that if two instances of vget are running in the same directory that they perhaps are using eachother's hashFile.xml and MediaInfo.xml files?

---

### Post by Zapotek on 2008-07-02
Right you are Quzart.
I hadn't thought of that, I'll update it during the weekend.

Thanks for the feedback. :)

---

### Post by davobrosia on 2008-07-02
It's awesome that you've written this, and I'd love to use it, but I'm getting an error about parsing MediaInfo.xml. I'm running Arch, I have libcurl, ncurses, and libxml2 installed, and my system is up to date.
```
davo:~/v0.2.r927/trunk$ bin/vget-i686 -v v6272417ktA6zTWy
bin/vget-i686: /usr/lib/libcurl.so.4: no version information available (required by bin/vget-i686)
vget v0.2 [$Rev: 925 $] initiated.
   Author: Zapotek <zapotek@segfault.gr>
   Website: http://www.segfault.gr

[vget.c:306]Failed to parse MediaInfo.xml.
Check Veoh permalink id and/or network connection and try again.
Exiting....

```
Any ideas?

---

### Post by Quzart on 2008-07-02
I'm able to download the video, so that's not the problem
```
Quzart@Ubuntu:~$ vget -v v6272417ktA6zTWy
vget v0.2 [$Rev: 925 $] initiated.
   Author: Zapotek <zapotek@segfault.gr>
   Website: http://www.segfault.gr

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                                                                                                Dload  Upload   Total   Spent    Left  Speed
100  256k  100  256k    0     0   323k      0 --:--:-- --:--:-- --:--:--  383k
Quzart@Ubuntu:~$ 
```

---

### Post by Zapotek on 2008-07-02
> **davobrosia said:**
> It's awesome that you've written this, and I'd love to use it, but I'm getting an error about parsing MediaInfo.xml. I'm running Arch, I have libcurl, ncurses, and libxml2 installed, and my system is up to date.
```
davo:~/v0.2.r927/trunk$ bin/vget-i686 -v v6272417ktA6zTWy
bin/vget-i686: /usr/lib/libcurl.so.4: no version information available (required by bin/vget-i686)
vget v0.2 [$Rev: 925 $] initiated.
   Author: Zapotek <zapotek@segfault.gr>
   Website: http://www.segfault.gr

[vget.c:306]Failed to parse MediaInfo.xml.
Check Veoh permalink id and/or network connection and try again.
Exiting....

```
Any ideas?
This is the 3rd time I get the same bug report, but I haven't been able to reproduce it.
Check the README file for what versions your libraries should be, update them if necessary and try to compile vget.

I can't help you further as I have no idea what's wrong.

Someone said that it was due to him being behind another network and as soon as he directly set his router as a gateway the problem was solved.
Unfortunately I can't test that.

<edit>
Can you attach the MediaInfo.xml file?
It might help me figure out what's wrong in your case....
</edit>

---

### Post by Zapotek on 2008-07-05
Hello people.

Following Quzart's observation vget v0.3 is released. :)

Downloads and info:
[http://segfault.gr/projects/lang/en/projects_id/15/secid/28/](http://segfault.gr/projects/lang/en/projects_id/15/secid/28/)

Thanks again for the feedback guys.

---

### Post by Quzart on 2008-07-31
ermmm, clicking the link above here ([http://segfault.gr/projects/lang/en/projects_id/15/secid/28/](http://segfault.gr/projects/lang/en/projects_id/15/secid/28/))
```

Congratulations, you just entered uncle Zapotek's **** list!
You can now find yourself in our "Stupid people" list on your right the next time you visit us.
Take care... 

```

Everything is now normal after deleting the cookies, only my IP is logged 4 times ^^. I checked the url, but couldn't find any MySQL injection, RFI, XSS or other stuff in it :P


Anyways, v0.3 (vget-x86_64) is working fine here, thanks for the update!

---

### Post by Zapotek on 2008-08-01
Hmmm... weird that...

I was optimizing Segfault's caching[1] system but I guess I need to take one more look at it. :)

And for the next release there'll probably be a resume download functionality.

[1] The warning page might have been cached from a previous attack.

---

### Post by Zapotek on 2008-08-13
A user informed me that vget was no longer working so I dug a bit
and found out that Veoh made some changes to it's protocol.

You can find the new vget version (v0.3.1) here:
[http://segfault.gr/projects/lang/en/projects_id/15/secid/28/](http://segfault.gr/projects/lang/en/projects_id/15/secid/28/)

Cheers,
Zapotek.

---

### Post by Zapotek on 2008-08-15
vget v0.3.4 is in the trunk.
**CHANGELOG**:
```

$Id: CHANGELOG 1013 2008-08-14 23:15:37Z zapotek $

Version 0.3.4
	* Added resume mechanism to continue interrupted downloads
	  (using the "-r" flag)
	* The "-v" parameter is no longer mandatory, you can pass a
	  Veoh URL or permalink ID as a normal argument like so:
	  	vget [http://www.veoh.com/videos/v6272417ktA6zTWy](http://www.veoh.com/videos/v6272417ktA6zTWy)
	
Version 0.3.3
	* Fixed off by 2 bug in a malloc() call
	* Added the "-D" flag to create a debugging log
	  
Version 0.3.2
	* You can now pass the whole Veoh url instead of the permalink ID
	  and vget will extract it for you
	  
Version 0.3.1
	* Veoh started verifying hashes, so vget now provides a valid one
	  for each veoh permalink ID

Version 0.3
	* XML files are now saved under "/tmp" and are prefixed with the current
	  Veoh permalink ID to enable multiple instances of vget to run
	  at the same time from the same directory
	
Version 0.2
	* Added the "--save-dir" parameter
	* Added "escape()" to fix Veoh's XML files
	* Updated code to work with Veoh's hash files changes

Version 0.1
	* First version.

```

Donwload here:
[http://segfault.gr/projects/releases/download.php?release_id=56](http://segfault.gr/projects/releases/download.php?release_id=56)

Test it and give me some feedback so that I'll add it as a new release.

---

### Post by Quzart on 2008-08-21
Just downloaded the newest, but unfortunately it isn't working on my computer (used vget_x86_64):

```
theadmin@Ubuntu:~$ vget http://www.veoh.com/videos/v1629417Z36qZyrZ -D
vget v0.3.4 [$Rev: 1032 $] initiated.
   Author: Zapotek <zapotek@segfault.gr>
   Website: http://www.segfault.gr

[vget.c:359]Failed to parse /tmp/v1629417Z36qZyrZ_MediaInfo.xml.
Check Veoh permalink id and/or network connection and try again.
Exiting....
theadmin@Ubuntu:~$ 

```
```

theadmin@Ubuntu:~$ cat vget.log 
							vget v0.3.4 [$Rev: 1032 $] debug log

Veoh Permalink ID: v1629417Z36qZyrZ
hashFile:     /tmp/v1629417Z36qZyrZ_hashFile.xml
MediaXMLFile: /tmp/v1629417Z36qZyrZ_MediaInfo.xml

XML Sent: 
-----------------
<MediaIdList><MediaId permalinkId="v1629417Z36qZyrZ"/></MediaIdList>
-----------------

[includes/initVeohData.c:158] In initVeohData():
theadmin@Ubuntu:~$ 

```
```

theadmin@Ubuntu:~$ cat /tmp/v1629417Z36qZyrZ_MediaInfo.xml 















<Response>
	<Result>1</Result>
	<ErrorText>Invalid request. ClientGUID not supplied on a client only page.</ErrorText>
</Response>theadmin@Ubuntu:~$ 

```
```

theadmin@Ubuntu:~$ cat /tmp/v1629417Z36qZyrZ_tmp.xml 















<Response>
	<Result>1</Result>
	<ErrorText>Invalid request. ClientGUID not supplied on a client only page.</ErrorText>
</Response>theadmin@Ubuntu:~$

```
I tried to download several other video's too, but with the same result. Perhaps they added something that forces you to login?

---

### Post by Zapotek on 2008-08-21
Unfortunately yes...
Damn, I'll have to add authentication in order to continue the project.

We'll see guys...

---

### Post by Zapotek on 2008-08-22
User authentication has been remedied for now.
Working code is in the trunk and is waiting for further testing in order to be added as a new release.

---

### Post by Zapotek on 2008-09-01
vget 0.3.5 has been released for quite a while now.
It has also been added in the Gentoo repositories under 'net-misc' and got attention from the Greek Linux Format magazine to which I also gave an interview, hehe. :)

More info regarding new features and bugfixes can be found here:
[http://segfault.gr/projects/lang/en/projects_id/15/secid/28/](http://segfault.gr/projects/lang/en/projects_id/15/secid/28/)

---

### Post by Francewhoa on 2009-07-03
There's an easier way. You can watch full Veoh videos with the 'Illimitux' plug-in for Firefox. Read more at [http://ubuntuforums.org/showthread.php?p=7554700#post7554700](http://ubuntuforums.org/showthread.php?p=7554700#post7554700)

---

