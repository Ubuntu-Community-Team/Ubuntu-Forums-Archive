---
title: "Checking drivers on Ubuntu 16.10 and other stuff"
date: 2016-11-13
forum: New to Ubuntu
---

### Post by notso23 on 2016-11-13
Being new to Linux, and I have no choice now as I deleted Windows 10 in the process,](*,) :D (it's probably the best thing I ever did) I am reading on how to get around and using the system. I was just thinking how would I know how to upgrade the drivers on the hardware.

Also going back to FF and Chatzilla, what is the best IRC channel to be on for help for all those stupid little questions that I would have. :D

Is it necessary to do the Terminal thing in Ubuntu? I think I will need to do some basic stuff, I guess.

Thank you in advance
Shane

---

### Post by TheFu on 2016-11-13
Linux isn't Windows. Many things you've learned don't apply anymore.

[https://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](https://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc) - a little dated, but still true. Basically, patch weekly and backup daily. New, tested, drivers are provided with the weekly patching.  There are a few exceptions, but if there isn't a specific issue that YOU ARE EXPERIENCING, I wouldn't bother looking for other solutions.  This is especially important for video drivers. If it is working, don't do anything special.

If you avoid the CLI/shell, then you'll only have 10% of the power of a Unix system. Basically, you'll be limited like Windows.

BTW, 16.10 support ends in a few months.  For everyone new to Linux, 16.04 would be better choice - 5 yrs of support. The next LTS will be release 18.04 (April 2018). I won't touch any of the intermediate releases - 6 months of support just isn't enough and running unsupported is foolish (almost always).

---

### Post by ajgreeny on 2016-11-13
Hi notso23. Welcome to the forum.

As TheFu says, Linux is not Windows, and please in future use the correct name for the Microsoft OS as some people get upset by what they believe to be derogatory names.  I have edited your post above to do this for you this time, but will not do so again.
Also it is true to say that it's not essential to usde the command line but if you never even consider it you are loosing out on a lot of the power available to you; there's no need to try to learn it all in one go, but try out some simple tasks bit by bit, look up how to create [aliases]("http://askubuntu.com/questions/17536/how-do-i-create-a-permanent-bash-alias") and you may find yourself using it more than you anticipate doing at present.

I do not use IRC much but there are several channels which have ubuntu in their names so you can search for them in whichever client you use. I do use the #ubuntuforums channel a little and you will find a lot of users there with whom you can chat.

Here's a couple of places for some background info on Linux in general, not specifically Ubuntu.
[http://linuxappfinder.com/](http://linuxappfinder.com/)
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by RobGoss on 2016-11-13
Hello and welcome to the forum, I think it's safe to say as a new user of Linux I would not have deleted Windows just yet, the reason I say this is you should really know what to expect from **Linux** is nothing like **Windows** but! if it's something you have already considered and have a full understanding then I welcome you to the world of Linux

I think this would be a good place to start with using Linux commands [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) it explains what each command can do. A word to the wise, only use command that you know what they can do if not used correctly it will and can break your system 

Then I would also bookmark this page for future reference it will come in hand as you progress [https://help.ubuntu.com/community/PopularPages](https://help.ubuntu.com/community/PopularPages) 

I've only use Hexchat a few times it seems to be very good not sure if there's one better channel but it's worth looking into [https://hexchat.github.io/index.html](https://hexchat.github.io/index.html) I prefer the forums over chatting it's more informative

---

### Post by TheFu on 2016-11-13
I completely missed the IRC question.  My LUG has an IRC channel - it isn't very active unless we have a planned event there.

For a client, I've been using an addon for Thunderbird.  Once in a while, I've used pidgin and found that to be ok if I was going to be in more than 1 room at a time. That usually happens when doing some scripting in ruby or perl or having specific issues with a server install (server in the generic term - software).  For example, I was having an issue with Nextcloud 2.0.x a few months ago due to new php dependencies. The good folks in that channel helped, quickly, efficiently.

I'd like to clarify.  Lots and lots of users never touch the shell. It isn't required unless you need more advanced capabilities OR if you run almost any service.  Then it is necessary. There is over 40 yrs of history with this, so don't expect it to change anytime soon.  Back in 1993, I got frustrated with the lack of GUI on Unix servers too. Eventually, as I learned more, it became clear why this was. Now I loath GUIs for systems management. GUIs make automation very hard, IME.

I'd also point out that even I, a LUG organizer, and nearly 100% Linux person, still have Windows on my network, not for gaming.  Every OS has a place and these days we don't have to select 1 or the other. Both can be used on the same machine, without dual/triple booting. Virtual machines solve that pretty well for many people. Use Linux for what it does well (98% of stuff) and use Windows for the remaining 2%. ;)

Plus there isn't any better way to learn a new language (or OS) than to force yourself to learn by complete immersion. If I wanted to learn Mandarin, I'd try to live in China for 6 months.  The same advice applies to Learning Linux.

---

### Post by oldos2er on 2016-11-13
> **notso23 said:**
>  how would I know how to upgrade the drivers on the hardware.

Check the Additional Drivers tool. Depending on your hardware there may or may not be anything there.

> **notso23 said:**
> what is the best IRC channel to be on for help for all those stupid little questions that I would have. :D

You can also use this forum for questions, it doesn't have to be IRC. Don't think your questions are stupid.

> **notso23 said:**
> Is it necessary to do the Terminal thing in Ubuntu? 

No, it's not necessary, but it does help in understanding and administering your system. A good beginner's resource is linuxcommand.org, as well as the other sites mentioned.

---

### Post by Mark Phelps on 2016-11-13
Up until very recently, I would have agreed that you could largely avoid using the Terminal and CLI and be OK in Ubuntu -- until I ran into serious problems after installing Ubuntu 16.10 Mate.

Updates simply would not complete. The GUI tools would hang, and since they showed no error messages, there was no indication of what was happening.

But, when I ran the same update in the terminal, I could see what was failing -- and that lead to solutions for the problem.

Another thing you will find quite different from Windows is that in the Linux world, configuration settings are nearly always stored in text files, and to change those, often editing those "hidden" files is the quickest and easiest way to go.  I had to do this, again in Ubuntu 16.10, in order to STOP Firefox from forcing me onto its home page every time I launched the Browser.  Sure, it had a GUI for changing the Home Page, but that was not working, and I had to resort to hand-editing the config file to fix it.

And finally, I ran into an IPV6 problem with doing system updates, and the fix was (again) to hand-edit a config file to disable IPV6 so IPV4 would be forced.  Until I did this, the updates would not complete, regardless of which mirrors I had designated.

So, you need to be prepared to learn the command line and how to edit files if you want to stay with Linux long-term

---

### Post by notso23 on 2016-11-13
Thank you all for your replies. I will answer in more detail later today as I have things to do today.
I have bookmarked many more pages to read later from your replies.

BTW I didn't want to delete windows, it was a total accident but I have been looking at Ubuntu for some time now and liked the way it is when I tried it. At least I had all my personal stuff backed up.

I will have to look at how to install 16.04 (if it's possible) as it has LTS and keep all the stuff I now have on 16.10.

Thank you all for your help and info
Shane

---

### Post by notso23 on 2016-11-13
While I am sitting here waiting I looked at installing 16.04 And I will get the name of the apps that I installed, which aren't large
Downloads, and do a clean install.
It sounds the easiest way for me to do it as I am not too computer savvy.
It does sound like it is better to post here than using IRC.

Once again thank you all.
Shane

---

### Post by notso23 on 2016-11-14
Thank you "TheFu" I am now using **Ubuntu 16.04** and I am about to do all the settings you mentioned for updating. Yes I will learn to use the terminal a bit :) if that's what shell means?

And by the way to the Moderator, the comment I made was "tongue in cheek" in other words I made it in jest and if I have offended then I am sorry for it.

Thank you all :D
Shane

---

### Post by mastablasta on 2016-11-14
if you are on 16.10 and if it all Works it is ok to stay there. just as long as you know you will need to upgrade every 6-9 months until version 18.04  (April 2018) when another LTS will be out. normally upgrade procedure is relatively painless, but not always. so it is good to backup first and then upgrade. reinstall is fast as well.

you can backup data only or the image the whole OS (usign redobackup or clonezilla)

LTS releases don't have ot upgrade for 5 years. just do regular updates instead. much, much safer.

---

### Post by notso23 on 2016-11-14
Thank you "mastablasta" for your comments and help. I download a new 16.04 iso and installed it (last night here downunder) with full network support, whereas the previous install of 16.04 I couldn't get any wifi no matter what I did.
So now I have a full working 16.04 and all is good. :D  I feel a lot better with the full support, just a lot of reading and learning to do. And I have bookmarked your links in your footer as well so I don't lose them.

---

