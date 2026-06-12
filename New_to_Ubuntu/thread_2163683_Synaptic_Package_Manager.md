---
title: "Synaptic Package Manager"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by DaveMcC on 2013-07-19
Hi

I want to remove the lines between ubuntu and winxp, done it before using a "HowTo: Remove Old Ubuntu Kernals"

As seen here [http://jaypeeonline.net/tips-tricks/howto-remove-old-ubuntu-kernels/](http://jaypeeonline.net/tips-tricks/howto-remove-old-ubuntu-kernels/)     .............but i now looks different,   :confused: so before I mess up I thought I should ask, those that know a lot more about this than I do

Here's a photo of what I wish to reduce, not destroy


[http://i7.photobucket.com/albums/y282/dtmcc/DM2_7987.jpg](http://i7.photobucket.com/albums/y282/dtmcc/DM2_7987.jpg)

Thanks

Dave

---

### Post by bmavbeard on 2013-07-19
Just curious, based on the title are you saying that synaptic manager looks different or you cannot find the synaptic manager?  

Or are you saying that you are having a hard time following the tutorial because synaptic doesn't look like that anymore?

I too need to simplify my grub menu I will give it a try and let you know how it goes.  Haven't done that since jaunty it didn't bug me enough I guess

---

### Post by grahammechanical on 2013-07-19
Is that a photograph of your actual Grub boot menu? If so then you do not have any old kernels. That tutorial does not apply. You only have 1 kernel (Linux 3.2.0-29) but 2 sets of boot parameters. The second entry is to set Ubuntu to boot bringing up a recovery menu with options that might fix what is broken. Recovery mode uses the same kernel.

If you want to remove those 2 memory test entries then this link will help.

[https://help.ubuntu.com/community/Grub2/Setup#File_Structure](https://help.ubuntu.com/community/Grub2/Setup#File_Structure)

> **20_memtest86+**[COLOR=#333333][FONT=Ubuntu] Searches for [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]/boot/memtest86+.bin[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] and includes it as an option on the GRUB 2 boot menu. There is currently no line option to remove this entry from the menu. The display of [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]memtest86+[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] can be inhibited by removing the executable bit from this file and running[/FONT][/COLOR]update-grub[COLOR=#333333][FONT=Ubuntu].[/FONT][/COLOR]

Run the 2 commands listed in that section 

```
sudo chmod -x /etc/grub.d/20_memtest86+
```
```
sudo update-grub
```

You are using Grub 1.99. Newer versions of Ubuntu use Grub 2.0 which has the ability to display sub-menus. See the image at the top of this link

[https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2)

The 2 memory test options are still there but recovery mode boot option and earlier kernels are now in the Advanced Options for Ubuntu sub-menu.
Which makes the Grub menu a little bit neater. We still have to use Synaptic to remove the old kernels.

Oh, it occurs to me that I better add if that really is a photograph or your present Grub menu and you use Synaptic to remove Linux kernel 3.2.0-29, then Ubuntu will be broken.

Regards.

---

### Post by DaveMcC on 2013-07-19
> **bmavbeard said:**
> Just curious, based on the title are you saying that synaptic manager looks different or you cannot find the synaptic manager?  

Or are you saying that you are having a hard time following the tutorial because synaptic doesn't look like that anymore?

I too need to simplify my grub menu I will give it a try and let you know how it goes.  Haven't done that since jaunty it didn't bug me enough I guess

It is in step 5 of "HowTo Remove etc" I have only one green image bit, and if I remove (that) I'm fubared

> **grahammechanical said:**
> Is that a photograph of your actual Grub boot menu? 

Yes it is, 

> **grahammechanical said:**
> 
If you want to remove those 2 memory test entries 

Yes I do

[https://help.ubuntu.com/community/Grub2/Setup#File_Structure](https://help.ubuntu.com/community/Grub2/Setup#File_Structure)

Don't understand the above.  tooo much information


> **grahammechanical said:**
> 
Run the 2 commands listed in that section 

```
sudo chmod -x /etc/grub.d/20_memtest86+
```
```
sudo update-grub
```


Does that remove the test things I don't care about ???

> **grahammechanical said:**
> 
You are using Grub 1.99. Newer versions of Ubuntu use Grub 2.0 which has the ability to display sub-menus. See the image at the top of this link

[https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2)

??? why do I want to muck around with some thing I do not understand

> **grahammechanical said:**
> 
The 2 memory test options are still there but recovery mode boot option and earlier kernels are now in the Advanced Options for Ubuntu sub-menu.
Which makes the Grub menu a little bit neater. We still have to use Synaptic to remove the old kernels. 
Not interested


> **grahammechanical said:**
> 
Oh, it occurs to me that I better add if that really is a photograph or your present Grub menu and you use Synaptic to remove Linux kernel 3.2.0-29, then Ubuntu will be broken.


Ah, so I was right, if I had of removed the green part, then it breaks

Yes, yes and yes again

sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub

That done the job, Shorten the whole thing down, just what I wanted

Thanks to grahammechanical for the links and also to bmavbread
We will call this solved,

Dave
 [h=1][COLOR=#000000]
[/COLOR][/h]

---

### Post by deadflowr on 2013-07-19
Yep, running chmod -x will make the memtest, and any other file in the grub.d folder unexecutable.

By my question, though, is why are you running such an old kernel?

3.2.0.29 is close to a year old.

---

### Post by DaveMcC on 2013-07-19
Nothing to do with me, its the software that loaded up from the live CD I made about 4 weeks ago, I quote
Ubuntu
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-29-generic
Gnome 3-4-2

This is viewed on System Monitor

Besides ver 13 of ubuntu is so unstable it couldn't even reboot itself here
I don't mind you, as you are only passing through
helpfull ???

---

### Post by deadflowr on 2013-07-19
> **DaveMcC said:**
> Nothing to do with me, its the software that loaded up from the live CD I made about 4 weeks ago, I quote
Ubuntu
Release 12.04 (precise) 64-bit
Kernel Linux 3.2.0-29-generic
Gnome 3-4-2

This is viewed on System Monitor

Besides ver 13 of ubuntu is so unstable it couldn't even reboot itself here
I don't mind you, as you are only passing through
helpfull ???

Ok, so you just haven't run a full update on it yet.

---

