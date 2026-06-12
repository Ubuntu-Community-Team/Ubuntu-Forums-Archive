---
title: "Another learner having problem with a Java program"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by SusieSA on 2008-06-07
Hi

I play bridge online but since I've upgraded to Ubuntu 8.04, I'm unable to use the java applet that the site uses.

Actually prior to 8.04, when I loaded up the java applet for the first time in a day, the applet would appear, but it would keep on refreshing and refreshing - each time getting a bit shorter and shorter.  So the applet would slowly diminish.  Every time I logged on, I'd open the applet once and then close it and when I opened it for the second time, it worked fine.  

Now in 8.04, I've got this diminishing problem all the time.  And when the Bridge Club Live Control applet tries to initialise the java applet, I get a "Load Problem".

I have tried many things...

In Firefox, when I select Edit / Preferences, and pick "Content", both "enable Javascript" and "Enable Java" are selected.  

When I select Edit / Preferences and then the "Manage Add-ons" button in the Main area and then select the "Plugins" option, there is no mention of any Sun Java 6 or anything about a Java plugin.

In Synaptic, if I search for Java, it seems as if synaptic recognises that I have Java 6 installed.  See attached screenshot.

I have run the "sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts" command

But when I type "ls -l /usr/lib/firefox/plugins", the only thing that I can see is "ls -l /usr/lib/firefox/plugins"



Interestingly, as I wrote this, I tried to run the "sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts" again and I got the following error:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

When I go to the Applications / AddRemove area, "Sun Java 6 Runtime" is installed.

When I go to the Sun website and try and verify my installation, it is not verified.

So then I downloaded the "jre-6u6-linux-i586-rpm.bin", ran a chmod statement to make the file executable and then tried to run the file.  I had to scroll down mountains of text and then type 'yes' to agree to the install, but I don't think that it worked correctly.  The terminal window closed too quickly for me to read any outcome.  It seemed like a very strange user interface to work from.


Sorry to chuck so much info here and I hope that somebody understands what I'm trying to do!!! 

Thanks
Susie


Some more info...

When I run "sudo apt-get install sun-java6-jre"

I get the following info...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
The following packages were automatically installed and are no longer required:
  libarts1c2a kdelibs4c2a libartsc0 kdelibs-data liblualib50 libavahi-qt3-1 libqt3-mt liblua50
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16 libnss3-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by RealPSL on 2008-06-07
First off thank you for all the information. It is a lot more detailed than the 2 lined requests that I generally see.

First test I would like you to run is entering [about:plugins]("about:plugins") in the firefox browser address window. It will help you determine which java you are using. 

I think what we need to figure out is if the java program you are trying to run supports java 6. maybe installing java 5 would help but let us make sure you browser plugin is working first by checking the output above.

---

