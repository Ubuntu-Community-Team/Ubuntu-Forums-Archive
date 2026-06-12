---
title: "Total beginner please help"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by munchkin360 on 2008-10-25
Hi I have an Elonex webbook and I think I have killed it :(

I wanted to reset it so I did the ls /home thing and deleted the user info and then I did oem-config-prepare and it said next time I started it up I would be able to do the setup again but after I typed exit and continued to boot the screen went black and has stayed black ever since.

It will not boot up at all. I can hit esc and enter the menu but thats it! I cannot get to the screen asking for user name and password. I have totally messed it up.

Can anyone help me?

---

### Post by drowner on 2008-10-25
What do you mean by 'I wanted to reset it'?

---

### Post by kdcoetzee on 2008-10-25
And what user info did you delete ? and how ?

---

### Post by drowner on 2008-10-25
I've not heard of the command 'oem-config-prepare' but apparently it is used for linux pre-installed computers to remove the 'Original Equipment Manufacturer' user, and then ask the questions for a new user at next log in.

Ok, that's cool. But we really should see what you have deleted.

I would like to look in your bash history -but this would be in your previous user's home directory - is it still there? What did you delete?

---

### Post by drowner on 2008-10-25
> **drowner said:**
> I've not heard of the command 'oem-config-prepare' but apparently it is used for linux pre-installed computers to remove the 'Original Equipment Manufacturer' user, and then ask the questions for a new user at next log in.

Ok, that's cool. But we really should see what you have deleted.

I would like to look in your bash history -but this would be in your previous user's home directory - is it still there? What did you delete?

Firstly, did you delete everything in the previous user's home directory?

---

### Post by munchkin360 on 2008-10-25
i wanted to reset the user info (user name and password). I pressed esc during the boot up and selected the recovery mode.

When it came up with a list of options I picked 'drop to root shell prompt'

typed ls /home and got a list of users.

Deleted these by typing deluser &#8211;remove-home XXX (XXX being the user name)

and then did oem-config-prepare

all went fine, I set it up as I wanted it (new user name and password) when the screen came up asking time zone, keyboard set up and so on. It then asked me to log in so i typed the new user name and password and it told me one of them was wrong. I tried again and again with no joy so shut down and tried to do the whole of what I had already done again (oem-config-prepare).

This time when I did it all it never got to the start up log in screen. just a plain black screen that never changes.

I can go back to the 'drop root shell' prompt and when I do a long list of words and i guess command lines comes up on the screen. All of them say ok next to them apart from one which is 'setting preliminary keymap' which said 'fail' next to it in red.

I know its all my fault user error and so on but I am really stuck. I know nothing about computers. I only just cope with MSN on a xp desk top LOL.

I hope I have explained that all ok. Sorry if I am confusing you.

---

### Post by twisted_steel on 2008-10-25
Were you following these steps?

[http://webbookblog.com/?p=6](http://webbookblog.com/?p=6)

---

### Post by munchkin360 on 2008-10-25
Yes thats the blog I was following, just did not know how to put a link in, told you I am useless with computers

---

### Post by twisted_steel on 2008-10-25
> **munchkin360 said:**
> Yes thats the blog I was following, just did not know how to put a link in, told you I am useless with computers

We all have to start somewhere :)

I'm not sure why the first time you were able to at least get the login screen and the second time it is just missing.  It sounds like there was a problem getting the display to start up.  This is known as X Windows (or just X) and if you are curious, you can get an overview of it on [wikipedia]("http://en.wikipedia.org/wiki/XOrg").  Are you able to run through the steps again once you get back to the root shell?  If you can at least get the login screen back following the original steps, you can probably reset your user's password from the root shell if you are unable to type it in the window.  The command to reset a user's password without going through the deleting of home directories, etc is:
```
passwd myuser
```where *myuser* is your username.  This has to be done from the root shell in order to have the proper permissions.

For anyone else following along, [this page]("http://www.geeksquadwiki.com/gsw/index.php?title=Resetting_Ubuntu") looks to have screenshots of the restore and root shell options that munchkin360 was referring to.

Now that I think about it, I wonder if perhaps your error about the keymap was preventing you from logging in in the first place.  It could be that the keys were wrong when login prompt started, causing your password entry to fail.  Do you have a USB drive (AKA USB stick, thumb drive) around that you could use if you need to get logs off of it to help people on the forums?

---

### Post by munchkin360 on 2008-10-25
Thanks for the fast reply.

I have a few UBS sticks sitting about. I even have a pink fluffy one :D It matches my handbag (yes its that sad). My boyfriend says girls and computers never mix well, I am sure he is right!

Anyway, I can get back to the drop to root shell prompt screen but not the log in screen, it will not even let me do the set up procedure now! when I type the oem-config thingy.

When I ask it to list users in the drop root shell prompt now by typing ls /home it shows no users at all. Its like the whole set up thing I went through did not save.

Is there any more information I can give you to help?

---

### Post by glotz on 2008-10-25
Pink fluffies :D

---

### Post by kdcoetzee on 2008-10-25
I still think X should work fine. because you only deleted the user account. except if there was a important .Xsomething file in your home directory.

do you by chance have a ubuntu live cd with you. then you can boot up in the liveCD.

mount your partitions. then we can get the logs as well.
and then try to create a new user for you.
and if there is any .Xsomething file needed. copy it from the live environment to your new user.



And just for the record I am thumb sucking all this. So it may work or it may not.

---

### Post by kdcoetzee on 2008-10-25
> **glotz said:**
> Pink fluffies :D

;) Got brain freeze on your strawberry ice cream ??

---

### Post by drowner on 2008-10-25
> **Juggernaut_KDC said:**
> I still think X should work fine. because you only deleted the user account. except if there was a important .Xsomething file in your home directory.

do you by chance have a ubuntu live cd with you. then you can boot up in the liveCD.

mount your partitions. then we can get the logs as well.
and then try to create a new user for you.
and if there is any .Xsomething file needed. copy it from the live environment to your new user.



And just for the record I am thumb sucking all this. So it may work or it may not.

I was thinking about the command logs, but i was under the impression they were logged in the /home/user/.bash_history file - wouldn't that have been deleted?

---

### Post by twisted_steel on 2008-10-25
> **drowner said:**
> I was thinking about the command logs, but i was under the impression they were logged in the /home/user/.bash_history file - wouldn't that have been deleted?

Yes, it sounds like the command history is probably gone.  However, other logs such as /var/log/Xorg.0.log and /var/log/Xorg.0.log.old should still be there.  These might have some detail as to whether X is failing to start from some sort of config error, or if there is something else going on.  From what I gather from munchkin360, the commands I found in the blog post on the previous page were executed to clear out the user.  It sounds like during the second attempt to reset the system back to the OEM config, something was screwed up.  Maybe the /var/log/messages file would also be helpful.

---

### Post by munchkin360 on 2008-10-26
I'm lost :(

Have a messed it up beyond repair.

I have no CD's or anything its the one you get free from carphone warehouse. I got it off ebay cheap so have no technical support. I did try phoning them, but they will not help me :(

I so hope I have not messed it up beyond repair. Anyone got any ideas?

---

### Post by kdcoetzee on 2008-10-26
You can just download the Ubuntu cd. from [www.ubuntu.com]("www.ubuntu.com"). the new one is coming out. so I would recommend to wait for that one. (if it is possible or else just download 8.04).

And if it is messed up beyond repair. just reinstall it. 
If you finished downloading.

And [http://ubuntuforums.org]("http://ubuntuforums.org") and [www.google.com]("www.google.com") is your tech support. That is the nice thing of such a big community.

---

### Post by munchkin360 on 2008-10-26
Ah thanks will try and re-install.

Do I download to like a USB key and stick it in the webbook?

I am not sure how to boot from UBS on Ubuntu.

If someone could give me instructions on how to reinstall I would be very happy :) I'm offering popcorn and beer as a reward (well virtual popcorn and beer LOL)

:popcorn:

---

### Post by kdcoetzee on 2008-10-26
I was thinking more with the cd.
don't bother with the USB.

when you start your download. you will see that it is an .iso file.

so you will need a cd writer and a blank.

---

### Post by kdcoetzee on 2008-10-26
Here is a few nice howto's on installing Ubuntu.

[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

downloading Ubuntu
[https://help.ubuntu.com/community/GettingUbuntu]("https://help.ubuntu.com/community/GettingUbuntu")

howto burn an ISO file on a blank cd.
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

And finally the installation howto.
[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

And here is another one just for reference.
[http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu]("http://developer.novell.com/wiki/index.php/HOWTO:_Install_Ubuntu")

if you are dual booting with windows here is a guide on howto install Ubuntu "inside" of Windows.
[http://seogadget.co.uk/the-ubuntu-installation-guide/]("http://seogadget.co.uk/the-ubuntu-installation-guide/")

And if you don't have a writer or blank. and want to install it with a USB stick.

[www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html]("www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html")

---

### Post by munchkin360 on 2008-10-26
I will try with USB Stick as the webbook has no cd drive built in and I don't have an external one.

The link to the UBS install help thingy does not work. Anyone got a different link?

---

### Post by gwenn on 2008-10-26
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by gwenn on 2008-10-26
just download ubuntu and reinstall.Is the faster way.Take a look at howto's

---

### Post by kdcoetzee on 2008-10-26
> **munchkin360 said:**
> I will try with USB Stick as the webbook has no cd drive built in and I don't have an external one.

The link to the UBS install help thingy does not work. Anyone got a different link?

Sorry about the link. its fixed.
and I didn't know about the webbook that didn't have a cdrom.

and give gwenn's howto a shot.
Ubuntu Help howto's is usually more helpful then other howto's.
(usually not always)

---

### Post by munchkin360 on 2008-10-26
Ok I have got the install files on a UBS key by using the UNetbootin program.

But I don't know how to get the webbook to boot from the USB.

I have looked at the howto's and am totally lost.

On starting the webbook I pressed Del and chenged the boot options but either I did it wrong or its not working.

I am sorry for so many questions but any help is most appreciated.

---

### Post by twisted_steel on 2008-10-26
> **munchkin360 said:**
> Ok I have got the install files on a UBS key by using the UNetbootin program.

But I don't know how to get the webbook to boot from the USB.

I have looked at the howto's and am totally lost.

On starting the webbook I pressed Del and chenged the boot options but either I did it wrong or its not working.

I am sorry for so many questions but any help is most appreciated.

Before we go any further, I saw this on the webbook blog site: "If you want to reinstall Ubuntu, or try any other Linux the[n] don&#8217;t go calling support and expecting them to help!"

How did you try changing the boot options?  I read a post on that webbook blog site that stated that sometimes changing it to boot from USB would not work.

"... I have booted Linux on a USB drive, in the bios you have to change the order of the hard drives, not change the order of the boot devices. After booting from it you have to go back into the hard drive section of the bios to turn back on the SATA drive."

Are you putting Ubuntu 8.04 or 8.04.1 on the USB key?  The following guide says it uses either, though they also mention the alternate CD as a possibility.

I came across these instructions about setting it up from scratch.  Note that they are booting from a 8.04 CD in a USB CD-ROM drive, but it should be the same for you with the exception of using a USB key.
1. [Keystroke guide to a factory reinstall]("http://webbookblog.com/?p=261")
2. [Reinstalling Ubuntu or other Linux on the webbook]("http://webbookblog.com/?p=171")

You probably don't need the last link to get it installed, but it might help later on if there is a problem with your screen resolution when it boots up.

---

