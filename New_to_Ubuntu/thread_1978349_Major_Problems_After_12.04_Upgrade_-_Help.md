---
title: "Major Problems After 12.04 Upgrade - Help?"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by oxontheroof on 2012-05-11
Hello, and thanks in advance for any help provided.

I am in no way a computer geek. A friend walked me through Ubuntu 10.something installation about a year ago when my computer continually crashed and my options were "buy a new computer" or "try Ubuntu." I've been very happy with Ubuntu until...

I got all trigger happy last Monday when I saw there was a new version (12.04). I upgraded. Now my computer is totally wacko.

Specifically, I have no launch area. I get online by right-clicking and choosing "Change Desktop Background," then going roundabout through Ubuntu One's "Get help online" link. I have no icons on the top right of my desktop (calendar, shut down). I have no minimize or exit buttons on my web browser, photo viewer, etc. Any documents I have saved to my desktop are all still there, but I have not figured out a roundabout way to access my Home folder (assuming it's still there somewhere).

There are other little glitches, too, such as my keyboard working sometimes and not working other times....I cannot click a combo box and use my mouse to move down....

When I first installed, there was one error message that I think was something like Compiz will not launch? I can't remember. If it gives me the error again, I will be happy to add it. I did send an error report, though.

Any ideas? I have put off asking here because I literally know NOTHING, and I am scared someone is going to give me a 146 step way to fix this through Terminal. :P

---

### Post by forrestcupp on 2012-05-11
You might try downloading the Ubuntu 12.04 iso from the web site and creating a LiveCD/USB. Then you can boot to that and see if it works. If so, your best bet might be to back up all your important files and do a fresh install, rather than an upgrade.

Upgrading from release to release usually works pretty well. But sometimes upgrading from an old release can cause major problems like this that are only going to be solved by doing a clean install.

Before you do that, though, maybe you could see if you can create a new user and boot to that user. Sometimes having fresh settings with a new user can fix things. If that works, you can just transfer your important files over to the new user's /home folder.

---

### Post by cbanakis on 2012-05-11
> **forrestcupp said:**
> You might try downloading the Ubuntu 12.04 iso from the web site and creating a LiveCD/USB. Then you can boot to that and see if it works. If so, your best bet might be to back up all your important files and do a fresh install, rather than an upgrade.

Upgrading from release to release usually works pretty well. But sometimes upgrading from an old release can cause major problems like this that are only going to be solved by doing a clean install.

Before you do that, though, maybe you could see if you can create a new user and boot to that user. Sometimes having fresh settings with a new user can fix things. If that works, you can just transfer your important files over to the new user's /home folder.

+1

No matter what anyone says, it is ALWAYS best to do a clean install instead of upgrading.

Wether your using Windows, Mac, Or Linux.

I am sure someone will soon make a post contradicting my statement.

In that case, I'm gonna have to make a bold statement, and say they are simply WRONG for thinking that way.

---

### Post by oxontheroof on 2012-05-11
Thanks for the replies!

I may have to go directly to the clean install, since I can't SEE a home folder ANYWHERE. It took mental gymnastics to figure out how to open Firefox.

I have a feeling it's going to be crazy trying to FIND my files so I can back them up.

---

### Post by grahammechanical on 2012-05-11
Is Ubuntu the only OS? If so you will not see a Grub menu. So, press and hold the Shift key should bring up the Grub menu and from that you can select Rescue mode.

And from there you can try Resume Normal Boot and see if that gets you to a working desktop.

You can also at the broken desktop press Ctrl+Alt+F2

and run the command

```
compiz --replace
```

and see what happens.

You might also need to Ctrl+Alt+F2 and run this command

```
unity --replace
```

Or at the log-in screen click the cog icon and select Ubuntu 2D. That should get you to a 2D desktop. And run thoose command s in the Terminal. Compiz is not used in 2D.

Regards.

---

### Post by oxontheroof on 2012-05-11
Thanks, grahammechanical.

Ubuntu is my only OS.

I am not sure what a grub is (other than the ones in my garden), but holding down Shift does nothing.

Ctrl+Alt+F2 goes to a completely blank screen with no response; repeating it reboots.

I have no cog icon on my long-in screen (or desktop).

I really don't mind doing a clean reinstall, but I can't get to my Home folder and really hate losing the pictures of my kids that I haven't backed up yet. Yeah, I know....always back it up before doing something crazy!

---

### Post by Nico-dk on 2012-05-11
> **oxontheroof said:**
> I really don't mind doing a clean reinstall, but I can't get to my Home folder [...]

Maybe you can ;)

As forrestcupp said, you could try to make a LiveCD/USB from the Ubuntu 12.04.

I havenøt tried this myself, but it should work.

You'll need:
> a computer with internet access and a cd burner
> a USB stick or harddrive with room enough for your pics and documents.

1)
Download Ubuntu Desktop from here; [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

... and burn it to a CD-R

2)
Boot up your botched Ubuntu machine with this dics in the drive. You may have to press F12 (usually) to select which device to boot from. You want the CD/DVD drive 

3)
You'll eventually be given the option to Try Ubuntu or Install Ubuntu, pick Try

4)
You should be taken to the Unity dekstop.
Plug in the USB device

5)
Hold down CTRL + ALT + T
This open a terminal

6)
Type ```
gksudo nautilus
```
A password box pops up, type your password

7)
This open a window.
Click Filesystem in the left panel and then the Home folder.
You should now be able to see your own home folder (ie. a folder with your username)

8 )
Open your home folder, and copy away

9)
Once you've backed up everything, restart the computer and follow this guide to install Ubuntu from scratch: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

Remember to delete all partitions before installing

---

### Post by forrestcupp on 2012-05-11
> **oxontheroof said:**
> 
I really don't mind doing a clean reinstall, but I can't get to my Home folder and really hate losing the pictures of my kids that I haven't backed up yet. Yeah, I know....always back it up before doing something crazy!

Like Nico-dk said, you'll be able to get to your /home folder from the LiveCD/USB. When you boot it, choose the option to "Try Ubuntu" rather than to install right away. From there, you should be able to get to your files and back them up before you reinstall.

I've used the LiveCD many times to back up people's files on crashed Windows PCs.

---

### Post by psycosmyth on 2012-05-12
To back-up the previous posts, yes a clean install may be the best option. As a tester I can say that even the pre release may be way buggier than the final even a day before. Sometimes the upgrades miss the newest packages and caus;)e problems.

---

### Post by anewguy on 2012-05-12
Okay, I have a dumb question:  is it a matter of there are no icons on your desktop and no menu options like Applications Places and System on the top bar?  I noticed you said you were previously in version 10.  If that was indeed Ubuntu 10.xx then I would ask if you have ever heard of or seen the Unity desktop - it would be completely different.  You have to move your mouse to the left side of the screen and see if a column of icons appears - if so, I believe the 2nd down (it looks like a file folder) will show your home folder.  Similarly, there should be something that looks like a series of little curves going up in the upper bar - that's the network manager icon now.  Click on it to see available networks.

If none of that is your problem, could you explain a little further?

Dave ;)

---

### Post by Prescilla on 2012-05-12
Try accessing your home directory via terminal.
Press Ctrl+Alt+T.
cd /home/user
ls

---

### Post by anewguy on 2012-05-12
Also, thanks to the integration of the unity desktop, the "menu" bar for a program, including the minimize and maximize buttons, would be in the upper right of the top bar, not necessarily on the window itself.  It can take a little getting used to.

---

### Post by oxontheroof on 2012-05-12
Ya'll are so nice! (Yes, I am in the South....)

I am off to my daughter's piano recital but will try this when I get back.

I did want to mention that I am familiar with using the Live CD as that is how my friend introduced me to Ubuntu when my computer kept crashing. I would get my friend to help, but he is graduating from high school today and I refused to let him have my computer. Yes, I said high school....these young whipper-snappers love Ubuntu! :P 

Also, I have upgraded each time there is a new version, so I do know about the Unity desktop and how the launcher is on the side and must be hovered over. To explain further, it is just NOT THERE. I have one Open Office document and one spreadsheet on my desktop, as well as a folder with some pics. All three of these are just personal stuff that I had created recently and hadn't filed away in my Home Documents folder. Other than that, my desktop is blank.

So after some right-clicking and playing around, I figured out how to get online from the Ubuntu One help link through "Change Desktop Background." If that makes sense. But when I open windows, I cannot close them.

Thanks again! I'll be back to try a fix in a little while.

---

### Post by oxontheroof on 2012-05-12
Okay, I am back and attaching a screenshot. This is not cropped. You can tell that there is no launcher...no menu area...no icons other than my own personal documents. You can probably also tell that I have small children. :lol:

I'll be trying the backup/clean upgrade later today. Again, thanks for your help!

---

### Post by anewguy on 2012-05-12
What's your video adapter make and model?

---

### Post by deadflowr on 2012-05-12
> **anewguy said:**
> What's your video adapter make and model?

Yes, definitely find out your video adapter. This problem sounds alot like the issues revolving around the latest Nvidia drivers and some Nvidia cards and compiz.
Something to try is logging out and logging in into ubuntu-2d.
To do this, at the login screen in the box right next to your name is a little(i think)ubuntu logo, click on it and it will give you two choices(unless you've install other desktop enviroments). Click on the Ubuntu-2d and log in, you will then be using unity-2d which doesn't use compiz.It won't be as robust as full unity, but hopefully it will at least give you a more workable desktop.

---

### Post by afz12 on 2012-05-12
Late reply, I know but I agree with cbanakis - I have never had an "upgrade" work even for single step upgrades. Even downloading all updates for a beta version of 12.04 resulted in problems and these only went away when I installed a recent completed version for 12.04. Perhaps the Ubuntu architects could just remove this "upgrade feature" until such time as it is proven secure?

---

### Post by oxontheroof on 2012-05-12
GENIUS!!! Ya'll are the best!!!

I saw anewguy's question about the video adapter and then deadflowr guessing correctly that I have Nvidia.

And grahammechanical had already mentioned 2D but I was looking for the cog in the top right on the log in screen, not by my username.

So right now I can see my launcher, menu bars, etc. WOOHOOO!!!!

Now I know what this guy is for:

:guitar:

So. I still have my old 11.04 Install/Live CD straight from the "press." Should I:

a) Keep installing 12.04 updates until it is fixed, or

b) Back everything up to my external hard drive, then use the 11.04 Install/Live CD, or

c) Back everything up to my external hard drive, then make a new Install/Live CD of 12.04 from the Interenet, or

d) None of the above, something different?

---

### Post by anewguy on 2012-05-12
nVidia - that's why I asked.  glad you've got things going now.

As far as what to do:

As I mentioned before, and many others have mentioned, using the "upgrade" usually results in problems. As I and the others mentioned, it would be best to backup everything you need to backup, then do a complete install of 12.04 -> if you want to change partitions around, now is the time.  At a minimum, use the manual method and be sure the existing (non-swap) partitions are marked to be formatted.

---

### Post by deadflowr on 2012-05-12
> **oxontheroof said:**
> GENIUS!!! Ya'll are the best!!!

I saw anewguy's question about the video adapter and then deadflowr guessing correctly that I have Nvidia.

And grahammechanical had already mentioned 2D but I was looking for the cog in the top right on the log in screen, not by my username.

So right now I can see my launcher, menu bars, etc. WOOHOOO!!!!

Now I know what this guy is for:

:guitar:

So. I still have my old 11.04 Install/Live CD straight from the "press." Should I:

a) Keep installing 12.04 updates until it is fixed, or

b) Back everything up to my external hard drive, then use the 11.04 Install/Live CD, or

c) Back everything up to my external hard drive, then make a new Install/Live CD of 12.04 from the Interenet, or

d) None of the above, something different?

It's good to see you get some functionality out of your system again. As for your next step. Definitely go with part one of plan b(back-up your stuff to an external hard drive).Whether to keep at it with 12.04 and hope a fix comes, or to reinstall 11.04, that depends on how you feel. Go with your gut. Unity2d is somewhat nice but it does lack the oomph and goodies of full on unity.
Of course you can always install a different Desktop Enviroment if you'd like.

---

