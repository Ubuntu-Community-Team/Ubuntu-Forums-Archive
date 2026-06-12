---
title: "Modifying the Ubuntu ISO"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by abnordude on 2011-11-03
Well......Tiz' just that most of my friends want to use ubuntu.....The fact is that most of them dont have an internet connection........I have an ubuntu iso file(with only the default software i.e no games like supertuxkart etc)........But I need to put some softwares and games in it........Can I modify the iso to add softwares and the games(like adding restricted extras,blender, video editing softwares, compiz effects etc)......i know it is possible.......But i need **detailed instructions **on how to do that.......I want step by step on how to do that.......PLease help me guys........

---

### Post by wolfen69 on 2011-11-03
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by mörgæs on 2011-11-03
You are likely to get more answers, if you give the thread a better title. I have changed it for you.

---

### Post by abnordude on 2011-11-03
> **wolfen69 said:**
> [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

Yes...But it seems all this have to be done in command line mode......Isnt there any GUI......Also i am going to put software that I have in my computer in the iso....not gonna download it from the internet separately.........

---

### Post by abnordude on 2011-11-03
> **mörgæs said:**
> You are likely to get more answers, if you give the thread a better title. I have changed it for you.


Thanks

---

### Post by wolfen69 on 2011-11-03
> **abnordude said:**
> Yes...But it seems all this have to be done in command line mode......Isnt there any GUI......Also i am going to put software that I have in my computer in the iso....not gonna download it from the internet separately.........

You could install Remastersys to create a re-distributable copy of ubuntu. You just set up your computer the way you want it, then in the terminal,
```
remastersys dist
```
it will create an iso of your installation that can be installed on any computer.
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by abnordude on 2011-11-03
> **wolfen69 said:**
> You could install Remastersys to create a re-distributable copy of ubuntu. You just set up your computer the way you want it, then in the terminal,
```
remastersys dist
```it will create an iso of your installation that can be installed on any computer.
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)


Yes...this is what I need........I'll download it.....But now  i wont be here in ubuntuforums [goin to sleep]...I'll be back 2morro..........Please help me if I face any problem while using remastersys.......

---

### Post by anewguy on 2011-11-03
> **wolfen69 said:**
> You could install Remastersys to create a re-distributable copy of ubuntu. You just set up your computer the way you want it, then in the terminal,
```
remastersys dist
```
it will create an iso of your installation that can be installed on any computer.
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

Thank you!!  I was trying to remember this and just couldn't for the life of me.  I need this to create a backup installer CD for another laptop I'm sending to my elderly parents.

Thanks again!
Dave ;)

---

### Post by Majorix on 2011-11-03
[This here]("http://aptoncd.sourceforge.net/") seems like what you asked for, and should be easier to handle than the solution you are offered.

EDIT: Just checked and saw that the project seems kinda abandoned. No updates since 2007. Still worth a check since .deb files are the same they were back then.

---

### Post by anewguy on 2011-11-06
> **Majorix said:**
> [This here]("http://aptoncd.sourceforge.net/") seems like what you asked for, and should be easier to handle than the solution you are offered.

EDIT: Just checked and saw that the project seems kinda abandoned. No updates since 2007. Still worth a check since .deb files are the same they were back then.

You need to understand - the OP posted wanting to add to the installation ISO image.  You are talking apples to everyone else's oranges here.


So now there are at least 2 ways being presented here:

- the original add to the ISO image

- the aptoncd to create a "package" cd with all the extra packages you might want to pick and choose from to install on those other PCs


It's important to keep in mind what you really want to do.  If you want to just take a single CD to the other PC's, install Ubuntu and the extra packages from it, you would be modifying the ISO as already mentioned here.  At this point you really need to take into serious consideration the size of the medium being used - the default 32-bit 11.10 LiveCD contains approx 728mb already - not much room left for adding anymore software to that.  So, maybe you'd need to use a DVD - but then you'll need to have a tool that can create that.  I would follow wolfen69's advice on setting up your PC as you want the others, then using something like remastersys.  What I don't know is if remastersys lets you create a bootable DVD image you can burn.  EDIT:  Just checked, and yes remastersys can create the DVD as well.

The aptoncd, if it's even still active and still works on the newer versions of Ubuntu, would let you use the LiveCD to install Ubuntu and then use aptoncd to create a software "package" cd with the extra packages and dependencies you wish to install and use it to install the extra packages on the other PCs.

There is another option as well, or at least I should say there used to be - I haven't checked in a while to see if it's still available.  You used to able to download DVD sets that basically included a lot of the software already.

Dave ;)

---

### Post by cbowman57 on 2011-11-06
[UCK]("http://uck.sourceforge.net/") is all he needs.  Ubuntu Customisation Kit, makes it so easy even I could do it. ;)

---

### Post by anewguy on 2011-11-06
Looks like it took over for aptoncd.  The only question I have:  it seems to build on the install ISO, so is it still limited to the size of the CD?  I suspect that when the OP adds some of the packages they want to that the result will be too large for the CD.

Ideally, and maybe this does it but it doesn't appear that way from their web site, is to have a current tool that will build a software CD or DVD.  Not an installation CD, but a CD or DVD of packages to add on.  The OP would be able to build a media containing the additional packages and their dependencies that they could hopefully either install with apt or via the software center.  In this way the OP would install from the LiveCD so that things like the drivers, etc., they have on their PC don't interfere like they would if they built an install CD from their installation.  In other words, just a plain install.  Follow that with a CD or DVD containing the packages and dependencies for the extra software they want.

I may need to do some hunting around to see if I can find something more current than aptoncd but that still provides its' functionality.

---

### Post by cbowman57 on 2011-11-06
Regarding UCK:

You'd have to really work to build an iso bigger than 4Gb.

The only real limitation is that the target iso has to be a live iso, though there is an Ubuntu Mini Remix iso on the web that will work also.  A good start if your plan is to strip it from the inside out anyway & practically rebuild it from scratch.

Oh, another limitation is that if you want to build a 64-bit iso it has to be built on a 64-bit machine.

Before you pass on it, install it and crack open an iso & see just how easy it is.

---

### Post by anewguy on 2011-11-06
So I guess you've answered my question - it must be able to write to a DVD since you're saying the limit is around 4gb.

I know what the OP is getting at, and I see everyone's point about using a single disk.  I just question building everything up on their PC then remastering the disk.  So, that leads to another question which may help the OP out more as well:

- does UCK or remastersys either take the LiveCD as input, allow you to add packages to it (but not to your PC necessarily) and create a new LiveCD with the additional packages that is truely the LiveCD - not the installation someone has on their PC?  Hope I'm asking that in a way that makes sense.  One way you'd be free of PC-specific drivers, etc..  The other way you wouldn't.

Thanks for the info, and look forward to the answer on this as well.

Dave ;)

---

### Post by cbowman57 on 2011-11-06
Ok, Remastersys takes your existing system and creates a backup or distro iso out of it.

UCK lets you extract the iso, add or subtract parts of it then reassembles it.  You end up with only what you add or subtract within the iso.  The files & settings on the machine you build with doesn't factor in at all.

Hope that makes some sense.


Just want to add, Remastersys is great at what it does too.

---

### Post by anewguy on 2011-11-06
That's perfect for me, and I think that would really be what the OP really should do.  That way it is always a "raw" install plus the additional software.

Thanks!
Dave ;)

---

### Post by cbowman57 on 2011-11-06
Glad to help Dave.

---

### Post by anewguy on 2011-11-07
> **abnordude said:**
> Well......Tiz' just that most of my friends want to use ubuntu.....The fact is that most of them dont have an internet connection........I have an ubuntu iso file(with only the default software i.e no games like supertuxkart etc)........But I need to put some softwares and games in it........Can I modify the iso to add softwares and the games(like adding restricted extras,blender, video editing softwares, compiz effects etc)......i know it is possible.......But i need **detailed instructions **on how to do that.......I want step by step on how to do that.......PLease help me guys........

After getting these questions answered, it would seem to me that you really do want to use UCK as recommended by cbowman57.

It will take the LiveCD ISO, let you add packages to it as you want to, then create a new ISO.  This allows you to install to your friends' PCs as a new install each time with the added software.  After some research, remastersys takes your existing system and creates an ISO from it.  This would be fine, but you need to consider drivers and settings set specifically for your hardware that you may not want to move to your friends' systems. 

Based on that, I would recommend trying UCK.  Keep in mind the 11.04 LiveCD already contains about 728mb, so there isn't much room left on that.  Since both UCK and remastersys allow you to create a DVD, if you have a DVD burner, and if your friends' systems have DVD readers, you would gain a lot of room by using a DVD instead - the source is still the LiveCD iso, it's just the output would be to DVD.

Thanks cbowman57 for your wonderful input to this thread.

Dave ;)

---

### Post by abnordude on 2011-11-08
> **anewguy said:**
> After getting these questions answered, it would seem to me that you really do want to use UCK as recommended by cbowman57.

It will take the LiveCD ISO, let you add packages to it as you want to, then create a new ISO.  This allows you to install to your friends' PCs as a new install each time with the added software.  After some research, remastersys takes your existing system and creates an ISO from it.  This would be fine, but you need to consider drivers and settings set specifically for your hardware that you may not want to move to your friends' systems. 

Based on that, I would recommend trying UCK.  Keep in mind the 11.04 LiveCD already contains about 728mb, so there isn't much room left on that.  Since both UCK and remastersys allow you to create a DVD, if you have a DVD burner, and if your friends' systems have DVD readers, you would gain a lot of room by using a DVD instead - the source is still the LiveCD iso, it's just the output would be to DVD.

Thanks cbowman57 for your wonderful input to this thread.

Dave ;)


Well.....I thought of using uck.....But for uck, i'd have to download the packages from the internet......HEnce I choose remastersys.......

But it seems there is a problem i cant understand.....After I create the iso with the remastersys option dist......and then i try that in the virtual box i get an error message.....something about an error 15:File not found(when i used grub option).....PLease help me...

---

### Post by anewguy on 2011-11-08
Using UCK or loading the packages to your own PC - someplace along the line they have to get downloaded.  

As far as your problem with remastersys, you'll need to find someone who's an expert with that - perhaps someone with that expertise will post here.  I'm not familiar with remastersys beyond what I've read on the net, so I guess I'm done here now.

Best of luck!

Dave ;)

---

### Post by Gene_J on 2011-11-08
I have been considering doing the same thing for friends computers. One thing I haven't heard mentioned is updates. Can updates to the distro and to the packages be included using UCK. I don't see any mention of that here or on the UCK site. Sorry if I missed it.

---

### Post by abnordude on 2011-11-08
I used remastersys....But I get this error....

The compressed filesystem is larger than the iso9660 specification allows for a single file. You must try to reduce the amount of data you are backing up and try again.

I know it should be less than 4gb, but i used the dist option and i have most "space consuming files in home".....but when using dist option home isnt considered. right?.......
So what happened?....
I have attached a screenshot of the process.....please help me.....I seriously want to create a remastered disc to share with ma friends...

---

### Post by abnordude on 2011-11-08
is there any other software that can help me do that.....

What I want to do is.......

$ I have ubuntu with some softwares that i downloaded from the internet
$ I need a software that can load an iso file in which I can add softwares to it (but only the ones that I have installed in my computer, not from the internet [<- like uck X])
$ Then save the remsatered iso in the computer (also if more than 4 gb, then it should give an option to create more than one dvd, (sort of like what aptoncd does)
$ In short, I want a software that combines UCK, remastersys and aptoncd......

Can a software developer create a software like this?

---

### Post by cbowman57 on 2011-11-08
> **Gene_J said:**
> I have been considering doing the same thing for friends computers. One thing I haven't heard mentioned is updates. Can updates to the distro and to the packages be included using UCK. I don't see any mention of that here or on the UCK site. Sorry if I missed it.

Working with UCK you can use the terminal and use apt, do updates & upgrades, dist-upgrades, add ppa's, etc.. 

The best way to figure out what it does is install it & crack open an iso and go exploring.

---

### Post by Gene_J on 2011-11-08
> **cbowman57 said:**
> Working with UCK you can use the terminal and use apt, do updates & upgrades, dist-upgrades, add ppa's, etc.. 

The best way to figure out what it does is install it & crack open an iso and go exploring.


I shall go exploring, thanks.

---

### Post by mysteriousdarren on 2011-11-11
remastersys +1

---

### Post by abnordude on 2011-11-11
yes...I finally was able to use remastersys(i had some problems initially, but is now okay)......tis' great.....I recommend remastersys to anyone who wants to make a remasted copy of your distro.......

[Huge Sigh] FInally.....I can give the modified distro to my friends......Thanks everyone....

---

