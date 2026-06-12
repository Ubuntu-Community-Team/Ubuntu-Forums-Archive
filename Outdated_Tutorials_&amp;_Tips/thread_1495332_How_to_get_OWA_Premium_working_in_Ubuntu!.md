---
title: "How to get OWA Premium working in Ubuntu!"
date: 2010-05-28
forum: Outdated Tutorials &amp; Tips
---

### Post by dmglouis on 2010-05-28
This is a tutorial showing you how you can access the Premium version of Outlook Web Access (OWA). Its pretty easy, but there are some outdated tips floating around on the web. For example, when I did a search on this, every tut had me installing Internet Explorer (yikes!).

The first thing you need to do is install Wine. You can do that by opening Synaptic Package Manager (System > Administration > Synaptic Package Manager), typing in wine, and installing or by using the following code:
```
sudo apt-get install wine
```

(I prefer the GUI way, because I'm more comfortable using GUIs, I feel less prone to screwing up something).

Then, after Wine is installed, go here: [http://www.mozilla.com/en-US/products/download.html]("http://www.mozilla.com/en-US/products/download.html"). 
Make sure to download the Windows version of Firefox. After the download is complete, you may notice that if you try to exceute the .exe file using Wine, an error pops up saying that the file needs to be executable.

This is easily resolved. Just use the following code in a terminal:
```
cd Downloads (or wherever you have downloaded the .exe file)
chmod u+x Firefox\ Setup\ 3.6.3.exe (the backslashes are to allow space characters, and the file name may be different)
```

Go through the installation, and once you're installed, you should be good to go. Just type in the address of your OWA website and the Premium version should greet you.

Now, in case it seems like Firefox doesn't start, go to the System Monitor (System > Administration > System Monitor), and end the firefox.exe process. Then, open up your home folder in Nautilus, press Ctrl + H to show hidden files. Then browse to .wine/drive_c/Program Files/Mozilla Firefox. Try opening up firefox.exe. In my case, it opened up a very tiny window (about 50x50), and I had to drag at the corner to make it bigger. Once this initial step is done, you should be fine. Also note that for me, I needed to double-click the X to close Firefox or any other dialog box encountered within.

If you have any questions, please feel free to post them here, and I will try to answer them.

---

### Post by bapoumba on 2010-05-28
Welcome to T&T.

---

