---
title: "Cannot enter gui ubuntu"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by Newbie94 on 2012-06-20
Hello everyone,

I have a problem with ubuntu, after the ubuntu splash screen, I am presented with a black screen. This was at the beginning.

However, after reading simmilar posts, there was a problem with my nividia driver. I somehow got the machine booted and I entered the desktop only once and updated the drivers through additional driver. Then after that, It only got me into the terminal.

I used nomodeset, but it gave me disconnected from plymouth in orange.

I have a Qosmio X-500 14N laptop.

I would prefer if I can solve this problem through the command line because I enter it when ubuntu boots up.

Could anyone help me out?

---

### Post by pissedoffdude on 2012-06-20
So you installed the proprietary nvidia drivers using the restricted drivers manager?  Let us know which drivers you installed and how you installed them.  For now, login and run these commands:```
sudo killall gdm
sudo dpkg-reconfigure xserver-xorg

```

You'll be asked to pick a driver.  Experiment with generic, or vesa, nv, and nouveau.  I think installing the proprietary nvidia drivers via the restricted manager blacklists the nouveau drivers, so if those were the ones that were working before, you'll have to reinstall them using apt-get.

---

### Post by Gone fishing on 2012-06-20
I think the problem is you have a graphics card that uses optimus technology ie sometimes uses the nvidia card and sometimes uses the intel card.

You need to use Bumblebee have a look at [http://ubuntuforums.org/showthread.php?t=1974380&highlight=bumblebee](http://ubuntuforums.org/showthread.php?t=1974380&highlight=bumblebee) and [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Newbie94 on 2012-06-20
> **pissedoffdude said:**
> So you installed the proprietary nvidia drivers using the restricted drivers manager?  Let us know which drivers you installed and how you installed them.  For now, login and run these commands:```
sudo killall gdm
sudo dpkg-reconfigure xserver-xorg

```

You'll be asked to pick a driver.  Experiment with generic, or vesa, nv, and nouveau.  I think installing the proprietary nvidia drivers via the restricted manager blacklists the nouveau drivers, so if those were the ones that were working before, you'll have to reinstall them using apt-get.

Alright, so I logged in and I entered the code, and I got this:

[IMG]http://i.imgur.com/hrzy1.jpg[/IMG]
(Sorry if the picture's too large, can have it thumbed).

Did I enter it wrong? not very experienced in command lines.

Also, I updated my Nividia Geforce GTS 250M's drivers through additional drivers,
It looked slightly  like this:
[IMG]http://www.cnx-software.com/wp-content/uploads/2011/12/Ubuntu-Additional-Drivers-ATI_Radeon_drivers_Catalyst.png[/IMG]

Except that there was another option beneath it, and I clicked activate. It installed them and restarted, and now I'm back to square 1 again :-|.

---

### Post by Newbie94 on 2012-06-20
> **Gone fishing said:**
> I think the problem is you have a graphics card that uses optimus technology ie sometimes uses the nvidia card and sometimes uses the intel card.

You need to use Bumblebee have a look at [http://ubuntuforums.org/showthread.php?t=1974380&highlight=bumblebee](http://ubuntuforums.org/showthread.php?t=1974380&highlight=bumblebee) and [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

No, my card doesn't have that kind of technology, you can take a look at the specs:

[http://eu.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=EU&com.broadvision.session.new=Yes&PRODUCT_ID=1076255&BV_Script=/jsp/fixup/productPage](http://eu.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?service=EU&com.broadvision.session.new=Yes&PRODUCT_ID=1076255&BV_Script=/jsp/fixup/productPage)

---

### Post by pissedoffdude on 2012-06-20
That's an old command. We might need to do a slightly different one then. For now, uninstall your current nvidia drivers with ```
sudo apt-get purge nvidia*
```  Then run```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If all goes well here, run ```
sudo reboot
``` and everything should be up and running again.  If you're dead-set on getting the nvidia drivers working properly, you may need to use the .run file provided by nvidia

---

### Post by Newbie94 on 2012-06-20
> **pissedoffdude said:**
> That's an old command. We might need to do a slightly different one then. For now, uninstall your current nvidia drivers with ```
sudo apt-get purge nvidia*
```  Then run```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If all goes well here, run ```
sudo reboot
``` and everything should be up and running again.  If you're dead-set on getting the nvidia drivers working properly, you may need to use the .run file provided by nvidia

This is what I entered:
[IMG]http://i.imgur.com/O9HV8.jpg[/IMG]

Rebooted and...
[IMG]http://i.imgur.com/DCwqu.jpg[/IMG]
Here we are again.

I used CTRL-ALT-F7 and I switched back to the gui version.

It gave me this:
[IMG]http://i.imgur.com/W7W8F.jpg[/IMG]

It says that plymouth command failed, maybe this could be part of the problem?

---

### Post by pissedoffdude on 2012-06-20
Try the purge command again.  Looks like you typed nividia instead of nvidia

---

### Post by NikTh on 2012-06-20
Hi , 
i think i will agree with this post

> **Gone fishing said:**
> I think the problem is you have a graphics card that uses optimus technology ie sometimes uses the nvidia card and sometimes uses the intel card.

You need to use Bumblebee have a look at [http://ubuntuforums.org/showthread.php?t=1974380&highlight=bumblebee](http://ubuntuforums.org/showthread.php?t=1974380&highlight=bumblebee) and [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

but to be sure , give this command 
```
lspci -nnk | grep -iA2 vga
``` this is one command . Write it carefully for the result to be correct. 
Take one more picture , to see if 2 cards listed. 
Thanks.

---

### Post by Newbie94 on 2012-06-20
> **NikTh said:**
> Hi , 
i think i will agree with this post



but to be sure , give this command 
```
lspci -nnk | grep -iA2 vga
``` this is one command . Write it carefully for the result to be correct. 
Take one more picture , to see if 2 cards listed. 
Thanks.

I'll try that. however, I have a Nvidia Geforce GTS 250. Does that have optimus technology?

---

### Post by Newbie94 on 2012-06-20
> **pissedoffdude said:**
> Try the purge command again.  Looks like you typed nividia instead of nvidia

Yup, I wrote that incorrectly. Here's what happened.
There was a massive amount of code and then I got this:
[IMG]http://i.imgur.com/3IDGk.jpg[/IMG]
When I rebooted, i entered low graphics mode. Afterwards, it returned back to the terminal.
[IMG]http://i.imgur.com/UQW3I.jpg[/IMG]

Any ideas from here?

---

### Post by pissedoffdude on 2012-06-20
Do you remember which driver you were running before?  I'm assuming you were using the nouveau drivers.  These commands should revert you to it```
sudo rm /etc/X11/xorg.conf
sudo apt-get purge xserver-xorg-video-nouveau
sudo apt-get install xserver-xorg-video-nouveau
```

Don't worry if you get an error about xorg.conf not existing, as you may not have it.  And note the X in X11 ix capitalized.  Run sudo reboot afterwards and let us know if you're still logging into the terminal

---

### Post by Newbie94 on 2012-06-20
> **pissedoffdude said:**
> Do you remember which driver you were running before?  I'm assuming you were using the nouveau drivers.  These commands should revert you to it```
sudo rm /etc/X11/xorg.conf
sudo apt-get purge xserver-xorg-video-nouveau
sudo apt-get install xserver-xorg-video-nouveau
```

Don't worry if you get an error about xorg.conf not existing, as you may not have it.  And note the X in X11 ix capitalized.  Run sudo reboot afterwards and let us know if you're still logging into the terminal

I've been using windows drivers before that, but in additional drivers, I activated some drivers of my graphics card. Afterwards, I uninstalled the drivers. Should I still do this?

---

### Post by pissedoffdude on 2012-06-20
> **Newbie94 said:**
> I've been using windows drivers before that, but in additional drivers, I activated some drivers of my graphics card. Afterwards, I uninstalled the drivers. Should I still do this?

So you're back to having a working gui then?  If everything's working like it used to be, there is no need to type the previous commands.  The additional drivers are supposed to give you better 3d support, so they are necessary for playing games and doing anything graphics intensive.  But it looks like the ones from the restricted drivers manager are having issues with your card, so if you're set on installing them, you'll need to use an external repo or the file that nvidia provides.

---

### Post by Newbie94 on 2012-06-20
> **pissedoffdude said:**
> So you're back to having a working gui then?  If everything's working like it used to be, there is no need to type the previous commands.  The additional drivers are supposed to give you better 3d support, so they are necessary for playing games and doing anything graphics intensive.  But it looks like the ones from the restricted drivers manager are having issues with your card, so if you're set on installing them, you'll need to use an external repo or the file that nvidia provides.

Entered the code.I have a black screen so far, waiting for something to happen.

---

### Post by pissedoffdude on 2012-06-20
After entering them, run sudo reboot, and you should have a working gui like you did before.

I'm gonna go to bed for now, so hopefully someone can fill me in if the issue is not resolved.

---

### Post by jmfal on 2012-06-20
If you can reboot to grub screen and select "recovery" > fix broken packages>

answer yes/no (y/n)  y>enter  > may ask to manually run command > manually enter command> enter

If output shows an error take a picture and at the command prompt > startx . enter
enter username and password at prompt > should put you on the desktop.

---

### Post by jmfal on 2012-06-20
I'm sorry not startx.enter
Try
```
 startx  
```

Then press enter

---

### Post by mastablasta on 2012-06-20
you still didn't check if you have optimus or not. th elink to your specs gives me an error page. however if the noteboko has one of the intel i procesors (i5 or something) and nvidia card it is quite a high chance that you have opotimus technology.
 
so even fi oyu do get your nvidia card to work, your battery will be drained fast(er) than if you had the option to switch.

---

### Post by Sylos on 2012-06-20
> **Newbie94 said:**
> Alright, so I logged in and I entered the code, and I got this:

[IMG]http://i.imgur.com/hrzy1.jpg[/IMG]
(Sorry if the picture's too large, can have it thumbed).

Did I enter it wrong? not very experienced in command lines.

Also, I updated my Nividia Geforce GTS 250M's drivers through additional drivers,
It looked slightly  like this:
[IMG]http://www.cnx-software.com/wp-content/uploads/2011/12/Ubuntu-Additional-Drivers-ATI_Radeon_drivers_Catalyst.png[/IMG]

Except that there was another option beneath it, and I clicked activate. It installed them and restarted, and now I'm back to square 1 again :-|.

So....

Jockey seems to think that you have ati/amd hardware as its offering you the fglrx driver. If you definitely have nvidia (type "lspci" in terminal to find out) then it appears jockey is having a fit and throwing a wobbler, hence your black screen.

Not sure if this is sorted yet but just thought I'd add my observation into the mix.

Cheers

EDIT: Unless you took that from another system for illustration only - then ignore my rambling.

---

### Post by Newbie94 on 2012-06-20
> **jmfal said:**
> If you can reboot to grub screen and select "recovery" > fix broken packages>

answer yes/no (y/n)  y>enter  > may ask to manually run command > manually enter command> enter

If output shows an error take a picture and at the command prompt > startx . enter
enter username and password at prompt > should put you on the desktop.

Alright, I don't want the two full days of getting this thing working to go to waste.

---

### Post by Newbie94 on 2012-06-20
> **mastablasta said:**
> you still didn't check if you have optimus or not. th elink to your specs gives me an error page. however if the noteboko has one of the intel i procesors (i5 or something) and nvidia card it is quite a high chance that you have opotimus technology.
 
so even fi oyu do get your nvidia card to work, your battery will be drained fast(er) than if you had the option to switch.

Problem is that I don't have the terminal anymore, how can I get it back? I'm convinced now that I may have it.

---

### Post by jmfal on 2012-06-20
reboot back to grub and select command prompt

---

### Post by Newbie94 on 2012-06-20
> **jmfal said:**
> reboot back to grub and select command prompt

Which one should I choose?

[IMG]http://i.imgur.com/vwg2k.jpg[/IMG]

---

### Post by jmfal on 2012-06-20
Recovery (2nd)>  then shell(command line)

---

### Post by Newbie94 on 2012-06-20
> **jmfal said:**
> Recovery (2nd)>  then shell(command line)

Should I choose root?
[IMG]http://i.imgur.com/5xtv3.jpg[/IMG]

---

### Post by jmfal on 2012-06-20
select   dpkg  fix broken psckages then answer yes=y  and enter command if it tells you to manually run command

sudo for username >enter password you will not see, it so be careful

---

### Post by Newbie94 on 2012-06-20
> **jmfal said:**
> select   dpkg  fix broken psckages then answer yes=y  and enter command if it tells you to manually run command

sudo for username >enter password you will not see, it so be careful

I'm sorry, but how do I enter my username and password again? I don't see anything as you said before.

---

### Post by jmfal on 2012-06-20
Di d you run the dpkg  if not select dpkg using arrows on keypad >make selection >press enter.

After you run dpkg and  at command prompt enter >

```
startx  
```

after that you will be prompted to enter username   >>enter user name > press enter  >

will prompt you to enter password > enter password you will not see your password  (security measure) >press enter
should put you at the desktop

---

### Post by Newbie94 on 2012-06-20
> **jmfal said:**
> Di d you run the dpkg  if not select dpkg using arrows on keypad >make selection >press enter.

After you run dpkg and  at command prompt enter >

```
startx  
```

after that you will be prompted to enter username   >>enter user name > press enter  >

will prompt you to enter password > enter password you will not see your password  (security measure) >press enter
should put you at the desktop

Did that, no login.
[IMG]http://i.imgur.com/0oOUW.jpg[/IMG]

---

### Post by jmfal on 2012-06-20
OK try this

```
 sudo service lightdm start  
```

I you come back to the  resume naomal boott/ dpkg/ etc...  screen select resume normal boot > press enter,  if not try>

  ```
  startx
```

---

### Post by Newbie94 on 2012-06-20
> **jmfal said:**
> OK try this

```
 sudo service lightdm start  
```

I you come back to the  resume naomal boott/ dpkg/ etc...  screen select resume normal boot > press enter,  if not try>

  ```
  startx
```

Is this correct?

[IMG]http://i.imgur.com/Vi4AV.jpg[/IMG]

FYI, I once chose safe graphics mode and it got me into the desktop, so it could actually be a driver problem, what do you think?

---

### Post by jmfal on 2012-06-20
When you enter the command you  press enter to run the command. 

enter one command at a time and press enter to execute the command.

---

### Post by Newbie94 on 2012-06-20
> **jmfal said:**
> When you enter the command you  press enter to run the command. 

enter one command at a time and press enter to execute the command.

That's what i'm doing. 

I have an Idea, why don't I enter safe graphics mode and update the drivers when I'm there. I was successful when I did that. Do you agree?

---

### Post by jmfal on 2012-06-20
I don't know what else to do!

If you don't have any files that you want/need  I would reinstall and start over.

As one OP suggested you can try  a nvidia from a ppa, do some research first.
 Everything that I'm trying to do should get you to your desktop, you will still have a problem that has to be fixed.

You can try deleting the nomodeset and run the commands that the others gave you.

let me do some research

---

### Post by jmfal on 2012-06-20
Yes try that  I  didn't see that at the bottom of your post  sorry

If you still have problems at least you can let somebody see the terminal outputs.

---

### Post by Newbie94 on 2012-06-20
> **jmfal said:**
> Yes try that  I  didn't see that at the bottom of your post  sorry

If you still have problems at least you can let somebody see the terminal outputs.

How do I enter safe graphics mode?

---

### Post by Newbie94 on 2012-06-20
I would really like someone to help me out right now....

---

### Post by jmfal on 2012-06-20
To enter failsafe graphics mode  reboot to the grub screen and select recovery kernal,
arrow down to failsafe graphics mode >enter

Good luck

---

### Post by Newbie94 on 2012-06-20
> **jmfal said:**
> To enter failsafe graphics mode  reboot to the grub screen and select recovery kernal,
arrow down to failsafe graphics mode >enter

Good luck

Dude, please don't give up on me. I know that we'll solve this problem. Just bare with me.

---

### Post by pissedoffdude on 2012-06-20
> **Newbie94 said:**
> Dude, please don't give up on me. I know that we'll solve this problem. Just bare with me.

So basically, you can only access the terminal as before?  If you can go into low graphics mode, let us know

If not, another possible thing to try is installing the proprietary nvidia drivers:
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot
```

---

### Post by jmfal on 2012-06-20
I'm not giving up 

If you can get to the desktop open a terminal and run the commands that the other OP'S gave you.
You can copy/ paste the outputs to your reply using the  ```

``` tag, which is the "#" symbol,  this will give you a scrolling window making it easier to read huge amounts of code.
You can also copy/paste commands from the forum to the terminal, just make sure that you get the whole command before you > enter<

---

### Post by Newbie94 on 2012-06-20
Have to take a rest guys, I've been working on this  scince 10 am. It's now 7:06 PM. See you tommorow.

---

### Post by Newbie94 on 2012-06-20
Also, sorry about the rudeness in a recent post, that was very immature of me

---

### Post by Newbie94 on 2012-06-21
Alright, so I'm back, does anyone have any ideas?

I entered the grub command line, can I use this to enter commands?
[IMG]http://i.imgur.com/WYVuZ.jpg[/IMG]

Problem is that I can't enter the sudo command, should I reinstall Ubuntu again and see what happens?

Question is...how do I reinstall ubuntu exactly? the CD is in, but it continues with normal boot?

---

### Post by pissedoffdude on 2012-06-21
You shouldn't need to use the grub prompt.  You can type those commands into the terminal you had before.  As another poster suggested, you can also try booting into recovery mode and selecting fail-safe graphics.

If you're going to reinstall ubuntu, just do what you did to install it the first time but don't select any restricted drivers.  If you're dead-set on getting the proprietary nvidia drivers working, you'll have to try an external repo (using the method in my previous post), or you can use the .run file from the nvidia website.

---

### Post by NikTh on 2012-06-21
> **Newbie94 said:**
> 

Question is...how do I reinstall ubuntu exactly? the CD is in, but it continues with normal boot?

You must check you bios configuration first. You must set the CD/DVD first in boot sequence. 
Just take a look at the pre-boot screen , it must have informations about the boot order or how to enter Bios configuration. Usually its a key like "del" or "F12" that you must hit before normal boot begin.

---

### Post by Newbie94 on 2012-06-23
I had to resort to taking my laptop to a repair store, the guy there could't find out what the problem was, and instead installed Fedora.

Oh well, at least I can begin my journey into the world of linux. Thanks for all of your help, especially pissedoffdude.

Goodbye.

---

