---
title: "[Tutorial]install gimp 2.6 on ubuntu 8.04 (Hardy Heron)"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-19
[I]Note: Gimp 2.6 is not officially supported by Ubuntu 8.04 Hardy.
However I find that the version provided is useless in comparison. 
Furthermore I see no reason that you should only be able to get *Gimp 2.6* if you use Intrepid. 
I use gimp a lot and have yet to have any issues with this install[/I]

First you will need to add the _getdeb_ source to your source list.

You can do this by opening terminal and entering the following code
```
gksudo gedit /etc/apt/sources.list
```
In the page that opens add this line to the end.
```
deb http://ubuntu.org.ua/ getdeb/
```

Click on save then close the window

Now we need to update our sources.

In terminal enter the following command
```
sudo apt-get update
```

After the update finishes (this should not take long at all)
Now we can Install *Gimp 2.6*

Enter the following command in terminal
```
sudo apt-get install gimp
```

**Congrats. You now have _Gimp 2.6_**

_*Note: This tutorial is almost a direct copy from the tutorial at ubuntugeek.com that can be found*_ [**HERE**]("http://www.ubuntugeek.com/how-to-install-gimp-261-on-ubuntu-804-hardy-heron.html"). 
*_However I believe in unity and I believe that you should not have to go any further than **Ubuntuforums** to find what you are looking for._*

_Also (this may just be me but) I like to go back into my sources.list and remove what I added after installing my desired software. Just because I am paranoid!!_

---

### Post by talsemgeest on 2008-11-19
Just a little suggestion, I think it is a bad idea to remove it from your sources.list, since if any updates become available, they will not be installed automatically.

---

### Post by nakama85 on 2008-11-19
> **talsemgeest said:**
> Just a little suggestion, I think it is a bad idea to remove it from your sources.list, since if any updates become available, they will not be installed automatically.

Thanks for the tip. I do periodically check for updates manually.

---

### Post by philinux on 2008-11-19
According to getdeb 2.6 is available for Hardy. 

Rating: **9.6** / 10, **9** vote(s) 	**Latest versions:**

 		      						Ubuntu 			Intrepid 			32 bits -  			[ 			2.6.2]("http://www.getdeb.net/release/3368") 			
						Ubuntu 			Intrepid 			64 bits -  			[ 			2.6.2]("http://www.getdeb.net/release/3369") 			
						Ubuntu 			Hardy 			32 bits -  			[ 			2.6.2]("http://www.getdeb.net/release/3453") 			
						Ubuntu 			Hardy 			64 bits -  			[ 			2.6.2]("http://www.getdeb.net/release/3454")

---

### Post by strydervtx on 2009-01-16
I just tried to run the commands as listed, but got the following:
The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (>= 2.6.3) but 2.4.5-1ubuntu2 is to be installed
        Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
        Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
        Depends: libpoppler-glib3 but it is not installable
E: Broken packages

I fear I could really muck things up if I start upgrading all of these. I thought perhaps I should uninstall my current 2.4 gimp, but it will also remove ubuntu-desktop. Any thoughts on how to accomplish the gimp upgrade on ubuntu 8.04?
Thx

---

### Post by strydervtx on 2009-01-16
I think I've figured this out. First, I removed getdeb from my sources and I'm glad I didn't actually update anything through that. Then I went to the original [http://www.ubuntugeek.com/how-to-install-gimp-261-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-gimp-261-on-ubuntu-804-hardy-heron.html) post and followed BobSongs' recommendations of installing it via [http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp) and the Debian package installer. It was also good to read that removing ubuntu-desktop with gimp doesn't actually remove your desktop.

---

### Post by mc4man on 2009-01-16
> just tried to run the commands as listed, but got the following:
You should **not** add getdeb to your your sources if your on hardy, it will attempt to install packages for intrepid.
The version available for hardy in getdeb is 2.6.2

[http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

It's very easy to install (gimp + 4 additional packages
Read thru this post carefully and you'll see (the op was being a little thick but it's all there

[http://ubuntuforums.org/showthread.php?t=1013954&highlight=gimp+2.6.2](http://ubuntuforums.org/showthread.php?t=1013954&highlight=gimp+2.6.2)

Basically just remove getdeb from your sources, remove your existing gimp and libgimp2.0, download the 5 packages to a folder, cd to that folder and run dpgk -i *.deb

You can reinstall ubuntu-desktop when your done

In any event remove getdeb from your sources, System -> Adim... -> Software Sources -> Third Party Software

Also note I have gimp 2.6.2 installed on hardy, works fine

Edit: I see you got it fixed while I was typing, beware of adding repo's that don't specify hardy, intrepid ect.

---

### Post by ImpressMe on 2009-01-20
It must be a strange feeling for some of you that Windows users can just upgrade to whatever version they like without tricks or upgrading. I start 8.04 and cannot upgrade to 2.6.4, but if I upgrade Linux then I can... who cares? Back to Windows.

---

### Post by dulbirakan on 2009-02-04
Well good luck to you trying to run a program written for vista on XP or vice versa.

---

### Post by stchman on 2009-02-04
You can get it from here.

[http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

---

### Post by Megrimn on 2009-02-15
mc4man's advice worked for me. :biggrin: just glad to have something better than 2.4!

---

