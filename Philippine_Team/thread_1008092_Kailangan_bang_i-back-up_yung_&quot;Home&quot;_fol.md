---
title: "Kailangan bang i-back-up yung &quot;Home&quot; folder?"
date: 2008-12-11
forum: Philippine Team
---

### Post by randytan on 2008-12-11
Mga 'Tol,

Una, pasensya na kung ingles ang ginamit ko nung unang post ko dito. Yun kasi ang pangunahing wika na ginagamit ko.

Tanong lang. Mga ilang linggo pa lang ako gumagamit ng dual boot na XP at Ubuntu pero mas gusto ko nang gamitin yung Ubuntu.

Balak ko nang mag reinstall na purong Ubuntu lamang at wala nang XP. Nagkakaproblema na ako ngayon tuwing medyo marami na akong nakabukas na windows at biglang titirik ng konti yung system ko at biglang magtatayp nalang ng letrang "n" na sunod sunod maski hindi pinipindot yung keyboard.

Ang payo sa akin ng kaibigan ko, i-back-up ko lang yung "Home" folder at masesave ko na yung mga email, contacts, bookmarks, at mga dokumento ko.

Tama ba ito?

Sana mabalikan ninyo ako kaagad at balak ko kasing mag reinstall sa susunod na mga araw.

Salamat at sana may makatulong sa akin. :p

---

### Post by jepong on 2008-12-11
ako kasi nilalagay ko sa hiwalay na partition yung \home ko... 

paano ba ginawa mo?

---

### Post by loell on 2008-12-11
> Ang payo sa akin ng kaibigan ko, i-back-up ko lang yung "Home" folder at masesave ko na yung mga email, contacts, bookmarks, at mga dokumento ko.

tama po yan. :)

pero nag-dual boot ka na, kailang mo ba talagang mag-reformat? 

at


Peh: Eeess,
Okie lang mag-post sa wikang ingles. :tongue:

---

### Post by randytan on 2008-12-11
Loell: Ay salamat! This helps. :p

Jepong: Installed kasi sa notebook ko dito sa trabaho. Nauna na yung XP kaya lang nung nagloloko, nilagyan namin ng Ubuntu kaya yon, dual boot na siya.

Since thing are still screwy and the problem has spilled over to Ubuntu. I've got little memory on the HD left since matakaw yung XP.

Thinking this may be the problem, I'm planning a wipe of the hard drive with Ubuntu to be reinstalled as the ONLY OS in there.

Salamat sa mabilis ninyong sagot! ):P

---

### Post by loell on 2008-12-11
> **randytan said:**
> 
Since thing are still screwy and the problem has spilled over to Ubuntu.

I don't think an XP problem can be contagious to an ubuntu install. :D

chances are, its a general hardware issue, could be a none bouncing key? hence the repetitive "N" key stroke?

could post your specs?

---

### Post by adredz on 2008-12-11
> **loell said:**
> I don't think an XP problem can be contagious to an ubuntu install. :D

chances are, its a general hardware issue, could be a none bouncing key? hence the repetitive "N" key stroke?

could post your specs?

yap yap yap. or maybe ur XP is just SICK? i'd say, wipe it out... however, if u can't live without 3D, reformat and reinstall ur SICK XP back.:lolflag: 
BTW, I got SICK XP installed in my system too... but i am not getting the 'n' thing, mine here is 'o' :)

as for the back up thing, yap it's true. just create a separate partition for home during installation. 

Hope this helps...

---

### Post by wersdaluv on 2008-12-11
Tama ang pag-backup ng home folder mo. Isesave nito ang lahat ng personal files mo sa Ubuntu install mo. Sa susunod mong install, mas magandang may separate /home partition ka para pwede ka na lagi mag-reformat ng OS mo nang hindi ginagalaw ang personal files mo. 

Good luck.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by randytan on 2008-12-11
Salamat sa lahat ng mga payo ninyo!

loell: I'm currently using my office issued Toshiba Satellite M50 harman/kardon. Since it was issued by the office, I'm not sure what else is in here. I don't think it's a stuck key since it works fine up to the point where it decides to go haywire.

adredz: Weird isn't it? My colleague had this problem with her office issued notebook but this time, her unit types out the letter "l" :lolflag:

In any case, the whole point of this thread is that I'll be wiping XP off the hard drive with a reformat then reinstall with just Ubuntu. But since I already moved some files, email, etc. I didn't want to have to back them up again individually if I could help it.

wersdaluv: So you guys recommend a separate partition for the home folder? How will I get the new install to recognize that? How much space should I allocate for the OS and for the Home folder?

I'm actually inheriting (read: arbor) my aunt's old Fujitsu Lifebook S2020 come January so I'm planning to wipe XP off that and install Ubutnu. This will be my personal notebook now.

Hope to hear from you guys again soon. :p

---

### Post by adredz on 2008-12-11
@randytan
yap. it's always good to create a separate /home partition so when everything goes wrong, you won't have to configure your system all over again. here's a howto for it: [http://easierbuntu.blogspot.com/2008/03/setting-up-your-home-directory-on.html](http://easierbuntu.blogspot.com/2008/03/setting-up-your-home-directory-on.html)

---

### Post by wersdaluv on 2008-12-11
You allocate 10GB for your Ubuntu Root Partition and everything else for /home and Windows partition in case you want one. 

If you are still going to have a Windows partition, you can access your Linux partitions with [http://www.fs-driver.org/](http://www.fs-driver.org/) . What I do is keep all my personal files on my /home partition so I can easily reformat my Ubuntu or Windows install.

You can easily go about having a separate /home partition by selecting a separate partition on the Live CD installer.  I just can't find screenshots to show you that but it's pretty easy to figure out. :)

---

### Post by randytan on 2008-12-11
Thanks Guys!

Helpful info.

Keep your advice coming.

Hopefully I can become a linux guru like yourselves soon. :p

---

### Post by randytan on 2008-12-12
Syanga pala...

Pag na-back-up ko na yung home folder ko, (300+MB lang pala, akala ko mas malaki pa diyan.) how do I get my new install of Ubuntu to recognize this folder as my home folder?

Will most likely do this tomorrow or early next week na.

Thanks.

:guitar:

---

### Post by _duncan_ on 2008-12-12
Kung malaki ang hard disk capacity mo, maganda rin kung may isa ka pang 8-10 GB spare root partition. So ang final configuration ng hard drive, ganito ang itsura:

partition 1: 8-10 GB (root partition 1)
partition 2: 8-10 GB (root partition 2)
partition 3: 512 MB to 1 GB swap partition (depende sa RAM size)
partition 4: home partition (lahat ng matitirang space)

Ang logic ng spare root partition, kapag may lumabas na bagong version ng Ubuntu, mas safe kung fresh install kesa update existing. Kaya doon sa spare partition muna ang bagong version.

Ma-appreciate mo ang approach na to kung sakaling may sabit ang bagong version (kadalasan driver-related) dahil usable pa rin ang dating version mo. Kapag naayos mo na ang kinks ng bagong version, yung unang root partition mo naman ang magiging spare partition, until the next ubuntu upgrade.

The 2 versions can use the same swap and home partitions, pero para intact pa rin ang original version, kailangan iba ang user name na gamit mo sa pangalawang version.

--------

Maganda rin ang ganitong set-up kung may balak kang sumubok ng ibang linux distros sa laptop mo in the future.

--------

Suggestion lang ito kaibigang Randy. As with most suggestions, you should take it with a grain of salt.

---

### Post by randytan on 2008-12-12
Hi Duncan,

I'll take your suggestion into consideration as it has some merit to it.

A few questions:

[INDENT][LIST]
[*]What is a swap partition?
[*]How do I get Ubuntu to recognize the home folder in the data partition?
[/LIST][/INDENT]

Thanks.

---

### Post by _duncan_ on 2008-12-12
> What is a swap partition?

This is what the OS will use if your RAM size is inadequate to support current processes. It is roughly equivalent to the pagefile in windows.

This is seldom used if you have plenty of RAM, but it's considered good practice to allocate swap space equivalent to your RAM size. Also there are some applications that specifically require a certain amount of swap space to execute. If I remember correctly Oracle is one such application.

> How do I get Ubuntu to recognize the home folder in the data partition?

Not sure I understand the question. The home folder is something you specify explicitly during installation. I always opt for manual partitioning instead of letting ubuntu decide for me.

---

### Post by randytan on 2008-12-12
Hi Duncan,

If my unit already has 1GB of RAM, is it ok to allocate another 1GB as swap partition?

As for my second question, I believe that you already answered it.

So once the partition is designated the home folder, can I just overwrite it with my backed up home folder or is there some sort of syncing process?

Thanks! :p

---

### Post by _duncan_ on 2008-12-12
> If my unit already has 1GB of RAM, is it ok to allocate another 1GB as swap partition?
1 GB swap should be OK for your system.

> So once the partition is designated the home folder, can I just overwrite it with my backed up home folder or is there some sort of syncing process?

What I'll probably do is to start with a fresh home folder, then access the back up folder and copy over only those files I need from the back up. My main reason for doing this is because ubuntu keeps a lot of hidden files in the home folder. Apps that you install/uninstall sometimes leave vestigial config files. These can accumulate over time.

But this is just my preference. What you are proposing is also feasible. There are caveats though: If there are apps you can't get running before due to borked configurations, there is a chance that those borked config files will be carried over to your new install.

----------

BTW, evolution has a feature to save email messages to a single archive file. This file can then be imported after reinstallation. So you'll end up with the same content in evolution as if you didn't reinstall.

I'm away from my ubuntu box so I can't give you the specifics, but maybe you can explore it on your own.

---

### Post by randytan on 2008-12-12
Thanks for the tips Duncan.

These really help.

Will do some back ups then.

If anything else comes to mind, please do share ):P

---

### Post by randytan on 2008-12-13
Hi Duncan, loell, and everyone else,

Before I forget, how do I set the swap partition? Will there be an option in the manual partition?

I'm planning to do the reformat of my work notebook on Monday.

Any last minutes tips for me?

Thanks.

Best regards. :p

---

### Post by _duncan_ on 2008-12-13
> Before I forget, how do I set the swap partition? Will there be an option in the manual partition?


Yes. What I normally do is use a GParted Live CD (a disk parititioning tool) to format the drive way before installation. Then during the manual partition phase of the install, I just point the root, /home and swap partitions to the proper place.

The Ubuntu Live CD itself has a built-in partition editor. Just boot the Ubuntu Live CD on your laptop, then go System > Administration > Partition Editor.

---

### Post by pendletone on 2008-12-13
hi randytan, you can create a swap partition through gparted that came with your ubuntu livecd. what i did on my system, however, was to create one through the [gparted livecd]("http://gparted.sourceforge.net/livecd.php") instead. you can read gparted's documentation [here]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") if you want.

once you've created your partitions to house your /, /home and swap, take note of it (i.e. /dev/sda1, /dev/sda2, etc.) and proceed with the ubuntu install. during installation, when you get to the part "Prepare disk space", choose manual and click forward. you should now see your newly created partitions there. select the partition that you intend to mount as /, click 'Edit Partition', and set its mount point to '/'.

do the same for your /home and linux-swap. once finished, you're good to go! :)

---

### Post by randytan on 2008-12-13
Thanks Guys!

All VERY helpful! :guitar:

I really appreciate the support. :p

---

### Post by randytan on 2009-01-23
Hi Guys and Gals!

Pahabol na tanong!

My friend just got his 8.10 CDs in the mail and when we installed Ubuntu in a computer of his, the whole appearance is different than what I saw.

This being the case, and since I'm encountering some problems, I'm thinking of doing a fresh install of the OS only.

Since I followed the partition advice of 10GB for the OS, 1GB for swap, and the rest for my home directory.

Now my follow up question is, how do I just reinstall the OS part without affecting the swap and home part? I plan to reinstall 8.10 from the CD this time around rather than installing 8.04 then updating to 8.10.

I did this before but I now forget how. :oops:

Thanks.

Hope to hear from y'all again soon.

---

