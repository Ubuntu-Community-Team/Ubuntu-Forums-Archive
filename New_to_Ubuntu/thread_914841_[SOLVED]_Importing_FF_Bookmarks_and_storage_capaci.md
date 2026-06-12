---
title: "[SOLVED] Importing FF Bookmarks and storage capacity....."
date: 2008-09-09
forum: New to Ubuntu
---

### Post by jakewc2 on 2008-09-09
Hi, I have been looking round my Ubuntu, and am really pleasantly surprised by it, the interface is good, the way it handles is good, good speeds when surfing the net. 

I have on my Windows partition, about 800 Bookmarks, which I would really like to import my bookmarks. 

What amazed me with this installation, is that it recognised my external hard drive, and I can see everything on it. The EHD updates everyday on Windows, and just looking now, I can see the bookmarks. Can I import from the EHD directly to FF in Ubuntu? 

Plus,  how do I find out how much disc space I have been allocated in this partition, and if needed increase the space.

Thank you for your help.

John.

---

### Post by Dill on 2008-09-09
If you open a terminal and type 

```
df -h .
```

You should see the space available and space used on your partition.

For importing your FF bookmarks... some others may be of more help, but what type of file is it? Your profile information is stored in a hidden directory called .mozilla in your home directory. The full path to your FF profile will be **~/.mozilla/firefox/aaabbbccc.default**, where aaabbbccc is some alphanumeric string. My profile, for instance, is named *l0qgjx2c.default*. Therefore, you'll probably want to open up a terminal and type...

```
cd ~/.mozilla/firefox
ls
cd aaabbbccc.default
ls
```

The only bookmark file I see in there is an html file called bookmarks.html. If the Windows bookmarks are in this format, you should be able to just copy them from your external HD and rock and roll

```
cp /path/to/bookmarks/bookmarks.foo ~/.mozilla/firefox/aaabbbccc.default
```

---

### Post by jakewc2 on 2008-09-09
Hi, thank you for the help. I just did that and found out its given me 13gig, and there's just over 9gigs left. 

How do I go about increasing it if its needed?

---

### Post by Dill on 2008-09-09
You might look into GParted:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

When I first partitioned my hard drive in preparation for installing Ubuntu, I used this and it worked great. I've resized the partitions multiple times without problem, or, for that matter, any loss of data.

---

### Post by Dill on 2008-09-09
This may help, too:

[http://www.ubuntux.org/how-to-install-partition-editor-gparted](http://www.ubuntux.org/how-to-install-partition-editor-gparted)

---

### Post by Victormd on 2008-09-09
Regarding your FF bookmarks, open a terminal and type (with FF closed):
```
firefox -profilemanager
```
Then create a new profile and point the profile directory to your windows profile folder. This way, anything you add to FF (bookmarks, themes, etc.) in ubuntu will automatically update in windows, and vice-versa...

---

### Post by jakewc2 on 2008-09-09
Hi, thank you all for your messages, sorry I took so long to reply.

Ok, I think I might go for the new profile approach. I opened the profilemanager, but I cant find anywhere to point to the directory. Can somebody show me how to do that please? Thank you.

Also, with the partition program, as I have not installed the partition, plus I am not up to date with installing programs, how do I go about what you suggested. 

I am so sorry for all the questions.

Thank you for you help.

John.

---

### Post by Therion on 2008-09-09
How does anyone who uses Firefox exist without the [Foxmarks](http://www.foxmarks.com/) bookmark synchronizer plug-in???

So essential IMO...

---

### Post by jakewc2 on 2008-09-09
Um,I tried to use my brain to see if I could manage the task, so decided to try and do it this way.....

Open a terminal window and type in:
sudo apt-get install gparted

After that you can find GParted in the Gnome menu under Applications -> System Tools.

That work sort of, but I couldnt find System Tools in the Application Tray, am I missing something?

Thank you.

John.

---

### Post by jakewc2 on 2008-09-09
I used to have it on my windows, but something just wouldnt work, I just kept loosing all my Bookmarks, none would be saved. They were there when I manually saved to the Bookmarks File, but when it Synchronised, all the new Boomarks got lost for some reason, so I uninstalled it. :( Which is a pain as I have 2 machines with about three different Browsers, all using it. I just gave up. :(

---

### Post by Victormd on 2008-09-15
> **jakewc2 said:**
> Ok, I think I might go for the new profile approach. I opened the profilemanager, but I cant find anywhere to point to the directory. Can somebody show me how to do that please? Thank you.

When you get to the profile manager, you should have something like the first screen shot (attached). Click on the "Create Profile..." button, then next, then you should get to the second screen shot (attached). Simply change the profile name (i.e., Default User) to whatever you want and hit the "Choose Folder..." button. Point to where you want the new profile to be located and click on Finish. Note that your original FF files are normally located under
> /home/YOURUSERNAME/.mozilla/firefox/PROFILENAME
You can copy the files from the above location to the new profile folder you've defined. This will copy all themes, add-ons, bookmarks, etc.

You can then do the same under Windows and point to the same folder so both will share the settings.

---

### Post by egalvan on 2008-09-15
> **jakewc2 said:**
> Hi, I have been looking round my Ubuntu, and am really pleasantly surprised by it, the interface is good, the way it handles is good, good speeds when surfing the net. 

[B]I have on my Windows partition, about 800 Bookmarks, which I would really like to import my bookmarks. 
[/B]
What amazed me with this installation, is that it recognised my external hard drive, and I can see everything on it. The EHD updates everyday on Windows, and just looking now, I can see the bookmarks. Can I import from the EHD directly to FF in Ubuntu? 


Thank you for your help.

John.

To import stuff from IE to FireFox, check out this page...

[http://support.mozilla.com/en-US/kb/Importing+bookmarks+and+other+data+from+Internet+Explorer](http://support.mozilla.com/en-US/kb/Importing+bookmarks+and+other+data+from+Internet+Explorer)


I used the info there to move over years of stuff from IE (over 4,000 bookmarks :shock:  since culled with some bookmark-editing addons).
Since I only use FireFox now, I no longer need to move from IE to FF.
I recommend sticking with one browser for your serios stuff, and using the others only as needed.
I do on VERY rare occasions use IE for some browsing.

FireFox and IE cannot directly share information.

FireFox on Windows and Linux CAN use the SAME profile, so you are always using the same profile no matter the operating system,

I keep my FF profile on a USB hard drive, and move it from my destop (dual-boot) to my laptop (dual-boot also). never have to worry about  not having bookmarks, add-ons, plug-ins, or security features such as passwords. Sweet, and simple... something MS seems to never manage quite right.

ErnestG

---

### Post by egalvan on 2008-09-15
> **Therion said:**
> How does anyone who uses Firefox exist without the [Foxmarks](http://www.foxmarks.com/) bookmark synchronizer plug-in???

So essential IMO...

How? Foxmarks keeps MY information on THEIR machine.

I prefer to keep MY information on MY machine, thank you very much.

It's all on a USB drive.
Encrypted.
Backed up.
Mine.

ErnestG

:popcorn:

---

### Post by egalvan on 2008-09-15
> **Victormd said:**
> ,,, you should have something like the first screen shot (attached). Click "Create Profile..."  ,,,then  get to the second screen shot (attached). ,,,,change the profile name (i.e., Default User) to whatever you want and hit the "Choose Folder...",,. Point to where you want the new profile to be located and click on Finish. Note that your original FF files are normally located under

You copy the files from the above location to the new profile folder you've defined. This will copy all themes, add-ons, bookmarks, etc.

You  then do the same under Windows and point to the same folder so both will share the settings.

As I read the OP, he is using Internet Explorer under Windows,
and Firefox under Ubuntu.

Is your post saying that Firefox and Internet Explorer will share the same folder?

---

### Post by Victormd on 2008-09-15
> **egalvan said:**
> As I read the OP, he is using Internet Explorer under Windows,
and Firefox under Ubuntu.

Is your post saying that Firefox and Internet Explorer will share the same folder?

The OP said that he has ~800 bookmarks on an external HD so I'm assuming he's using firefox under windows and Ubuntu so my post lets both versions of firefox use the same profile. As far as I know, Firefox and IE will not share the same folder.

---

### Post by egalvan on 2008-09-15
> **victormd said:**
> the op said that he has ~800 bookmarks on an external hd so i'm assuming he's using firefox under windows and ubuntu so my post lets both versions of firefox use the same profile. As far as i know, firefox and ie will not share the same folder.

ok

---

### Post by jakewc2 on 2008-09-15
Hi both, thank you for your help, I really appreciate it.

I do have my bookmarks on my external hard drive,but they are nightly backups of all bookmarks.

I was just wondering, I dont have the same look and addons for windows and ubuntu, and I quite like the way they both look. I was just wondering, can I move my bookmarks to my external hd, and point to it, instead of setting up a new profile? Just thought it might be easier.

John

---

### Post by Therion on 2008-09-15
> **egalvan said:**
> How? Foxmarks keeps MY information on THEIR machine.

I prefer to keep MY information on MY machine, thank you very much.

It's all on a USB drive.
Encrypted.
Backed up.
Mine.

ErnestG


Whoopee.  So use your USB drive and be happy.

Some of us don't mind having immediate access to our bookmark's from an offsite archive from any computer anywhere that sports an internet connection.  

I understand how fascinated the entire world is to know what you've got bookmarked, though, and specifically the folks at Foxmarks!!  My gawd I've personally been losing sleep over this for I don't know HOW long now...

:rolleyes:

---

### Post by jakewc2 on 2008-09-15
Oh dear, I am really sorry that I seem to have caused a little bit of a problem here. I didnt mean too, I am goin to be enough of a problem as it is, with all the questions I will have as I M trying to learn.

I just wondered if I could mention, Foxmarks can actually be used on your own website, in its own folder, but they wont give you support for it if you use it that way. I am still not happy with it though as its messed my pc up. 

I am still trying to wrack my brains about how to store my bookmarks folder on my ext hd and point both to that folder.

---

### Post by Victormd on 2008-09-15
> **jakewc2 said:**
> Hi both, thank you for your help, I really appreciate it.

I do have my bookmarks on my external hard drive,but they are nightly backups of all bookmarks.

I was just wondering, I dont have the same look and addons for windows and ubuntu, and I quite like the way they both look. I was just wondering, can I move my bookmarks to my external hd, and point to it, instead of setting up a new profile? Just thought it might be easier.

John

The only way I can think of is importing them under "organize bookmarks" from your backup whenever a major addition has been made.

You might (I haven't tested this) be able to create a link in your profile folder that points to your external HD. When I get home I'll test this to see how it behaves and let you know.

---

### Post by jakewc2 on 2008-09-15
Hi Victormd, that was something along the lines of what I wanted, but, been searching myfiles and I've found my C drive, and my bookmarks folder in my windows FF. Is there any way to link directly to that through Ubuntu? 

Thank you again.

p.s. YOu live in the USA and I'm in the UK, so the time difference is quite a lot, if I dont answer tonight, I've gone to bed, but will answer tomorrow. :)

---

### Post by egalvan on 2008-09-15
> **Therion said:**
> Whoopee.  So use your USB drive and be happy.

Some of us don't mind having immediate access to our bookmark's from an offsite archive from any computer anywhere that sports an internet connection.  

I understand how fascinated the entire world is to know what you've got bookmarked, though, and specifically the folks at Foxmarks!!  My gawd I've personally been losing sleep over this for I don't know HOW long now...

:rolleyes:

You asked,
I answered.

But you're right on one thing, I am limited to a computer with a working USB port.

And them being as rare as they are.



I like my privacy, and I will (and have) defend yours.

---

### Post by egalvan on 2008-09-15
> **jakewc2 said:**
> Hi both, thank you for your help, I really appreciate it.

I do have my bookmarks on my external hard drive,but they are nightly backups of all bookmarks.

I was just wondering, I dont have the same look and addons for windows and ubuntu, and I quite like the way they both look. I was just wondering, can I move my bookmarks to my external hd, and point to it, instead of setting up a new profile? Just thought it might be easier.

John

OK, I'm a little lost here... so a few questions...

Are you wanting to use Firefox under Windows and Linux?
  or are you using IE under Win & FF under Linux?

If you want FF under both Win & Linux,
 can they look and feel the same? 
or do you want (or need) to have different looks and/or add-ons for each?


As I stated, I use FF under WinXP and Ubuntu (dual boot) under six different computers.

ALL use the same profile, which is stored on a USB drive. I just plug it into whatever computer I'm using.
Firefox looks and acts the same, because it IS the same. The profile determines the look&feel, also the bookmarks, and your password file (if you use one)

If this is what you want, yes it's possible.

And I have not found a way to separate just the bookmarks.
It's all or nothing for a shared profile among different Firefox's.

---

### Post by jakewc2 on 2008-09-15
Hi, sorry about the confusion, I am usng FF under both Windows and Ubuntu, I use IE but only for certain sites. I installed the Ubuntu version of IE, and use that, but dont bother with the Favourites on there.

So far I am just using the pc for both OS's. but do want to install Ubuntu on my Lap Top as well once I can work out how to get round the problem of the Wifi.

On the PC I have quite a few addons, of which I use about half, but not sure how much of them would work on Ubuntu, though. 

I have tried using the Portable version of FF (with no addons on the usb stick), but for some reason it runs really slow on both the pc and the laptop, as in almost dead stop. which is why I just wanted to connect the bookmarks. 

John

---

### Post by Victormd on 2008-09-16
> **jakewc2 said:**
> p.s. YOu live in the USA and I'm in the UK, so the time difference is quite a lot, if I dont answer tonight, I've gone to bed, but will answer tomorrow. :)

Hey Jake,
I have to apologize. I'm in the middle of moving and haven't set up my comp. at home yet and here at work I only use windows so I can't test the Ubuntu stuff for you. I'll post back as soon as I'm up and running again...

---

### Post by Beth1957 on 2008-09-16
> **Therion said:**
> How does anyone who uses Firefox exist without the [Foxmarks](http://www.foxmarks.com/) bookmark synchronizer plug-in???

So essential IMO...

Yay another Foxmarks user! I was just about to recommend it myself ;) It's got me out of problems when FF has crashed & eaten my bookmarks, and through the not-really-Ubuntu-ready FF ver 3 debacle, when I had to downgrade,  as well as meaning I can share them across my 2 machines. Hooray for Foxmarks! :D

---

### Post by Victormd on 2008-09-16
I just tested the link work-around in windows and it looks like it worked! To test it, this is what I did:
1. copied my original bookmarks.html file from firefox profile folder to my c:\bookmarks.html
2. created an html shortcut in my firefox profile folder pointing to c:\bookmarks.html (right click on c:\bookmarks.html and create a shortcut then copy into the ff profile folder).
That's it!

Now you can copy this link into the ff profile under windows and ubuntu and when you open FF, both will be linked to the same bookmarks.html file.

You'll need to check if ubuntu will recognize the shortcut created by windows. The shortcut created by windows is actually called bookmarks.html as well but I don't know (and can't check at least until Friday) if ubuntu will recognize it. Let me know if you test this and if it works. If it doesn't work, let me know because I have a few other suggestions... I think we're on to something now!

---

### Post by jakewc2 on 2008-09-16
Hi Victormd, thanks for getting back tome, I really appreciate it. I understand how that is, stressful. No problem, I really appreciate your help.

I'll give it a go.

At the moment though I have a big problem with my laptop not working in my ubuntu partition, have started a thread trying to get that sorted first.

Thank you again for your help.

---

### Post by jakewc2 on 2008-09-17
Hi Victormd, I wonder if  could ask, I have never created an html shortcut before, and I just tried and it opened a box asking me to type the location of the item, which file do I put in there?

Thanks again,

John.

---

### Post by Victormd on 2008-09-18
As I mentioned in my previous post, I created the shortcut in Windows so basically, right-click on the bookmarks.html file and select Create Shortcut. The shortcut will automatically be called bookmarks.html and will be linked to the original file. Then you can copy that shortcut to where you need it, i.e., firefox profile folder in ubuntu and firefox profile folder in windows.

---

### Post by egalvan on 2008-09-18
> **jakewc2 said:**
> Hi, sorry about the confusion, I am usng FF under both Windows and Ubuntu,

OK

> On the PC I have quite a few addons, of which I use about half, but not sure how much of them would work on Ubuntu, though.

Well, it never occurred to me that there would be 'windows' specific add-ons (or Linux-specific). 
I always thought they were firefox-version-specific.
I just used the exact same add-ons, never gave it a thought.
And never seem to have any problems.


> I have tried using the Portable version of FF (with no addons on the usb stick), but for some reason it runs really slow on both the pc and the laptop, as in almost dead stop. which is why I just wanted to connect the bookmarks.
John

I was going to go this route, but got side-tracked using a shared-profile style solution.
Now that 8gb sticks are becoming wide-spread, I may look at it again.
I did try  a few other pieces of software from the Portable Web site, they seemed to run OK.

---

### Post by janes604 on 2008-09-18
Hi i don't know if this was mention but if not it worked for me ...

there is a add-on for fire fox called 
fox marks-  if you install on the windows side and the fire fox in Ubuntu it will automatically sync your book marks .
 just do a Google search for it 


again if this was said b4 sorry did have time to read the whole post 

hope it helps

---

### Post by jakewc2 on 2008-09-19
Hi, thank you for your suggestion, that has been mentioned before, but as it uses an online server to hod the bookmarks, and it can loose your bookmarks, which I have discovered, I want to see if there was another way.

I am not very computer savvy, so when people try to explain things I sometimes find things really confusing. Old school way of being taught, shown first, then learn. I am still confused as to how  its trying to be explained, I have tried to follow the instructions but it doesn't seem to be working. :(

John

---

### Post by Salpiche on 2008-09-19
This is what I did: opened "Organized Bookmarks" from FF bookmarks > selected "import and backup" > "export html" to my jump drive > reboot / open FF and repeat the above but selecting "import html" 

done

---

### Post by avanrens on 2008-09-19
I use Firefox's plugin Foxmarks works great, especially if you run a few different systems your book marks are synchronize between the different systems.

---

### Post by jakewc2 on 2008-09-19
I did for a while but everytime it Synch'd, it lost all the new Bookmarks I added. I also dont like that its on a server I have no control over, so I would rather have it so I can cntrol it.

HI Salpiche, I managed to work  out how you suggested, and it seemed to work, well at last both programs have the same bookmarks now, but havent bookmarked anything yet.

Thank you all for your help. :)

---

### Post by Salpiche on 2008-09-19
btw, I also use Foxmarks and recommend it to everyone, specially if you are away from your computer and have to access one of your bookmarks instead of trying to remember the url all you have to remember is foxmarks.com I have over 1300 bookmarks and thanks to foxmarks I don't have to worry about it as much at work, where my browser only have one bookmark foxmark.com

---

### Post by jakewc2 on 2008-09-20
Hi, just wanted to mention that it does work. It shows on both my windows and my Ubuntu Bookmarks.

Thank you,

---

