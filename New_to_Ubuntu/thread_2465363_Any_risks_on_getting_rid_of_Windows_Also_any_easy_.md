---
title: "Any risks on getting rid of Windows? Also any easy ways for me to do it"
date: 2021-07-30
forum: New to Ubuntu
---

### Post by mrredpanda69 on 2021-07-30
Hi, I'm relatively new to Ubuntu and Linux in general, but I'm loving it so far, and since I'm no longer using Windows, i wanna delete it, but my question is, how safe is it for me to do it?
And in order for me to do it, do i have to install linux all over again and go with the option to keep only ubuntu? Or is there any other option to do it?
I'm using ubuntu 20.04

---

### Post by sudodus on 2021-07-30
I think it is a good idea to keep Windows for some more months, maybe a year before you remove it. There might be some task, that you do rather seldom, and you may need time to learn how to find and use a Linux tool for that purpose. Or, worst case, there is no such tool.

Nowadays I use use almost only Ubuntu family flavours, mainly a Lubuntu + Xubuntu combo, and standard Ubuntu. But I need Windows to manage some unusual tasks at my bank and at my son's school. Those tools are made only for Windows and MacOS (and mobile phones with Android).

Updating Windows is very time-consuming, and using it only a few times every year makes updating consume much more time than the particular tasks, so it would be nice to get rid of it.

---

### Post by yancek on 2021-07-30
Are you using UEFI or the older Legacy BIOS?  In either case it should not be a problem but you don't delete windows, you simply format the ntfs (windows) partitions from Ubuntu with a tool such as GParted..  I've been using Linux for many years and still have windows on the computer though I don't use it.  The main reason to format the windows partitions would be if your dirive is small or you don't have enough room available for data on your Linux partitions.  You may be able to simply shrink the windows partitions if that's the case.

---

### Post by QIII on 2021-07-30
The risk you run is the same as with any heart-lung transplant (or the computer equivalent in this case):  Losing a lot of things you would rather have kept.  Data.  Old photos.  Emails. Documents. Etc.

If you just throw out Windows, any of that stuff you have there will go with it.  Before you even consider such a move (and I wouldn't -- I'd recommend keeping it around as a couple of users have said above), you should take stock of what you want to keep and do very thorough backups.  

Backup.  Backup.  Backup.  Three words to live by.

---

### Post by grahammechanical on 2021-07-30
If you do reformat the Windows partitions or delete them and enlarge the Linux partitions afterward you must run this command

```
sudo update-grub
```

Otherwise Windows will still be in the Grub boot menu. Be careful not to delete the BIOS boot/EFI partition as that contains code for launching the grub boot loader.

So, to answer you question. Yes, there are easy ways to do it. It is so easy that it is also easy to also break Ubuntu. If you do decide to go ahead seek advice from this forum. Provide information on whether the motherboard is BIOS or UEFI and perhaps provide a screenshot of your disk partitions.

The Disks utility will give a visual representation of the disk partitions. Then we can advise on how to remove, move, resize, create partitions using GParted. Which we run from a Ubuntu live session and not from a working Ubuntu.

Some of us have several Linux operating systems on our hard drives. We can only have those operating systems by using GParted to remove, move, resize and create partitions. It is a scary business but it works fine if we are careful.

Regards

---

### Post by ActionParsnip on 2021-07-31
Is the system currently a dual boot system and you want to remove the Windows section or do you only have Windows and want to then only have Ubuntu on the disk?

---

### Post by Tadaen_Sylvermane on 2021-08-02
The only risk in my case was disappointment. I wanted to switch to Linux exclusively but I like my games. Proton / Lutris / Wine are good but they do have issues. I ultimately went bare metal Windows with Xubuntu in a vm as needed. Even a vm with a passed through gpu didn't quite cut it for me.

Whatever happens try not to be disappointed if you can't maintain the switch. I was with not being able to run Linux exclusively. At the end of the day you should use the right tool for the job. If a philosophy is a good enough reason to run either (along with whatever issues it brings) then go for it. For me its about my needs, don't much care about the why.

---

### Post by TheFu on 2021-08-03
Usually, people new to Linux, which is NOTHING LIKE Windows, need some time to migrate to any new OS effectively. At least a year if you are learning Linux at the same time.  Often the Linux solution to a problem is nothing at all like the Windows solution. Learning to think in the Unix-way is very important for any successful migration.

I'm a die hard fan of non-commercial OSes. Linux, BSD, FreeDOS, and older out-of-support OSes like OS/2 Warp.  Over the decades, I've slowly removed my dependency on MS-Windows.  Today, I'm down to about 3 things that still only work on Windows.  I've used WINE and had my solution for Quicken to work on WINE at WINE-HQ.  Quicken under WINE for a few years, but about 20% of the features didn't work (and would never work).  The other things are tax/finance/stock investing related and video editing. There will likely never be Linux solutions to my needs, though a few times, I thought it was getting close.

I run most of those inside a Windows virtual machine now. It works fine for me, except the video editing part.  More and more, I use Linux tools and 1 tool came very close to ending my Windows commercial tool use, but then that Linux tool stopped working (it was a snap package), so I moved back to the Windows program.  For video creators, Linux has great editing tools, but all those tools transcode the video as part of the render process, which is NOT what I want in a clip cutting editor. I don't want any transcoding that isn't needed.

I don't think there is a realistic way to never use Windows again for my needs.  We all different have different requirements.  Start by making a list of all the programs you use daily and order them by importance.  Then work through your belief for how well the Linux alternatives address your needs.  90% working might be sufficient or it may leave critical capabilities impossible.  Only you can decide. Do that for every program. Note the things that don't work, do some research, ask for help. Don't expect the solution to be the same as it is in Windows.  Linux is fantastic at automation, but Windows people seldom make that transition in the first year.

If I were you, I'd put Windows into a Virtual Machine and have that as a backup plan, but avoid using it unless absolutely necessary.  Compromises will be needed, until you start thinking in the Unix-way and learn to harness the available tools.

---

### Post by sudodus on 2021-08-03
+1 for this good advice by TheFu :KS

---

### Post by monkeybrain20122 on 2021-08-03
OK, let me offer a different opinion from others' (whose opinions I respect) I would say if you are asking the question that means you probably don't have any specific need for Windows in mind. In that case just wipe Windows and switch all the way. Sometimes in order to learn something new you have to throw away your clutches and get out of your comfort zone (e.g Learning a new language, you will never achieve native fluency if you always do translation in your head). If you do need Windows for some software you can set up a VM. Except for some very specific needs like games it is an adequate solution, but now you can install a lot of games on Linux with steam. 

For people who have ditched Windows for Mac there is never such trepidation, they do it in a heartbeat. For some use cases and niches  I can imagine there are things (e.g games) which work on Windows but not Mac but for most who have switched that is obviously not a problem. I don't see how switching to Ubuntu should be different for common use cases, it is not gentoo.


As a caveat, if you have peripherals like printers, check that there is a driver for Linux or (preferably they work out of the box)

---

### Post by garvinrick4 on 2021-08-05
i believe you use Sudodus posts and his +1 and you have your answer

---

### Post by Tadaen_Sylvermane on 2021-08-05
> [COLOR=#000000]For people who have ditched Windows for Mac there is never such trepidation, they do it in a heartbeat. For some use cases and niches I can imagine there are things (e.g games) which work on Windows but not Mac but for most who have switched that is obviously not a problem. I don't see how switching to Ubuntu should be different for common use cases, it is not gentoo.

Interesting point. Never looked at it like that. Maybe due to the reputation Linux has. First thing people seem to think of is a command line nightmare. That or it's association with a hacker / programmer os. They think you need all kinds of knowledge or a college degree or something. [/COLOR]

---

### Post by T6&amp;sfpER35% on 2021-08-05
i quess i did it the hard way lol  
i completely ditched windows and installed linux and started learning from there.
never regretted it either,i have zero use for windows

---

