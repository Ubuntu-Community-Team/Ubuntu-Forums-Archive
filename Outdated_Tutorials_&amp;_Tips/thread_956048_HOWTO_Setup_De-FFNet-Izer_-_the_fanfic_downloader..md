---
title: "HOWTO Setup De-FFNet-Izer - the fanfic downloader."
date: 2008-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by SilverWave on 2008-10-22
[SIZE="4"]**De-FFNet-Izer allows the saving of the Whole Story.**[/SIZE]

**No Linux version so we will be using the source.**

1. Go to the home page:

[http://www.deffnetizer.com/download.html](http://www.deffnetizer.com/download.html)

2. Download the source zip and the default template to your desktop and extract.

[http://www.deffnetizer.com/downloads/source.zip](http://www.deffnetizer.com/downloads/source.zip)

and

[http://www.deffnetizer.com/downloads/templates/DefaultTemplate.zip](http://www.deffnetizer.com/downloads/templates/DefaultTemplate.zip)

3. On Ubuntu 8.04 I needed to install "python-tk"
Go to the Synaptic Package Manager and search for  "python-tk" and install.

4. "source.zip" extracts to "Source Code" I renamed this to "deffnet".

5. "DefaultTemplate.zip" extracts to "templates" move this into "deffnet" also create a directory called "fanfic".

6. In a terminal issue the following command:
```
python ~/Desktop/deffnet/deffnet.py
```

7. The De-FFNet-iser application then starts up.
On first use you will need to click File > Set Preferences.

Save to Location:
 /home/YourName/Desktop/deffnet/fanfic

Template to Use: 
/home/YourName/Desktop/deffnet/templates

Now you are good to go!

**Usage Example:**
Enter your story ID (check the number in your fanfic URL) and click fetch.
Then click the "Fetch" opposite "Chapters"
Then click "Save".

If all has worked as it should the story has been saved to "fanfic" in a separate directory.
In this directory are the saved chapters and a "index.html" click this to open all in your browser.

For convenience I have attached a archive ready to be extracted to your desktop.
This has all the above work done for you :)

Note: Tested on Ubuntu 8.04 64bit.

---

### Post by bornagainpenguin on 2009-04-25
Would you happen to know of a way to lock in python-tk as the dependency for de-FFNet-izer?  Right now synaptic and apt insist they are unneeded and I keep getting prompted to remove them whenever I do cleanup..

--bornagainpenguin

---

