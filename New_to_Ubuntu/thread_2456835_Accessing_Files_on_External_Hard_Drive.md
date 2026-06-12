---
title: "Accessing Files on External Hard Drive"
date: 2021-01-20
forum: New to Ubuntu
---

### Post by fido1982 on 2021-01-20
Hello guys and girls.

After being very fed up with the performance of Windows 10 for a long while, I have made the jump today and switched over to Ubuntu.

Things seem promising so far. The programs that I have been struggling to use on Win 10 run much faster and smoother on Ubuntu.

One issue I have found though relates to my external hard drive. It is recognised and I can access all my files when I click on the specific icon for the drive yet I can't access the files when using other programs (for example the drive does not show when I trying to add a photo on Facebook while using the Brave browser).

Thank you in advance for any input.

---

### Post by howefield on 2021-01-20
Was your browser installed from a snap package ?

---

### Post by fido1982 on 2021-01-20
I downloaded Brave using the Ubuntu Software app.

---

### Post by howefield on 2021-01-20
> **fido1982 said:**
> I downloaded Brave using the Ubuntu Software app.

I think the the Ubuntu Software application contains only the snap version, so try opening up the Brave page in the Software app and look for a permissions button, click on it and there should be an option to allow access to removable media.

---

### Post by fido1982 on 2021-01-20
I am afraid after clicking on that specific permission plus a number of others that sounded like they may help, I still can't upload / access directly from the external hard drive.

---

### Post by howefield on 2021-01-20
> **fido1982 said:**
> I am afraid after clicking on that specific permission plus a number of others that sounded like they may help, I still can't upload / access directly from the external hard drive.

Perhaps you need a restart of the browser to pick up the new settings, if you haven't already tried that ?

---

### Post by fido1982 on 2021-01-20
I tried restarting the browser and restarting the computer completely too. Thanks for your input thus far.

---

### Post by CelticWarrior on 2021-01-20
Look for your external drive under /media.
I think that's the problem all along. Even without the permission for accessing mass storage devices these are shown but often not as a convenient shortcut in the left column like they appear in the file manager.

---

### Post by fido1982 on 2021-01-20
No media option unfortunately and I checked all available options before I wrote the original post. 

How frustrating!

---

### Post by CelticWarrior on 2021-01-20
Yes. it's frustrating because you don't understand. /media isn't an option, it's a folder under which all external media is typically mounted.

---

### Post by fido1982 on 2021-01-20
[IMG]https://imgur.com/a/J7Z5iNt[/IMG][https://imgur.com/a/J7Z5iNt](https://imgur.com/a/J7Z5iNt)

No option to open /media folder.[IMG]https://imgur.com/a/J7Z5iNt[/IMG]

---

### Post by CelticWarrior on 2021-01-20
> **fido1982 said:**
> [IMG]https://imgur.com/a/J7Z5iNt[/IMG][https://imgur.com/a/J7Z5iNt](https://imgur.com/a/J7Z5iNt)

No option to open /media folder.[IMG]https://imgur.com/a/J7Z5iNt[/IMG]

That's doesn't look like the "open file" dialog. That's looks like the file manager file manager ("Files", formerly known as "Nautilus") and the drive is either in "Other..." or it isn't properly recognized. Or you need to - as I told you before - start at Other... > Computer and drill down to find /media and inside it a folder with your username and inside that the automatically mounted external medias.

---

### Post by #&amp;thj^% on 2021-01-20
many unpredictable bug's show up with people installing brave using snap, from the ubuntu software application.
Remove the snap if you want a better usage experience.
```
sudo snap remove brave
```
Re-install with Apt:
```
sudo apt install brave
```
If your concerned about sandboxing, install firejail:
```
sudo apt install firejail firetools
```

and to run it simply run:
```
firejail brave
```
You should now have access to external drive/s.

---

### Post by howefield on 2021-01-20
> **1fallen said:**
> Re-install with Apt:
```
sudo apt install brave
```

Doubt you'll can do it as simply as that, the deb package is not in the default repositories. Only the snap package. One would need to get the .deb package from somewhere first ;)

---

### Post by CelticWarrior on 2021-01-20
Indeed, from their website only.

And, again, NOT the problem here ;)

---

### Post by #&amp;thj^% on 2021-01-20
> **CelticWarrior said:**
> 
And, again, NOT the problem here ;)

Can you help me test that theory?
Even the Brave developer's hate it when they learn it was installed via Snap.

---

### Post by #&amp;thj^% on 2021-01-20
> **howefield said:**
> Doubt you'll can do it as simply as that, the deb package is not in the default repositories. Only the snap package. One would need to get the .deb package from somewhere first ;)

Thanks for that, I'm not on Ubuntu today.
Install from direct:
```
sudo apt install apt-transport-https curl gnupg

```
```
curl -s https://brave-browser-apt-release.s3.brave.com/brave-core.asc | sudo apt-key --keyring /etc/apt/trusted.gpg.d/brave-browser-release.gpg add -

```
```
echo "deb [arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main" | sudo tee /etc/apt/sources.list.d/brave-browser-release.list
```
```

sudo apt update
```
install:
```
sudo apt install brave-browser
```

---

### Post by CelticWarrior on 2021-01-20
> **1fallen said:**
> Can you help me test that theory?
Sorry, I don't have Brave installed in this computer and I don't intend to.
But clearly this has nothing to do with snap limitations. Again, even without the specific permission to access mass storage devices all appear in the dialog.
The issue here is the OP still don't understand that they need to go to /media to find it... That's all.

---

### Post by CelticWarrior on 2021-01-20
> [COLOR=#000000]Install from direct:[/COLOR]

Nice instructions but that will only result in more frustration as it changes nothing about the open file dialog, as explained before, twice!

---

### Post by #&amp;thj^% on 2021-01-20
> **CelticWarrior said:**
> changes nothing about the open file dialog, as explained before, twice!

I see his open file dialog>>>>See Screenshot.
OP's only option will be the "Download" Folder period. (That's the way it works with a sand box)
I'm really not trying to be augmentative, just accurate.

---

### Post by CelticWarrior on 2021-01-20
> [COLOR=#000000]OP's only option will be the "Download" Folder period. (That's the way it works with a sand box)[/COLOR]
[COLOR=#000000]I'm really not trying to be augmentative, just accurate.[/COLOR]
Err.. No.
For accuracy here's the workflow: Other... > "Computer" (which is /) > scroll down until and clcik on "media" > click on username > the folder for the external drive will be there, **be it the regular deb installed Brave or the snap Brave**. The difference is if using snap Brave without permissions it won't let you open any file from there or not even see the drive's contents, but up to that point the file tree is exactly the same and it can't be any other way.

The problem here is a newbie, not the software. It's like if, in Windows, we say "it's in the D drive" and the OP retorts with "what's the D drive?". You and I know lots of things "by heart", the OP, quite understandably, don't.

---

### Post by fido1982 on 2021-01-20
I have just downloaded Firefox and when using this browser I am offered the option to upload directly from my external hard drive.

It seems it's an issue with my version of Brave or Brave in general.

[https://imgur.com/a/PtNZPxy](https://imgur.com/a/PtNZPxy)

---

### Post by CelticWarrior on 2021-01-20
> **fido1982 said:**
> It seems it's an issue with my version of Brave or Brave in general.

[https://imgur.com/a/PtNZPxy](https://imgur.com/a/PtNZPxy)

If you call this an issue, OK... Except it ISN'T.
One software (Firefox) presents the external drives (or additional partitions) conveniently as a shortcut in the left column. The other (Brave) like many hundreds more, DON'T. For those you have to find it as /media/your_username/external_drive's_name. Please tell us which part you don't understand...

---

### Post by fido1982 on 2021-01-20
Success!!

[https://imgur.com/a/W2vwn9K](https://imgur.com/a/W2vwn9K) 

I deleted the Software App version of Brave and downloaded it again by using code in Terminal. 

Brave now offers direct uploads from my external hardrive on the Facebook (plus other sites).

Thank you 1Fallen.

---

### Post by #&amp;thj^% on 2021-01-20
Thank You for the confirmation, adds clarity. Cheers!

@ fido1982 [S]**If** you want to test and learn, give this a try, we will remove the sandboxing f_or this test run only_.
```
brave --no-sandbox
```
Now you will get a warning about the "--no-sandbox" but we are just seeing if this helps you see your desired device, drive, usb.
And still follow the suggestions with choosing the "Other" "Media"locations.
Did this help?[/S]

---

### Post by fido1982 on 2021-01-20
@1Fallen 

No need to dig any deeper as the functionality is exactly what I need it to be.

Thanks again for your insight.

---

### Post by #&amp;thj^% on 2021-01-20
That's why it was struck-through. You replied before i had seen your changes.
Best Regards

---

### Post by ajgreeny on 2021-01-20
I have not used brave so am not sure if it is really worth it or not, particularly as it is most easily installed as a snap, which I personally try to avoid, I have even uninstalled snapd, so without adding that again I can not install any snaps.

What are the advantages of brave over chromium, which I use from one of the two PPAs from [COLOR="#FF0000"]deb [http://ppa.launchpad.net/saiarcot895/chromium-dev/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-dev/ubuntu) focal main[/COLOR], again to avoid the snap.

See the thread at [https://ubuntuforums.org/showthread.php?t=2456615&amp;goto=newpost](https://ubuntuforums.org/showthread.php?t=2456615&amp;goto=newpost) about brave which may be some help to you, along with the download and installation instructions at [https://brave.com/linux/](https://brave.com/linux/)

---

