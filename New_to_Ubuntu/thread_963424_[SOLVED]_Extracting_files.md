---
title: "[SOLVED] Extracting files"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by sag7392 on 2008-10-30
First let me say that I love Ubuntu and the outstanding support that this community gives! I have taken the plunge into this distro and I absolutely love it...however, being a long time victim of Windows I have a few questions that I couldn't find digging around the forums and other sites. 

Here goes...

Being a noob that loves eye candy, I have been having problems understanding how to extract files that contain themes from Gnome-look. I was trying to change the theme of my MPlayer and the instructions stated to extract the files and then copy them to the MPlayer skins folder...I have tried to do that using the default active manager (I believe), but coming from Windows...I am totally lost. I was wondering if someone could give some step by step instructions on how to do that. 

Also, I have a PPC and I use activesync on a regular basis. Although I can dual boot to my Windows side, I would prefer to do it on the Linux side...any help or thoughts on that...also I do have Wine installed as well.

Thanks in advance for any help and again Linux/Ubuntu rocks :guitar:!

---

### Post by brandoncolorado on 2008-10-30
Sorry, for some clarification, do you mean activesync -- syncing to windows mobile devices?

Does this help?
[http://www.synce.org/moin/](http://www.synce.org/moin/)

Doesn't seem to work well with WINE:
[http://appdb.winehq.org/appview.php?appId=622](http://appdb.winehq.org/appview.php?appId=622)

For copying the theme files, you can use the terminal and use the cp command (search google for that one).
[http://www.computerhope.com/unix/ucp.htm](http://www.computerhope.com/unix/ucp.htm)

---

### Post by brandoncolorado on 2008-10-30
Sorry, I should have been more specific with the skins problem probably.  Here is a more detailed guide:
[http://www.ubuntugeek.com/decorate-your-mplayer-with-mplayer-skins.html](http://www.ubuntugeek.com/decorate-your-mplayer-with-mplayer-skins.html)

---

### Post by sag7392 on 2008-10-30
Thanks for the quick response! On the ActiveSync side...that link was very helpful and I plan to give it a try. 

On the extraction side, I still have some trouble. I found that if I save the file instead of opening it using active manager, I can extract it in the folder in which it resides...no problem there. But, when I try to move the extracted file (cut/copy) and paste it inside the folder I need it in, it states that I do not have permission do so. So, is there something I need to do differently? Also, since I am the only user on my system, why wouldn't I have permission to complete the move? I am still learning how to use terminal commands, so is there a walk through this way?

Again thanks for all your support and help.

---

### Post by brandoncolorado on 2008-10-30
Someone else may be able to help you more, but I believe to copy to those folder you have to use the sudo or gksudo command before the copy command.

---

### Post by dorkdork777 on 2008-10-30
My advice for the skins would be to:
[list=1][*]Make a new folder in /home called "MPSkins" (minus quotes)[*]Extract the files into this folder[*]Run these commands:[/list]
```
mkdir ~/.mplayer/skins/
cd MPSkins
cp * ~/.mplayer/skins/
```

That's the way I'd do it. However, as long as you have the command right, simply placing "sudo" in front of it would most likely work too.

---

### Post by sag7392 on 2008-10-30
Thanks everyone...I figured it out. After I extracted the file, I would cut it, then open the terminal, go with "gksudo nautilus", and then paste the folder into the MPlayer folder...which worked. 

I had to do some digging to understand how "root" works and the purpose of "sudo"...which a little research really educated me. So I am on my way. If you all believe I am doing it incorrectly or there is a faster way, please let me know.

Thanks again!

---

### Post by andrew.46 on 2008-10-30
Hi,

You maay be interested in the collection of skins on the MPlayer site:

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

  Andrew

---

