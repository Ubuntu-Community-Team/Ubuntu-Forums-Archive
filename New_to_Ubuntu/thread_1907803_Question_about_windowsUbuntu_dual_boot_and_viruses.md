---
title: "Question about windows/Ubuntu dual boot and viruses"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by AnnB on 2012-01-12
[FONT=Verdana]My teenage daughter is a malware magnet.  I run multiple scans on her computer weekly and always find evil stuff.  I just got rid of a bad one yesterday and we decided to install Ubuntu (Oneiric) in a small partition for her to use exclusively for surfing.  Now I'm wondering if it's possible to infect the windows partition while using FireFox on Ubuntu.  It sounds unlikely, but since the windows file system is visible to Ubuntu it made me wonder....

Thank you!

Ann
[/FONT]

---

### Post by thbeau@gmail.com on 2012-01-12
reply to AnnB: I would recommand to have Microsoft essential (a virus protection) free downloadable from Microsoft site and activate it. A antivir under ubuntu shoul dalso be installed. Do a full scan under Windows before going further - b rgds - Thierry BE

---

### Post by HappyLinux on 2012-01-12
I'm wondering basically the same thing.

I'm running a dual boot setup of Mint and Win7. I'm already running an Internet security suite under windows but I'm mainly using Mint.

I know that Linux can't actually be harmed by the vast majority of Windows viruses and malware, if any at all. However, Linux can be a carrier.

However, I spotted a report that malware for Linux is on the rise due to more and more people moving from Windows.

Should I or look into a scanner for Linux, or not bother?

---

### Post by AnnB on 2012-01-12
Thierry BE,

Thank you!  Yes.  Before I installed Oneiric, I updated MSE and did a full scan, I updated Avira and did a full scan and then updated MalwareBytes and ran a full scan.  I also ran CCLeaner to remove junk files and I ran a registry cleaner.  After rebooting, I ran a full defrag/optimize using myDefrag, rebooted and then shrank the windows partition to make room for the Ubuntu installation.

So, I think if we still had a virus there, it's hiding really well.

If we use only Ubuntu for internet access, could we acquire a virus or other malware that could find and infect the windows file system?

Thank you!

Ann

---

### Post by Double.J on 2012-01-12
Hi there Happy and AnnB:

There is nothing reported as "in the wild" at the moment for linux specific malware - though of course there have been virus worms, and trojans for the system - always stay safe online; AnnB - your teenage daughter is still an obvious target, Whilst there's a lot less risk, there is still risk - malware in downloadable desktop themes, that kind of thing.

To answer can Ubuntu infect Windows - YES. Ubuntu can act as a "typhoid Mary", carrying the infections - the windows malware can't run on Ubuntu, but it can still exist there, and windows based security can't scan for it - because windows can't read the partition. 

When dual booting it is always safest to have a shared ntfs partition for things like data. This means that if she's on ubuntu and downloads a "song" that's really windows malware, or the folder contains it, it won't run (woo!) because it's in linux, but it also isn't deleted - it just stays there. If you copy it to the windows partition and run it then it's in and actually past your firewall and download scanners - so downloading in ubuntu and copying to windows could actually be more dangerous. If it's on a shared data partition a windows scanner can see and remove it.

With teenagers I suggest a "quarentine" partition - you could set up their fstab so that the windows C drive isn't writeable... only readable (or is that too mean ;) )

Either way you should have a malware scanner for each OS you have - in the case of windows I find it's best to use a paid one due to the high volume of malware!  

Don't worry you're not alone - most of the fixing of computers I've done has been to undo teenage damage.. but which of us were perfect teens?!

---

### Post by AnnB on 2012-01-12
gnu/mirow,

Thank you!  So, it sounds like a human would have to actually copy the infected file from the Ubuntu file system to the windows file system.

I have explained to her that the two different operating systems are like two different computers, but she's not stupid and can figure stuff out, so the fstab thing sounds like something I probably want to do.  What is this?  Can you point me to info about setting this up?

About paid anti-virus, I know it's probably safer than multiple layers of freebies, but malware gets by those too and I've reinstalled Vista on her machine twice already to get rid of a rootkit so if I have to do it again, what the heck.  It's tedious and boring but not technically difficult.  Plus, I'll be able to give Ubuntu a way bigger partition - she's in there right now happily installing some cool games from the Software Center, so the meager partition I made isn't going to last too long. :)

Thanks again for your detailed answer!

Ann

---

### Post by Double.J on 2012-01-12
The file fstab, located at /etc/fstab is just a table that describes how different partitions are mounted. 

The Ubuntu [help page]("https://help.ubuntu.com/community/Fstab") for fstab is a bit heavy going for a new user, so maybe also have a look at the [wikipedia entry]("http://en.wikipedia.org/wiki/Fstab"), easier going of the basics and the emaple table is very useful.

Before editing, it's probably best to do a couple of terminal things. Open a terminal with ctrl+alt+t, then copy and paste

```
sudo mkdir /Windows
```
Then
```
sudo fdisk -l
```
this should display a list of things connected to the computer - make a note of the /dev/drive number given to the windows partition (for exmaple /dev/sda2) You can close the terminal now :)

You can edit the fstab by opening the file browser, clicking on "filesystem" on the left, then the "etc" folder and scrolling down to "fstab" double click to open it in a notepad type program called gedit.

if you look at the example table on the wikipedia page, you want an entry that looks like the one called "# NTFS Windows XP partition" don't worry if your table looks a lot smaller - it probably does! The things you'd be looking to change would be where the partition is - the /dev/sda number, change the "/mnt/winxp" to /"Windows" and in the list of arguments "quite,defaults...." you'd want to add the letters "ro" and then save!

Restart to take effect, Just remember that your daughter would be able to edit the fstab herself, and that if she signed up to the forums and posted "windows unwritable" she would instantly be told how to change it, so it may be worth telling her it's meant to be that way for security... but of course that's up to you!
If you're having trouble, just post the results of your partition list (using copy and paste from terminal) and your fstab file in a reply. stick them in a quotes box by highlighting and clicking the <> button :)

---

### Post by AnnB on 2012-01-12
gnu/mirow,

Thank you!  I use Wikipedia all the time when I don't understand a technical term - the first paragraph always clears things up and gives me a context.  The problem is the wiki format - I will start with your link and a couple hours later, I will be reading about Napoleon or Reykjavik.  :)

I will read up on this and give it a try.  I don't think I will have too much trouble in the way of non-compliance.  I had to do so much tweaking to get Skyrim to quit stuttering and she knows that malware will kill performance.  The problem with windows is that stuff gets installed to run at boot time without your knowing about it and having a chance to say "no" - like when you play a Sony CD. :)

Thank you so much for your help.  Folks like you make Ubuntu even better!

Ann

---

### Post by nothingspecial on 2012-01-12
Hi AnnB,

Before you edit your fstab, make a copy of your original. If you mess it up and don't have a copy, Ubuntu may not boot anymore and it's rather complex to fix.

---

### Post by Double.J on 2012-01-12
Glad to help :) if you get into any problems, feel free to post for help!

---

### Post by mastablasta on 2012-01-12
> **AnnB said:**
>  
The problem with windows is that stuff gets installed to run at boot time without your knowing about it and having a chance to say "no" - like when you play a Sony CD. :)
 
That is not true. I am not sure what the command is in Win7/vista, but in windows you run msconfig and it opens a nice GUI where you can disable stuff that you don't want to run on boot.
 
as they already said virus can cross over. However you might have an easier time catching it if you use a virus scan on linux. rootkits will also effect linux and linux is not immune to them.
 
an even better way IMO is to teach her how to browse safely. install htings like script blocker to Firefox. 
you use Avira, but do you also use a firewall?
well even if you did the problem is still if user confirms something. like in linux. you can get a virus/malware, yet nothing will happen unless you give it your user password :-) once you confirm it can run on your computer the doors are open...
 
my kid is not so big yet, to be able to type, but i am sensing trouble ahead as well....

---

### Post by HappyLinux on 2012-01-12
Referring back to an earlier post. Fortunately for me, I use 2 USB HDDs formatted as NTFS. As for protection under Linux, which Antivirus and Malware/spyware scanner is suitable?

Under Windows I make use of a nice little selection. Norton Internet Security, SpyBot Search & Destroy.

Under Linux, the only free AV program that I know of is ClamAV, with the GUI add-on ClamTK. However, I've been reading reviews that's been saying ClamAV is rather buggy and doesn't like to update. There is a premium AV program that I know of in the form of ESET, but I don't want to be forking out money unless absolutely necessary.

---

### Post by Double.J on 2012-01-12
> **HappyLinux said:**
> Referring back to an earlier post. Fortunately for me, I use 2 USB HDDs formatted as NTFS. As for protection under Linux, which Antivirus and Malware/spyware scanner is suitable?

Under Windows I make use of a nice little selection. Norton Internet Security, SpyBot Search & Destroy.

Under Linux, the only free AV program that I know of is ClamAV, with the GUI add-on ClamTK. However, I've been reading reviews that's been saying ClamAV is rather buggy and doesn't like to update. There is a premium AV program that I know of in the form of ESET, but I don't want to be forking out money unless absolutely necessary.

I would say AVG is the best known cross platform, and I think I like avast the best. 

In terms of closed source, definitely bit defender - I can't actually work out the cost of this, I tried a 30 free trial a while back and then got warned it was going to cost me over a hundred quid and it got promptly booted off, HOWEVER I've just seen [this]("http://www.bitdefender.co.uk/site/Products/ScannerLicense/") on their sight - no mention of a time limit on the free licence - may be worth investigating? I've requested a licence, and this time havn't had to fill out any payment info - looks like I did it wrong the first time! will report back once installed that it is payment free permanently.

If it is definitely bitdefender, unless you're for the opensource,or you intend it for anything other than home usage? then as I say AVG or Avast?

All the best

---

### Post by HappyLinux on 2012-01-13
I'll give Avast a try and get back to you.

---

### Post by HappyLinux on 2012-01-14
I just tried Avast. there's no 64bit version, and AVG is for Linux Servers.

---

