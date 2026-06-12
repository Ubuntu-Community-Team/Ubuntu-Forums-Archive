---
title: "What is up with software center"
date: 2019-08-30
forum: New to Ubuntu
---

### Post by hvaria2 on 2019-08-30
I am unable to install firefox from software center. Please see my screenshot. Keeps on asking me to login to Snap store but there is no way to create that account. I am at a total loss.

[IMG]https://drive.google.com/open?id=16I401gjXtZuwguHMmc3K44NWKaQEYBcZ[/IMG]https://drive.google.com/open?id=16I401gjXtZuwguHMmc3K44NWKaQEYBcZ

---

### Post by coffeecat on 2019-08-30
Firefox comes pre-installed with Ubuntu. Why are you trying to install the snap version?

Please state which release of Ubuntu you are using (16.04, 18.04 or 19.08) and which flavour (Ubuntu, Xubuntu, Lubuntu, etc).

---

### Post by TheFu on 2019-08-30
Try
```
sudo apt install firefox
```

---

### Post by hvaria2 on 2019-08-30
My apologies should have clarified. I installed Ubuntu 19.04 build in LXD containers available to chrome OS. I know how to manually install a ton of software on Debian but decided to go with Ubuntu because of the software center and it's ease of use. I tried installing the center on my Debian container and it kept crashing. On Ubuntu everything works except for I keep getting the message to sign in to snap store account. When I go to snap store online it keeps on asking me to create an Ubuntu one account. I am trying to get out of this loop so I can fully use the software center. I already have an Ubuntu one account but that does not seem to be enough. Please let me know if anyone can help otherwise I'll ditch the software center and move back to Debian but I'd rather not.

---

### Post by crip720 on 2019-08-30
What happens if you just ignore the notice?  Don't use software centre much myself, but just checked it and had to click on the little menu box to find the notice.  First time I have seen it.  The few snaps that I have installed, I found they usually had some limitations compared to the non-snap versions, usually ended up replacing the snaps.

---

### Post by TheFu on 2019-08-30
I have never used software center. Not once.  I don't run non-LTS releases.

I've read that Ubuntu expects more and more software to be shipped using snaps. If that becomes mandatory, many people will be switching, especially people with lower-end systems or running VMs/Containers already.

Hopefully, Canonical will provide a complete backout plan should snaps fail similar to the way that Wayland failed in 17.10.

---

### Post by cruzer001 on 2019-08-30
> I'll ditch the software center and move back to Debian
Just install Synaptic package manager.
```
sudo apt install synaptic
```

---

### Post by hvaria2 on 2019-08-30
Thanks for the replies everyone... @cruzer001 I will try synaptic... I really liked the software center overall but a bummer that it does not work... 
@crip720 it's no so much a warning as a requirement for me to install any snaps using the software center. New to linux and I am trying a lot of things and a GUI just made things super easy.
@TheFu see that is why I was hoping this would work... but oh well.

---

### Post by crip720 on 2019-08-30
Just went to install firefox snap from software store and it only asked for my regular password, same as when I make any change to OS.  No sign in to anything required or asked for.

---

### Post by TheFu on 2019-08-30
Software Center hides many packages from end-users AND mixes 25 yr old APT technology with 2 yr old snap technology.  

Synaptic shows all the APT packages in the configured repos and PPAs.

apt, apt-get, aptitude are all CLI interfaces into the APT sub-system. At some point, 'apt' (the command) might become like Software Center, but hopefully not.

Unfortunately, we see all sorts of issues with snap-packaged programs still.  Mainly it breaks workflows between programs or external addons.  Few of us have figured out how to troubleshoot snap issues, so the easy answer has been to uninstall the snap version of the package and reinstall the APT version.  Snaps and flatpaks are a good idea with good goals, but they aren't the total replacement for APT that is being pushed.  Until installing helpers and addons which might work with another installed program recognizes every possible workflow option and asked for user confirmation that those tools work together, so interactions need to be allowed, snaps will be broken.  Actually, I don't see how this can be accomplished without a snap-interface DB and application to maintain all those permissions between different programs.
For example, do you want your email program, thunderbird, to be able to directly open a PDF file and launch evince?  What if the PDF helper is atril instead?  What if both of those are also in snap packages and locked down?
Snaps are bad enough in that they won't open USB storage files or files in /tmp/ by default already.  My workflow for downloading PDF files puts them in /tmp/ by default, since I don't usually keep a copy.  /tmp/ is for temporary files and gets cleaned up at reboot.  Every Unix person does this. It is how we work.  Disallowing snap packaged programs to access /tmp/ if a complete 100% failure.

There are many subtle snap package issues that aren't nearly so clear.

---

### Post by hvaria2 on 2019-08-30
I think I finally found the reason why this is happening.

[https://www.phoronix.com/scan.php?page=news_item&px=GNOME-Software-Dropping-Snap](https://www.phoronix.com/scan.php?page=news_item&px=GNOME-Software-Dropping-Snap)

Looks like GNOME is dropping snap

---

### Post by CatKiller on 2019-08-30
> **TheFu said:**
> Software Center hides many packages from end-users AND mixes 25 yr old APT technology with 2 yr old snap technology.  

I don't personally like snaps, and I don't use them myself, but I talk to new Ubuntu users elsewhere.

For those new users that are used to installing stuff in Windows, they just want random applications that are *never* going to be in the repositories - because they're niche, or proprietary, or not primarily developed for Linux. Having proper packages and all the snaps from Snapcraft all available and updateable in the same place is a massive boon. They just aren't interested in the libraries and command line programs that don't show up.

I do wish Synaptic was still installed by default, too, though. There's nothing like seeing the packages and their dependencies all get installed together to really make the process click.

---

### Post by TheFu on 2019-08-30
> **CatKiller said:**
> I don't personally like snaps, and I don't use them myself, but I talk to new Ubuntu users elsewhere.

For those new users that are used to installing stuff in Windows, they just want random applications that are *never* going to be in the repositories - because they're niche, or proprietary, or not primarily developed for Linux. Having proper packages and all the snaps from Snapcraft all available and updateable in the same place is a massive boon. They just aren't interested in the libraries and command line programs that don't show up.

I tried a flatpak for a video editing program. No snap was available and the developer stopped producing .deb packages or having a PPA.
The program was 32.7 MB in size.  The flatpak was **over 900 MB in size** because it included dependencies.  Almost 1GB for a 33 MB program?  Bloated.  But for 1 specialized program, fine.  When I have 50 of those on my system, that's 50 GB with mostly wasted storage.  Ok ... so more storage - fine.

Those dependencies will be loaded into RAM at runtime.  The CS should be 33 MB, but now it will be 900 MB.  That's almost half the RAM on a 2GB low-end laptop.  It's 1/4 of the RAM on a reasonable 4GB laptop. So, with 10 similar snaps loaded, I'll need 10G of RAM?  Only 1 of my systems has more than 8 GB of RAM, most have less than 4 GB.  That doesn't include the DS, just the code segments. The DS shouldn't be any different between native packages or snaps.

Then I tried to actually run the program and got an error at startup.  So much for "just download and run."

Hopefully, when I need a snap package, it will exist and work.

---

### Post by walts48 on 2019-08-31
> **hvaria2 said:**
> I am unable to install firefox from software center. Please see my screenshot. Keeps on asking me to login to Snap store but there is no way to create that account. I am at a total loss.

[IMG]https://drive.google.com/open?id=16I401gjXtZuwguHMmc3K44NWKaQEYBcZ[/IMG]https://drive.google.com/open?id=16I401gjXtZuwguHMmc3K44NWKaQEYBcZ

As was previously stated Firefox comes preinstalled with Ubuntu.

I prefer installing it directly from Mozilla so I get the updates without waiting for them to be available from Ubuntu.

[https://www.mozilla.org/en-US/firefox/all/#product-desktop-release](https://www.mozilla.org/en-US/firefox/all/#product-desktop-release)

---

### Post by uRock on 2019-08-31
+1 for Synaptic Package Manager. I've not used snaps, either. If I don't know the package name for something I want to install, then I go to Synaptic. I only use Ubuntu in VM for a certain app that doesn't work in Debian. The few things I do need to install in it usually get installed via CLI.

---

### Post by deadflowr on 2019-08-31
> **hvaria2 said:**
> I am unable to install firefox from software center. Please see my screenshot. Keeps on asking me to login to Snap store but there is no way to create that account. I am at a total loss.

[IMG]https://drive.google.com/open?id=16I401gjXtZuwguHMmc3K44NWKaQEYBcZ[/IMG]https://drive.google.com/open?id=16I401gjXtZuwguHMmc3K44NWKaQEYBcZ

What desktop is that?
Differing desktops have various affects on what happens.
The default on Ubuntu is that when clicking on any of the sign-in options a popup window will appear,
giving you options to login or create new accounts.

If you're clicking and no popup window shows something's wrong with the desktop setup.

---

