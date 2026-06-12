---
title: "Thunderbird, Lightening, and SoGo Installation Help"
date: 2014-12-07
forum: New to Ubuntu
---

### Post by coleus2 on 2014-12-07
Hello Ubuntu People,

I'm relieved to have found this forum! I'm an EXTREME novice with Ubuntu. My first exposure to the OS happened today when I installed it on my computer via USB. If I have overlooked relevant threads, kindly point me to them.

My goal is to get Thunderbird running smoothly with Lightening and SoGo for CalDAV and CarDAV support. I attempted to block automatic updates of Thunderbird and Lightening to prevent update-related incompatability among the applications. I'm unsure if it worked. I'm posting here because my fundamental ignorance about Linux/Ubuntu has undermined my ability to troubleshoot this myself. Below I'll list my questions; the relevant specs; and what I've already tried to resolve the issue. No feedback is too basic. I truly need all the help I can get. Ugh ... Have I messed things up? Thanks for reading.

QUESTIONS:
(1) Are the below versions of Thunderbird, Lightening, and SoGo mutually compatible and compatible with Ubuntu?
(2) Does the error &#8220;Unable to lock the download directory&#8221; mean that I failed at freezing the current version of Thunderbird and/or Lightening?
(3) What is my next step in getting SoGo installed? FYI: There's no add-in option via Thunderbird.

SPECS:
Ubuntu 14.04
Thunderbird 31.3.1 (preinstalled on Ubuntu)
Lightening 3.3.3 (installed by me via add-on in Mozilla)
SoGo 2.1.1b-1 (HELP!)

WHAT I TRIED:
I found 2-step instructions on the bottom of this SoGo page [http://www.sogo.nu/english/](http://www.sogo.nu/english/)
support/faq/article/how-to-install-sogo-on-ubuntu.htm. I &#8220;think&#8221; the signature-command step worked (sudo apt-key adv --keyserver keys.gnupg.net --recv-key 0x810273C4). However, the apt-source-list step (deb [http://inverse.ca/ubuntu](http://inverse.ca/ubuntu) trusty trusty) doesn't seem to have worked. I entered the command in the terminal but still can't access SoGo. Synaptic permitted me to then install SoGo and SoGo Common. Other SoGo entries produced
E: Can't be authenticated
E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Unable to lock the download directory

---

### Post by nerdtron on 2014-12-07
HHmmmm.. I may not help you with SoGo but I think if you are a novice and creating an email server, I have a suggestion.

I used iRedMail package to install a complete mail server, with antivirus, Rouncube web mail, spam filter, postfix, dovecot, fail2ban, etc. Basically I just run the installer, provide details and credentials, and it would setup itself in maybe less an hour.
I'm not saying it would be perfect for your but I would say it is worth a shot if you are having a difficulty settings up a email server.
Website: [http://iredmail.org/](http://iredmail.org/)
installation:  [http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html](http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html)

---

### Post by coleus2 on 2014-12-07
Hi Nerdtron,

Thanks for taking the time to reply.

I don't think what I'm setting up is an email server. I'm simply looking to set up my personal email, calendar, and contacts with open sorce software.  My email provider manages the server. That email provider recommends Thunderbird with the Lightening (for CalDAV) add SoGo for CardDav, so I know that combo can work well together. 

My problem is that I just took the plunge into Ubuntu less than a day ago and I'm not sure how to troubleshoot command lines, package managers, and repositories! Despite the troubles, I'm really impressed with Ubuntu. 

Do you think my post is best suited to stay in the current forum?

Also,  I just noticed about 4 lines of text scrolling by very quickly before the purple Ubunto screen loaded. I'm concerned that indicates errors are present but the texts scrolls too fast to read. How to I know what's going on?

Thanks for taking your time. And yes, I Googled this stuff but couldn't find a definitive answer. :-)

---

### Post by grahammechanical on 2014-12-07
> [COLOR=#000000]I just noticed about 4 lines of text scrolling by very quickly before the purple Ubunto screen loaded. I'm concerned that indicates errors are present but the texts scrolls too fast to read. [/COLOR]

Ubuntu is built on Linux. First Linux is loaded and then at some point Ubuntu loads on to Linux. It is normal for Linux to print messages to the screen as it goes through the process of loading various hardware modules and stuff. Do not get distracted by this.

We know when we have problems. Oh yes. If the boot loader cannot find the Linux kernel. You will know it. If the Linux kernel cannot do its stuff you will know it. If Ubuntu cannot load. You will know it. If the desktop cannot load beyond the login screen. You will know it. Believe me.

Even if we get a system crash after loading to a desktop it does not necessarily mean Ubuntu will stop working. Applications can crash and Ubuntu will keep on working.

Where did you get SoGo from? Has it been packaged for Ubuntu? And has it been packaged for Ubuntu 14.04?

Regards.

EDIT: The Ubuntu Software Centre is a very useful tool and not just for those new to Ubuntu. I see that SoGo is in the software centre. In my opinion, installing from the software centre is much preferable to downloading the software from some web site because we can be assured that all the dependant libraries (packages) will also be installed. We are less likely to get that broken packages problem when we install applications using the Ubuntu Software Centre.

When updating or installing packages the relevant utility needs to lock certain directories to prevent their contents being modified by some other process. This is why we should not use more than one method of installing/updating software at the same time. One utility will lock those directories and prevent the next one from also locking them or editing the contents.

---

### Post by coleus2 on 2014-12-07
Hi drahammechanical: ):P

Thanks so much for taking time to reply. 

I've found conflicting information about whether SoGo is compatible on Trusty Tahr. I went to the download center (Duh ... thanks for the clue!) and found three SoGo choices, none of which were compatible with Ubuntu 14.04.  [https://apps.ubuntu.com/cat/search/saucy/?q=sogo](https://apps.ubuntu.com/cat/search/saucy/?q=sogo). 

However, on the SoGo installation page [www.sogo.nu/english/support/faq/article/how-to-install-sogo-on-ubuntu.html](www.sogo.nu/english/support/faq/article/how-to-install-sogo-on-ubuntu.html) it says this: "How to install on Ubuntu. If you're using Ubuntu Trusty Tahr (14.04), add to your apt source list (/etc/apt/sources.list):deb [http://inverse.ca/ubuntu](http://inverse.ca/ubuntu) trusty trusty.  (That's what I did but I dont know how to actually get SoGo out of Synaptic (so to speak) and communicating with Thunderbird.

To which source should I defer? 

Have a fully-functioning email client is the top priority for me and the threshold issue to address before removing windows from my life. I appreciate the feedback so far and look forward to more.

For now, I'm confused. :confused:

---

### Post by Rex Bouwense on 2014-12-07
When you are confused it is best to ask a question.  I discovered a few years ago that if I wanted applications to run flawlessly, my best bet was to look in the repository.  I am not using Ubuntu but rather Lubuntu 14.04.  The repositories are basically the same.  Thunderbird and SoGo are there and as grahammechanical has already stated using the Software Center is the best way to get it installed.  If you have already installed Lightening as a plug in and it is working don't worry about it.  If a Thunderbird plug in will not work, Thunderbird will tell you.

---

### Post by Bucky Ball on 2014-12-07
I'm using Synaptic Package Manager, but you'll find Sogo in Software Centre, too. I did a search for it and it gives me Sogo version 2.1.1b-1. Am using 14.04. 

A 'Scalable groupware server' it tells me. Is that it? If so, in the Software Centre. With Ubuntu, always a good idea to look there first and avoid dragging in numerous PPAs and third-party bits.

* Ninja-ed by Rex: +1 to what he imparts.

---

### Post by coleus2 on 2014-12-07
Hi Rex,  Thanks for taking time to comment.  Thunderbird is behaving nicely, but without the addition of Lightening and SoGo, I can't get full use of my calendar and contacts. I went to the Ubuntu Software Center on my computer and see that SoGo is installed.   How do I actually access SoGo so I that can connect it to Lightening? That seems like such a basic question, but I'm used to installing a program on Windows and then accessing it in the programs folder.  Or seeing a shortcut on the desktop.   Previously, I had used SoGo as an adjunct to Thunderbird in a Windows environment. I just assumed it would be possible to do that in Ubuntu, also. Maybe not?    Thanks again.

---

### Post by Bucky Ball on 2014-12-07
Just throwing this in. Launch Thunderbird>Tools>Add-ons>search for Lightening. It's right there. I have it installed and working beautifully and didn't even realise that's what I was using. ;)

I spotted it about six months ago, thought it looked useful, so gave it a try. I don't use it often, but does come in handy.

---

### Post by coleus2 on 2014-12-07
Hi Guys,  I'm already using Thunderbird, too. If my posts have seemed to indicate that I couldn't find it, that's not the case.  I just cant figure out how to get SoGo out of the Ubuntu Software Center so I can set it up with Thunderbird. I know it's here somewhere but I can't figure out how to open it.  The software center just tells me that it's installed but doesn't let me execute it to set things up.  Looking forward to hearing a really simple solution that I somehow missed!  Thank You!

---

### Post by Bucky Ball on 2014-12-07
Have you tried 'sogo' in a terminal? Might work. And you have Lightening installed as a Thunderbird add-on via Tools in Thunderbird (not via a third-party ppa or .deb file)?

---

### Post by coleus2 on 2014-12-07
Bucky Ball,        I didn't know I could try "SoGo" in a terminal.  But I just tried and got the following:    "No command SoGo Found. Did you mean command 'sogod' from package SoGo (universe)?"        So, I entered "sogod" in the terminal. I got: "command not found."     Anything else I can try at this point?     To answer your question: I installed Lightening by using the add-on feature in Thunderbird for Ubuntu.  Does that shed light on the situation?        How does one typically execute a program installed on Ubuntu? It can't be as complicated as it seems. I must be missing something, no?  Like I said, my frame of reference (Windows) has been clicking on a shortcut or the program itself. Teach me the ways of Ubuntu! ;-)      Thanks everyone for your time.

---

### Post by Bucky Ball on 2014-12-07
Terminal commands should be lower case. Have you tried 'sogo' in a terminal, all lower case?

See my PM regarding paragraphs. Stuff of a new thread. ;)

---

### Post by amanchesterman on 2014-12-08
Hi Coleus2, I'm a little puzzled as to why you are having such difficulties. I don't use SoGo myself but the instructions on line seem simple enough?
If you go here [http://www.sogo.nu/files/docs/SOGo%20Mozilla%20Thunderbird%20Configuration.pdf](http://www.sogo.nu/files/docs/SOGo%20Mozilla%20Thunderbird%20Configuration.pdf) there's a document which explains how to set up Thunderbird with Lightning and SoGo. It points you to a page on the SoGo website from where you can download **SoGo extensions for Thunderbird** that 'plug in' in the same way as Lightning (which you have already done). There are two of them so that you can choose the degree of integration you want to have.
You don't mention that you have tried these extensions, and I don't understand why not: don't they work on your machine?

---

### Post by coleus2 on 2014-12-08
Bucky:

Yes, I did try lower case command at the terminal. The terminal couldn't find "sogo."  

I can see In the Ubuntu Software Center that SoGo has been installed.  I just dont know where to go to execute it/connect it to Thunderbird. (I need to enter CarDAV links etc.)  

When I set it up previously in Windows, it was not a conventional Thunderbird add-on via Mozilla's site but an external link from SoGo.

So, that being said, does anyone know where I click to use SoGo once it's been installed?

Thanks much!

---

### Post by coleus2 on 2014-12-08
Hi Amanchesterman,



You are not the only one who's puzzled about why I'm having such difficulties! ](*,)

Thanks for providing the link for that documentation.  I believe I've already downloaded all the software mentioned therein (although I haven't given that document the attention it deserves yet). That being said, SoGo does not automatically connect itself to Thunderbird, and I just need to know where to click to open it.  

I do plan to give that documentation a very close read as soon as possible.

Thanks for taking the time to give feedback.

Coleus2

---

### Post by amanchesterman on 2014-12-09
Thunderbird extensions do not 'automatically connect themselves' to Thunderbird when you download them. None of them -- it's not just SoGo. What you have to do is:
1) Download the extension from the address specified in the document (not from the Software Center)
2) Install it in Thunderbird by
a) going to Tools > Add-ons to bring up the Add-ons Manager
b) going to the small tools icon which is immediately to the left of the search bar at the top right of the page
c) using the tools menu to select 'Install add-on from file'
d) following the dialogue to find and click on the extension you downloaded
3) When that has completed, restart Thunderbird
But first read the document I recommended to you: it contains a lot of information on how to get SoGo working successfully.

---

### Post by joe1232 on 2015-10-01
Hey there,
I know it's a little late, but for people searching for the **_SOLUTION_**:

Just follow the instructions from the post above. There is only one little trick which drove me crazy until I found it out... When you try to download the add-on from the sogo-homepage Firefox will try to install the add-on. Which is obviously not possible since it's not a firefox-add-on.
Right-click the download-link for the SOGo Connector (not the Integrator!) and click "Save target in..." (or whatever the English text says). You can then download the add-on and follow the instructions above.

[http://www.sogo.nu/downloads/frontends.html](http://www.sogo.nu/downloads/frontends.html)

---

