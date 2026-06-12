---
title: "What's the easiest way to d/l  &amp; open files on Ubuntu/i386?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by NewsAndHistory on 2008-09-29
I'm using Ubuntu 8.04 on a Dell Laptop (i386) What's the easiest way to download and open a file on Ubuntu? If the easiest way is by using the terminal, please tell me how to "unpackage a file"?

When I was using a non-intel processor, I always had to use the terminal to download files.

1 more question: May .rpm files be downloaded on Ubuntu?

I got instructions from [Adobe Flash Instructions page]("http://www.adobe.com/products/flashplayer/productinfo/instructions") -but those instructions don't explain how to "unpackage a file".

                                  > Click the "Download .tar.gz"     link. A dialog box will appear asking you where to save the file.      
     Save the .tar.gz file to your     desktop and wait for the file to download completely.      
     Unpackage the file. A directory     called install_flash_player_9_linux will be created.      
     In terminal, navigate to this     directory and type ./flashplayer-installer to run the installer.     Click Enter. The installer will instruct you to shut down your     browser(s).      
     Once the installation is complete, the plug-in will be     installed in your Mozilla browser. To verify, launch Mozilla and     choose Help > About Plug-ins from the browser menu.      


---

### Post by JoshuaRL on 2008-09-29
So before we go into techincal things, what are you trying to accomplish here?  We might be able to find a better or easier way to do it.

---

### Post by davec64 on 2008-09-29
First off have you added Medibuntu to your repositories?

If not read the Repository Howto here:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Then using Synaptic you'll be able to add codecs for MP3's & Video's etc.

Secondly as you're trying to install Flash, have you tried directly installing the Plugin through Firefox?

Lastly to uncompress a file, In a terminal:

```
tar xvf filename.tar.gz
```

 (I think thta's right if memory serves me right!)

---

### Post by James Little on 2008-09-29
Most packages in the Linux world are distributed as a tarball - a file or files/directories archived as a tar and then compressed with Gzip, i.e. filename.tar.gz. You can unpack them at the command-line with:

tar -xvzf <filename>

---

### Post by jerome1232 on 2008-09-29
> **NewsAndHistory said:**
> I'm using Ubuntu 8.04 on a Dell Laptop (i386) What's the easiest way to download and open a file on Ubuntu? If the easiest way is by using the terminal, please tell me how to "unpackage a file"?

When I was using a non-intel processor, I always had to use the terminal to download files.

1 more question: May .rpm files be downloaded on Ubuntu?

I got instructions from [Adobe Flash Instructions page]("http://www.adobe.com/products/flashplayer/productinfo/instructions") -but those instructions don't explain how to "unpackage a file".

If you are just trying to install flash it's available in the repos.
```
sudo apt-get install flashplugin-nonfree
```
to get support for mp3's and such you could install this meta package (will install flash and java plugins too)
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by kansasnoob on 2008-09-29
Here's a .deb for Flash 10 RC:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

NOTE: That will only work with 8.04 / Hardy! It'll mess with the repos in earlier versions! (And it's not necessary in Intrepid)

Look at post #7 here:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)

---

### Post by kansasnoob on 2008-09-29
Oh and you asked: 

> May .rpm files be downloaded on Ubuntu?

Yes. You must first install alien from the repos:

```
sudo apt-get install alien
```

Then use this guide:

[http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html](http://www.ubuntugeek.com/install-rpm-files-in-ubuntu.html)

But IMO you're better off using tar.gz:

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by oldsoundguy on 2008-09-29
> **kansasnoob said:**
> Here's a .deb for Flash 10 RC:

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

NOTE: That will only work with 8.04 / Hardy! It'll mess with the repos in earlier versions! (And it's not necessary in Intrepid)

Look at post #7 here:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)
  
Beg to differ.  I have it running on 3 Gutsy machines.  I also have FF 3.03 on those machines (installed by going to the Ubuntuzilla site at Source Forge since that version or better will never be put in the Gutsy repositories.)
Hardy will not work on one of those machines AT ALL as it is an old Via chipset and Hardy tries to see the drive as a SATA drive!

---

### Post by NewsAndHistory on 2008-09-30
Thanks for helping me & others, OldSoundGuy. I appreciate your time & help.

> **JoshuaRL said:**
> So before we go into techincal things, what are you trying to accomplish here? We might be able to find a better or easier way to do it.
    I want to install Flash.
   
   > **davec64 said:**
> First off have you added Medibuntu to your repositories?
   
   [...]
   
   Secondly as you're trying to install Flash, have you tried directly installing the Plugin through Firefox?
   I didn't download either of those things, yet. I appreciate your help. I will download them, now. 
  
  > **James Little said:**
> Most packages in the Linux world are distributed as a tarball - a file or files/directories archived as a tar and then compressed with Gzip, i.e. filename.tar.gz. You can unpack them at the command-line with:
  
  tar -xvzf <filename>
  Thanks for helping me & others.
  
 > **jerome1232 said:**
> If you are just trying to install flash it's available in the repos.
[...] to get support for mp3's and such you could install this meta package (will install flash and java plugins too) [...]
 Thanks for telling me all of that. I appreciate your help.

> **kansasnoob said:**
> Here's a .deb for Flash 10 RC:
[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)
NOTE: That will only work with 8.04 / Hardy! It'll mess with the repos in earlier versions! (And it's not necessary in Intrepid) Look at post #7 here:
[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)
Thanks for your kindness & help.

---

### Post by JoshuaRL on 2008-09-30
> **NewsAndHistory said:**
> Thanks for helping me & others, OldSoundGuy. I appreciate your time & help.


    I want to install Flash.
   
   
   I didn't download either of those things, yet. I appreciate your help. I will download them, now. 
  
  
  Thanks for helping me & others.
  
 
 Thanks for telling me all of that. I appreciate your help.


Thanks for your kindness & help.

You seem to be a thankful kind of guy.  Thats nice to come across.

So like has been said, put this into the terminal to have Flash:
```

sudo apt-get install flashplugin-nonfree

```
Then make sure you restart your browser, and go to a Flash site to see if it is installed correctly.

Let us know how that worked.

---

