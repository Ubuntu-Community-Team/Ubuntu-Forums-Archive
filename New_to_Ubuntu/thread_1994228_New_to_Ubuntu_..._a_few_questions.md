---
title: "New to Ubuntu ... a few questions"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by History Teacher on 2012-06-02
I am relatively new to Ubuntu but I would like to switch over from Windows and learn a new OS.  I have an old laptop I'd like to experiment with.  It is a Dell 4100 Inspiron, made in 2001.  And this is pretty much all I know about it:

It's running Windows XP 
It has an Intel (R) Pentium (R) III
Mobile CPU 866 MHz
863 MHz, 320 MB of RAM

It only works when plugged into the wall.  I think the battery is dead (if that matters).  

I'm not a techie ... just an academic, I teach history at a community college.

I have a few questions before I start.  I would like to erase the Windows OS and permanently install Ubuntu.  There is nothing on this machine I want (I've saved the few things I needed).

1.  Do I need to wipe the hard drive before I start?  If so how do I do that?

2.  Will I be able to read my papers and documents I have written in MS Word in the Ubuntu word processor?

That's all I have for now.

Thanks in advance!

---

### Post by traditionalist on 2012-06-02
> **History Teacher said:**
> I am relatively new to Ubuntu but I would like to switch over from Windows and learn a new OS.  I have an old laptop I'd like to experiment with.  It is a Dell 4100 Inspiron, made in 2001.  And this is pretty much all I know about it:

It's running Windows XP 
It has an Intel (R) Pentium (R) III
Mobile CPU 866 MHz
863 MHz, 320 MB of RAM

It only works when plugged into the wall.  I think the battery is dead (if that matters).  

I'm not a techie ... just an academic, I teach history at a community college.

I have a few questions before I start.  I would like to erase the Windows OS and permanently install Ubuntu.  There is nothing on this machine I want (I've saved the few things I needed).

1.  Do I need to wipe the hard drive before I start?  If so how do I do that?

2.  Will I be able to read my papers and documents I have written in MS Word in the Ubuntu word processor?

That's all I have for now.

Thanks in advance!


1. Just put your Ubuntu disc into the machine and it will give you all the options when it boots. It will set up the machine for you.

2. Yes.

I am pretty sure you will need the 32 BIT edition of Ubuntu for that processor.

---

### Post by forrestcupp on 2012-06-02
Boot to the LiveCD before you just try to install it. That computer may not be able to handle the latest versions of Ubuntu. If not, you might want to try out Xubuntu or Lubuntu, which are lighter OSs than the main Ubuntu. Xubuntu uses the Xfce desktop environment, and Lubuntu uses the LXDE desktop environment, both of which are much lighter on resources than Unity, which is what the main Ubuntu uses.

Ubuntu comes with LibreOffice, which is their office suite with apps comparable to Word, Excel, and PowerPoint. They have compatibility with MS Office formats, but to be honest, the compatibility is far from perfect. You may notice some differences in formatting. It *is* possible to install MS Office in Ubuntu with Wine if you need perfect compatibility. Wine is a Windows compatibility layer that allows us to run _some_ Windows programs in Linux. MS Office happens to be one thing that we can get working with some tweaking. If you only need to read your .docx files and perfect formatting is not necessary, LibreOffice will do just fine.

---

### Post by LiamOS on 2012-06-02
> **History Teacher said:**
> I am relatively new to Ubuntu but I would like to switch over from Windows and learn a new OS.  I have an old laptop I'd like to experiment with.  It is a Dell 4100 Inspiron, made in 2001.  And this is pretty much all I know about it:

It's running Windows XP 
It has an Intel (R) Pentium (R) III
Mobile CPU 866 MHz
863 MHz, 320 MB of RAM

It only works when plugged into the wall.  I think the battery is dead (if that matters).  

I'm not a techie ... just an academic, I teach history at a community college.

I have a few questions before I start.  I would like to erase the Windows OS and permanently install Ubuntu.  There is nothing on this machine I want (I've saved the few things I needed).

1.  Do I need to wipe the hard drive before I start?  If so how do I do that?

2.  Will I be able to read my papers and documents I have written in MS Word in the Ubuntu word processor?

That's all I have for now.

Thanks in advance!
Since the laptop has rather low memory and processing power, I'd recommend using lubuntu instead of ubuntu. They are essentially the same, but lubuntu has a much lighter graphical frontend making it a lot easier to run on low spec machines. Lubuntu would also probably be more straightforward if you're coming from a windows background, I think. You could have a look at the two on youtube to get an idea of the differences if you're curious. I believe lubuntu comes with Abiword, which should have little trouble reading and writing MS Word documents. Regular ubuntu has the libreoffice suite which is little different from the newer MS Office programs.
You also do not need to wipe your disc before beginning(But you can if you want); the installation will give you the option of installing alongside windows or simply installing on the entire disk.

Edit: Apparently there are some slight differences in the word processors; I've obviously not used them extensively enough to notice, but I don't use them too much.

---

### Post by Curtis6767 on 2012-06-02
> **History Teacher said:**
> I am relatively new to Ubuntu but I would like to switch over from Windows and learn a new OS.  I have an old laptop I'd like to experiment with.  It is a Dell 4100 Inspiron, made in 2001.  And this is pretty much all I know about it:

It's running Windows XP 
It has an Intel (R) Pentium (R) III
Mobile CPU 866 MHz
863 MHz, 320 MB of RAM

It only works when plugged into the wall.  I think the battery is dead (if that matters).  

I'm not a techie ... just an academic, I teach history at a community college.

I have a few questions before I start.  I would like to erase the Windows OS and permanently install Ubuntu.  There is nothing on this machine I want (I've saved the few things I needed).

1.  Do I need to wipe the hard drive before I start?  If so how do I do that?

2.  Will I be able to read my papers and documents I have written in MS Word in the Ubuntu word processor?

That's all I have for now.

Thanks in advance!

Okay, first, have you downloaded a CD or USB  image of Ubuntu and if so have you tried to boot from that CD/USB? If you have not, then you should first try that. You will be running Ubuntu in a more or less virtual mode but Ubuntu will still detect your hardware, especially your internet setup and your video set up. 

If Ubuntu is able to detect these and you can get on the internet, have sound, etc, then the next step could/might be a full install.

Look over the following site and test drive Ubuntu before wiping out XP. 

[http://www.ubuntu.com/download/help/try-ubuntu-before-you-install](http://www.ubuntu.com/download/help/try-ubuntu-before-you-install)

---

### Post by linux653 on 2012-06-02
Your system probably does not have enough capacity to run Ubuntu or Kbuntu. Try an Ubuntu distro that runs XFCE or something light like that.

---

### Post by GregA on 2012-06-03
It's problematic that your system can run any current Linux system in the Ubuntu family of distributions.  Xubuntu requires aprox 512 to run with any speed, and Lubuntu is still going to be sluggish.

You may want to try a distro that specializes in "Fluxbox" - - a very light desktop interface.   Antix  has about the best live CD, installer, and Fluxbox version around.  

See here:  [http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

---

### Post by mastablasta on 2012-06-03
Lubuntu should be fine. what is the graphics card? that one might give an issue.

other light OS options:
Bodhi Linux (ubuntu based) - needs 833Mhz CPU and 128 Mb ram.
Debian LXDE (or debian based distros such as Antix, Chrunchbang, etc. for easy install)
Slitaz
Puppy
.
.
.

---

### Post by History Teacher on 2012-06-06
Thanks to everyone for the helpful information!  From the comments here, I'm thinking it might be best to install Lubuntu for this machine.  I just learned the audio card might be out.  Will that be a problem for the install?  I don't care, personally because I won't be using this machine for audio.

---

### Post by Swagman on 2012-06-06
Audio is an irrelevance to a successful install.

---

### Post by Javelin Dan on 2012-06-06
History Teacher -
 
I'm not as technically versed as most of the others, but I have a lot of experience doing what you're trying to do. I have a Dell Inspiron 8000 with a Pentium III processor and 128 original MB of RAM. I've tried all of what's been suggested (with Ubuntu and derivitives) and it won't fly on this machine.
 
First - fire up XP, click on "My Computer", go to "System Tasks", and click on "View System Info". at the bottom, you will see your current RAM displayed. If it shows less than 512 MB, you can forget about any meaningful experience with any Ubuntu derivitive. I'm not saying it won't boot, but it will be sluggish and the internet will be slooow. As previously stated, Lubuntu would be your best choice as it requires fewer resources. I successfully installed Lubuntu 12.04 on an old Dell Optiplex GX110 with 512 MB of Ram and it ran well. 
 
To be perfectly honest, if your RAM is below 512 and you don't plan to upgrade (I would consider that), your best bet would be Wary Puppy 5.3 (derivitive of Puppy Linux) that will make your old Dell fly!
 
If you have any questions about how to download, burn a disk, install or anything else, let me know and I can coach you off-line. Most of the people who monitor these forums have a lot on their plates and don't like to cover the same territory over and over again. But my learning curve sure would have been a lot smaller if someone had taken the time to drag me over the finish line.

---

### Post by Andrewmham on 2012-06-06
Max memory on that laptop should be around 1GB I would think...upgrading it isn't too hard, and the sticks (512mb) run around $30 each, might be worth looking into.

[http://www.buy.com/pr/product.aspx?sku=219856356&sellerid=18914987](http://www.buy.com/pr/product.aspx?sku=219856356&sellerid=18914987)

---

### Post by snowpine on 2012-06-06
There's a discussion of Ubuntu's hardware requirements here:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Personally my experiments with old Pentium 3 systems and Linux have been very disappointing. Have you considered upgrading your hardware? If you ask your college, colleagues, friends, family, freecycle, craigslist, you might be able to upgrade your system for free or at a very low cost. I just scored an "old" (5 years old dual core) Windows Vista computer that blows away anything in the Pentium 3/Windows XP class. It's amazing what people will give away to save the $15 recycling fee!

Just a suggestion from someone who's "been there, done that." If you assign a value to your time (say, $10/hour) then spending a few dollars on a hardware upgrade is an excellent investment. Maybe you will even find something with a working battery. :)

---

### Post by History Teacher on 2012-06-06
Thanks Javelin Dan!  Everyone has been so helpful here. I really appreciate all the thoughtful ideas. I'm considering my options right now ... and not sure what I'll do.  

By the way someone just gave me a 10 year old IBM Thinkpad.  But I'm not sure that will help me any more than the 11 year old Dell I have ... :)

I'm so new here ... how do I contact you off line?

I feel like such a newbie!

---

### Post by blackbird34 on 2012-06-06
You can send a Private Message to someone by clicking on their user name on the left and selecting "send private message to [x]" (although it's always good to post publicly, you get help from more people :D )
Alternatively you could post in the Hardware and Laptops sub forum, where there might be more competent people to help you (and give a link to this thread). In fact (maybe better) you can press the "Report Abuse" button under your user name and request for your thread to be moved there (I know, it's not strictly a case of "abuse"). 

I agree, Lubuntu would be just about OK under 320 MB of RAM, but if you can get something better, do :D

---

### Post by Javelin Dan on 2012-06-07
I *_do _*feel your pain. I'm still a very raw rookie myself. Everyone here *_is_* very polite and helpful and that isn't necessarily the case in many other forums for other Linux distributions. Even so, there is so much to know that there is naturally a certain amount of assumption of basic knowledge about Linux in particular and computers in general that you probably don't have at this point. I have always said that as a newbie, you don't even know *_what_* you don't know. In the beginning, I was so green that when I was told to simply change the boot order in my BIOS, it took me a week to figure out how to do it because no one would walk me through the process. There were certainly places to learn this, but I didn't even know where to look or what questions to ask. If I (or anyone who is willing) can help you through this process, I will. Linux is not a secret society, it's for everyone. A great place to start is to go here: [http://www.ubuntupocketguide.com](http://www.ubuntupocketguide.com). It will give you a great introduction to Ubuntu specifically, and Linux in general. Let me know if I can help and good luck!

---

### Post by Andrewmham on 2012-06-07
If it helps at all, I fired up my old (ancient really) laptop and removed a stick of RAM to give me some comparable specs to what you described...It does work, but running 12.04 LTS on a system like this is going to rob you of the full experience in my opinion. 

I was able to get things going, but it was quite painful...just very sluggish, and I had some graphics issues. Added some memory back (to give me 1GB total) and it was much better, but honestly still lacking in "snappiness." 

However, if you're not worried about having a Ferrari, I think you'll be able to tinker around enough to satisfy yourself!

---

### Post by I2k4 on 2012-06-07
Just three things:

1.  On my old machine experience (Inspiron 8100 866mhz with 512RAM and an Atom netbook) I don't think you can effectively run any version of Ubuntu after version 10.x, including the lightweights, very well on your specs.  I'd recommend Lubuntu 10.10 as being reliable (though a little crude and "frozen" for updates), or just sticking with Windows XP, for reasons below.

2.  For an academic, ability to handle MS Office documents depends dramatically on the complexity of the document - ignore the blah blah blah of those who think writing a note to grandma is a test of MS Office / OpenOffice compatibility.  If a document has a TOC or Index or any other format complexities it will likely be crudely readable, but will require big hours of work to edit for serious use in any competing (e.g. LibreOffice or OpenOffice) office software.  _If it's written in MS Office, and it's important, assume you need MS Office to work on it._

3.  I am running a clean new install of Microsoft XP Home on my 8100 (specs above) with fully functional MS Office 2000 and it is very snappy, as good as any recent Linux.  So the main thing is, decide how you want to use the machine, what software you need to do it, and then put in the right operating system.  I'm quite enjoying Linux, but would not bend myself out of shape to use it for things it cannot do well.

---

### Post by History Teacher on 2012-06-07
That's a good point ... I was wondering how well the Libre word processor software would work with bibliographic reference software such as EndNote, Refworks, or Zotero.  I just became familiar with MS Word's bibliographic management tools.  I'm not sure if Libre, Open Office, or other open source equivalents exist.

I know a lot of this can be handled online and then imported into the document.  

I haven't played around enough with Ubuntu yet to know what it can or can not do for me ... heck right now I'm trying to figure out if I have a machine I can put it on ... :)

---

### Post by Anuovis on 2012-06-07
Ubuntu***** has LibreOffice. As others have mentioned, the compatibility is far from perfect. You can be almost certain your margins and tables in *doc* files will be messed up when opened in Libre. That's the most obvious thing but there might be others.

What you can do is install LibreOffice on Windows (it's free) and try opening your files. See how it goes. 

Fortunately, it might possible to run Ms Office with Wine on Ubuntu, so that might be your best choice.

In any case, be careful with the migration. There is a good chance you will fall in love with Linux but if things go sour, it is good to have enough time to revert back to Windows or use another PC for work in the meanwhile. 

Dual-booting (when you have both Windows and Ubuntu on the same machine) might work for you too, at least temporarily.

***Note:** I am talking about Ubuntu here but, as others have mentioned, your machine is probably too old for that. So you would need to consider its derivatives like Xubuntu or Lubuntu instead. They have the same core system, lighter desktop environment and user interface (hence, saving the resources) but each of them can run LibreOffice anyway. It might not be installed by default but it's easy to add any software you want.

---

### Post by Senior_Buckethead on 2012-06-07
I was a dedicated Windows Junkie from way back, but I have to say that I have found Linux very very good.
Sure there is software that you can't get replicated in open source, but the majority of the software that I use is every bit as capable as Windows based software. Its just a different way of looking at the same problem.

I think in a low Ram machine, Lubuntu would be the way to Go. But try running live cd for a while, just to get a feel of Linux. Or dual boot, where you can have a foot in both camps.

But enjoy Linux, its changed so so much to what it was, its much more user friendly and compatible with modern file formats, such as docx and mp3.

And always feel free to ask questions. Speaking from a personal point of view its the best way for me to learn.

Take care.

---

### Post by Shadius on 2012-06-07
I agree with the Lubuntu suggestions instead of the main Ubuntu. Go for the lighter OS due to your system's specifications. Also, I'd suggest testing out how the different operating systems run on your system with the use of the LiveCD or other Live media. I tested out Ubuntu for about 2 weeks before deciding to install it. Good luck!

---

