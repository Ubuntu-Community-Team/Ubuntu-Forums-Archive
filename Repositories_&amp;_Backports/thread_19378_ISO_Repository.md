---
title: "ISO Repository?"
date: 2005-03-11
forum: Repositories &amp; Backports
---

### Post by telmo on 2005-03-11
I downloaded Hoary's Preview and i would like to upgrade my Warty. It so happens that my CD and DVD burner is not very healthy and i cannot record anything on it.

Can i add an ISO as an repository?

thx.

Oh yeah...by the way.... UBUNTU ROCKS!!!   :twisted:

---

### Post by Juergen on 2005-03-12
You can mount the iso via:
```
mount -o loop -t iso9660 <isofilename> <mountpoint>
```and then add a 'file:' entry to your sources.lst.

I'm not sure if the preview is prepared for this though, so after mounting the iso look for files like 'Packages.gz' on it...

---

### Post by daniels on 2005-03-12
If you can download stuff, just change your repositories from 'warty' to 'hoary' in Synaptic and do a Smart Upgrade.

---

### Post by telmo on 2005-03-14
Thank you! I would download it again, but it costs me! ;)

---

### Post by graabein on 2005-03-15
[QUOTE=daniels]If you can download stuff, just change your repositories from 'warty' to 'hoary' in Synaptic and do a Smart Upgrade.[/QUOTE]
I have no internet at home and I'm having problems with setting up Synaptic and apt-get with file:, where to put my debs and something or other with Packages.gz. 

Anyone know of a good manual/howto somewhere. I've tried the Debian HOWTO on [http://www.uk.debian.org/doc/manuals/apt-howto/apt-howto.en.txt](http://www.uk.debian.org/doc/manuals/apt-howto/apt-howto.en.txt) but it *doesn't do it for me*...

I want to copy main and restricted off of the install cd and have a dir to put debs I download at work... and I prefer to use Synaptic because of the GUI. I'm rather new to Linux...

---

### Post by graabein on 2005-03-16
I've successfully set up /etc/apt/sources.list and updated Packages.gz. Works like a charm. Now I'm in a rut with the package dependencies for gtkpod, Neverball and other apps...
```
The following packages have unmet dependencies:
  gtkpod: Depends: libatk1.0-0 (>= 1.9.0) but 1.8.0-1ubuntu2 is to be installed
          Depends: libglib2.0-0 (>= 2.6.0) but 2.4.7-0ubuntu2 is to be installed
          Depends: libgtk2.0-0 (>= 2.5.6) but 2.4.10-1ubuntu1 is to be installed
          Depends: libid3tag0 (>= 0.15.0b) but it is not installable
          Depends: libpango1.0-0 (>= 1.8.0) but 1.6.0b-0ubuntu1 is to be installed
```When I search the Warty repos I just got the old libatk version but Hoary had it. Can I just download the Hoary one and apt-get install it?

[http://higgs.djpig.de/cgi-ubuntu/search_packages.pl?keywords=libatk&searchon=names&subword=1&version=hoary&release=all](http://higgs.djpig.de/cgi-ubuntu/search_packages.pl?keywords=libatk&searchon=names&subword=1&version=hoary&release=all)
[http://higgs.djpig.de/ubuntu/www/hoary/libs/libatk1.0-0](http://higgs.djpig.de/ubuntu/www/hoary/libs/libatk1.0-0)

I reckon I must download every dependent package for each package. This is going to take a while.

Is there any way of getting a bundle of updated packages in a tar.gz somewhere?

---

### Post by Juergen on 2005-03-16
> When I search the Warty repos I just got the old libatk version but Hoary had it. Can I just download the Hoary one and apt-get install it?If you install gtkpod from Hoary, the packages it depends on also need to be from Hoary.
You can install packages with 'dpkg -i blah.deb'
But I wouldn't recommend such a warty/hoary mix.
> Is there any way of getting a bundle of updated packages in a tar.gz somewhere?Since you don't know in advance which packages are needed, you'd have to download the whole repository
I don't know if a single DVD is big enough to transfer this home...  :smile: 

I'm allowed to run Ubuntu in a Virtual PC at work.
I do my updates there and then take the package-cache home. This way I have no probs with dependencies.
Maybe you can set up something similar? How/where do you do your downloads?

---

### Post by graabein on 2005-03-16
[QUOTE=Juergen]I'm allowed to run Ubuntu in a Virtual PC at work.
I do my updates there and then take the package-cache home. This way I have no probs with dependencies.
Maybe you can set up something similar? How/where do you do your downloads?[/QUOTE]

That could work for me too. What software do you use? Microsoft Virtual PC, Server or WMWare? I have internet connection at work and download from there after hours... I have an external USB HD but I usually download debs and howtos to my laptop and bring that home.

Maybe I should download the Hoary ISO and just do an upgrade at home? What do you recommend?

---

