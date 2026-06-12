---
title: "Docking applications to the panels?"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by NinthJake on 2011-11-03
Hi all, I have installed lubuntu 11.10 on my father's laptop and I have installed firefox which I want to use as the default browser, I have undocked the chromium web-browser and want to add firefox to where chromium was instead but I can't find how I would do that.

I have installed firefox in the /home directory because I don't have permission to install it anywhere else.

---

### Post by ajgreeny on 2011-11-03
What do you mean by "undocked the chromium web-browser" and how did you install firefox?

I presume you may be talking about the Application launch bar by the menu button in the panel.  If I am correct you can just right click in the launch bar and go to "Application Launch bar settings" where you can add and remove things as you please.

For your firefox problem with installation, you need to use synaptic and search for it then click the empty box and click again for installation.  That is the best way (with gui) to install or remove anything.  You can also use ```
sudo apt-get install firefox
```in terminal, just the same as if using Ubuntu.

If you downloaded the package direct from mozilla, you can "system" install that, but it is much more complicated, and at this stage not worth your trying;  why re-invent the wheel when synaptic can do it so easily?  I presume that you downloaded from mozilla, which means firefox will not appear in the main menu, and therefore not in the listed applications for the launch bar.  Use synaptic and it will be available both in the main menu and for the launch bar.

---

### Post by Paddy Landau on 2011-11-03
It is worth adding to ajgreeny's comments why you should always, whenever possible, use the repository (via either Synaptic Package Manager or Ubuntu Software Centre).

The repository:
[LIST]
[*]Is validated and tested by the Ubuntu team
[*]Checks for dependencies and automatically installs required libraries
[*]Checks for conflicts and either resolves them or warns you
[*]Remembers what you've done, so uninstalling is dead easy and safe
[*]Performs extra actions such as adding entries to your menu
[*]Automatically sends updates to your computer (via Update Manager) so you don't have to worry about keeping your programs up-to-date
[/LIST]

Sometimes you may want a program that is not on the official repositories. The developer may offer his own repository (which is easy to add to the package manager), so you still get all the advantages apart from the reassurance of Ubuntu's testing. Google tends to do this.

Occasionally, you may want a program that is not available on any repository. However, in those cases you should get something called a "deb", which the package manager understands. Of course, you don't get the automatic updates or the reassurance of Ubuntu's testing, but you still get all the other advantages.

Never install any other way unless you *really* know what you are doing. If the application offers neither a repository nor a deb, you probably don't want the application.

---

### Post by Miljet on 2011-11-03
Unfortunately the "Powers That Be" decided that Synaptic Package Manager is no longer needed. It is no longer included in version 11.10 unless you install it yourself. 

First Gimp and now Synaptic. What's next to go?

---

### Post by Garland Fox on 2011-11-03
When did gimp go? I just updated to 11.10 and it was there

---

### Post by NinthJake on 2011-11-03
Thanks for the answers guys, I'll do my best to answer but I have never touched a Linux system before so I am not so hot on the "linux savvy" :P

By "panels" I mean the lubuntu version of the windows taskbar.
[IMG]http://www.askdrtech.com/solutions/image.axd?picture=2009%2F10%2FWin7-task-bar-1.png[/IMG]
On my lubuntu install chromium was "docked" like IE is in the image above, I wanted to switch it with firefox so I opened up the "Application launch bar" settings but I could not find any way to add firefox to this list, this probably is due to my "installation" of firefox which is most likely wrong, I basically have no idea how to properly install applications in lubuntu so I just extracted the .tar.bz2 file in my /home/[user]/ directory, I could open firefox from the folder and it worked so I just assumed that I had installed it, as I said, most likely wrong of me, I will try to install it via the terminal but I have never used the Linux terminal in my life so it will probably take some getting used to.

I have heard the repository mentioned many times before (I hang out on the BlenderArtists forums) but I have no idea what it is or what it does. I am fairly positive that neither Synaptic nor the Ubuntu Software Center is included in lubuntu 11.10, at least I did not find anything about it in my hours of searching.

Thanks again for the answers, I'll search around some more based on what you have told me :D

---

### Post by dFlyer on 2011-11-03
Firefox is the default in 11.10 and has been for a long time with ubuntu. I'm not sure what you mean by setting it as default on the launcher since it should be. If your install another web browser and marked that as default your will have goto system settings/default applications and change it back to firefox. To get it on the launcher you need to start firefox and then right click the launcher and click keep in launcher.

---

### Post by gamblor01 on 2011-11-04
Yeah I'm going to agree with those above...Firefox should be installed as the default browser.  You can click on the "Start" menu and mouse over "Internet" to see which applications are installed.  Firefox should be there and if not you can launch a terminal ("Start" > Accessories > LXTerminal) and then type:

```

sudo apt-get install firefox

```

Once you have it installed you can simply right-click on the "File Manager" icon.  It should be the little folder with a mouse pointer on it...right next to the "Start" button.  Now click "Application launch bar settings" and then navigate to Internet > Firefox and add it to the launch bar.

If you deleted the launch bar or all items from it then just right-click any where on the task bar and select "Add / Remove panel items".  Select the "Application Launch bar" and click add.  It should now opens the preferences panel so you can choose which applications to add to it.

Hope that helps!

---

### Post by Paddy Landau on 2011-11-04
> **Miljet said:**
> First Gimp and now Synaptic. What's next to go?
They have been removed from the installation disk because of lack of space. Simply install them from Ubuntu Software Centre.

> **dFlyer said:**
> Firefox is the default in 11.10 and has been for a long time with ubuntu.
 The OP is using Lubuntu, where the default is Chromium.

> **gamblor01 said:**
>  Firefox should be there and if not you can launch a terminal ("Start" > Accessories > LXTerminal) and then type:```
sudo apt-get install firefox
```
Or, if you prefer the GUI, you can open either Ubuntu Software Centre or Synaptic Package Manager (I'm not sure which one comes with Lubuntu 11.10), search for *firefox* and install.

Delete your Firefox installation from /home.

---

### Post by NinthJake on 2011-11-04
Thanks a lot for the help Paddy, I installed the lubuntu software center and it made my life so much easier ^^

I've got both firefox and thunderbird and synaptic installed now so my father should be good for now.

Just one more question though, is it possible to remove the password for an account in lubuntu?

---

### Post by gamblor01 on 2011-11-04
> **NinthJake said:**
> Thanks a lot for the help Paddy, I installed the lubuntu software center and it made my life so much easier ^^

I've got both firefox and thunderbird and synaptic installed now so my father should be good for now.

Just one more question though, is it possible to remove the password for an account in lubuntu?

Sounds great!  I actually prefer the command line myself so I have never used the software center but good to know it worked for you!

In regard to the password question, I do not think that you can remove the password entirely.  What you should be able to do is to bypass the login screen at system startup such that the computer will log directly into LXDE.  You can see this thread for details on how to do that:

[http://ubuntuforums.org/showthread.php?t=1472113](http://ubuntuforums.org/showthread.php?t=1472113)

You will still be prompted to enter it when you need to install software, modify system files, etc.  This is just a protection mechanism so that you don't accidentally run a command that you didn't 100% mean to run.  I am fairly confident that you cannot delete the password from the account entirely.

---

### Post by Miljet on 2011-11-04
> When did gimp go? I just updated to 11.10 and it was there

Gimp disappeared in version 10.04. If you have been upgrading instead of doing fresh installs, of course Gimp would have been brought forward. But it has not been included in new installs since at least 10.04.

---

### Post by amjjawad on 2011-11-05
> **Miljet said:**
> Unfortunately the "Powers That Be" decided that Synaptic Package Manager is no longer needed. It is no longer included in version 11.10 unless you install it yourself. 

First Gimp and now Synaptic. What's next to go?

We are talking about Lubuntu 11.10. The OP is using Lubuntu NOT Ubuntu :)

Synaptic is there and will remain even with Lubuntu 12.04.

GIMP never been there, at least from 10.04.

---

### Post by amjjawad on 2011-11-05
> **NinthJake said:**
> Hi all, I have installed lubuntu 11.10 on my father's laptop and I have installed firefox which I want to use as the default browser, I have undocked the chromium web-browser and want to add firefox to where chromium was instead but I can't find how I would do that.

I have installed firefox in the /home directory because I don't have permission to install it anywhere else.

Hello and Welcome to Ubuntu Forum :)

As a new user to Linux and Lubuntu, kindly have a look at my signature, you'll find a thread: Lubuntu One Stop Thread. Make sure to bookmark it because you'll need it a lot :)

By the way, you need to get used to Linux Names/Features/Stuff :)
I understand you are still new but Linux is not Windows :)

There is a nice article (Linux is not Windows) on my thread, don't miss that :)

---

### Post by amjjawad on 2011-11-05
> **NinthJake said:**
> Thanks a lot for the help Paddy, I installed the lubuntu software center and it made my life so much easier ^^

For anyone who is interested:
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_install_Lubuntu_Software_Center_.28LSC.29](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_install_Lubuntu_Software_Center_.28LSC.29)

> Just one more question though, is it possible to remove the password for an account in lubuntu?
Do you mean to auto login?

If yes, I don't really recommend it but: [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LXDM](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LXDM)

Everything above is found in Lubuntu One Stop Thread under FAQs Section.

---

### Post by Miljet on 2011-11-05
> We are talking about Lubuntu 11.10. The OP is using Lubuntu NOT Ubuntu
You are quite correct and I stand corrected. I was thinking Ubuntu.
I just installed Lubuntu last night and was pleasantly surprised to find Synaptic Package Manager already installed.

---

### Post by amjjawad on 2011-11-06
> **Miljet said:**
> I just installed Lubuntu last night and was pleasantly surprised to find Synaptic Package Manager already installed.

Welcome to Lubuntu Club :D

---

