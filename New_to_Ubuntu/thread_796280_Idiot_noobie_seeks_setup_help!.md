---
title: "Idiot noobie seeks setup help!"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by johnwillyums on 2008-05-16
Hi All.

About 6 months ago I got a new PC running Windows Vista 64 bit. Soon after that I installed Gutsy Gibbon on a small partition and ran a dual boot system.

This might have been a bit ambitious and I don't think I really got to grips with Ubuntu as I was busy wrestling with problems in Vista.
Quite recently a catastrophic failure with Vista SP1 caused me to have to do a complete Vista reinstall. This wiped my Ubuntu install as well.

However, as I say I don't really think I did very well with Ubuntu last time. I had software on that I didn't understand what it was for etc. 
So a clean install yesterday from the Shipit CD that dropped through my door in the morning has been completed.
I now have Hardy Heron 64x installed on a partition on a second 500gb drive with Vista on the other drive. So I get a choice of OSs at boot.

So far so good and it looks lovely, I've even managed a driver for my GPU but in other areas I'm not doing as well as last time.
I can't seem to enable compiz-fusion and the cube thingy.

I looked in synaptic and enabled everything to do with compiz. There are several compiz files installed- compiz, compiz-core, compiz-fusion-plugins-extra and more. So that seems to be alright.
However I can't seem to figure out how to get more than two desktops. I can switch between these by clicking on them but don't know how to get two more or enable the cube.  

Another issue is software repositories. I seem to remember medibuntu being useful last time (can't remember why though) so I tried to put it in software sources.

I went to the medibuntu site and found the hardy heron version. I then opened system-administration-software sources-third party software.
The instructions seem to be to copy and paste this:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

into the box saying "Enter the complete APT line of the repository you wish to add as source" so I did. Copied the whole line and pasted in but it won't. The "+ Add Source" box is greyed out and the "+ Add" in the main box does nothing.

I'm struggling here. Not even sure why I need medibuntu. Got wobbly windows though so somethings happening on the graphics front.

I must be missing something with both of the above issues. I'm not sure I have the knowledge base to do this and everywhere I look people are posting things I don't understand assuming a level of knowledge I don't have.

Any ideas on the above?, John

specs: Asus P5N-E SLI, Q6600 CPU, BFG 8800GTS OC 512 MB GPU, 4GB RAM, 2x500GB Samsung HDDs, Thermaltake 650 watt PSU, Thermaltake Golden Orb Cooler, Thermaltake Tsunami case, Vista HP 64 bit with SP1+ Hardy Heron 64 bit

---

### Post by dca on 2008-05-16
This is how I add the medibuntu, click on link:
 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
 
...scroll down to 'Adding the Repositories' section and find your vers then copy/paste into CLI.

Don't forget after copy/paste initial repo, to go to bottom and copy/paste the GPG key command...

---

### Post by phr0ze on 2008-05-16
This is a line you would type into a command line. Have you tried it there?

---

### Post by forestpixie on 2008-05-16
First - compiz install the settings manager, which we'll do in a minute. When it's installed - open it from admin>pref menu - go to general options, desktop size tab - horizontal virtula size should be 4.

Medibuntu - easiest way is to install from the terminal

Commands to do both are, do them seperately

```
sudo apt-get install compizconfig-settings-manager
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Some useful compiz info to start with

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by vjkeito on 2008-05-16
##compiz

right to configure compiz you want to install ccsm by doing the following

sudo apt-get install compizconfig-settings-manager

then after it is installed run it by typing ALT+F2 then in the dialog box type ccsm then hit enter.

all setting for your system compiz-wise can be set here

---

### Post by vjkeito on 2008-05-16
it would appear forestpixie has beaten me to it ;0)

medibuntu is for adding packages that aren't always available in default canonical repos.

though most of the stuff it used to be useful for are now available by running

sudo apt-get install ubuntu-restricted-extras

that will install msttfcorefonts (fonts) and most of the codecs you'll need.  it'll install libdvdread too though that is for playback only. if you want to rip a dvd (another reason most would enable the medibuntu repo to get libdvdcss2) then once the ubuntu restrcted extras is installed run

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

hope that make sense
peace
k3ito

---

### Post by johnwillyums on 2008-05-16
Hello and many thanks to you all.

Your instructions re compiz were great and I now have the spinning cube. Also thanks to forestpixie for the link to forlong's blog. I haven't studied it yet but it seems really useful.

I followed vjkeito's advice and input:

sudo apt-get install ubuntu-restricted-extras

This got loads of action and took a little while. I then input:

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

and that seems to have succeeded as well.
I don't really know what I've just done but no doubt it will become clear (or not) as time goes by.

However, I did not have any luck with medibuntu. I tried copying and pasting the sudo-get command from forestpixie's reply into a terminal but got: resolving [www.medibuntu.org](www.medibuntu.org) failed:name or service not known.

Might this be because I've already input the restricted extras command?
Does it matter?

I have another issue whilst I've got your attention (there will no doubt be more as I go along) regarding gmail.
When I first installed yesterday I began setting up Firefox as I like it, I'm also using 3.05 in Vista. I added speed dial and began to populate the windows with my regularly visited sites including my gmail inbox.
I found gmail.com through google put in my username and password and got to my inbox that way.
However it looks nothing like it does in Vista. It's very poorly rendered and consists of just a list of emails stretching across the page. There are no headers or contacts sidebar nor any command buttons. If I open an email it appears as a badly typed thing and once again no buttons to return to inbox, delete etc. All these commands/buttons appear at the end of the text.
It's usable but ugly. Have I done something wrong or is this just the way it is in Ubuntu?

Once again thank you so much for your help. This sort of support is what I remember from my last attempt with Ubuntu and it's just fantastic and encouraging.

Cheers, John

---

### Post by Golem XIV on 2008-05-16
> **johnwillyums said:**
> 
I have another issue whilst I've got your attention (there will no doubt be more as I go along) regarding gmail.
When I first installed yesterday I began setting up Firefox as I like it, I'm also using 3.05 in Vista. I added speed dial and began to populate the windows with my regularly visited sites including my gmail inbox.
I found gmail.com through google put in my username and password and got to my inbox that way.
However it looks nothing like it does in Vista. It's very poorly rendered and consists of just a list of emails stretching across the page. There are no headers or contacts sidebar nor any command buttons. If I open an email it appears as a badly typed thing and once again no buttons to return to inbox, delete etc. All these commands/buttons appear at the end of the text.
It's usable but ugly. Have I done something wrong or is this just the way it is in Ubuntu?

Once again thank you so much for your help. This sort of support is what I remember from my last attempt with Ubuntu and it's just fantastic and encouraging.

Cheers, John

Beauty is in the eye of the beholder, as they say, and while I certainly won't call Gmail's interface "beautiful" it's a lot better than what you describe.  Make sure you're at [http://mail.google.com/mail/#inbox](http://mail.google.com/mail/#inbox)

It could be an error in the script that Gmail uses to render the page.  try emptying your cache, closing and re-launching Firefox and opening the Gmail page again.

To clear the cache, go to Firefox's Edit menu, choose Preferences and then click on the Advanced icon.  The button to clear the cache will be there (Clear Now).

---

### Post by johnwillyums on 2008-05-16
Thanks Golem. You were right I was at the wrong address. Have now changed it on my speed dial so no need to empty cache.
Thanks for your help, John Williams

---

### Post by vjkeito on 2008-05-21
> **johnwillyums said:**
> 
I followed vjkeito's advice and input:

sudo apt-get install ubuntu-restricted-extras

This got loads of action and took a little while. I then input:

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

and that seems to have succeeded as well.
I don't really know what I've just done but no doubt it will become clear (or not) as time goes by.


here is some information on exactly what the package ubuntu-restricted-extras is and why it is not installed on a default ubuntu system.

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

here is some information on what exactly got installed with ubuntu-restricted-extras

Adobe Flash - non free plugin (as opposed to swfdec or gnash)
unrar - allows rar files to be decompressed
codecs to allow the playback of mp3 aac etc etc
java
[COLOR="Red"]dvd playback - not copy-protected playback*[/COLOR]
m$fonts

[http://packages.ubuntu.com/hardy/ubuntu-restricted-extras]("http://packages.ubuntu.com/hardy/ubuntu-restricted-extras")

[COLOR="Red"]* the script you run afterwards[/COLOR]...

*sudo /usr/share/doc/libdvdread3/examples/install-css.sh*

... then allows you to copy dvd's with copy-protection.  afterwards your system can decrypt CSS (content scramble system) [http://en.wikipedia.org/wiki/Content_Scramble_System]("http://en.wikipedia.org/wiki/Content_Scramble_System") thanks to this [http://en.wikipedia.org/wiki/DeCSS]("http://en.wikipedia.org/wiki/DeCSS")

---

### Post by darknight2183 on 2008-05-21
Something else to remember when it comes to compiz.  In order to use the compiz cube, you need to make sure that you have both the nvidia-glx-new drivers installed (for you BFG 8800) and you you've enabled desktop affects by going to System->Preferences->Appearences

I'm betting that compiz isn't working b/c you X isn't configured properly. To reconfigure, follow these steps below

Remember the command line is your friend. Start by pressing Ctrl + Alt + F1, that will bring you to tty1 and a command line log on prompt.  Log in and then stop gnome by typing "sudo /etc/init.d/gdm stop"

Once gnome is stopped, look at your X folder by typing "ls /etc/X11"  You should see several files, one being xorg.conf, which is your current X configuration. You now have 2 choices, manually edit the xorg.conf file or run the following command "sudo dpkg-reconfigure xserver-xorg" For you, I would suggest running the command rather than manually editing. Just remember to select nvidia instead of nv for the driver source.  Once done, start gnome again by typing "sudo /etc/init.d/gdm start"

If you receive a message on you monitor that it is out of sync or range, it means the resolution is set to high.  Don't panic, just go back to tty1 and run "sudo dpkg-reconfigure xserver-xorg" and when you get to the resolution prompt remove what ever the highest resolution is, I find that unless you have hawk eyes or need a tremendous amount of desktop space 1280x1024 is a good res.  Hope this helped.

---

