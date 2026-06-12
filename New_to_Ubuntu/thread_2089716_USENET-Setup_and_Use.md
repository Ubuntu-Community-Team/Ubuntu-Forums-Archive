---
title: "USENET-Setup and Use"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by Kenyan-Newbie on 2012-11-30
Please walk me through setting-up and using free USENET. I've tried reading a few guides but I'm guessing I'm a little slow:(

I use a dongle to connect to the net.
Thank you

---

### Post by Lars Noodén on 2012-11-30
Probably the easiest way is to connect to the Usenet server provided by your ISP.  On your side you'll have to choose a newsreader and point it at the Usenet server.  There are quite a few good ones.  I prefer tin, even though it is text-based, it is quite easy to use and flexible.

---

### Post by Zill on 2012-11-30
Kenyan-Newbie:  As Lars Noodén has suggested, first see if your ISP provides a Usenet (NNTP) server as this should be the easiest option.  However, please note that NNTP has gradually fallen into disuse, mainly due to incredible amounts of spam, and so many ISPs no longer provide NNTP servers.

If your ISP does not supply a NNTP server then there are (or used to be!) some free servers available.  One example (that I have previously used) is [albasani.net]("http://albasani.net/index.html.en").

There are many good NNTP clients around, such as [Pan]("http://pan.rebelbase.com/") and [claws-mail]("http://www.claws-mail.org/").  However, if you already have Thunderbird installed then this has NNTP capability built-in.

See "[Creating a Newsgroup Account]("https://support.mozillamessaging.com/en-US/kb/creating-newsgroup-account?s=usenet&as=s")" for configuration details.

---

### Post by andrew.46 on 2012-11-30
Free nntp servers are not the thing they used to be, I would suggest paying the small sum of €10 per year for quality, filtered access from individual.net. This is a service I have used for many years (text groups only) and I would highly recommend it. One of the better usenet clients is slrn and there is a nice Ubuntu Community Docs page dedicated to its setup:

[https://help.ubuntu.com/community/slrn](https://help.ubuntu.com/community/slrn)

But if a full gui is your choice there is Pan...

---

### Post by Kenyan-Newbie on 2012-12-01
Thank you Lars Noodén, Zill and andrew.46 for your prompt replies.

There is too much info out there, which makes its all too confusing. For 2 whole days :(I've installed, uninstalled, tried this tried that but nothing seems to work! My ISP is Orange, a mobile network that doesn't seem to support any Usenet server. I'm in Kenya.

This is where I am. I've registered with NZBMatrix (I get to download files newer than 20 days, for a test of this NZB its ok), then I installed SABnzbd+. 

I tried to download an nzb, the prompt 'Open With' has no SABnzbd+ in it:(
When I try opening the web-site interface [[http://localhost:8080/sabnzbd/queue/]](http://localhost:8080/sabnzbd/queue/]) to troubleshoot settings, I get 
[Firefox can't establish a connection to the server at localhost:8080]   (I'm using Iceweasel):(

Help (But please lets limit ourselves to this two, as a start. Any more providers or readers and my head might explode. I've tried setting up slrn and klibido but ended up more frustrated)



Additional info
This is how my Network Settings looks like (I've adjusted it a few times, afraid I could have messed it up)
**General Tab**
Host name ~ Kenyan-Newbie
Domain name ~ Blank
**Hosts Tab**
127.0.0.1  ~  Kenyan-Newbie  localhost.localdomain  localhost
::1   ~     ip6-localhost  ip6-loopback
fe00::0   ~  ip6-localnet
ff00::0   ~   ip6-mcastprefix
ff02::1   ~  ip6-allnodes
ff02::2   ~  ip6-allroutes


When I tried  [[http://host:port/sabnzbd/api]](http://host:port/sabnzbd/api])  in root, it gave me [No such file or directory]

---

### Post by Zill on 2012-12-01
> **Kenyan-Newbie said:**
> ...This is where I am. I've registered with NZBMatrix (I get to download files newer than 20 days, for a test of this NZB its ok), then I installed SABnzbd+...
I have never heard of NZBMatrix but their [website T&Cs]("http://nzbmatrix.com/terms.php") state:
> NEWSGROUP / USENET ACCESS
This site (nzbmatrix.com) does not provide any access to The Usenet, Newgroups or the Internet. It only provides a automated index of The Usenet.

If you require access to Usenet please use your ISP's own Usenet server or a third-party paid "Premium" provider.
The information you have posted seems to relate to internet connectivity, rather than newsgroup access.  Host names and domain names etc are irrelevant to an NNTP newsgroup/usenet server.

Firstly, I must ask if you are confusing internet access with Usenet?  In other words, does your broadband dongle connect to the net correctly so that you can surf websites and send emails etc.  If so then your network connectivity is working OK, meaning that the hosts and domains are set up correctly.

If this is working then you need to choose a suitable newsgroup/Usenet NNTP server.  If your ISP does not provide one then you will need to register with a free or subscription service, such as those already listed in this thread.

Once you have done this it is simply a matter of opening your chosen client application and entering the newsgroup server and username details for your Usenet account.  You can then subscribe to any of the thousands of newsgroups available.

---

### Post by Kenyan-Newbie on 2012-12-01
> **Zill said:**
> I have never heard of NZBMatrix but their [website T&Cs]("http://nzbmatrix.com/terms.php") state:

The information you have posted seems to relate to internet connectivity, rather than newsgroup access.  Host names and domain names etc are irrelevant to an NNTP newsgroup/usenet server.

Firstly, I must ask if you are confusing internet access with Usenet?  In other words, does your broadband dongle connect to the net correctly so that you can surf websites and send emails etc.  If so then your network connectivity is working OK, meaning that the hosts and domains are set up correctly.

If this is working then you need to choose a suitable newsgroup/Usenet NNTP server.  If your ISP does not provide one then you will need to register with a free or subscription service, such as those already listed in this thread.

Once you have done this it is simply a matter of opening your chosen client application and entering the newsgroup server and username details for your Usenet account.  You can then subscribe to any of the thousands of newsgroups available.

I am connecting to the net, its how I got to post this.

I have sent mail to [albasani.net]("http://albasani.net/index.html.en"). (their requirement for registration) and will let you know how it goes. That way, we can work with [albasani.net]("http://albasani.net/index.html.en") and SABnzbd. Thank you.

---

### Post by Zill on 2012-12-01
> **Kenyan-Newbie said:**
> ...I have sent mail to [albasani.net]("http://albasani.net/index.html.en"). (their requirement for registration) and will let you know how it goes. That way, we can work with [albasani.net]("http://albasani.net/index.html.en") and SABnzbd...
The albasani.net registration is all you need.  I don't know why you have chosen SABnzbd as a client when you probably already have Thunderbird installed!

Just set up "news.albasani.net" as the server with your account details as authorisation and away you go...

---

### Post by Kenyan-Newbie on 2012-12-02
> **Zill said:**
> The albasani.net registration is all you need.  I don't know why you have chosen SABnzbd as a client when you probably already have Thunderbird installed!

Just set up "news.albasani.net" as the server with your account details as authorisation and away you go...

:) I'm learning. Now I have an account with albasani, I've downloaded Icedove (I read its Thunderbird renamed) set up news.albasani.net and its shows connected, albeit for a few minutes before being timed out.

So with this, where do I go to choose an NZB file for download? And how will I know its downloading?

---

### Post by Zill on 2012-12-02
> **Kenyan-Newbie said:**
> ... I have an account with albasani, I've downloaded Icedove (I read its Thunderbird renamed) set up news.albasani.net and its shows connected, albeit for a few minutes before being timed out...
I am surprised you had to install Icedove as later versions of Ubuntu have Thunderbird installed by default!  However, Icedove is effectively the same program so works in exactly the same way.  If you have configured this correctly (as per my earlier link [Creating a Newsgroup Account]("https://support.mozillamessaging.com/en-US/kb/creating-newsgroup-account?s=usenet&as=s")) then this should work OK.  Time-out problems may be due to server congestion or, more likely, your internet connectivity.

With a good connection, Icedove should download a list of newsgroups for you to choose the ones you wish to subscribe to.  This will enable you to read and post to your chosen newsgroup threads.
> **Kenyan-Newbie said:**
> ...So with this, where do I go to choose an NZB file for download? And how will I know its downloading?
Until I read your postings I knew nothing about NZB files!  Having now done some research it seems that they basically relate to the sharing of  binary files.

The original concept of Usenet was to allow users to exchange info via simple text files and these "newsgroups" were only later expanded to include binary files.  AIUI, the main use for Usenet binary files is to distribute "warez" with dubious legitimacy.  Please correct me if I am wrong!

The information I, and others, have provided to you in this thread relates to connecting to simple text newsgroups.  You should therefore now have this access.

However, if you wish to download binary files of dubious legality then I regret to advise that I cannot (and would not!) help with this.

---

### Post by Kenyan-Newbie on 2012-12-02
> **Zill said:**
> I am surprised you had to install Icedove as later versions of Ubuntu have Thunderbird installed by default!  However, Icedove is effectively the same program so works in exactly the same way.  If you have configured this correctly (as per my earlier link [Creating a Newsgroup Account]("https://support.mozillamessaging.com/en-US/kb/creating-newsgroup-account?s=usenet&as=s")) then this should work OK.  Time-out problems may be due to server congestion or, more likely, your internet connectivity.

With a good connection, Icedove should download a list of newsgroups for you to choose the ones you wish to subscribe to.  This will enable you to read and post to your chosen newsgroup threads.

Until I read your postings I knew nothing about NZB files!  Having now done some research it seems that they basically relate to the sharing of  binary files.

The original concept of Usenet was to allow users to exchange info via simple text files and these "newsgroups" were only later expanded to include binary files.  AIUI, the main use for Usenet binary files is to distribute "warez" with dubious legitimacy.  Please correct me if I am wrong!

The information I, and others, have provided to you in this thread relates to connecting to simple text newsgroups.  You should therefore now have this access.

However, if you wish to download binary files of dubious legality then I regret to advise that I cannot (and would not!) help with this.

:(I hear you, but I might have been judged abit too harshly!

I'll give you examples, when I get out of my abode, there are all manner of people walking around. From priests to hooligans. Does it mean that I don't get out? The selection of food lies between the very nutritious to the toxic. Do I not eat? Even worse is when I go to hospital. From terminal illness to minor check-ups, would you have me go? Internet? Hackers, Spammers, Educators, healers and more. All in the basket.

@Zill, Please let me make my choices, this with the utmost respect. If it makes you feel any better, I might not have much use for items of 'dubious legality'.

---

### Post by Zill on 2012-12-02
> **Kenyan-Newbie said:**
> :(I hear you, but I might have been judged abit too harshly!...
@Zill, Please let me make my choices, this with the utmost respect. If it makes you feel any better, I might not have much use for items of 'dubious legality'.
You are, of course, free to make your own choices and please accept my apologies if I have misunderstood your intentions.

If you know of legitimate NZB/binaries on Usenet then I would be interested to know what they are.

---

### Post by Lars Noodén on 2012-12-03
I've never used binaries of any kind on Usenet.  As far as I saw, it still sees a lot of activity in various hobbies and interest groups.  For low-connectivity, it is a good communications method.  It is unfortunately heavily attacked by astroturfers and trolls, some paid, depending on the topic.

---

