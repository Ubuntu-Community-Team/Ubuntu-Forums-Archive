---
title: "Mozilla firefox 3.0 beta (new)"
date: 2008-03-02
forum: Outdated Tutorials &amp; Tips
---

### Post by robertchahine on 2008-03-02
hey everybody.I was surfing on the internet when suddently i knew that firefox 3.0 was released.so here are the steps that i found them to install this version of firefox (you can read them on this url :[http://news.softpedia.com/news/Install-Firefox-3-Beta-3-on-Ubuntu-7-10-78875.shtml](http://news.softpedia.com/news/Install-Firefox-3-Beta-3-on-Ubuntu-7-10-78875.shtml))
[B][U]
Step 1 - Enable the unsupported repositories[/U][/B]
Go to System -> Administration -> Software Sources and enter your password when asked.


In the Software Sources window, go to the third tab (Updates) and check the "Unsupported updates (gutsy-backports)" option. Then click the 'Close' button and, when you will be asked if you want to reload the information about available software, click 'Reload' and wait until the Software Sources window disappear.



**_Step 2 - Install Firefox 3 Beta 3_**

Now, go to System -> Administration -> Synaptic Package Manager and search for firefox 3. The search will return exactly what you were looking for!



Click on the first result (firefox-3.0) and install it by selecting the 'Mark for Installation' option from the context menu that will appear. Click 'Apply' and the installation will begin. Click 'Yes' to any questions and close Synaptic Package Manager when the installation is over.

**_Step 3 - Cleaning up and a few magic tricks!_**

*[COLOR="Red"]WARNING: The software updates icon will appear in your system tray. Ignore it! Do NOT install any of those updates, because they are unstable and unsupported![/COLOR]*

Now we need to close the unsupported repositories because the software updates notification will stay in tray all the time and it's pretty annoying. So, go again to System -> Administration -> Software Sources, click the third tab (Update) and uncheck the "Unsupported updates (gutsy-backports)" option. Then click the 'Close' button and I guess you know the drill...

Magic Trick 1 - Power up Firefox 3 with plugins: Because Firefox 3 Beta 3 doesn't have the plugins that you already have in your Firefox 2 installation, we need to do some "dirty work" and copy the installed plugins from the FF2 directory to the FF3 one. So, open a terminal (Applications -> Accessories -> Terminal) and type or paste the following command:

CODE

sudo cp /usr/lib/firefox/plugins/* /usr/lib/firefox-3.0-3.0b3pre/plugins


That it, my friends! You can find the brand new Firefox 3 browser under the Internet category of your main menu.

Magic Trick 2 - Set Firefox 3 as default browser: If you want to set it as the default browser for your system, because, I should warn you that any HTTP link (URL) you will click from other applications, such as Pidgin, Thunderbird, etc, will open in Firefox 2. Therefore, you need to open the Preferred Applications tool from System -> Preferences -> Preferred Applications, select 'Custom' and type in the 'Command' field: firefox-3.0 %s and close the window.

---

