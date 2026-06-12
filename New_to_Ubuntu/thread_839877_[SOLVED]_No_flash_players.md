---
title: "[SOLVED] No flash players"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by taminrob on 2008-06-24
Just hoping that someone can help me get Adobe Flash installed properly.  

I know that there have been numerous postings and suggestions about this and I have tried all that I have come across with no success.

I installed Ubuntu 8.04 a few days ago and have really enjoyed it (almost a week without a system crash!!), but in browsing the web I discovered that I can't view videos on flash sites (YouTube/my local news site), not a big deal at first, but very frustrating now that I have been unable to resolve this.

To date I have tried: uninstalling/installing flashplugin-nonfree, uninstalling/installing flash player 9 .tar.gz, and even trying flash player 10 beta (Got that one to install, but still no video...could it have gone to the wrong place?).

Help!

I am not shy about using a terminal but admit that I don't really know what I am doing, I usually just copy and paste, so terminal commands would be very helpful in your replies.

---

### Post by Joeb454 on 2008-06-24
Did you follow the instructions from the Adobe website?

---

### Post by Methuselah on 2008-06-24
Did you try enabling the medibuntu repositories and installing it from there? (Search for flash in add/remove). 
I'm not sure what effect your previous attempts might have but it might still work.

The following commands should enable medibuntu.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

See medibuntu.org for more info.
It's a convenient way to get skype as well.

---

### Post by taminrob on 2008-06-24
Thanks Joe, yes I did follow the instructions from their site but recieved md5sum error durring the install process.

---

### Post by undertakingyou on 2008-06-24
I have always had an ok time with gnash.  Have you tried that? It is in the repos.

---

### Post by Methuselah on 2008-06-24
> **taminrob said:**
> Thanks Joe, yes I did follow the instructions from their site but recieved md5sum error durring the install process.

That seems to indicate some corruption of the downloaded files.

---

### Post by taminrob on 2008-06-24
> **Methuselah said:**
> Did you try enabling the medibuntu repositories and installing it from there? (Search for flash in add/remove). 
I'm not sure what effect your previous attempts might have but it might still work.

The following commands should enable medibuntu.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

See medibuntu.org for more info.
It's a convenient way to get skype as well.

Just attempted that and received this-

rob@robs-acer:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[sudo] password for rob: 
--20:14:32--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.

---

### Post by iaculallad on 2008-06-24
+1 to GNASH.

---

### Post by dominiquec on 2008-06-24
I prefer downloading the plugin from Adobe and installing it myself.  Tried the other repository options and found them not up to par.

Here are instructions for installing the plugin manually -> [http://ubuntuliving.blogspot.com/2007/02/installing-flash-for-mozilla.html](http://ubuntuliving.blogspot.com/2007/02/installing-flash-for-mozilla.html)

---

### Post by taminrob on 2008-06-24
Undertakingyou; I believe so, gnash was enabled in firefox plugins.

---

### Post by taminrob on 2008-06-24
> **Methuselah said:**
> That seems to indicate some corruption of the downloaded files.

It appears to be a common error code in this.  Many of the forums on this subject list it...I just don't seem to be able to get around it the way they suggest.

---

### Post by Methuselah on 2008-06-24
The flash available from medibuntu is the same as the one from adobe, just packaged for ubuntu. I'm not sure why you can't access medibuntu.org. I just tried and had no problem. I installed my flash and skype through medibuntu because I'm running 64 bit and it's configured to work even though skype/flash are 32 bit without me installing the needed dependencies manually.

---

### Post by iaculallad on 2008-06-24
> **taminrob said:**
> It appears to be a common error code in this.  Many of the forums on this subject list it...I just don't seem to be able to get around it the way they suggest.

You could try to fix that by:

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by taminrob on 2008-06-24
> **dominiquec said:**
> I prefer downloading the plugin from Adobe and installing it myself.  Tried the other repository options and found them not up to par.

Here are instructions for installing the plugin manually -> [http://ubuntuliving.blogspot.com/2007/02/installing-flash-for-mozilla.html](http://ubuntuliving.blogspot.com/2007/02/installing-flash-for-mozilla.html)

Installation seems to have worked...no errors...but when I tried to test view at YouTube all I see is a blank white square where the video is supposed to be.

---

### Post by Methuselah on 2008-06-24
> **taminrob said:**
> Installation seems to have worked...no errors...but when I tried to test view at YouTube all I see is a blank white square where the video is supposed to be.

I've seen that before.
I remember having to close firefox and/or logout/login.

---

### Post by taminrob on 2008-06-24
> **iaculallad said:**
> You could try to fix that by:

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get upgrade
```

Did that, and I was able to access medibuntu.org that time...but didn't fix...I closed firefox and Logout/Login to Ubuntu, still no luck when I tried to view a flash video.

---

### Post by chelovik on 2008-06-24
I installed Flash 9 about five minutes ago. I am on Ubuntu 7.(Gutsy) but this is a Firefox issue, not OS.

My steps were:
1. unload the AdobeFlash installer from their site (you probably have ... I found the "install_flash_player_9_linux.tar.gz" works, so get that version

2. extract this to a folder, say "Documents" ... if you aren't sure how to extract, simply open the downloaded file, and you will see an Extract button. Navigate to an appropriate directory and press Extract

3. Open a terminal, and "cd" to the folder ... in my case it was:
  cd /home/pe/Documents/install_flash_player_9_linux

4. Issue the following command:
./flashplayer-installer

5. You will now need to close any Firefox sessions you are using, and follow the instructions on the terminal ... ie, reply "y", "y", "y" ...

Done .... it worked first time for me.

Should you get a problem with the install, try:
sudo ./flashplayer-installer

This will bump your security to root, and run. Not the best command to run for every action, but in this case, Adobe software is trusted.
- cheers

---

### Post by taminrob on 2008-06-24
> **Methuselah said:**
> I've seen that before.
I remember having to close firefox and/or logout/login.

As per your suggestion, I just tried that again.  No go.


I hope some of you enjoy a good challenge!!

---

### Post by taminrob on 2008-06-24
chelovik;
  Following a previous posting suggestion (exactly the same as yours) the installation supposedly was successful, but I still have no video.  When trying to view a flash video all I get is a flicker and a blank white square where the video is supposed to be.

---

### Post by taminrob on 2008-06-24
So with the mention of corrupted files...would I be better off downloading a new Ubuntu 8.04 cd and reinstalling a fresh copy?  On my initial install I went ahead and let it particaian my drive, will a fresh install cause any problems other than having to set up my Ubuntu and Firefox preferences again?  Or is there a way to "repair" or restore Ubuntu?

---

### Post by Methuselah on 2008-06-24
Are you trying multiple flash videos?

---

### Post by taminrob on 2008-06-24
> **Methuselah said:**
> Are you trying multiple flash videos?

If I understand you correctly, yes I am.  I am just going to YouTube and clicking on a random video or two to test.  Always the same flicker and white square.

I also checked "about:plugins" on Firefox browser and it shows libflashplayer.so and libgnashplugin.so listed as enabled under separate shockwave flash plugins.   If that helps any.

---

### Post by taminrob on 2008-06-25
Problem solved!!!   found this post by "FEDZ"  while exploring more threads and it worked perfectly!  I think the what did it was deleting libflashplayer.so from ./home/mozilla/plugins/, that is the only difference in what I had tried before that didn't work.


 Re: can't watch youtube videos in FF3
Maybe consider Adobe FlashPlayer 10.

Goto: Places > Home > View > Show Hidden Files.

Find .mozilla > plugins and delete libflashplayer.so (if available).

Or uninstall from SPM.

1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
2. Save the .tar.gz file to your desktop and wait for the file to download completely.
3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

Hope this helps

---

### Post by Methuselah on 2008-06-25
Congrats. :D

---

