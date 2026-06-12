---
title: "How to install Vuze on Ubuntu &amp; Debian"
date: 2008-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by VuzeLover on 2008-11-27
This howto is based on a howto by Artificial Intelligence.  That old howto is no longer updated or maintained and is long out of date for Vuze.  That said it was very helpful back in the day and this howto could not exist with out it.  The improvements I have made are for the name change and better security.

The original howto is [[color=green]Here[/color]]("http://ubuntuforums.org/showthread.php?p=824358").  And Artificial Intelligence user profile is [[color=green]Here[/color]]("http://ubuntuforums.org/member.php?u=19").

**[color=green]You need Java installed.  Any of the Java flavors will work.  I myself use Sun-Java6.[/color]**
**[color=green]Tested on Ubuntu 8.10 and Debian Lenny.[/color]**
**[color=green]Ready![/color]**




**Step 1**
Create a dedicated user account for Vuze.  The reason is that Vuze is for all intents and purposes a server.  This is even more true in the case of users who activate the built in tracker and web server.
```
sudo adduser --home /opt/vuze --shell /bin/false --no-create-home --disabled-login vuze
```**[color=red]At this point adduser will ask you for some info BUT and a big BUT simply hit the enter button without filling in any data![/color]**  I should mention that this simply puts the files and folders under a non-root account.  The Vuze process however will still run as the user who called Vuze.  I have not found a good method yet for running the Vuze process as the Vuze user.  The annoying but simple method is to create the Vuze user with "--home /home/vuze".  Then you would enter a password and use the user switching applet to switch to the Vuze user.








**Step 2**
Download Vuze from [[color=green]Here[/color]]("http://azureus.sourceforge.net/download.php").  You can select 32bit or 64bit.  The tutorial is the same for both.








**Step 3**
Open up a terminal and cd to where you downloaded Vuze.
```
cd [color=red]Location_of_your_file[/color]
```[color=green]  Example would be "$cd /Desktop" or "$cd /Downloads" or "$/home/steve/Downloads"[/color]



```
sudo tar jxvf [color=red]REPLACE_WITH_THE_NAME_OF_THE_FILE[/color].tar.bz2 -C /opt/
```[color=green]The -C is an upper case letter by the way[/color]








**Step 4**
Change permissions temporarily.
```
sudo chown -R [color=red]YOUR_USERNAME_GOES_HERE[/color]**[color=black]:[/color]**[color=red]YOUR_USERNAME_GOES_HERE[/color] /opt/vuze/
```[color=green]Example would be "$sudo chown -R steve**[color=black]:[/color]**steve /opt/vuze"[/color]








**Step 5**
To get Vuze into your Applications Menu.
```
sudo nano /usr/share/applications/Vuze.desktop
```
add or copy and paste this into the nano text editor.> [Desktop Entry]
Name=Vuze
Comment=P2P Client
Exec=/opt/vuze/vuze
Icon=/opt/vuze/vuze.png
Terminal=false
Type=Application
Categories=Application;Network;To exit press Ctrl x and hit y for yes.









**Step 6**
It's a good idea to be able to launch Vuze from a terminal and in order to do that...
```
sudo nano /usr/bin/vuze
```
add or copy and paste this into the nano text editor.> #!/bin/sh

/opt/vuze/vuze "$*"To exit press Ctrl x and hit y for yes.








**Step 7**
Make the /usr/bin/vuze executable.
```
sudo chmod +x /usr/bin/vuze
```







**Step 8**
Open Vuze up and get any updates that are available.  **[color=red]Do not install plugins at this time[/color]**.  Then restart Vuze and check for updates again as some updates won't appear until other updates are installed.  If updates showed a second time then restart Vuze a third time and check for updates.  Repeat until there are no updates.  **[color=red]Do not install plugins at this time!**[/color]  Exit completely at this point by selecting "File/Exit".








**Step 9**
Change permissions to the user and group "vuze" that we created in step 1.
```
sudo chown -R vuze:vuze /opt/vuze
```This takes care of the directory where we installed Vuze.  It also secures all files and sub directories contained within "/opt/vuze"








**Step 10**
Change the permissions on the "/usr/bin/vuze" file we created earlier.
```
sudo chown vuze:vuze /usr/bin/vuze
```








**Step 11**
Now start up Vuze and install any plugins you desire.  The plugins will now install to your user directory at ".azureus".  This way you can install and remove and update without having to change permissions.








**Step 12**
To update Vuze itself, we need to change permissions.
```
sudo chown -R [color=red]YOUR_USERNAME_GOES_HERE[/color]**[color=black]:[/color]**[color=red]YOUR_USERNAME_GOES_HERE[/color] /opt/vuze/
```Now start up Vuze and update.  Repeat until there are no updates any longer.
When there are no more updates you need to change the permissions back to a secure setting.  To do this...
```
sudo chown -R vuze:vuze /opt/vuze
```




Many thanks go to [[color=green]Artificial Intelligence[/color]]("http://ubuntuforums.org/member.php?u=19")

---

### Post by muks on 2009-02-16
Hey,

Y do I need to do all this? Can't I simply install from Synaptic/Aptitude? I can see it there.


Regards
Muks

---

### Post by binbash on 2009-02-17
Excellent howto, it works like a charm here

---

### Post by rvgeelen on 2009-02-17
My NAT will not go "green" it keeps saying firewalled!! even though I openened the ports on Iptables, forwarded the ports on router and my firewallbox. 
It works on my XP machine (different ip, same rules) what could possible be the problem.


edit: Aaaaaaaah.... made a typo in the portforwarding rules. I can't believe it. took me 2 days to find!!!! stupid n00b move.

---

### Post by mister_playboy on 2009-05-07
Hmmm... this tutorial is less messy and works perfectly for me:

[COLOR="Red"][http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu]("http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu")[/COLOR]

Note that the Vuze download page at [COLOR="Red"][http://www.vuze.com/Download.html]("http://www.vuze.com/Download.html")[/COLOR] will only give you the 32-bit package, if you need the 64-bit package, get it here:

[COLOR="Red"][http://azureus.sourceforge.net/download.php]("http://azureus.sourceforge.net/download.php")[/COLOR]

---

### Post by jjosotoro on 2009-06-02
you can also add the getdeb repository to your source list and follow this steps.

echo "deb [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty/" | sudo tee -a /etc/apt/sources.list.d/getdeb.list && sudo apt-get update

now if that gives an gpg error like this:

W: GPG error: [http://getdeb.masio.com.mx/](http://getdeb.masio.com.mx/) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D

you must use the following command in the terminal:

gpg --keyserver hkp://subkeys.pgp.net --recv-keys "XXXXXXXXXX"
sudo gpg --export --armor "XXXXXXXXXX" | sudo apt-key add -
sudo apt-get update

replacing the "XXXXXXXXXX" whit the number that appears in the message ex: B152F042D246C25D

$sudo apt-get update

just to check about the gpg error (it shouldnt appear anymore)

$sudo apt-get install vuze

this will install the version of vuze that is on getdeb (4.2.0.2) whit all dependencies, or you can install it using synaptics.

$sudo chmod -R 777 /usr/share/vuze

this will let vuze to do any upgrade

---

### Post by tomas_ed on 2009-07-04
great tutorial...thnx :)

---

### Post by gottatrieit on 2009-07-05
I've been trying for two days to get this to work!  I'm a noobie and am a little unfamiliar with the command line, although I don't mind working with it.
Some how, I'm not getting nano to work right for when I try to edit.  Another thing is the changing of ownerships. It is very confusing to me what is needed at a couple of the spots when "I'm" asked to "chown" from one (vuze:vuze) to my username and then back.  I'm missing something in the installation because when I start Vuze, it seems to run good one time and then it freezes on the next startup.
As a note: on the last edit for "#!/bash/sh" etc., I used gedit instead of nano.  Will that make any difference in how the file is read?
Any help will be appreciated as I have been trying to learn a little bit about using torrents and haven't as yet gotten one to work for very long!

---

### Post by atreidex on 2009-07-22
great tutorial man, thank you!

---

### Post by mister81 on 2009-09-16
Thanks. Nice post.

---

### Post by foxxman on 2009-12-16
OH man Thanks A bunch Much Help.  YOU :guitar:

---

### Post by janthonywj on 2010-01-21
Thanks a bunch... Works great. No more waiting for getdeb.net to update.

---

### Post by SILLAT on 2010-03-28
Thanks alot.......
Tutorial work like a charm on UBUNTU JAUNTY 9.10
Deluge is my Torrent Client of choice but i have to try Vuze now bcuz of some broken updates from the Deluge PPA crippled my installation

---

### Post by sikander3786 on 2010-04-02
> **SILLAT said:**
> Thanks alot.......
Tutorial work like a charm on UBUNTU JAUNTY 9.10
Deluge is my Torrent Client of choice but i have to try Vuze now bcuz of some broken updates from the Deluge PPA crippled my installation

It worked for me as well but I am not too much excited to quote my Ubuntu Karmic 9.10 as "UBUNTU JAUNTY 9.10"

:D

---

### Post by astrobeaver on 2010-04-03
Simply use Synaptic!!

---

### Post by SILLAT on 2010-04-05
> **sikander3786 said:**
> It worked for me as well but I am not too much excited to quote my Ubuntu Karmic 9.10 as "UBUNTU JAUNTY 9.10"

:D

@sikander3786 
That was a mistake :p i actually meant KARMIC KOALA ;)
I guess i was just happy it worked ):P
@astrobeaver Snaptic is OK but i enjoy installing software from source more because its always the latest and it just feels GooooD

---

### Post by cuttail on 2010-04-07
Awesome tutorial - Still very relevant today. Works a treat on 64bit installations and in my case very much needed as simply using the synaptic versions always bleated about being out of date and wanting updates... Other tutorials never quite got me to the end of the road (simply downloading and extracting will then running vuze will not do).

---

### Post by Kanna2412 on 2010-04-15
Hi Guys,

I love Vuze. I installed Vuze on Ubuntu 9.10 from repositories. When I opened it, it was asking me to upgrade. I clicked on the upgrade button, it went to Vuze website. Again I downloaded Vuze software and installed manually. Again I encountered the same problem.

My friend installed Vuze for windows XP on his laptop. The version has more features than I got and it is not asking for upgrade.

Please help me fix this.


Indian.

---

### Post by rifter on 2010-04-22
> **Kanna2412 said:**
> Hi Guys,

I love Vuze. I installed Vuze on Ubuntu 9.10 from repositories. When I opened it, it was asking me to upgrade. I clicked on the upgrade button, it went to Vuze website. Again I downloaded Vuze software and installed manually. Again I encountered the same problem.

My friend installed Vuze for windows XP on his laptop. The version has more features than I got and it is not asking for upgrade.

Please help me fix this.


Indian.

If you follow the tutorial you will get the new Vuze.  You could also try the method mentioned above, _[color=blue][linked here](http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)[/color]_.

---

### Post by LucianoP on 2010-05-06
messy but it works

---

### Post by JustSteph on 2010-07-03
When I tried to run the program at Step 8, nothing happened, so I ran it in terminal and got this message:

Starting Azureus...
Suitable java version found [java = 1.6.0_18]
Configuring environment...
Java exec found in PATH. Verifying...
find: &#8216;/home/steph/.azureus/plugins&#8217;: No such file or directory
Exception in thread "main" java.lang.NoClassDefFoundError: org/gudy/azureus2/platform/unix/ScriptBeforeStartup
Caused by: java.lang.ClassNotFoundException: org.gudy.azureus2.platform.unix.ScriptBeforeStartup
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Could not find the main class: org.gudy.azureus2.platform.unix.ScriptBeforeStartup. Program will exit.
Loading Azureus:
java -Xmx128m -cp "./*.jar" -Djava.library.path="/home/steph" -Dazureus.install.path="/home/steph" -Dazureus.script="/home/steph/vuze" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
Exception in thread "main" java.lang.NoClassDefFoundError: org/gudy/azureus2/ui/swt/Main
Caused by: java.lang.ClassNotFoundException: org.gudy.azureus2.ui.swt.Main
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Could not find the main class: org.gudy.azureus2.ui.swt.Main. Program will exit.
Exit from Azureus complete
Exception in thread "main" java.lang.NoClassDefFoundError: org/gudy/azureus2/platform/unix/ScriptAfterShutdown
Caused by: java.lang.ClassNotFoundException: org.gudy.azureus2.platform.unix.ScriptAfterShutdown
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Could not find the main class: org.gudy.azureus2.platform.unix.ScriptAfterShutdown. Program will exit.
Azureus TERMINATED.


Help?

---

### Post by rifter on 2010-07-03
> **JustSteph said:**
> When I tried to run the program at Step 8, nothing happened, so I ran it in terminal and got this message:

Starting Azureus...
Suitable java version found [java = 1.6.0_18]
Configuring environment...
Java exec found in PATH. Verifying...
find: ‘/home/steph/.azureus/plugins’: No such file or directory
Exception in thread "main" java.lang.NoClassDefFoundError: org/gudy/azureus2/platform/unix/ScriptBeforeStartup
Caused by: java.lang.ClassNotFoundException: org.gudy.azureus2.platform.unix.ScriptBeforeStartup
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Could not find the main class: org.gudy.azureus2.platform.unix.ScriptBeforeStartup. Program will exit.
Loading Azureus:
java -Xmx128m -cp "./*.jar" -Djava.library.path="/home/steph" -Dazureus.install.path="/home/steph" -Dazureus.script="/home/steph/vuze" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
Exception in thread "main" java.lang.NoClassDefFoundError: org/gudy/azureus2/ui/swt/Main
Caused by: java.lang.ClassNotFoundException: org.gudy.azureus2.ui.swt.Main
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Could not find the main class: org.gudy.azureus2.ui.swt.Main. Program will exit.
Exit from Azureus complete
Exception in thread "main" java.lang.NoClassDefFoundError: org/gudy/azureus2/platform/unix/ScriptAfterShutdown
Caused by: java.lang.ClassNotFoundException: org.gudy.azureus2.platform.unix.ScriptAfterShutdown
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Could not find the main class: org.gudy.azureus2.platform.unix.ScriptAfterShutdown. Program will exit.
Azureus TERMINATED.


Help?

It looks to me like you are trying to run it from your home directory instead of where you should have installed it if you were following the steps.  Look at the line where it shows the command it is using to run vuze.

```

java -Xmx128m -cp "./*.jar" -Djava.library.path="/home/steph" -Dazureus.install.path="/home/steph" -Dazureus.script="/home/steph/vuze" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 

```

  -cp is the class path, which tells java where the rest of the program is.  That's not your home directory, so when it looks there it does not find the files.
This is what I get when I run it from the terminal on my system:
```

java -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/opt/vuze" -Dazureus.install.path="/opt/vuze" -Dazureus.script="/opt/vuze/azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 

```

This is the bit of the script that fills out the classpath:
```

# get the app dir if not already defined
if [ -z "$PROGRAM_DIR" ]; then
                PROGRAM_DIR=`dirname "$0"`
                PROGRAM_DIR=`cd "$PROGRAM_DIR"; pwd`
else
        if [ "$(echo ${PROGRAM_DIR}/*.jar)" = "${PROGRAM_DIR}/*.jar" ]; then
                echo "You seem to have set an invalid PROGRAM_DIR, unable to continue!"
                exit 1
        elif [ ! -f "${PROGRAM_DIR}/Azureus2.jar" ]; then
                echo "Unable to locate Azureus2.jar in $PROGRAM_DIR, aborting!"
                exit 1
        fi
fi

# Change path here so we can do for loop on program dirs with spaces
cd "${PROGRAM_DIR}"

# build the classpath
for FILE in ./*.jar; do
        CLASSPATH="${CLASSPATH:+${CLASSPATH}:}$FILE"
done

```

So unless you have altered PROGRAM_DIR in the /opt/vuze/azureus script (which you should not do) the program will start looking for class files under the directory from which the /opt/vuze/azureus script is run (which would be /opt/vuze if you installed according to the instructions above).  So if you followed the instructions the class files will be under /opt/vuze and so will the script.

---

### Post by JustSteph on 2010-07-04
Okay. Sorted it. Thanks =]

---

### Post by tito_drum on 2010-08-05
When I installed vuze this way I couldn't removed it using apt-get remove vuze. Why is that? Looks like it can't find it. What do you recommend to do?
Thanks

---

