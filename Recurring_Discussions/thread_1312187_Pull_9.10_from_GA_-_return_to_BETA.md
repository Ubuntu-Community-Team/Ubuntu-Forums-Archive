---
title: "Pull 9.10 from GA - return to BETA"
date: 2009-11-02
forum: Recurring Discussions
---

### Post by rockney on 2009-11-02
Ubuntu 9.10 Karmic is NOT ready for GA (General Availability).

 1) An upgrade from 2-week old 9.04 Jaunty + DTC trashed the web stuff and turned the box into molasses - painfully slow. Even the "pulsing" logo thing is so slow you don't notice it changing. Ubuntu 9.04 Jaunty ran pretty well. So, burned it down losing 2 weeks of work.

 2) Clean fresh install with 9.10 Desktop Live CD. Running Live off the CD seemed to run pretty well allowing for a little slowness due to the CD drive. However after default Desktop install during which the SSD was cleared and re-formatted it fell apart :

  a) Very slow to install.
  b) 14 minutes to boot where 9.04 was nominal.
  c) 8.5 minutes to see the desktop after login.
  d) Several desktop applets died on the FIRST login!
  e) Painfully slow.

So -- upgrades just don't work properly - to say nothing of the arrogant changing of boot configuration to full Upstart with no consideration of the existing setup.

Further - scratch clean installs produce similar results.

Conclusion -  Ubuntu 9.10 Karmic needs to go back to beta state for a while until it's more fully cooked. At this point it is my opinion this release is causing more harm than good and is wasting a lot of people's time. You don't want to be accused of this being "Ubuntu's Vista".

For reference this is an Intel Atom 1.6GHz system with 2GB of DDR2 and a 32GB SSD intended to be a fan-less appliance, not a production server. And no it's not overheating, I checked.

One final small one - that "pulsing" logo thingy is really poor ... ugly, hard to see it change in normal light, and utterly useless for having a clue what the box is doing.  Overall Karmic 9.10 provides far too little feedback during installation and boot. (ya ya - I'll go turn 'splash' off in grub, but come on folks - it isn't an iThingy or whatever).

---

### Post by fielious on 2009-11-03
I agree. I was very excited about 9.10, but it still is very buggy.  

I have a Lenovo y530
to get the live cd to work had to disable the acpi settings.
the couple of minuets of work before the system freezes and becomes unresponsive.

On the other hand my lcd back-light finely had the full range of adjustments.

After two days of trying to get it to work i went back to mint 7.

---

### Post by Ginsu543 on 2009-11-03
Vista? This is my being totally sarcastic but it seems like Karmic is more like Ubuntu's ME than Vista. I can't even get Karmic installed on my rig (still can't get around the installer seeing my drives as being in RAID when they are not). I had such a smooth installation and transition from 8.10 to 9.04 (and 9.04 has been great), I was totally psyched expecting the same thing with 9.10. But no such luck, unfortunately. The one good thing that came out of all this is that I discovered this forum and was desperate enough to register and post. It's been a great learning experience just reading through some of the posts made by some knowledgeable people.

---

### Post by Mochtroid-X on 2009-11-03
Is there anyone else here of the opinion that every Ubuntu release since 7.04 hasn't been ready for GA? *** removed by ubuntuforums staff ***

---

### Post by rockney on 2009-11-03
> **Ginsu543 said:**
> Vista? This is my being totally sarcastic but it seems like Karmic is more like Ubuntu's ME than Vista

Good point ... I've run every Micro$oft O/S since DOS 1.02 in 1984, but I did skip ME and (oh what was the name?) ... that one M$ did just for kids that bombed badly.

I've complained about Karmic 9.10 (loudly :p ) but am confident the Ubuntu team will get it together. The real shame is all that lost time and frustration.

---

### Post by DejitaruJin on 2009-11-03
> **Mochtroid-X said:**
> Is there anyone else here of the opinion that every Ubuntu release since 7.04 hasn't been ready for GA? I mean come on, Ubuntu 9.10 is a piece of f*cking trash.

Hey now, there's no need to be so harsh.

Then again, my system hasn't gone a single day since the official 9.10 release without hanging...

---

### Post by MightyMe on 2009-11-03
I can only agree. After doing a clean fresh install, the "magical" GRUB2 failed to find my only hard drive during boot!! I have never had any problems with this before while doing upgrades and clean installs. GRUB2 seems to be i beta still.
After several trials and errors while manipulating boot scripts I managed to boot into 9.10 without using the LiveCD. First thing I did was to uninstall GRUB2 and re-install the old GRUB which solved my problem.

---

### Post by Acer3810T on 2009-11-03
I've upgraded 5 computers to 9.10 without any major problems. Upgrading this soon after the release has always been a game of russian roulette. I've had worse luck before.

---

### Post by AlbertTatlocksCap on 2009-11-03
I have also already upgraded to 9.10 on a couple of my machines with very few problems

I am fairly pleased so far

---

### Post by Algus on 2009-11-03
I've had more problems with 9.10 then I've had with any other version of Ubuntu but I don't know how much that says since I've only had a couple problems that I think I've fixed.

1. Aesthetic choices.  The new icons messed my theme up pretty bad, had to spend awhile reconfiguring it so everything was readable (and for some reason the popup when I connect to a wireless network doesn't show my connection strength anymore)

2. Weird video problem.  For some reason all the video I was playing had a messed up blue hue.  Found a solution on the intrawebs to fix it.  

3. Incorrect webcam hue.  For some reason Cheese Webcam  Booth is displaying the wrong colors in the video feed it provides.  Seems to be a problem specifically with that app though since when I take pictures they come out normally and when I use other progs that connect to my webcam  (Skype) the feed looks normal.  

So I dunno.  I mean, 9.10 does a few things a little differently which annoys me in the sense that I have to learn where some stuff has been moved but I guess in the long run it will be better.  Ubuntu Software Center doesn't seem as good as Add/Remove Program was but if the changes they claim are coming in future revisions happen, it should get there.  

I suppose the moral of the story is if you don't want the headache of a new OS version, stick with the LTS releases.

---

### Post by frodon on 2009-11-03
Moved to recurring discussions.

It has been said many times, if what you are looking for is stability just stick with LTS releases.

---

### Post by Nightstrike2009 on 2009-11-03
Pleased with some progress in karmic but i agree its not fit for general release as:

OpenAL (Audio Layer) results in buggy sound popping & Hissing and has to be turned off.

3G Mobile modems no longer connect to internet all though detected with karmic, jaunty managed this fine.

On a minor note login changer/viewer has dissapeared from karmic too, first too problems far more serious. Only sticking with karmic as i can dual boot and am using it for practice with lucid. (Too many bugs with karmic that should have been ironed out before release, suitable for testing, gives bad impression to new users as it is) :(

---

### Post by snowpine on 2009-11-03
This happens with every single Ubuntu release... a new release is never perfect for all users on all hardware. What do you expect with a distro based on Debian Unstable? Ubuntu is not designed to be super-stable; it's designed to be relatively up-to-date and competitive with other leading desktop operating systems. 

Once suggestion I'll repeat because I don't read it often enough: If you are considering upgrading to a new Ubuntu release, dual boot! Use Jaunty and Karmic side-by-side for a while before you take the plunge and risk messing up your system. You don't have to upgrade the week a new release comes out...

---

### Post by TheLastDodo on 2009-11-03
> **snowpine said:**
> This happens with every single Ubuntu release... a new release is never perfect for all users on all hardware. What do you expect with a distro based on Debian Unstable? Ubuntu is not designed to be super-stable; it's designed to be relatively up-to-date and competitive with other leading desktop operating systems. 


The point is that being basically beta-quality at this point makes it harder to compete with other desktop offerings, be they Linux distros or something from Apple or Microsoft. It's not that it's not super-stable, it's that it's only partially functional for a large portion of its user base.

---

### Post by rockney on 2009-11-04
Sorry - in this case I don't agree. Given the volume of bad problems discussed within these forums and the nature of many of those problems 9.10 Karmic is damaging Ubuntu's status and reputation. To say nothing of the incalculable number of hours of human time lost.

I've been using Ubuntu for years on a wide variety of platforms. But no release has done this much damage. If "it's been said many times" don't you suppose there is some validity to these issues? I hope you don't write them off as unknowledgeable average citizens whining because they didn't do it right.

I've been an at-the-keyboard software engineer for 33 years and was head of engineering for the 3rd largest software company in the world until it was bought by Computer Associates.  I don't use a strong opinion like this lightly.

When a simple upgrade on brand new "standard" Intel hardware going from a 2-week old default install of 9.04 up to 9.10 trashes the system so badly it has to be rebuilt from scratch there's definitely serious problems in the release.

---

### Post by spoons on 2009-11-04
Can I just say that Ubuntu 9.10 works better than any Ubuntu I've tried so far. Of course, if you don't like it... ask for your money back. Heh. I wonder how many people who have had problems have bothered their bum to file a bug report?

---

### Post by Chronon on 2009-11-04
> **rockney said:**
> 
 1) An upgrade from 2-week old 9.04 Jaunty + DTC trashed the web stuff and turned the box into molasses - painfully slow. Even the "pulsing" logo thing is so slow you don't notice it changing. Ubuntu 9.04 Jaunty ran pretty well. **So, burned it down losing 2 weeks of work.**

That bit isn't exactly Ubuntu's fault, is it?  It sounds like you got frustrated. . . unless you're claiming that Ubuntu totally wrecked your partitions tables and reformatted without permission.  You should be able to install a fresh Jaunty install over the top by manually partitioning and reserving your /home partition so that it doesn't get formatted.

> 
For reference this is an Intel Atom 1.6GHz system with 2GB of DDR2 and a 32GB SSD intended to be a fan-less appliance, not a production server. And no it's not overheating, I checked.

It's working very smoothly with my Atom N270 in an Eee PC 1000HEB.  It's also a 1.6 GHz Atom processor.  

I'm sorry to hear about your difficulty, but it's hard to gauge statistics based on anecdotes.  I really don't have any idea about the relative frequency of problems with Karmic compared with previous releases.  My personal anecdote is that while I couldn't get the 64-bit LiveCD to run on my Dell 630i, I was able to upgrade both that machine and this netbook to 32-bit Karmic with no problems.  Everything works well.  The integrated sound in my Dell Monitor's webcam even works out of the box now.

---

### Post by Screwdriver0815 on 2009-11-04
I too have to say: Karmic rocks! I installed Kubuntu Karmic last night with a strange feeling... but it turned out nicely. Runs great and the wireless works!! Yippie! In Kubuntu Jaunty, wireless was a PITA. Now... it is a piece of cake. 

speedwise it is the same as Jaunty - so it is okay. It beats any Windows machine in this area over here easily, like snapping the fingers.

---

### Post by eragon100 on 2009-11-04
Yeah it should be returned to beta:

- Only 2 out of 5 speakers worked right after installation

- I had a very irritating problem, namely that the mouse did not behave correctly in any 3d game, making it impossible for me to play games such as nexuiz, ut2004, shadowgrounds, warsow, etc. I had to change my xorg.conf to not load a certain extension to fix this issue, which I have never had before since I switched to ubuntu at the time of 7.04

- Software store does not have enough features yet, I mean come on, you can not even see how much needs to be downloaded for installation! You can not even select multiple packages at the same time to install or remove!

- Sometimes I get very crackly ugly sound, especially in games.

Please, please spend some more time on getting karmic really ready for release, then put it on the site again :wink:

---

### Post by capnthommo on 2009-11-04
sorry folks
i have to say that whilst i feel sympathy with those who have had issues, for me the upgrade went fine.  really fast and no problems to speak of - certainly fewer than intrepid to jaunty and what i did have was simply resolved and minor in character.
i have been very impressed so far.
but then knowing it went fine for me doesn't really help you if you have a serious problem with the o/s i suppose.

cheers
 capnt

---

### Post by NoaHall on 2009-11-04
One of the problems is there aren't enough beta testers. However, now, we have almost every user using and reporting bugs. It'll be patched and fixed much quicker.

---

### Post by SunnyRabbiera on 2009-11-04
> **NoaHall said:**
> One of the problems is there aren't enough beta testers. However, now, we have almost every user using and reporting bugs. It'll be patched and fixed much quicker.

Indeeed, we do need beta testers to assure all goes well, a OS is only as good as those who test it.

---

