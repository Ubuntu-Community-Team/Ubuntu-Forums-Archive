---
title: "Is There a Different File Browser I Can Use?"
date: 2015-02-27
forum: New to Ubuntu
---

### Post by Anigai on 2015-02-27
Hi guys, I'm somewhat new to Ubuntu. I used Ubuntu 14.04 LTS on my laptop as my main OS for about a month in December but ended up going back to Windows 7 and dual booting with a few different distros trying to see if they all had this same problem.

I regularly partake in image sharing websites and posting images on the dreaded Facebook and I want to return to using Ubuntu but I can't figure out how to turn this:
[https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-xpf1/v/t34.0-12/10981197_979162955428013_4588557903330043859_n.jpg?oh=0c4642590f2ce62807ceba48b9eab62c&oe=54F36C90&__gda__=1425232879_2455f03cbc95ca4fb3fff91f492b5fa1](https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-xpf1/v/t34.0-12/10981197_979162955428013_4588557903330043859_n.jpg?oh=0c4642590f2ce62807ceba48b9eab62c&oe=54F36C90&__gda__=1425232879_2455f03cbc95ca4fb3fff91f492b5fa1)

Into this:

[https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-xpf1/v/t34.0-12/10933692_979162938761348_322644883337894595_n.jpg?oh=af56f724f7b4590fe7e8013bdeaa3a0c&oe=54F3A6C7&__gda__=1425244536_309c96a0854c92ded268799875765977](https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-xpf1/v/t34.0-12/10933692_979162938761348_322644883337894595_n.jpg?oh=af56f724f7b4590fe7e8013bdeaa3a0c&oe=54F3A6C7&__gda__=1425244536_309c96a0854c92ded268799875765977)
I asked a friend of mine who is a long term user of Ubuntu since version 10 I think he said and he mentioned something about GTK and QT. I'm somewhat handy with Windows but my Linux knowledge is limited. Any help would be appreciated.

(The OS being used in the 1st image is "Zorin OS 9" and the 2nd one is "Windows 7")

---

### Post by Anigai on 2015-02-27
It's really just the lack of thumbnails I don't like, I know they are other desktop environments than Unity but they all seem to use this window type without the thumbnails.

---

### Post by ajgreeny on 2015-02-27
You are missing window decorations and titlebar which means there is no configuration icon for nautilus showing. Do you have those window decorations on other windows?
If you could configure nautilus preferences you would be able to set the view to thumbnails; you can still do so, I think from the menu which ought to show in the top panei when you put the cursor in the panel.

---

### Post by Anigai on 2015-02-27
I do yes in normal windows but these windows are opened by clicking "Add Photos" in a Facebook conversation in both Windows 7 and Linux.

I found more settings if I open my home folder from my desktop but none that change how this separate window works when I open it from the Facebook "Add Photos" option.

---

### Post by wildmanne39 on 2015-02-27
Please use thumbnails or URL's for images because many people have slow connections and can not load pages with large images on them. 
Thanks

---

### Post by ajgreeny on 2015-02-28
> **Anigai said:**
> I do yes in normal windows but these windows are opened by clicking "Add Photos" in a Facebook conversation in both Windows 7 and Linux.

I found more settings if I open my home folder from my desktop but none that change how this separate window works when I open it from the Facebook "Add Photos" option.
I suspect that is not a nautilus window, in that case, but just some file chooser window perhaps, and if it also shows in Windows then it is nothing to do with Ubuntu. 
It is probably a Facebook window of some sort, and there you are on your own as far as I'm concerned as I don't use or subscribe to Facebook, so I certainly can not help you at all, I'm afraid.

---

### Post by Anigai on 2015-02-28
> **Wild Man said:**
> Please use thumbnails or URL's for images because many people have slow connections and can not load pages with large images on them. 
Thanks

Duly noted, makes sense thanks.

> **ajgreeny said:**
> I suspect that is not a nautilus window, in that case, but just some file chooser window perhaps, and if it also shows in Windows then it is nothing to do with Ubuntu. 
It is probably a Facebook window of some sort, and there you are on your own as far as I'm concerned as I don't use or subscribe to Facebook, so I certainly can not help you at all, I'm afraid.

Well if it were a Facebook window then it would be the same between both types of operating systems but thanks for your help.

I had no idea what Nautilus was until I googled alternatives to it. I found Nautilus Elementary so i think my next step is to try and get it onto my system, the website I found had some instructions that look good so I'd better get to work.

---

### Post by newb85 on 2015-02-28
I, too, suspect that first screenshot is not a nautilus window.  In fact, if that really was Ubuntu, someone had spent some time customizing it.  The theme is completely different, the window buttons have been moved, the icons are different, and the file browser is different.  Here's a shot of my Ubuntu system, with nautilus open, exhibiting the thumbnails in question.

---

### Post by coldraven on 2015-02-28
In Nautilus, like most file browsers, you have the option of seeing thumbnails or a list. It's in the top right corner. What you're seeing is the upload gadget

---

### Post by Anigai on 2015-02-28
Now that makes a lot of sense. The upload gadget doesn't seem to have the same options as the standard file browser window like list/thumbnail view and that's what threw me for a loop.

---

### Post by CantankRus on 2015-02-28
> **Anigai said:**
> Now that makes a lot of sense. The upload gadget doesn't seem to have the same options as the standard file browser window like list/thumbnail view and that's what threw me for a loop.
You can't change the view in the gtk-file-chooser.
One option is to bypass the gtk-file-chooser and use your file browser in thumbnail view 
to drag and drop your file into the web page upload dialog,
as you can with attachments in this forum.

---

### Post by vasa1 on 2015-02-28
> **Anigai said:**
> Now that makes a lot of sense. The upload gadget doesn't seem to have the same options as the standard file browser window like list/thumbnail view and that's what threw me for a loop.So which distro are you using? Zorin or Ubuntu?

---

### Post by Anigai on 2015-03-01
> **CantankRus said:**
> You can't change the view in the gtk-file-chooser.
One option is to bypass the gtk-file-chooser and use your file browser in thumbnail view 
to drag and drop your file into the web page upload dialog,
as you can with attachments in this forum.

Ok I'll be honest and say that I'm a bit confused now, I had thought it was called Nautilus?

> **vasa1 said:**
> So which distro are you using? Zorin or Ubuntu?

I was using Zorin up until yesterday when I thought switching to lubuntu would give me a different file browser with thumbnails but alas it did not although I am really liking lubuntu more at this stage than Zorin, it seems much more responsive.

---

### Post by CantankRus on 2015-03-01
> **Anigai said:**
> Ok I'll be honest and say that I'm a bit confused now, I had thought it was called Nautilus?



As I understand it the **gtk-file-chooser** window is independent of your default file browser which
in the Zorin distro is **nautilus** and in the Lubuntu distro is **Pcmanfm**.

---

### Post by Anigai on 2015-03-01
> **CantankRus said:**
> As I understand it the **gtk-file-chooser** window is independent of your default file browser which
in the Zorin distro is **nautilus** and in the Lubuntu distro is **Pcmanfm**.

Now that's interesting. I done a search for gtk-file-chooser and it looks like it's not easy to replace but a lot of technical information and terms I didn't understand have probably slewed my interpretation of it.

Is there a way I can:
(a) Replace gtk-file-chooser with an alternative which is similar to the Windows 7 version?
or
(b)Enable gtk-file-chooser to view different folders in different ways such as thumbnails for image/video folders and lists for all other folders?

At this stage I'm starting to think that the idea CantankRus had where I could use the standard file browser in a drag and drop thumbnail style might be the only way to go.

Thank you to everyone for putting up with this newbs silly questions.

---

### Post by Bill Tetzeli on 2015-03-01
I would suggest ditching vanilla Ubuntu and going with an Ubuntu spinoff such as Mint or Xubuntu for a whole host of reasons.  In this case, Mint comes with nemo as the default browser that has buttons at the top of each window that you can click to switch between icon view, detail view and compact view.  And in any other Ubuntu spinoff you can just type "sudo apt-get install nemo" in Terminal and you're all set.  Nemo also has built in, recursive search very similar to Windows 7 (except you can't search for text within a file).

---

### Post by Anigai on 2015-03-01
> **Bill Tetzeli said:**
> I would suggest ditching vanilla Ubuntu and going with an Ubuntu spinoff such as Mint or Xubuntu for a whole host of reasons.  In this case, Mint comes with nemo as the default browser that has buttons at the top of each window that you can click to switch between icon view, detail view and compact view.  And in any other Ubuntu spinoff you can just type "sudo apt-get install nemo" in Terminal and you're all set.  Nemo also has built in, recursive search very similar to Windows 7 (except you can't search for text within a file).

I used Linux Mint with the Cinnamon desktop for a few days and while I really liked it I found that it was somewhat slow on this old laptop I'm using it with so I had to let it go.
Xubuntu is what I have installed right now but it dual boots with Windows 7.

I can't let go of Windows 7 because this laptop can play 720p youtube videos and sometimes 1080p barely but for some reason no matter what distro I use(I've tried about 10 thus far) I can always only go as high as 480p with Linux and even that's unreliable and jumpy. I'm probably comiting blasphemy right now accessing the forum from Windows 7.

---

