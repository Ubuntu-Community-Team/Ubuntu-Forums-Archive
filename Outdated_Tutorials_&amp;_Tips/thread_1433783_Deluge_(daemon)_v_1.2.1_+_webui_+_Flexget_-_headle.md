---
title: "Deluge (daemon) v 1.2.1 + webui + Flexget - headless on Ubuntu Server"
date: 2010-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by gottijr on 2010-03-19
**All this I've got from this website *great tutorial for how to build a me[B]**dia server on ubuntu* [*_Build Media Server_*]("http://havetheknowhow.com")[/B]

  * all the thanks to Ian that made all those available.  

  [SIZE="4"]**How to install Deluge (v1.2.x) headless on Ubuntu Server**[/SIZE]

  Deluge is a great BitTorrent client that you can install on Ubuntu to allow you to share your favourite files with the rest of the BitTorrent community.

  In the newer versions of Ubuntu, Deluge comes in two parts; the server (also called the daemon) and the user interface. This means you can install the Deluge daemon as a headless service and then control it from a remote machine. You can either control the daemon using the Deluge client itself (for example the Windows version of Deluge) or alternatively you can use your browser to control it. If you've not installed [**VNC**]("http://havetheknowhow.com/Configure-the-server/Install-VNC.html") and are running a purely headless setup then running Deluge headless is pretty much your only option! So, here's how you install it:

If you wish to install the released version of Deluge (v1.1.9) then see the guide here: [**Installing Headless Deluge version 1.1.9**]("http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html")

**Updating the Source Repository**

We firstly need to make a simple change to add the Release Candidate version of Deluge as a valid Ubuntu "source repository".

So, type the following command into your Putty session or directly into the command line on your server to install the PPA:

```
sudo add-apt-repository ppa:deluge-team/ppa

```


Next type/paste:

```

sudo apt-get update

```

Now we need to create a new user called "deluge" and perform a couple more steps. So type/paste the following:

```

sudo adduser --disabled-password --system --home /var/lib/deluge --gecos "SamRo Deluge server" --group deluge

```

```

sudo touch /var/log/deluged.log

sudo touch /var/log/deluge-web.log

sudo chown deluge:deluge /var/log/deluge*

```

**Install the Deluge Daemon**

Next we'll install the Deluge daemon itself:

```

sudo apt-get update

sudo apt-get install deluged
```

 Next we'll install the Web interface by typing:

```

sudo apt-get install deluge-webui
```

**Run the Deluge Daemon on startup**

Now we've got the components installed we need to make everything run on start-up. So, let's create the first script we need by typing the following command in a Putty Session:

```

sudo vim /etc/default/deluge-daemon
```

This will create and open a file called deluge-daemon

Next, assuming you're using Putty, highlight the following 5 commands, right-click on them and select Copy

```

# Configuration for /etc/init.d/deluge-daemon
# The init.d script will only run if this variable non-empty.
DELUGED_USER="deluge"
# Should we run at startup?
RUN_AT_STARTUP="YES"

```

  ***when you paste this with windows putty go back at the top of the file and make sure everything was pasted cause sometimes i'm missing some lines or letters!!!**

Toggle back to the Putty Session and press the [Insert] key once and then right click and the 5 lines we've just copied above will be pasted into the file.

Now press the [Esc] key once and type **:wq** to save and quit out of the script. If you make a mistake editing the file then issue **:q!** instead of **:wq** to abort your changes.

**Creating the "Init Script"**

Now we need an "init script". This script is rather long but we can do some more copying and pasting to implement this script. So, type the following command in your Putty Session to create and open the script:

```

sudo vim /etc/init.d/deluge-daemon

```

Next, highlight and copy [**_this script_**]("http://havetheknowhow.com/scripts/deluge-daemon_rc.txt").

Toggle back to your Putty Session and press the [Insert] key once and then right click and the whole script you've just highlighted will be pasted into the screen.
 
***when you paste this with windows putty go back at the top of the file and make sure everything was pasted cause sometimes i'm missing some lines or letters!!!**    

**IMPORTANT: By default the init script starts the Deluge Daemon on port 9092. However, Squeezebox Server also uses port 9092. So, if you're installing Squeezebox Server along with this release of Deluge then you must change the port that the Deluge Daemon uses else only one of these two application will work at any one time. ie. you'd have to stop one application running so that you can run the other one. So, the line in the script which currently reads:**

```

DAEMON2_ARGS="-p 9092 -c /var/lib/deluge -l /var/log/deluge-web.log -L warning"
```

must be changed to:

```

DAEMON2_ARGS="-p 8112 -c /var/lib/deluge -l /var/log/deluge-web.log -L warning"

```

As before, press the [Esc] key once and type **:wq** to save and quit out of the script. If you make a mistake editing the file then issue **:q!** instead of **:wq** to abort your changes.

We now need to make this script executable. So:

```

sudo chmod a+x /etc/init.d/deluge-daemon
```

Now we need to make sure this script runs on start-up. To do this type the following command:

```

sudo update-rc.d deluge-daemon defaults
```

Cross your fingers and restart the server by typing the following command:

```

sudo reboot -h now
```

**Accessing Deluge via the web interface**

You should now be able to access the Web front-end for Deluge by typing **[http://MyMediaserver:9092](http://MyMediaserver:9092)** (or 8112 for port) into the address bar of your browser where **MyMediaserver** is the name you gave to your server when you installed Ubuntu. Alternatively the IP address of the server works just as well.

You should now be presented with the Deluge login-screen. Enter deluge for the password and you should then see a screen similar to this:

Once you are in you could 

[IMG]http://havetheknowhow.com/images/Install_the_software/Install_Deluge/Deluge_initial_RC.JPG[/IMG]

Opening the correct ports on your router

Inorder to start downloading Torrents you need to open up some ports on your router. If you click on the Preferences icon (the screwdriver/spanner) on the Deluge web interface and select **Network**, the **Incoming Ports** (the **From**: and **To**: ports inclusively) are the ports you need to open on your router. You can obviously change these ports if so wish, but make sure they match your router settings. Make sure you also uncheck the **Use Random Ports** option if you're going to be opening a specific port range on your router.

Starting and stopping the web daemon:

If at any time you want to stop the web daemon then you can do so by issuing the following command:

```

sudo /etc/init.d/deluge-daemon stop
```

To start it again use **start** instead of **stop** in the above command. To restart it use **restart**.


*IAN NOTE: The above instructions are a summary of the excellent guide which can be found [**_here:_**]("http://dev.deluge-torrent.org/wiki/UserGuide/InitScript")


**[SIZE="4"]How to configure RSS for Deluge using FlexGet in Ubuntu[/SIZE]**

The classic way to download files using torrents is as follows:

Go to your favourite torrent site

Search for the torrent you want

Once you've found it, download the torrent file manually

Add the downloaded torrent file to your favourite torrent client

Once it has finished downloading manually move the file to its final location. (although some torrent clients can do this step for you)

There is a better way, a fully automated way, and that is to use RSS functionality. So, let's say you're a Lost fan and you currently manually download each episode of Lost as and when it becomes available. Using RSS you can automate this task meaning you can get Deluge to automatically download each episode for you as and when it becomes available. And then, once it's downloaded it will automatically move the file to the location you specify. And this final location can be different for each and every series you download.

There is a truly excellent tool called [**FlexGet**]("http://flexget.com/")which can do this, and indeed much more. However, FlexGet can be a little tricky to get up and running and so I've explained how I did it below:

**IMPORTANT: Downloading TV shows and the like from the internet can have questionable legality in many countries. So, if you're not familiar with the particular law in your part of the world then let you conscience be your guide as to what you do and do not download!**

Install easy_install[/B]

First off we need to install a python setup tool called easy_install. So type or paste the following two commands into a **Putty** session or directly into the command line of your Ubuntu installation:

```

sudo apt-get update

sudo apt-get install python-setuptools

```

**Download and install FlexGet**

We now want to download and install FlexGet itself. So, create a temporary download location and switch into it:

```

mkdir tmp

cd tmp

```

Next download FlexGet by typing or pasting the following command:

  *this presumes that you have a version of python 2.6 installed so please check [**the set up enviroment**]("http://flexget.com/wiki/InstallWizard/Linux/Environment") from flexget website

```

wget http://download.flexget.com/unstable/FlexGet-1.0r1197-py2.6.egg

```

Now install FlexGet:

```

sudo easy_install FlexGet-1.0r1197-py2.6.egg

```

Next, switch back out of the temporary download location and delete this folder and the file within it as we no longer need it:

```

cd ..

rm -r tmp

```

TIP: this tutorial was originally made for a previous version of flexget that was not available anymore. So i can't guaranty it would work for you or if will get you any troubles. I've tested it myself and it worked apparently fine.

**Create the FlexGet working area**

Often scripts and applications are run as the default Ubuntu User. However, the recommendation with FlexGet is to run FlexGet using the "deluge" user. The deluge user is the username the Deluge daemon runs under. If we don't do so then we will hit permission problems since the two parts of the setup (Deluge and FlexGet) will be creating files and folders using different usernames and thus will be using different file/folder permissions.

So we first need to create the working area which FlexGet will use:

```

sudo -u deluge mkdir /var/lib/deluge/.flexget

```

Next we need to add the deluge user as a valid user for the deluge API. So:

```

sudo -u deluge vim /var/lib/deluge/auth

```

This will open a file called **auth** which lives in the **/var/lib/deluge** folder.

There is already one line in this file but we need to insert an extra line. So press the [Insert] key once (to go into "edit" mode) and insert a new blank line. Next type or paste the following string into this new blank line:

```

deluge:deluge

```

Now press the [Esc] key once and type the following:

```

:wq

```

This should save your changes and bring you back to the command line. If you make a mistake editing the file then issue **:q!** instead of **:wq** to abort your changes.

**Create the FlexGet configuration file**

Now we need to create the FlexGet configuration file. The configuration file is where we'll store all the instructions for FlexGet. ie. What to download and from where. So type the following command to create the file and to open it:

```

sudo -u deluge vim /var/lib/deluge/.flexget/config.yml

```

Enter the configuration parameters as required. See the [**FlexGet website**]("http://www.flexget.com/") for configuration examples.

I've included a working example to allow you to test the process is working correctly: [Sample config.yml file]("http://havetheknowhow.com/Install-the-software/sample-flexget-config-file.html")

 *I means Ian again this tutorial is copied from [**How to build a Media Server**]("http://havetheknowhow.com")

**Running FlexGet as the "deluge" user**

FlexGet uses an SQL database to keep tabs on what files it has and has not downloaded. The first time you run FlexGet you need to initialise this database. So, run Deluge with the --initdb argument to initialise the database and run the script:

```

sudo -H -u deluge flexget --initdb

```

Thereafter you can omit the --initdb. So:

```

sudo -H -u deluge flexget

```

Run FlexGet as a cron job using webmin

FlexGet will execute your script each time it runs and pull down any new torrent files it finds. It is therefore desirable to run this script regularly and the best way to do this is via the use of a cron job. I use [**Webmin**]("http://havetheknowhow.com/Configure-the-server/Install-Webmin.html") to administer my server and creating cron jobs using Webmin is an absolute breeze.

So, launch Webmin then click on **System **and then **Scheduled Cron Jobs**. Then click **Create a new scheduled cron job** at the top of the screen that opens.

Click the button next to the **Execute cron job** as and choose the "deluge" user.

Type the full path of FlexGet into the **Command box**. So: **/usr/local/bin/flexget**

In the **When to Execute** section select **Simple Schedule** and choose **Hourly** from the drop down list.

Then click the **Create** button.

FlexGet will now check every hour for new torrent files and download them for you. Deluge will then take over and start downloading the actual files themselves.

**How to wipe the database and start over**

As mentioned above, FlexGet will keep a record of what files it has and has not downloaded. If you ever want to wipe everything and start over then issue the following command:

```

sudo -u deluge rm /var/lib/deluge/.flexget/db-config.sqlite

```

TIP: Don't forget to use the --initdb argument the next time you run FlexGet after issuing this command.

  Enjoy!

  * again special thanks to Ian that made this tutorial and many other on his website [**How to build Media Server**]("http://havetheknowhow.com")

  ****EXTRA**
  **Enable connection through GTK** 
  to connect through the GTK you have to enable first (by connection through webui) the **Allow Remote Connections** from **Edit -> Preferences -> Daemon **
  than return to the terminal on server and we need to add a user and password from the remote connection from GTK

  ```

  sudo vi /var/lib/deluge/auth
  
```

  than enter a new line by pressing **o** (letter o not number 0) and inster your new "**your_username:your_password:level**" ex:

  ```

  obama:obama:10
  
```

  exit insert mode and save the file by

  ```

  :wq
  
```
  
  **Enable Scheduler Plugin** - you can do that connecting through GTK. The scheduler plugin is not available yet through webui.

---

### Post by McButt on 2010-03-22
Thanks for re-posting this here, and of course thanks to the original author for producing it in the first place.
The addition of flexget is particularly awesome :)

---

### Post by gottijr on 2010-03-22
took me too much to figure everything right so i felt that it was needed

  glad u find it helpfull

---

### Post by Cas07 on 2010-03-27
You should really reference the Deluge [website]("http://deluge-torrent.org/") as it has the upto date init script [here]("http://dev.deluge-torrent.org/wiki/UserGuide/InitScript") that adds the umask option along with the full thin client guide [here]("http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient") and you should mention the Deluge FAQ [here]("http://dev.deluge-torrent.org/wiki/Faq")

To be honest it would have been more helpful to create/update the guides on the Deluge website as they are wiki based so anyone can update it in the future and then reference them here because the fragmentation that occurs from constantly referencing out of date blogs and forum posts causes more issues.

Case in point is that the forum topic heading is out of date as version 1.2.2 is out, i suggest using 1.2.x instead.

One more thing is that is much quicker to install the PPA with this command as it also adds the keys.
sudo add-apt-repository ppa:deluge-team/ppa

---

### Post by Yfrwlf on 2010-04-21
Thanks for the post.  Anyone having problems with the buttons not working in the Deluge web interface in 10.04? :???:  i.e. version 1.2.2.

---

### Post by SpikeBolt on 2010-05-06
> **Yfrwlf said:**
> Thanks for the post.  Anyone having problems with the buttons not working in the Deluge web interface in 10.04? :???:  i.e. version 1.2.2.

I have this problem.

---

### Post by mala88 on 2010-05-08
I am getting the following error when trying to run deluge via a SSH tunnel. The server and webUI are running fine.

I tried to "export DISPLAY=0.0" but it did not help. I am running deluge 1.2.2 on lucid.

Any ideas on how to fix this?


```

~$ deluge
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/lib/pymodules/python2.6/deluge/ui/gtkui/gtkui.py:167: GtkWarning: cannot open display: :0.0
  self.gnome_prog = gnome.init("Deluge", deluge.common.get_version())
```

---

### Post by sinnadyr on 2010-07-14
I did as in the guide, trying to "sudo /etc/init.d/deluge-deamon start" and get ```
 * Not starting deluge-daemon, edit /etc/default/deluge-daemon to start it.

``` so I assume it is already started, but I still can't get the webUI to open...

Any suggestions? Trying directly on the server with "http://localhost:8112" (and yes, I've changed the port in the config).

Thanks in advance, and great job man!

EDIT: Had to start deluge-web manually, now it works like a charm... Just added "deluge-web --fork" in startup applications

---

### Post by lomik on 2010-07-21
hi,
I'm having trouble setting the autoadd folder.
Trying to set it to a DropBox enabled folder but always get:

> "autoadd:72 Invalid AutoAdd folder"

Solved - changed some user settings

---

### Post by Shinger on 2010-08-12
I got a problem. Everything that has been downloaded by deluge is restricted to sudo or deluge only. I cant delete it with normal user. If i want to do that i have to chmod/chown everything to perform this action. Does somebody has a solution??

---

### Post by fimbar on 2010-08-18
> **Shinger said:**
> I got a problem. Everything that has been downloaded by deluge is restricted to sudo or deluge only. I cant delete it with normal user. If i want to do that i have to chmod/chown everything to perform this action. Does somebody has a solution??
 
Add your username to the deluge group:
 
```
sudo adduser YourUserNameHere deluge
```
 
Then log off and back on again and try again.

---

### Post by thebrandon on 2010-08-20
So I have followed this guide and for some reason its just not working for me.  When I point my browser to the address of my server and the port 9092 i get cannot connect!  I have tried to check the logs in /var/log directory for deluged and deluge-web and they are both blank.  Ive tried starting and stopping the daemon from the command prompt and I get no error msg or anything.  What have I done wrong?

---

### Post by sideaway on 2010-09-07
I completed this by myself and this would have been very helpful when setting up mine! Thank you very much for writing this up!

---

### Post by Shinger on 2010-09-18
Nevermind :P

---

### Post by maniaq on 2010-10-06
> **Yfrwlf said:**
> Thanks for the post.  Anyone having problems with the buttons not working in the Deluge web interface in 10.04? :???:  i.e. version 1.2.2.

I too have this problem - is there a solution? Should I downgrade or something?

---

### Post by ergosteur on 2010-10-10
> **maniaq said:**
> I too have this problem - is there a solution? Should I downgrade or something?

Same here. Can't add, pause or delete torrents, or basically use the Web UI for anything other than checking status. Running Deluge 1.2.3 from the ppa. Did I miss something? Is there a config file somewhere?

---

### Post by guilamuu on 2010-10-16
Okay guys, i'm stuck here :

> sudo -H -u deluge flexget --initdb
Usage: flexget [options]

flexget: error: no such option: --initdb

Any idea?

---

### Post by CommandCrowd on 2010-10-23
Hi everyone, just finished this article and I'm stuck

I get the following error:
```
start-stop-daemon: unable to open pidfile '/var/run/deluged.pid' for writing (Permission denied)
student@ubuntuServer:~$ start-stop-daemon: unable to open pidfile '/var/run/deluge-web.pid' for writing (Permission denied)
```

I've tried to do this: 
```

sudo touch /var/run/deluge-web.pid
sudo touch /var/run/deluged.pid
sudo chown deluge:deluge /var/run/deluge*

```

But that didnt work for me,

Any suggestions?

Running Ubuntu Server 10.10

---

