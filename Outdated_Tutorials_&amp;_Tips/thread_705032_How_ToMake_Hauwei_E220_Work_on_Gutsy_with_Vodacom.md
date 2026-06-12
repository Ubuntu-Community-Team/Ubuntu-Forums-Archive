---
title: "How ToMake Hauwei E220 Work on Gutsy with Vodacom"
date: 2008-02-22
forum: Outdated Tutorials &amp; Tips
---

### Post by jbb on 2008-02-22
A  HOWTO get the HUAWEI E220 USB modem to work on GUTSY for BEGINNERS

Firstly I'd like to thank the many people who offered me help. Many thanks for your help.

Yes I also surfed the net on Windows as I could not get the USB modem to work on Ubuntu
I tried many options learning a bit here and there but did not succeed. Eventually I managed to get it to work using the following method;   I have subsequently reinstalled ubuntu 3x and each time followed this proceedure to get online 1x more

1/  Check that you have the following files installed     Note this also the order for installing without problems.
 
	python-crypto 
	python-pysqlite2	
	python-serial
	python-twisted-bin
	python-zopeinterface
	python-twisted-core
	python-twisted-conch
	python-twisted-mail
	python-twisted-lore
	python-twisted-names
	python-twisted-news
	python-twisted-runner
	python-twisted-web	
	python-twisted-words	
	python-twisted	
	
You can find and download them using Windows Just be carefull to select the correct package according to the version you have. I only had access to internet via Windows until I got it working in Ubuntu.  I found that I only had to download and install the above files.  It is possible that earlier versions may require a few extra files.   This I assume from all the QA's Howto's etc that I tracked down, read and tried while trying to get Gutsy  to work.  

	[http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

I do not know how to install the above files as a group - perhaps some guru could submit a teaching for us beginners, Yes it's laborious but it works

	sudo dpkg -i name
You can use copy and paste to save typing   Note must be full file name  I usually have a file browser window and a terminal window together so I can see the files. 
	
2/ Download and install the file   It comes as a deb type file.  so get the right one for your OS
	
	Vodafone-mobile-card-driver-for-linux 			(check for correct version)

	http:/forge.vodafonebetavine.net
3/ Having done this we need to activate the modem. Look in Applications -  Internet
You should now see an entry    “ Vodafone Mobile Connect Card Driver for Linux”

Clicking on this will cause a Splash Screen similar to this to appear.    When plugging the E220 in an info bubble will appear informing you that it has found 'new hardware'  viz  ' Huawei E220'

 
After initialising the splash screen will change to that of Vodafone as shown below.

To connect check the preferences screen  by clicking on  Tools  then     Preferences
      
      Change the entries for Username and Password to
            YOUR PINCODE

     Change Preferred Host to 
              3G preferred

     Change APN host  to 
                  internet  

Tick  box   "Use static nameservers"

Untick box  "Manage my /etc/pp..........  "
 
Leave Primary and Secondary addresses as they appear  (auto detected)


  I found that these settings work 100% for Vodacom SA   
   For other ISPs ;
  It may be necessary to untick   “ Use static nameservers”
  it maybe necessary to use a different APN host name      eg Vodafone
  it maybe necessary to use another name for User Name and Password

  NOTE  I ONLY had to make changes here to get my Huawei E220 up and running on Vodacom SA
   NO I did not have to write any scripts,  edit any *.conf files  or anything like that    

  Note the Red Disconnect Button shown is also the Green Connect button
	Yes you can send and receive sms's    (beat that Windows)
	Yes you can surf and upload/download files

I hope that readers will find this HOWTO useful and be able to solve their problems with the Huawei E220

I have only tried this on the Ubuntu Gutsy revision    but it should work on others

You can email me for the screen shots if you feel u need them

 [EMAIL="jbb@gmail.com"]jbb@gmail.com[/EMAIL]

---

### Post by Isthisok on 2008-03-11
Thank you very much. After two weeks faffing about with huaweiAktBbo and wvdial.config, 
](*,) 
I now have a useable interface which not only connects but was able to enable my PAYG account with 3UK. I'd tried your route before on Mandriva, but rapidly ran into dependency problems. No problems at all with Gutsy, though, once I'd got the configuration right (3UK send you irrelevant DNS addresses if you let them - use static DNS - and the DNS supplied on install are those of Vodafone Spain)

One niggle, there is a complaint from Synaptic about dependencies when you try to install -twisted-lore; swap this with -twisted-web in your install order and all is well.


Anyone else,
Downloaded the packages on a Windoze box and burnt them to CD (which Synaptic likes); just open the CD and click on them. You'll need to enter your username 14 times, which is quicker than typing the 14 package names into dpkg, I reckon...

 And don't waste your time with the other fixes. This one works, and it doesn't take as long.

At last. Many many thanks! \\:D/

---

### Post by onegreenparker on 2008-05-12
Anyone tried this with Hardy yet?

---

