---
title: "Using Gnome with Ubuntu 14.04"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by JesseJones on 2014-04-27
Hello All,

I've used ubuntu briefly before, decided to go back to using it full time. Usually on the log in screen there is an Ubuntu icon I can click on to change the "shell" (is this the correct term?). The logo is not there so I can't select gnome. I suspect the reason it's not there is because it dosen't come pre-installed in Ubuntu 14.04. I've tried searching for Ubuntu 14.04 and Gnome but I can only find directions to download gnome for 12.04 and 13.10, as well as a lot of news articles saying that Gnome 3.10 will be included in 14.04 and that 3.12 is going to be relased soon.

I'm sorry for the dumb question. Can someone help me figure out how to install gnome on 14.04. Also is 3.12 working well enough to try?

I also found a Gnome release of ubuntu which I think is new. Do I have to install Ubuntu Gnome 14.04 in order to use Gnome? I just finished setting up a Win 8 / Ubuntu Dual boot and would rather not have to reinstall ubuntu.

Thanks for the help!

---

### Post by jmbell on 2014-04-27
Have you tried running this in a terminal?
```
 sudo apt-get install gnome-shell ubuntu-gnome-desktop 
```
Let me know if that works. I haven't tested it, but I'm installing it as I'm typing this post.

---

### Post by jmbell on 2014-04-27
Have you tried running this in a terminal?
```
sudo apt-get install gnome-shell ubuntu-gnome-desktop
```
Let me know if that works.

---

### Post by ibjsb4 on 2014-04-27
Sounds like your after the old gnome desktop look.  To install it:

```
sudo apt-get install gnome-session-flashback
```

---

### Post by Vladlenin5000 on 2014-04-27
Although the method commented in the previous post should work, why not install Ubuntu Gnome from the start? Also keep in mind that if you try just adding the Gnome desktop to a vanilla Ubuntu you should first do

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by sammiev on 2014-04-27
I thought that you were not to mix the two any more and that why they were seperate ISO.

---

### Post by ibjsb4 on 2014-04-27
Yes, Ubuntu Gnome has its own iso and its own spin of flashback.  All based on gnome-shell.

Ubuntu/Unity install also has its flashback session that runs on either compiz or metacity.

[http://packages.ubuntu.com/trusty/gnome-session-flashback](http://packages.ubuntu.com/trusty/gnome-session-flashback)

---

### Post by Odyssey1942 on 2014-04-27
I am running Gnome under 12.04, but would like to move to 14.04. I have seen previous posts saying not to use gnome under 14.04 and have followed up to ask for the issues, but not received any reply.

Vladlenin5000 / ibjsb4, how does one "use gnome from the start"? Is this a separate download from the regular 14.04 or a mod to the regular download? In either case, how does one do this?

Thanks.

---

### Post by tea for one on 2014-04-28
> **JesseJones said:**
> Hello All,

I've used ubuntu briefly before, decided to go back to using it full time. Usually on the log in screen there is an Ubuntu icon I can click on to change the "shell" (is this the correct term?). The logo is not there so I can't select gnome. I suspect the reason it's not there is because it dosen't come pre-installed in Ubuntu 14.04. I've tried searching for Ubuntu 14.04 and Gnome but I can only find directions to download gnome for 12.04 and 13.10, as well as a lot of news articles saying that Gnome 3.10 will be included in 14.04 and that 3.12 is going to be relased soon.

I'm sorry for the dumb question. Can someone help me figure out how to install gnome on 14.04. Also is 3.12 working well enough to try?

I also found a Gnome release of ubuntu which I think is new. Do I have to install Ubuntu Gnome 14.04 in order to use Gnome? I just finished setting up a Win 8 / Ubuntu Dual boot and would rather not have to reinstall ubuntu.

Thanks for the help!

If you install 14.04 with Unity and then add Gnome-shell, you also have to add:-

```
sudo apt-get install gnome-session
```

I found it on the ask ubuntu site with a fuller explanation [http://askubuntu.com/questions/45238...ome-shell-icon](http://askubuntu.com/questions/45238...ome-shell-icon)

---

### Post by ibjsb4 on 2014-04-28
> [COLOR=#000000]Vladlenin5000 / ibjsb4, how does one "use gnome from the start"? Is this a separate download from the regular 14.04 or a mod to the regular download? In either case, how does one do this?[/COLOR]

Post #4 is how I do it and then choose your desktop at the login window.

I do not run gnome-shell, someone else will have to guide you on that.

---

### Post by Odyssey1942 on 2014-04-28
tea41,

The link you posted does not resolve properly. Pasting the thread number brings up this thread
> How can I know the usernames connected to my system?
which does not appear to be the one you intended.

---

### Post by tea for one on 2014-04-28
> **Odyssey1942 said:**
> tea41,

The link you posted does not resolve properly. Pasting the thread number brings up this thread

which does not appear to be the one you intended.

Apologies for the broken link - here is the correct one

[http://askubuntu.com/questions/452385/lightdm-is-missing-gnome-shell-icon](http://askubuntu.com/questions/452385/lightdm-is-missing-gnome-shell-icon)

---

### Post by Odyssey1942 on 2014-04-28
ibjsb4, does your method result in a desktop experience that would be same or very similar to gnome 2 under 12.04, in particular top and bottom panels/multiple workspaces/desktop icons/etc.?

Vladlenin5000 (or anyone) is this the download to "use gnome from the start"?

> [https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME](https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME)

Thanks.

---

### Post by ibjsb4 on 2014-04-28
> [COLOR=#000000]ibjsb4, does your method result in a desktop experience that would be same or very similar to gnome 2 under 12.04, in particular top and bottom panels/multiple workspaces/desktop icons/etc.?[/COLOR]

Ubuntu 12.04 runs gnome3, gnome2 is no longer used (dead project).  But to answer your question, yes.  In 12.04 it was called 'fallback or classic'.  In 14.04 it is now called 'flashback'.  This desktop is setup to look like gnome2, but is really gnome3.

---

### Post by kansasnoob on 2014-04-28
> **Odyssey1942 said:**
> ibjsb4, does your method result in a desktop experience that would be same or very similar to gnome 2 under 12.04, in particular top and bottom panels/multiple workspaces/desktop icons/etc.?

Vladlenin5000 (or anyone) is this the download to "use gnome from the start"?



Thanks.

Look here:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

But IMHO 12.04 is much more stable and it's still supported until April 2017.

---

### Post by JesseJones on 2014-04-28
Thank you everyone for the overwhelming responce. Last night I was in a hurry to get to bed so after reading jmbell's responce I ran 
```

sudo apt-get install gnome-shell ubuntu-gnome-desktop
```

In the terminal and it worked fine. I can now select gnome when logging in.

There have been a lot of questions as to why I didn't just use Ubuntu Gnome in the first place. Also I've noticed a couple of people wondering if Unity and Gnome can be run together

 "I thought that you were not to mix the two any more and that why they were seperate ISO. " sammiev

To clear things up I didn't use Ubuntu Gnome because I never knew it existed. I only found out about it after trying to google instructions to install Gnome on Ubuntu 14.04. It took me forever to get a Dual Boot of Win 8 / Ubuntu on my Thinkpad T530. I've always had issues with the video driver which usually ruins my install and I have to reinstall ubuntu which breaks the GRUB. Anyway like I said this is my first time getting a working dual boot so I would rather not have to reinstall Ubuntu Gnome 14,04. Can someone please clairfy (or point to a clairifying resource), if Unity and Gnome can be run together? What are the advantages of using Ubuntu Gnome over Unity Ubuntu + Gnome? 

Last question: Someone mentioned that I need to be sure to run sudo apt-get update before installing Gnome. I didn't, what are the consequences?

Thanks for all the help again. Appreciate the time you guys take to help a newb!

---

### Post by ibjsb4 on 2014-04-28
Unity and flashback are built on gnome3.  Gnome3 is needed for either one to function.

---

### Post by swarup on 2014-04-28
With regard to getting gnome with 14.04, I am still confused about the various options, their differences and benefits. Like JesseJones, I also installed 14.04 unity before I realized there was a separate iso for the "pure" gnome version of 14.04. Now I need to consider whether it is worth reinstalling from scratch to get gnome 14.04, or whether adding the gnome option to my already installed unity will be sufficient / as good. If someone could explain the benefits of each and the differences between them this would be wonderful.

Also, with regard to the unity + gnome option, what is the difference between

> sudo apt-get install gnome-shell ubuntu-gnome-desktop

and

> sudo apt-get install gnome-session-flashback

As a side note, with regard to the latter option this below site seems to be potentially very helpful. From following the writer's other guides, I got the experience that he is quite skilled:

[http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html](http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html)

---

### Post by tea for one on 2014-04-28
> **swarup said:**
> With regard to getting gnome with 14.04, I am still confused about the various options, their differences and benefits. Like JesseJones, I also installed 14.04 unity before I realized there was a separate iso for the "pure" gnome version of 14.04. Now I need to consider whether it is worth reinstalling from scratch to get gnome 14.04, or whether adding the gnome option to my already installed unity will be sufficient / as good. If someone could explain the benefits of each and the differences between them this would be wonderful.

Also, with regard to the unity + gnome option, what is the difference between



and



As a side note, with regard to the latter option this below site seems to be potentially very helpful. From following the writer's other guides, I got the experience that he is quite skilled:

[http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html](http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html)

Good evening

The first option will pull in extra packages such as Evolution, Gnome chess etc

The second option will allow you to switch between Unity and Gnome-shell without the additional packages that you may or may not want.......

I use the second option because I prefer to add software that I need rather than receive a bundle containing unrequired software.

For example, Ubuntu already includes Thunderbird (for e-mail) therefore I have no need to download and install Evolution.

If you install synaptic and load the first option, you can see all the packages that are contained in ubuntu-gnome-desktop

Kind regards

---

### Post by swarup on 2014-04-28
Many thanks for your kind and helpful reply. From reading it, I understood that by "first option" you refer to [sudo apt-get install gnome-shell ubuntu-gnome-desktop]; and by "second option" you refer to [sudo apt-get install gnome-session-flashback]. From your post I could understand that indeed, these are two different ways of adding gnome as an alternate desktop for an already installed unity 14.04. And I think were I to select this "altenative desktop" pathway, then like you I'd probably select the second option for doing it. 

My first question I would also be very interested to hear your thoughts on: What are the differences between installing from scratch to get gnome 14.04, versus adding the gnome option to an already installed unity 14.04? Are there any differences in the functionality / stability of gnome in the two setups. In the unity option, one has the obvious benefit of switching freely to unity. In the "from scratch" pure gnome option, does one get a better functioning gnome in some way, than one gets with the unity + gnome flashback?

---

### Post by tea for one on 2014-04-29
> **swarup said:**
>  What are the differences between installing from scratch to get gnome 14.04, versus adding the gnome option to an already installed unity 14.04? Are there any differences in the functionality / stability of gnome in the two setups. In the unity option, one has the obvious benefit of switching freely to unity. In the "from scratch" pure gnome option, does one get a better functioning gnome in some way, than one gets with the unity + gnome flashback?

I do not think that Gnome-shell functions any better or worse if you add Gnome-shell to a Unity installation or install Ubuntu-Gnome version.
There are certain differences in the software with each ISO, eg Thunderbird with Unity and Evolution with Ubuntu-Gnome.
Ubuntu-Gnome comes with approx 10 pre-installed extensions but you will have to pick and choose your own extensions if you start with Unity.
(You are familiar with extensions?)
You have different "Tweak" tools at your disposal for each desktop environment.

As I mentioned previously, I start with Unity (which I did with 12.04 and 14.04) and then add Gnome-shell without the extra packages.

As a matter of interest, I reckon I spend 75% of my computer time in Gnome-shell and 25% in Unity - there is no great reason for this because I could comfortably work 100% with either.

Best wishes

---

### Post by swarup on 2014-04-29
I see-- so it sounds like one is really not missing anything by adding Gnome as a shell instead of installing it primarily via iso. And by adding it as a shell, there is the benefit of having unity to experiment with as desired. 
1. I'm not familiar with extensions, but just googled it and got a bit of an idea.
2. In "User Accounts", I had set up automatic login so as not to have to type in my password every time I boot. But now that I've added the Gnome shell, even though login is set to automatic it still gives me the login page and associated requirement that I type my password-- presumably to give me the option of which shell I want at that login. But is there some way to avoid having this login page come every time I boot? Say, have it set up so it will boot automatically to the shell I used the previous time as a default. And then if a particular session I want to change it, I can push some key to make the login screen appear at boot. Otherwise it is just a pain to have to deal with the login screen every boot-- if it can be avoided somehow that would be very nice.

Thanks,
Swarup

---

### Post by tea for one on 2014-04-29
> **swarup said:**
> 
2. In "User Accounts", I had set up automatic login so as not to have to type in my password every time I boot. But now that I've added the Gnome shell, even though login is set to automatic it still gives me the login page and associated requirement that I type my password-- presumably to give me the option of which shell I want at that login. But is there some way to avoid having this login page come every time I boot? Say, have it set up so it will boot automatically to the shell I used the previous time as a default. And then if a particular session I want to change it, I can push some key to make the login screen appear at boot. Otherwise it is just a pain to have to deal with the login screen every boot-- if it can be avoided somehow that would be very nice.

Thanks,
Swarup

I do not use automatic login, therefore I suggest you start a new thread with this question and I'm sure somebody will be able to offer advice.

Kind regards

---

### Post by swarup on 2014-04-29
> **tea for one said:**
> I do not use automatic login, therefore I suggest you start a new thread with this question and I'm sure somebody will be able to offer advice.

Ok, sure-- thank you. [Here is the new thread]("http://ubuntuforums.org/showthread.php?t=2220822&p=13007503#post13007503"). Let us see what advice comes.

---

