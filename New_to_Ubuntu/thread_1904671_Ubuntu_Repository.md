---
title: "Ubuntu Repository"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by nickelbox on 2012-01-05
Been looking at Ubuntu to install on a laptop but I can't seem to locate what apps are available in their repository. This is important as there are several programs I need to make sure they have before I make the switch.

Any help?

Thanks

---

### Post by Lars Noodén on 2012-01-05
If you have Ubuntu installed then you can browse via the Software Center or via Synaptic.  

If you do not yet have Ubuntu installed, then you can browse packages at the site below:

[http://packages.ubuntu.com/oneiric/](http://packages.ubuntu.com/oneiric/)

That will show you what is available.

What activities are you looking to do?

---

### Post by nickelbox on 2012-01-05
> **Lars Noodén said:**
> If you have Ubuntu installed then you can browse via the Software Center or via Synaptic.  

If you do not yet have Ubuntu installed, then you can browse packages at the site below:

[http://packages.ubuntu.com/oneiric/](http://packages.ubuntu.com/oneiric/)

That will show you what is available.

What activities are you looking to do?
Just want to make sure the programs I use in windows are available. For example I use teamviewer and skype

I've been looking around on your link and I can't seem to find either one although I would say the website isn't the most user friendly. Anyone else find these?

---

### Post by tomopotamus on 2012-01-05
> **nickelbox said:**
> Just want to make sure the programs I use in windows are available. For example I use teamviewer and skype
[Skype](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/) is available and so is [Teamviewer]("http://www.teamviewer.com/en/download").

Remember too though, that even if the exact Windows program isn't available for Ubuntu, there is often an alternative that is.  (For example, LibreOffice instead of Word.)

---

### Post by nickelbox on 2012-01-05
> **tomopotamus said:**
> [Skype]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/") is available and so is [Teamviewer]("http://www.teamviewer.com/en/download").

Remember too though, that even if the exact Windows program isn't available for Ubuntu, there is often an alternative that is.  (For example, LibreOffice instead of Word.)

I have been to both sites and see that they do have Linux versions but I am looking specifically for Ubuntu compatibility which is why I wanted to confirm they were in the repository.

Also Skype for Windows is on 5.7 beta whilst Linux is 2.2 Beta. Does anyone know the differences between the 2 versions?

---

### Post by mcduck on 2012-01-05
> **nickelbox said:**
> Been looking at Ubuntu to install on a laptop but I can't seem to locate what apps are available in their repository. This is important as there are several programs I need to make sure they have before I make the switch.

Any help?

Thanks

You can search for available packages at [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

...and keep in mind that there are many third-party repositories that provide you with stuff that isn't available in the official repositories, and with more up-to-date package versions. The PPA repositories would be a good place to start if you don't find what you are looking for from the official repositories.

---

### Post by Ms. Daisy on 2012-01-05
> **nickelbox said:**
>  I have been to both sites and see that they do have Linux versions but I am looking specifically for Ubuntu compatibility which is why I wanted to confirm they were in the repository.

Also Skype for Windows is on 5.7 beta whilst Linux is 2.2 Beta. Does anyone know the differences between the 2 versions? Regarding the first bit, the best way to really understand what's available and if you'll like it is to burn a live Ubuntu CD or flash drive.  You can run these on your computer without installing ubuntu and you'll be able to use it like it was installed (although it will run a bit slower than it would if it were actually installed).  

Regarding skype: I have it installed on my Ubuntu and use it successfully.  It is a "beta" version, but I personally have encountered no bugs. The biggest problem I've seen on these forums is getting the webcam & microphone to work (but that's like most everything else in Linux- there's almost always a workaround or fix, you just have to find it).  The version numbers are different because they are different platforms.  It's worth noting that Microsoft purchased skype last year, and Microsoft is not in the business of making free software.  So there's a Linux version right now but it's unlikely that it will remain compatible indefinitely.

---

### Post by nickelbox on 2012-01-05
> **Ms. Daisy said:**
> Regarding the first bit, the best way to really understand what's available and if you'll like it is to burn a live Ubuntu CD or flash drive.  You can run these on your computer without installing ubuntu and you'll be able to use it like it was installed (although it will run a bit slower than it would if it were actually installed).  

Regarding skype: I have it installed on my Ubuntu and use it successfully.  It is a "beta" version, but I personally have encountered no bugs. The biggest problem I've seen on these forums is getting the webcam & microphone to work (but that's like most everything else in Linux- there's almost always a workaround or fix, you just have to find it).  The version numbers are different because they are different platforms.  It's worth noting that Microsoft purchased skype last year, and Microsoft is not in the business of making free software.  So there's a Linux version right now but it's unlikely that it will remain compatible indefinitely.
Well, at this point I didn't want to have to go through the whole process of burning a live CD. I was hoping that someone here who is running ubuntu could look in their repository and confirm if teamviewer was there

---

### Post by Lars Noodén on 2012-01-05
> **nickelbox said:**
> Well, at this point I didn't want to have to go through the whole process of burning a live CD. I was hoping that someone here who is running ubuntu could look in their repository and confirm if teamviewer was there

That's what the link in post #2 above was for.  The short answer is that neither Skype nor Teamviewer are in the repository.  Teamviewer does have a **package** for Ubuntu on its download page.  That it is packaged is a very important distinction.  Skype also has a package for Ubuntu.  Skype is also available in the partner repositories: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

So the short answer is that you can get both for Ubuntu as packages and Skype, specifically, via a partner repository.

Looking further into the future, [Skype was bought by MS](http://www.bbc.co.uk/news/business-13343600) and there is no reason to expect that the Linux versions will be given much care or even stick around in the times to come.  There is a growing number of SIP-based alternatives that you can run along side Skype for the time being.

---

### Post by nickelbox on 2012-01-05
> **Lars Noodén said:**
> That's what the link in post #2 above was for.  The short answer is that neither Skype nor Teamviewer are in the repository.  Teamviewer does have a **package** for Ubuntu on its download page.  That it is packaged is a very important distinction.  Skype also has a package for Ubuntu.  Skype is also available in the partner repositories: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

So the short answer is that you can get both for Ubuntu as packages and Skype, specifically, via a partner repository.

Looking further into the future, [Skype was bought by MS]("http://www.bbc.co.uk/news/business-13343600") and there is no reason to expect that the Linux versions will be given much care or even stick around in the times to come.  There is a growing number of SIP-based alternatives that you can run along side Skype for the time being.
I did follow the link in post 2 but was unable to find either which brought on the subsequent posts.

I have a daughter who lives 6 hrs away that I webcam with through Skype. I need to be compatible with what she has in Windows because she won't be switching to Linux. When the time comes that Microsoft drops all Linux support, I will look into alternatives.

Thanks!

---

### Post by Lars Noodén on 2012-01-05
The SIP-based VoIP solutions are also available for older systems like Windows.  The open secret about them is that they all can talk to each other.  So your daughter could use Blink on Windows and still talk to you if you use Ekiga on Linux.  I still have a Skype account but only use it as a backup for when I can't get through via SIP (occasional firewall problems still).  That way I'm phasing it in gradually instead of waiting for the crisis.

---

### Post by waynefoutz on 2012-01-05
Skype works just fine with  every machine I've installed it on. The trick is getting a webcam that's compatible with the Linux kernel. As long as you have a common, name brand webcam, it should be fine. If you get an unknown brand out of the bargain bin, you might ave problems getting it to work with Linux.  I also use Teamviewer quite a bit, and I've never had a problem.

I've been using Skype for years, and since Microsoft has bought them, they've updated the Linux and Android versions more than once. I don't see them making it a Windows only application any time soon. It could happen, but so far all the evidence has pointed to the contrary.

---

### Post by oldos2er on 2012-01-05
There's a Skpye-equivalent program called Jitsi, available for both Linux and Windows (open source). I haven't tried it yet but it looks interesting. [http://jitsi.org/](http://jitsi.org/)

---

### Post by Lars Noodén on 2012-01-05
> **oldos2er said:**
> There's a Skpye-equivalent program called Jitsi, available for both Linux and Windows (open source). I haven't tried it yet but it looks interesting. [http://jitsi.org/](http://jitsi.org/)

<tangent>
The bug report requesting that Jitsi be packaged can be found here:

[https://bugs.launchpad.net/ubuntu/+bug/846532](https://bugs.launchpad.net/ubuntu/+bug/846532)

Other SIP clients include Blink, Ekiga, Linphone, Qutecom, and Twinkle.  They can all speak to each other regardless of which OS they are running on.  
</tangent>

---

