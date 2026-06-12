---
title: "HOWTO: Printing from your Android using Google Cloud Print with Linux"
date: 2011-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by bferd on 2011-06-29
This works best if the computer you are using is turned on all the time. I set this up on my fileserver which runs 24/7. The printer that I use is a network printer on my home LAN. 

Your printer will only be available by your Android device if your computer is turned on.

Before you start...

Make sure the printer you want to share using Google cloud print is installed and working on your Ubuntu box. You can use a network printer or a printer that is hooked directly to your computer.



***Setting up Cloudprint for Linux***

Use GIT to download armooo's Cloudprint for Linux source. To use GIT, you first need it installed. You also need python and python-cups installed.

Copy the following code to a terminal:

```

sudo apt-get install git-core python python-cups

```

Now use git to download the source code to your home folder:

```

git clone git://github.com/armooo/cloudprint.git

```

change permissions on the folder:

```

chmod -R 777 ~/cloudprint

```

Change to the cloudprint directory:

```

cd ~/cloudprint

```

Run the setup.py script:

```

python setup.py build

```

Install Cloudprint for Linux that you have just built:

```

sudo python setup.py install

```

You have just installed the script to the following folder:

/usr/local/lib/python2.6/dist-packages/cloudprint/cloudprint.py

Run the script and it should ask for your gmail address and password:

```

python /usr/local/lib/python2.6/dist-packages/cloudprint/cloudprint.py

```

After you enter your Google username and password your printer will automatically be added to Google Cloud Print

Follow this link to manage your Google Cloud Print.

[http://www.google.com/cloudprint/manage.html]("http://www.google.com/cloudprint/manage.html")

Note you can also share this printer with other people (eg. family members)by clicking on the "Action" menu beside the printer name and selecting "Share"


***Setting Up Your Android Device***

There are three ways to do this, installing Cloudprint or Printershare or both on your android device.
I prefer the PrinterShare app. With the free version you can't print directly to a network printer while connected to your LAN, but who cares. Going through Google Cloud Print is almost instant anyway and works just fine. Cloudprint is ok but the adds are annoying and the features go overboard.

Way one (preferred)

Install the Printershare by searching for "Printershare" in the market app on your phone, or by clicking the following link.

[https://market.android.com/details?id=com.dynamixsoftware.printershare&feature=search_result]("https://market.android.com/details?id=com.dynamixsoftware.printershare&feature=search_result")


Way two

Install the Cloudprint by searching for "Cloudprint" in the market app on your phone, or by clicking the following link.

[https://market.android.com/details?id=com.pauloslf.cloudprint&feature=search_result]("https://market.android.com/details?id=com.pauloslf.cloudprint&feature=search_result")



That's it. To print use the "share" button in the app you want to print from. Choose either Printshare or Cloudprint from the menu.




--References--
[http://forum.xda-developers.com/showthread.php?t=991772]("http://forum.xda-developers.com/showthread.php?t=991772")
[http://blog.nguyenvq.com/2011/05/12/google-cloudprint-on-linux/]("http://blog.nguyenvq.com/2011/05/12/google-cloudprint-on-linux/")
[http://forum.xda-developers.com/showthread.php?t=950312&highlight=cloudprint]("http://forum.xda-developers.com/showthread.php?t=950312&highlight=cloudprint")

---

