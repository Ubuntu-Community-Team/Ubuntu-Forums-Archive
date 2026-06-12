---
title: "Amazon MP3 downloads from cloud player"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by Davethehedgehog on 2012-10-04
I used to buy albums from the Amazon MP3 store via the link in Banshee.  Since Amazon have introduced their cloud player, this doesn't work any more. Songs are automatically added to the Cloud Player and you can only download them one at a time as Amazon's downloader doesn't work in linux.
I'm running UBUNTU 12.04.

Any suggestions?

---

### Post by rcayea on 2012-10-04
I see you only have two beans which leads me to guess you are fairly new to linux so I ask, have you tried WINE?
Link: winehq.org

---

### Post by Davethehedgehog on 2012-10-05
I've used wine before but not for this.  I'll give it a try.

---

### Post by adempewolff on 2012-10-07
Hi Dave,

I can confirm this problem.  Unfortunately this is not a technical issue but rather a rather unusual choice on the part of Amazon to restrict via browser user agent string all devices running linux from being able to download multiple files at the same time.

You can get around it by installing the user agent switcher add-on for Firefox, setting it to IE, authorizing that browser with Amazon Cloud Player, and then using it to download the .amz files which you can then open with Banshee and it will import the music as normal.

I'm in the process of writing an illustrated how-to for this workaround and will post a link once it's done.  It's also likely that the developers could simply spoof a Windows user agent for the Banshee browser to create a smoother experience.

However for something as simply, arbitrary, and irrational as unilaterally restricted browsers from downloading multiple songs solely based on their user agent string's stated operating system, I believe the correct response to this is contacting Amazon and asking them to explain their actions.

Here is the email I just sent to them:

> Hello,

I have been a regular customer of the Amazon MP3 store for awhile now.  Whenever I heard about a new album I would preview and buy the album from your store.  Part of the reason for this was the great Amazon MP3 integration with Banshee Media Player ([http://banshee.fm](http://banshee.fm)).  I could browse Amazon, preview songs, and import my music all from within Banshee Media Player.  Having to use a third party client to download music that I have purchased has always been a very big turn off for me--hence, I don't like using Google Play, and before I discovered Banshee's Amazon integration I didn't like purchasing music from Amazon either.

With my most recent purchase however I was very displeased to discover that Banshee's automatic import of songs purchased from Amazon MP3 was no longer working.  After a little research I determined that the cause of this was that Amazon had decided to lock out any browsers with a Linux user agents strings from being able to download multiple songs.  If I authorized and used a browser with a Windows user agent to download the .amz file then I was able to open that file with Banshee and import the songs normally.  I understand the need to authorize devices for use with the cloud player, but the decision to unilaterally lock out linux machines from being able to download .amz files seems completely arbitrary, and to this customer is a very disappointing development.

I'm not going to threaten to boycott Amazon MP3, in all likelyhood I will continue to purchase MP3 albums from your service.  However, from this point on I will likely only purchase the promotionally priced albums, I will now have no incentive to buy the full priced albums (where you make the most money) from your service rather than another service--especially those which have better support for linux.

What really bothers me about this is that it is not a technical issue.  I am not expecting you to support another operating system, additional software, or to make a version of the Amazon MP3 downloader for linux.  It is a matter of Amazon--inexplicably--choosing to restrict via user agent all browsers running on Linux systems from being able to use features that they otherwise are fully capable of using.  To me this seems not only unreasonable but also a poor business choice and not what I expect from Amazon in terms of how you treat your customers.

Furthermore, I am disappointed by the lack of an explanation behind why this decision has been made.  Linux users are greeted by a message apologizing that support isn't offered, but given that support was previously available, and applications such as Banshee are still technically able to use the service if they use another browsers user agent key to download the .amz while, I believe that we deserve an explanation of why this change has been made.

Thank you for your time reading this.  What I would like is both for you to please convey my comments along the appropriate channels and I would also like to receive a response stating, 1) why this change was made, and 2) if there are any plans to re-enable Linux devices in the future.  Even if the answers to these two questions are not what I hope to hear, a thorough response addressing these issues would likely keep me a loyal customer of Amazon.  I would however be rather disappointed with a generic response that I could have found myself in an FAQ.  As such, please take your time if you need to ask around to find out more about this situation before responding. Thank you again for your time.

Best,
Austin Dempewolff

You can find their email contact form [here]("https://www.amazon.com/gp/help/customer/contact-us/").

---

### Post by adempewolff on 2012-10-07
Wrote up a quick workaround [here]("http://askubuntu.com/q/197409/63478") on Ask Ubuntu.

Here is the juice of it:

> Quick and dirt workaround:

[LIST=1]
[*]Install the User Agent Switcher extension for Firefox. Any other user agent switcher/browser combination should work as well, I just have not tested them.
[*]Use the user agent switcher to switch your user agent string to IE 8. You can add the user agent switcher icon to your toolbar by right clicking the Firefox toolbar area and clicking Customize.
[*]Authorize this pseudo-browser for use with Amazon Cloud player by clicking this link. This tricks Amazon Cloud Player into thinking that you have already installed Amazon MP3 downloader--setting a cookie that will allow you to download .amz files instead of being prompted to install Amazon MP3 downloader first.
[*]Use Amazon Cloud Player to select tracks and click Download.
[*]Use Banshee to open the downloaded .amz file and it will automatically download and import the songs!
[/LIST]

Hopefully some other people will post more detailed answers, so you can keep an eye on that question for more info.

---

### Post by cybergalvez on 2012-10-08
> **adempewolff said:**
> Wrote up a quick workaround [here]("http://askubuntu.com/q/197409/63478") on Ask Ubuntu.

Here is the juice of it:



Hopefully some other people will post more detailed answers, so you can keep an eye on that question for more info.

did this today and it seemed to work work, however the files are downloaded to /tmp/banshee_amazone_downlaod folder and names withed what apprears to be random generated names. In the past there were downloaded to my music foler and named corrctly. Is there a setting I need to adjust?

---

### Post by adempewolff on 2012-10-09
Mine appear to be downloaded and named correctly to my music folder as before.  Are you sure that they aren't in your music folder as well?  Also are you sure the downloads completely successfully. I could imagine that the randomly names files are just temporary files used while it is downloading them, and when it finished it names them and copies them to the correctly folder.

---

### Post by Bigjack08 on 2012-10-30
I have just put the phone down from speaking to an Amazon technician.  She was very apologetic and agreed that I was right to be upset.  She then asked me to try following her instructions:

1. open [www.amazon.co.uk]("http://www.amazon.co.uk") and sign in.
2. open cloud player (you need to go through a few screens).
3. once into the cloud player you will see your MP3 purchase list.
4. tick the box for a download.
5. if the file is an MP3 file press save; this will save the file into your My download files.
6. if the file is an amz file press open to do the same.
7. Rythmbox application will automatically add the music.

She also agreed that the information on Amazon needs to be altered in order to show this method.  She is also sending feedback on my experience to her supervisor.


Hope this helps.

---

### Post by Bigjack08 on 2012-10-30
This is an email received from Amazon; should be useful I think.

[IMG]https://mail.virginmedia.com/mail/images/cleardot.gif[/IMG]
Hello,

I'm sorry to hear about the difficulty you had downloading "Dreamsurf: Ocean Waves For Relaxation".

To download music to your computer, visit Amazon Cloud Player ([http://www.amazon.co.uk/cloudplayer](http://www.amazon.co.uk/cloudplayer)) and check the box next to the song you want to download. Click "Download" and your selected file will begin downloading.

When you click "Download", you'll see a pop-up window with an option to  Open or Save the file. You'll also see a file name ending in .amz or  .mp3. If the file name ends in .amz, click "Open". If it ends in .mp3,  click "Save".

**Shame that they added this bit though, bit like rubing salt in the wound!!**
To download multiple files at once, the Amazon MP3 Downloader is needed.  The Amazon MP3 Downloader lets you easily download content from the  Amazon MP3 Store or from Amazon Cloud Player and automatically add your  Amazon MP3s into iTunes or Windows Media Player. You can select up to  500 files to download at one time using the Amazon MP3 Downloader.

Thanks for your interest in Amazon Cloud Player.

---

### Post by malty on 2012-11-03
This works but only one track at a time, ridiculous, I have just bought Scarlatti's Stabat Mator, 23 tracks, 23 individual downloads plus manual creation of a folder. Complaints are winging their way right now.

---

### Post by Davethehedgehog on 2012-11-03
> **malty said:**
> This works but only one track at a time, ridiculous, I have just bought Scarlatti's Stabat Mator, 23 tracks, 23 individual downloads plus manual creation of a folder. Complaints are winging their way right now.
Thanks to all for your observations.  I'm sorry to be tardy in posting this, I've been away.
I realize it's an Amazon problem, not Linux.
I tried to follow adempewolff's instructions, but can't work out how to authorize the pseudo-browser in Amazon cloud.
Perhaps I'm missing something!

---

### Post by oldos2er on 2012-11-03
The program clamz will download songs if you point it to an *.amz file. It's in the repositories: ```
sudo apt-get update && sudo apt-get install clamz
```

---

### Post by 1Geek&amp;3LittleLadies on 2012-11-18
I was just writing to say that I was now having trouble getting the AMZ file. However, when I went back to grab a screenshot of the problem, I got the AMZ file.

<fingers crossed>

---

### Post by 1Geek&amp;3LittleLadies on 2012-11-19
> **1Geek&3LittleLadies said:**
> I was just writing to say that I was now having trouble getting the AMZ file. However, when I went back to grab a screenshot of the problem, I got the AMZ file.

<fingers crossed>
The AMZ download via Firefox emulating IE8 did work last night. I was able to get my albums using clamz. I just finished listening to my downloads here at work. :-)
 
One thing I learned that wasn't at all clear to me before I got through the process is the nature of the .amz file itself. I had gotten the mistaken impression that it was like a configuration file for making a connection to your Amazon Cloud Drive. Instead, it operates more like a download script for collecting the data you requested.
 
Note: In spite of what my profile says, I'm now running Precise Pangolin 12.04 LTS. Because I haven't participated enough in the forum yet, it appears that I may be locked out of updating that information.

---

### Post by Sigma1 on 2013-08-29
Hello there,
I realise this thread is not recent, but it would seem Amazon have tightened things up again. I've followed the instructions scrupulously, but with no success. I'd be ok if I could get to the .amz files... I have even managed to get Amazon thinking I was on a IE8 W7 machine. The problem is, Amazon keeps throwing up a message telling me to install its cloudplayer. And so the link given earlier which aims to fool Amazon into thinking this is already installed does not seem to work, whether I go via my own branch of Amazon (France) or amazon.com. Any help would be very gratefully received!

---

### Post by speartip on 2013-08-29
I'm using Amazon UK but hopefully this should work for you, I have used this today so I know things are OK.
1. If not already done install clamz.
2. Go here & select your country. (At the bottom)
[http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)
3. Go to your Amazon account & deauthorize all your devices. This is in Your Cloud Player / Settings / Amazon mp3 settings.
4. Now try downloading a free song. When the review your purchase box comes up, click "Continue" , Then "Download your music now".
You should now be able to save the .amz file. Right click it & open with clamz.

---

### Post by Sigma1 on 2013-08-29
Great, thanks a lot for this. I've checked it on the Amazon France website, and it looks as if it will work. In between posts I came across an alternative solution -- which is a challenge to any logical thought -- here: [http://code.google.com/p/pymazon/wiki/HowToAmzDownload](http://code.google.com/p/pymazon/wiki/HowToAmzDownload) and in particular in this answer, about 3/4 down the page, in a comment by kael something:
> 1. When I make One-Click purchases, I get the option at that point to download the .amz file, which I can do and open in Pymazon or Clamz and all is well. 2. If I DON'T download at that point, my only option is the Cloud Player. 3. To download in the Cloud Player, I changed my user-agent via User Agent Switcher (FF extension) to IE8 and tried a bulk (.amz) download. It still told me I had to download the Amazon MP3 Downloader, so I clicked on the download button, then simply cancelled the download. After that, I saw a screen that said, "when you've installed the MP3 Downloader, click on the 'Download Your Music' button", but the button was grayed out. BELOW THE BUTTON, there was a link that said, "'Download Your Music' button not working? click here." I clicked and it apparently filled in the right cookies for the download to go through and I did a full download! 
If this turns out to be a temporary fix, though, I'll try your solution, which makes more sense to me, somehow.
Best.

---

### Post by baptx-is on 2014-01-05
I've made a Greasemonkey script so users can do multiple downloads on Amazon Cloud Player for Web: [http://userscripts.org/scripts/show/210177](http://userscripts.org/scripts/show/210177)

---

### Post by Sebastian_Gellweil on 2014-03-24
That's funny I did the same thing didn't realized somebody did that before, anayway here is mine:
[http://userscripts.org/scripts/show/426973](http://userscripts.org/scripts/show/426973)

---

