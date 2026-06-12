---
title: "things that still stops me in Ubuntu"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by osviweb on 2008-11-28
hallo I don't know if this may be the right place but I'd like to try to make a short list of things that stops me in Ubuntu and which seems to have no solutions or turnaround:

[LIST]
[*]Evolution limit to 2gb
[*]amsn cannot type inside chat
[*]cannot listen to youtube videos in firefox
[*]java not working in firefox
[*]sometimes cannot mout ntfs or external drive
[*]missing a quick image editor / viewer as irfanview
[*]missing something similar to Dreamweaver
[*]missing fonts in gedit
[/LIST]

Details:

- It has been reported in bugzilla a evolution bug with apparently no solution which limitate the Ubuntu email client to max 2gb of emails. My office mailbox is 5gb and I may lose huge part of my emails importing them to Evolution 

- I use a lot messenger. In amsn there is a bug that stops the possibility of actually typing in a chat window. It happens to me everytime I try to chat

- frequently I cannot listen to audio from youtube in firefox. after a reboot maybe works maybe not

- java works fine for me in ephipany browser but does not work in firefox

- I frequently cannot mount my fat32 external hd or my windows ntfs disks. I have to force mount them with long and time consuming terminal comands

- I did not find a image viewer, cropper, resizer fast as Irfanview. Tried about 10 but found no one in which you can paste a image (not saved), resize it, crop and save. Managed to have Irfainview via Wine  

- I did not find anything similar to Dreamweaver. I mean with the preview of code written, site management, find and replace in a whole site etc

- I have missing fonts in gedit like : è , à, € and others. It seems to happen only when I paste text in gedit , not opening a file for a Unicode problem. Unfortunately in Gedit seems impossible to change unicode of a opened file.

I'm on Ubuntu 8.4 some of these are fixed in 8.10 .
Do you thing it's still a point to try and fix or I'm just too far of having a working Ubuntu pc?

thank you very much for suggestions

---

### Post by meborc on 2008-11-28
hi,

some of my thoughts:

*amsn is not the only option you have... i find emesene has many more features and looks good too

*sound/flash/java issues for hardy and intrepid are solved here - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) just follow the instructions for HARDY (this is the main thread to follow if you notice pulseaudio issues)

---

### Post by northern lights on 2008-11-28
Using thunderbird instead of evolution should solve the email issue.

For better flash and video content in firefox, replace *totem-mozilla* by *mozilla-mplayer*:```
sudo apt-get autoremove totem-mozilla && sudo apt-get update && sudo apt-get install mozilla-mplayer flshplugin-nonfree
```

Try pidgin as an amsn replacement.

---

### Post by osviweb on 2008-11-28
I receive the error 
Couldn't find package flshplugin-nonfree

:(

thanks for your suggestions.
Ok for thunderbird

Amsn is not a valid software I see

---

### Post by philinux on 2008-11-28
Typo Flash.

2gig limit - you need ubuntu64 bit to keep evolution.

---

### Post by ashmew2 on 2008-11-28
[LIST]
[*]Evolution limit to 2gb

Use Thunderbird.

[*]amsn cannot type inside chat
Pidgin , Gaim , Kopete , all of them support MSN (if memory serves me well)

[*]cannot listen to youtube videos in firefox
Well , im using 8.10 and i can conclude that flash works flawlessly.

[*]java not working in firefox
It does in Intrepid , atleast on my end.

[*]sometimes cannot mount ntfs or external drive
Yeah well that also works out more or less with a lil help from psychocats.net tutorials.

[*]missing a quick image editor / viewer as irfanview
GIMP should cut it but im not really sure.


In a nutshell..I think you should do a fresh install of Intrepid.

---

### Post by philinux on 2008-11-28
Allegedly irfanview works with wine.
[http://www.wine-reviews.net/applications/irfanview-410-on-linux-with-wine.html](http://www.wine-reviews.net/applications/irfanview-410-on-linux-with-wine.html)

---

### Post by Dedoimedo on 2008-11-28
> **osviweb said:**
> hallo I don't know if this may be the right place but I'd like to try to make a short list of things that stops me in Ubuntu and which seems to have no solutions or turnaround:

[LIST]
[*]Evolution limit to 2gb
[*]amsn cannot type inside chat
[*]cannot listen to youtube videos in firefox
[*]java not working in firefox
[*]sometimes cannot mout ntfs or external drive
[*]missing a quick image editor / viewer as irfanview
[*]missing something similar to Dreamweaver
[*]missing fonts in gedit
[/LIST]

Details:

- It has been reported in bugzilla a evolution bug with apparently no solution which limitate the Ubuntu email client to max 2gb of emails. My office mailbox is 5gb and I may lose huge part of my emails importing them to Evolution 

- I use a lot messenger. In amsn there is a bug that stops the possibility of actually typing in a chat window. It happens to me everytime I try to chat

- frequently I cannot listen to audio from youtube in firefox. after a reboot maybe works maybe not

- java works fine for me in ephipany browser but does not work in firefox

- I frequently cannot mount my fat32 external hd or my windows ntfs disks. I have to force mount them with long and time consuming terminal comands

- I did not find a image viewer, cropper, resizer fast as Irfanview. Tried about 10 but found no one in which you can paste a image (not saved), resize it, crop and save. Managed to have Irfainview via Wine  

- I did not find anything similar to Dreamweaver. I mean with the preview of code written, site management, find and replace in a whole site etc

- I have missing fonts in gedit like : è , à, € and others. It seems to happen only when I paste text in gedit , not opening a file for a Unicode problem. Unfortunately in Gedit seems impossible to change unicode of a opened file.

I'm on Ubuntu 8.4 some of these are fixed in 8.10 .
Do you thing it's still a point to try and fix or I'm just too far of having a working Ubuntu pc?

thank you very much for suggestions

Hello,

1. Try Thunderbird.

2. Try Pidgin with MSN protocol.

3. Get Flash:
[http://www.dedoimedo.com/computers/flash_firefox_linux.html](http://www.dedoimedo.com/computers/flash_firefox_linux.html)

4. Similarly as above, check my Ubuntu Intrepid tutorial (sig).

5. Automounting NTFS drives in Ubuntu + useful commands and configurations (including mounting):
[http://www.dedoimedo.com/computers/automount_ntfs.html](http://www.dedoimedo.com/computers/automount_ntfs.html)
[http://www.dedoimedo.com/computers/linux_commands.html](http://www.dedoimedo.com/computers/linux_commands.html)

6. Nothing to add there. IW is great. On Linux, I use GIMP.

7. Bluefish.

8. Not sure what the problem is, please elaborate a little more.

The effort is entirely your choice. If you want, keep trying. If not, give up. Personally, I think you are not that far from enjoying Ubuntu properly :)

Dedoimedo

---

### Post by m_duck on 2008-11-28
**1.** Not sure.
**2.** Pidgin is what I use for msn, there is also emesene.
**3.** Flash works for me on Intrepid 64-bit (and did on Hardy as well) just installing the "flashplugin-nonfree" package. I think it is included with "ubuntu-restricted-extras" as well.
**4.** Whatever java is included with "ubuntu-restricted-extras" works on my system as well.```
sudo apt-get install ubuntu-restricted-extras
```
**5.** The NTFS partitions will need to be properly unmounted to be able to mount them in Ubuntu without the "force" option. I.e. if you end up hard resetting Windows, then boot straight to Ubuntu, it will require a forced mount as this resets the status file on the disk (or whatever it is called). Another good guide for automounting on startup is: [How To Fstab]("http://ubuntuforums.org/showthread.php?t=283131") and the [Ubuntu wiki]("https://help.ubuntu.com/community/Fstab")
**6.** Not sure. I think you can resize and do other things on the command line with the "mogrify" command. I think it is part of the "imagemagick" package. Some info [here]("http://www.imagemagick.org/www/mogrify.html").
**7.** Not sure.
**8.** Not sure.

---

### Post by osviweb on 2008-11-28
thanks to everyone for the kind suggestions
I'll keep trying that's sure!
I'm tring to follow some of your suggestions: With my actual knowledge it takes me time but then for sure I'll update this thread.

I just hope that thunderbird will be able to handle my very large mailbox (>5gb)

---

### Post by jamesstansell on 2008-11-30
> java works fine for me in ephipany browser but does not work in firefox

Tell us more about the failure.

Also, does epiphany have a different plugin list than firefox?

[http://browserspy.dk/plugins.php?detail=1](http://browserspy.dk/plugins.php?detail=1)

-james.

---

### Post by Xiong Chiamiov on 2008-11-30
People seem to have covered everything pretty well, but I'd like to leave a note on this one:

> **osviweb said:**
> I did not find anything similar to Dreamweaver. I mean with the preview of code written, site management, find and replace in a whole site etc

Most Linux users like to have fairly good control over things themselves.  Thus, all code is written by hand, they manage projects using an SCM and sensical folder structures, and do find/replace over multiple files using perl.

While you don't have to do all of that (for instance, the editor I use, Komodo Edit, has project management, as well as find/replace among files), you have to realize that most of the people writing the software do things this way.  They're writing software for themselves, and giving it to other people because they're awesome.  That's why there's an abundance of programming tools that just aren't available on Windows, but also why there are many areas that are sadly lacking.

---

### Post by Kai-vana on 2008-11-30
As a last resort I have successfully gotten Dreamweaver CS3 to run in wine, It is just a bit tricky to get set up.

---

