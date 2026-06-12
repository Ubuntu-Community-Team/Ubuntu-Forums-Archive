---
title: "Blank screen, black GRUB, can't login"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by Mohammad_Khalid_Hussain on 2012-10-05
Assalamu'alaikum,
and Hi! to everyone else.

I've recently decided to enter the Linux world seriously after several failed attempts.

I've successfully installed Ubuntu 12.04 LTS and updated it. I installed various programs and panel indicators using various tutorials across the web. In the end before I got this problem, I ran the Bleeding Edge Script to enable me to install a lot of applications at once.

After all of that, I could still not find some of the apps it promised to install such as Google Chrome. Before restarting since I thought that would fix the problem as maybe there was some system wide files needed upgrading (I come from Windows environment), I decided to install VLC (or some other program) but it gave me an error about some dependencies (I don't recall the error exactly).

I read online that to solve this problem, you have to use:
```
sudo apt-get -f install
```
And so I did. My heart felt really weird when I saw the lines "Removing ..." scrolling through the terminal but I thought maybe they were getting upgraded by newer ones from the internet or something. After this I could not use ```
apt-get
``` as it told me something along the lines of "Cannot find command specified". I thought "Here we go again... a re-install".

So after this process, I restarted the computer. To my surprise the GRUB bootloader now had huge fonts and black background instead of the usual purple background and smaller fonts. After selecting the usual Ubuntu choice, I get the Ubuntu splash for like a second before the screen turns black but the laptop stays on.

Some Questions:
1) Any idea how to fix this and get me back into Ubuntu?
2) If I'm going to reinstall Ubuntu, how can I save all the files I've downloaded as I only have fast internet here at a lab on my uni campus so it would be nice if I could just save it all.

My Specs:
1) Asus K43S i5 2.3Ghz
2) ATI Radeon 6730M 2GB
3) 8GB Ram
4) Anything else you need?

Thanks for a lot for reading this far, I know the post is long but please bear with me.

Regards,

---

### Post by androssofer on 2012-10-05
> **Mohammad_Khalid_Hussain said:**
>  I get the Ubuntu splash for like a second before the screen turns black but the laptop stays on.

Some Questions:
1) Any idea how to fix this and get me back into Ubuntu?
2) If I'm going to reinstall Ubuntu, how can I save all the files I've downloaded as I only have fast internet here at a lab on my uni campus so it would be nice if I could just save it all.

My Specs:
1) Asus K43S i5 2.3Ghz
2) ATI Radeon 6730M 2GB
3) 8GB Ram
4) Anything else you need?

Thanks for a lot for reading this far, I know the post is long but please bear with me.

Regards,

Hi and Welcome..

when you get to the blank screen, try pressing the buttons:

```
Ctrl  Alt  F1
```

it will come up with a black screen with some writing and a login prompt..

if it does this report back and we might be able to repair your system.

---

### Post by Mohammad_Khalid_Hussain on 2012-10-05
> **androssofer said:**
> Hi and Welcome..
if it does this report back and we might be able to repair your system.

Unfortunately I can't see anything on the screen, it actually turns off. I also tried ```
Ctrl Alt F2
``` but to no avail. But when I hit the power button on the laptop, the Ubuntu splash screen comes back on with the white dots becoming orange and then successfully shuts down (supposedly, since I can't see what goes on before).

Can't I use that Repair mode I see in GRUB to do anything about this? How about restoring from a Live CD flash disk?

---

### Post by critin on 2012-10-05
[http://www.omgubuntu.co.uk/2011/05/bleedingedge-script-lets-you-quickly-add-beta-software-to-ubuntu](http://www.omgubuntu.co.uk/2011/05/bleedingedge-script-lets-you-quickly-add-beta-software-to-ubuntu)
>    [B]Sometimes it seems like there just aren&#8217;t enough ways to endanger your stable Ubuntu set-up. 

[/B] *Seriously though folks, BleedingEdge is **not recommended** for casual users or anyone unable to undo issues that arise due to its use.*Installing one thing at a time is safer.

---

### Post by Mohammad_Khalid_Hussain on 2012-10-05
Okay, looks like I messed up.

I guess I'm back to a re-install. Just a couple of questions:
1) All the updates and packages I downloaded through apt-get, how can I back them up so that I can restore them after the re-install?
2) After restoring them, I should be able to use the apt-get command and it will bypass the download part and just install them right?

Thanks a lot for the help.

P.S. Is the command, ```
sudo apt-get -f install
``` safe for use with noobs?

---

### Post by critin on 2012-10-05
apt-get is safe

> 2) After restoring them, I should be able to use the apt-get command and  it will bypass the download part and just install them right?I don' know.  This doesn't sound quite right to me, but  I've never tried to do this from a restore.

You should be able to save them copying to a flash or cd, but it would probably be safer to reinstall them.  You don't know what was deleted during the "removing' incident you mentioned.  So you may just be saving incomplete programs that will present you with the same problem.  Just saying for your information.

---

### Post by Mohammad_Khalid_Hussain on 2012-10-05
Okay thanks a lot for the time you've put in to help me. I guess it's as the saying goes: "No Sacrifice, No Victory". Off I go to reinstall.

---

