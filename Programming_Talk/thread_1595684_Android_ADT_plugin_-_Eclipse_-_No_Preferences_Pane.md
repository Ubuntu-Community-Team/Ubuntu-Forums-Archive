---
title: "Android ADT plugin - Eclipse - No Preferences Pane"
date: 2010-10-13
forum: Programming Talk
---

### Post by razorbuzz on 2010-10-13
[COLOR="Blue"]Short version:[/COLOR] Upgraded to Maverick, Android ADT preferences no longer in Eclipse and Android apps fail to run due to missing resources.

**[COLOR="Blue"]Long version: [/COLOR]**
On 10.04
     Eclipse and the Android ADT plugin were working perfectly.  I could run apps in the virtual devices, I could moved them to my Droid2 and they'd run.  All libraries were available, and the Preferences pane for Android was in place so I could direct Eclipse to the /tools directory in the SDK.


I upgraded to Maverick.  Eclipse runs, Java apps run.  Android apps? Nada. 
Eclipse can't find any of the tools. ADB isn't available, so errors galore.

Attempted resolution:  Removed Android plugins, reinstalled. Nothing.  Removed Android plugins, completely removed Eclipse, and removed Android SDK.   Redownloaded the SDK, installed Eclipse, installed the Android plugins through Eclips (help>Install New Software).  Install went fine.   Restarted Eclipse - still nothing for Android in the Preferences pane, nor anywhere else.

Anybody have a solution?



Details;
Eclipse SDK
Version: 3.5.2
Build id: M20100211-1343
Android DDMS    0.9.9.v201009221407-60953
Android Development Tools  0.9.9.v201009221407-60953
Ubuntu 10.10

---

### Post by r-senior on 2010-10-13
No solution, but might be worth a look at the Eclipse log files. 

The main one is usually created in your workspace as .metadata/.log. You may also find individual plugin logs in .metadata/.plugins/<name-of-plugin>/.log.

---

### Post by Guitou on 2010-10-13
Hi,
Same problem, logs didn't help. Maybe the java jdk should be the problem.

---

### Post by razorbuzz on 2010-10-13
Thanks for the replies - Guitou is right, nothing in the logs shows problems with it.  The only log entries are in regards to missing Help documents.

!SUBENTRY 1 org.eclipse.help.base 4 4 2010-10-13 12:27:16.633

Pretty sure those are unrelated to Android since they're in regards to the Eclipse base?

-RB

---

### Post by ritusrivastava on 2010-10-14
Here is the solution:
[http://sonalsantan.blogspot.com/2010/10/eclipse-adt-plugin-on-ubuntu-1010-after.html](http://sonalsantan.blogspot.com/2010/10/eclipse-adt-plugin-on-ubuntu-1010-after.html)

Hope this helps.
-Ritu

---

### Post by razorbuzz on 2010-10-14
ritusrivastava - Excellent, thank you!  Glad to see it was just posted this morning and I didn't miss it when searching previously.


To add to the instructions on the blog (5b)

   1. Exit eclipse if running
   2. Delete ~/.eclipse/org.eclipse.platform_3.5.0_155965261
   3. Start eclipse
   4. Open Help->Install New Software
   5a. Install GEF plugin from [http://download.eclipse.org/tools/gef/updates/releases](http://download.eclipse.org/tools/gef/updates/releases). Note that GEF is required for ADT
**   5b. Install WST Server Adapters from the Eclipse updates (Help>Install new software > [http://download.eclipse.org/releases/galileo/](http://download.eclipse.org/releases/galileo/) ) - Also required for ADT.**
   6. Install ADT plugin from [https://dl-ssl.google.com/android/eclipse](https://dl-ssl.google.com/android/eclipse)

Thanks all.

-RB

---

### Post by joshb86 on 2010-10-15
> **razorbuzz said:**
> ritusrivastava - Excellent, thank you!  Glad to see it was just posted this morning and I didn't miss it when searching previously.


To add to the instructions on the blog (5b)

   1. Exit eclipse if running
   2. Delete ~/.eclipse/org.eclipse.platform_3.5.0_155965261
   3. Start eclipse
   4. Open Help->Install New Software
   5a. Install GEF plugin from [http://download.eclipse.org/tools/gef/updates/releases](http://download.eclipse.org/tools/gef/updates/releases). Note that GEF is required for ADT
**   5b. Install WST Server Adapters from the Eclipse updates (Help>Install new software > [http://download.eclipse.org/releases/galileo/](http://download.eclipse.org/releases/galileo/) ) - Also required for ADT.**
   6. Install ADT plugin from [https://dl-ssl.google.com/android/eclipse](https://dl-ssl.google.com/android/eclipse)

Thanks all.

-RB


Thanks bud. Works like a charm.

---

### Post by boralyl on 2010-12-20
Many thanks, that worked like a charm!

---

### Post by big-wave on 2011-03-27
Fixed it for me as well

---

### Post by pyman on 2011-04-08
Worked fopr me too thanks!! :)

---

### Post by ThomasMarkas on 2011-04-18
Thanks works for me as well. Shame upgrade from 10.04LTS to 10.10 did not work, have had to manually fix.

---

### Post by mkarnicki on 2011-05-08
In step 5b, it's sufficient to add Galileo source
[http://download.eclipse.org/releases/galileo/](http://download.eclipse.org/releases/galileo/)

WST will be installed as a dependency when ADT plugin is installed.

---

### Post by drwatson_droid on 2011-06-29
> **ritusrivastava said:**
> Here is the solution:
[http://sonalsantan.blogspot.com/2010/10/eclipse-adt-plugin-on-ubuntu-1010-after.html](http://sonalsantan.blogspot.com/2010/10/eclipse-adt-plugin-on-ubuntu-1010-after.html)

Hope this helps.
-Ritu

> **razorbuzz said:**
> ritusrivastava - Excellent, thank you!  Glad to see it was just posted this morning and I didn't miss it when searching previously.


To add to the instructions on the blog (5b)

   1. Exit eclipse if running
   2. Delete ~/.eclipse/org.eclipse.platform_3.5.0_155965261
   3. Start eclipse
   4. Open Help->Install New Software
   5a. Install GEF plugin from [http://download.eclipse.org/tools/gef/updates/releases](http://download.eclipse.org/tools/gef/updates/releases). Note that GEF is required for ADT
**   5b. Install WST Server Adapters from the Eclipse updates (Help>Install new software > [http://download.eclipse.org/releases/galileo/](http://download.eclipse.org/releases/galileo/) ) - Also required for ADT.**
   6. Install ADT plugin from [https://dl-ssl.google.com/android/eclipse](https://dl-ssl.google.com/android/eclipse)

Thanks all.

-RB

Thanks to above post, we got some direction to solve the same problem we had. In addition to above, we were behind a proxy server and the Eclipse update was having some problem with SOCKS server (we found this by checking eclipse logs in command line). Even after setting the correct proxy server settings in eclipse, the update was not working. We did the following steps

    1. Install eclipse using Synaptic package manager.
    2. Delete the following folder
    > rm -r ~/.eclipse/org.eclipse.platform_3.5.0_155965261    3. Download the following from internet.
         Eclipse IDE for Java Developers (linux 64-bit version) [eclipse-java-galileo-SR2-linux-gtk-x86_64.tar.gz]from [http://www.eclipse.org/downloads/packages/release/galileo/sr2](http://www.eclipse.org/downloads/packages/release/galileo/sr2)
         GEF-Update-3.5.2.zip from [http://www.eclipse.org/gef/downloads/index.php](http://www.eclipse.org/gef/downloads/index.php)
         ADT-11.0.0.zip from google site.

    4. Extract the zip file "eclipse-java-galileo-SR2-linux-gtk-x86_64.tar.gz" to some directory eg: /home/<userid>/Desktop/
    5. Change directory to "/usr/lib/eclipse"
>     cd /usr/lib/eclipse    6. Copy all contents from "plugins" and "features" directory in extracted folder done in Step 4 to "/usr/lib/eclipse/plugins" & "/usr/lib/eclipse/features" respectively. Run the following commands from "/usr/lib/eclipse" folder.
>     $ sudo cp -r /home/<userid>/Desktop/eclipse_linux/plugins/ .
    $ sudo cp -r /home/<userid>/Desktop/eclipse_linux/features/ .    7. Change permission for contents inside those folders to include execute permission. Run the following commands from "/usr/lib/eclipse" folder.
    > sudo chmod 777 -R plugins/ features/    8. Start Eclipse and Install first "GEF" and then "ADT" plugin downloaded in Step 4.
        Help->Install New Software->Add & select "Archive". Give path to the above mentioned zip files downloaded Step 4.
        Install "GEF" first and "ADT" next.
        Check all plugin packages and Install. Accept any agreements or certificate confirmations. 

    9. Map path to Android SDK in Eclipse ADT. Window->Preferences->Android and give the path to Android SDK installed.
    10. After this we can launch Window->Android SDK and AVD Manager.

---

### Post by King Sasquatch on 2013-04-18
> **joshb86 said:**
> Thanks bud. Works like a charm.

That also worked for Ubuntu 12.04.

P.I.T.A.  if you ask me.  Ubuntu should make setting up an Android development environment  easier.

---

