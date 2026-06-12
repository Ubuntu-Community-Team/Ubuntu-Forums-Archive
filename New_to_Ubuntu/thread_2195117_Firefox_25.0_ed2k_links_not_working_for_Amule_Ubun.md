---
title: "Firefox 25.0 ed2k links not working for Amule Ubuntu 13.04 13.10 14.04{daily build}"
date: 2013-12-22
forum: New to Ubuntu
---

### Post by Prairieboy on 2013-12-22
Hello, this is more of an FYI guide to help people to avoid loosing the week that I have... when trying to get Amule to work with Firefox & clicking on ed2k links.

Previously I had chosen to use Ubuntu 9.04 in order to be able to use Amule so Firefox would be able to handle clicking on ed2k links.  Following this guide { [http://web.archive.org/web/20100212130059/http://wiki.amule.org/index.php/Ed2k_links_handling](http://web.archive.org/web/20100212130059/http://wiki.amule.org/index.php/Ed2k_links_handling) } had always worked in the past when setting up single user configuration.  However, whenever I tried newer Ubuntu versions, links would never work by clicking on them (& I always got the error message "Firefox doesn't know how to open this address, because the protocol (ed2k) isn't associated with any program.").  Until now, I had never found the solution to overcome the issue.

As I needed to update my OS (9.04 was no longer fully supported), & alot of the information online has become outdated/not relevant, I finally solved the issue as follows:



Step 1)  

Follow original guide previously mentioned (I used Configuration for a single user):

     Firefox 2 & 3 (or later):

       -  Insert **about:config** in the Firefox address bar
       - Right click on the list, select New, then Boolean; insert **network.protocol-handler.external.ed2k** as Preference Name and **true** as Value
       - Right click on the list, select New and String; insert **network.protocol-handler.app.ed2k** as Preference Name & **/usr/bin/ed2k** (aka the path to where ed2k application is installed on your system, unless you placed it elsewhere) as Value. 

     Also, for Firefox 3 (& higher only):

       - Right click on the list, select New, then Boolean; insert **network.protocol-handler.expose.ed2k** as Preference Name and **false** as Value

     *Note:  At this point, this* --> "click over an ed2k link, & Firefox should ask which app you want to use to open the link. Choose /usr/bin/ed2k and it should work." --> *doesn't work.* (At least it didn't for me with newer versions of Ubuntu).



Step 2)  

Info from Post 18 on this thread:  { [http://www.linuxquestions.org/questions/linux-software-2/ed2k-links-handling-with-firefox-and-amule-774697/page2.html](http://www.linuxquestions.org/questions/linux-software-2/ed2k-links-handling-with-firefox-and-amule-774697/page2.html) }  *Note:  I am not sure if this step is necessary (as such, one may want to skip Step 2 initially & try Step 3 first) but while troubleshooting I performed it.  Afterward doing so, I tested ed2k link but still received back the above error message... so I then performed Step 3.*


       -  Right click on the list, select New, then Boolean; insert **network.protocol-handler.warn-external.ed2k** as Preference Name & **True** as Value

       -  Right click on the list, select New, then String; insert **extensions.torrentserver-handler.protocols** as Preference name **ed2k** as Value



Step 3)

Info from Post 18 on above thread in Step 2:

     - Open Terminal

     - Type (or copy & paste) the following (hit 'Enter' after line):

         **sudo gedit /usr/share/applications/ed2k.desktop**

     - (you will need to enter *your* password)

     - A document will open.  Copy & paste the following text (that is between the two lines, then save & close the document):

----------------- Copy Below --------------------
[Desktop Entry]
Name=ed2k
Exec=ed2k %u
Type=Application
Terminal=false
Categories=System;
MimeType=x-scheme-handler/ed2k;
Comment=aMule ED2K Link Parser
------------------ Copy Above --------------------

     - Return to the Terminal & type (or copy & paste) the following (hit 'Enter' after each line):

         **gconftool-2 -s /desktop/gnome/url-handlers/ed2k/command '/usr/bin/ed2k %s' --type String**

         **gconftool-2 -s /desktop/gnome/url-handlers/ed2k/enabled --type Boolean true**

         **sudo update-desktop-database**

     - Close Terminal & test an ed2k link.




Finally! Step 3 was finally the key to solving the issue for me.  After clicking the first ed2k link, a window opens.  One must direct the 'application to use' to **/usr/bin/ed2k** (don't forget to select/tick the box that specifies to always handle the same way for future ed2k links!).  Credit, & my humblest thank-you, to ntsc525 for posting his solution, albeit on another forum, after he discovered it!


ps, Moderators, my apologies if I have posted incorrectly... if so, please let me know so I can correctly edit the post.

---

### Post by AndyA121 on 2014-04-18
I got down to the last command " **/usr/bin/ed2k"and it said I wasn't in root so I couldn't complete the action**. I'mrunning Ubuntu 13.10.

---

### Post by AndyA121 on 2014-04-18
I got down to the last command " **/usr/bin/ed2k"and it said I wasn't in root so I couldn't complete the action**. I'mrunning Ubuntu 13.10.

---

### Post by Prairieboy on 2015-01-16
Update: 

As of today, using a fresh install of 14.04, I only needed to complete up to step one (as listed above).

---

