---
title: "How to install headless  dropbox  (with no GUI frontend) on ubuntu"
date: 2010-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by ukripper on 2010-02-26
[B][U][CENTER][SIZE=3]Dropbox on headless ubuntu 9.10 server.[/SIZE][/CENTER]
[/U][/B]

References : [http://wiki.dropbox.com/Regole/TextBasedLinuxInstall](http://wiki.dropbox.com/Regole/TextBasedLinuxInstall) and [http://wiki.dropbox.com/TipsAndTricks/TextBasedLinuxInstall](http://wiki.dropbox.com/TipsAndTricks/TextBasedLinuxInstall)

This guide is a mixture of howtos from dropbox wiki above and some  new points added by myself to make dropbox work on ubuntu 9.10 server. My special thanks to dropbox folks for a such nice wiki.


1. Log in to your Ubuntu Linux server so you obtain a shell prompt, and change to your home directory.

 

```
cd ~
``` 

2. Use wget to download the Dropbox Linux client, using either the link to the latest stable version (32-bit or 64-bit), or go to the forums and find a link to the latest forums version.

 

 This example is the 32-bit build of version 0.7.110 of the client

```
wget -O dropbox.tar.gz http://dl.getdropbox.com/u/17/dropbox-lnx.x86-0.7.110.tar.gz

```(0.7.110 works perfectly with my ubuntu server 9.10)

 

3. Use tar to extract the client. It will be placed in folder ~/.dropbox-dist/

 

```
tar zxof dropbox.tar.gz
```
 

4. Use wget to download the Python scripts needed to set this up.
 
```
cd .dropbox-dist
``````
wget http://dl.getdropbox.com/u/637552/Dropbox/dbmakefilelib.py
```
dbreadconfig.py doesn't work anymore with my ubuntu 9.10 server

 
5. Now first open  dbmakefakelib.py script - this creates fake stub copies of the GUI libraries so dropboxd will start in command line. 


I had problem with dbmakefakelib.py which started throwing errors and won't terminate after being run. Hence, to make it work here is my workaround:
```
vi dbmakefakelib.py
```
edit and replace all occurences of "dropboxd" to "dropbox" within this file. Then save and exit

I also found out python2.5 is needed to run the file, therefore, first install python2.5 from repos. ```
sudo apt-get install python2.5
```


6. Python2.5 is installed and now run

```
python2.5 dbmakefakelib.py
```


which will give this output:

> dropboxd ran for 15 seconds without quitting - success?

Terminate


 
7. At the end of the last script, dropboxd should have run successfully for a few seconds - long enough to contact the Dropbox servers and construct the initial pieces of data required for the client to run. The most important of these for identification of the client is the host id, a 128-bit number uniquely assigned to every instance of the client. 


In the last output, you got an url something like this ([https://www.getdropbox.com/cli_link?host_id=](https://www.getdropbox.com/cli_link?host_id=) ) with encrypted hostid then just go on different machine with GUI browser and copy paste it there which will direct you to dropbox website and will add your machine. Go to a web browser on any computer (it doesn't have to be the Linux server, but it requires that you're logged into your Dropbox account) and fill in the details to register or link to an existing account.

 

8. Create a folder ~/Dropbox for the Dropbox files.

 
```
mkdir ~/Dropbox
```

 

9. Run dropboxd as a background process; it should pick up the details you entered on the web page and set itself up completely.

 

```
~/.dropbox-dist/dropboxd &
```

 

Following on from that, there are a few different options to run the Dropbox client on an ongoing basis. You could put the above line in your server startup scripts, e.g. /etc/rc.local, or maybe just a certain user's login scripts.


10. It is recommended to download the official dropbox daemon to start the dropbox daemon (as an unprivileged user) and get its status.


```
mkdir -p ~/bin
```
```
wget -P ~/bin http://www.dropbox.com/download?dl=packages/dropbox.py
```
```
chmod 755 ~/bin/dropbox.py
```
```
~/bin/dropbox.py help 
```



11. You can also use system service script to automatically run dropboxd, here's the script which i am using:


```
sudo vi /etc/init.d/dropbox
```


paste below script and replace user1 by username on your system.

 
```

# dropbox service
DROPBOX_USERS="user1"
start() {
echo "Starting dropbox..."
for dbuser in $DROPBOX_USERS; do
start-stop-daemon -b -o -c $dbuser -S -x /home/$dbuser/.dropbox-dist/dropboxd
done
}

stop() {
echo "Stopping dropbox..."
for dbuser in $DROPBOX_USERS; do
start-stop-daemon -o -c $dbuser -K -x /home/$dbuser/.dropbox-dist/dropboxd
done
}

status() {
for dbuser in $DROPBOX_USERS; do
dbpid=`pgrep -u $dbuser dropboxd`
if [ -z $dbpid ] ; then
echo "dropboxd for USER $dbuser: not running."
else
echo "dropboxd for USER $dbuser: running."
fi
done
}


case "$1" in
start)
start
;;

stop)
stop
;;

restart|reload|force-reload)
stop
start
;;

status)
status
;;

*)
echo "Usage: /etc/init.d/dropbox {start|stop|reload|force-reload|restart|status}"
exit 1

esac

exit 0

```
save and exit


then


```
sudo chmod +x /etc/init.d/dropbox
```
```
sudo update-rc.d dropbox defaults
```

 now dropbox is added to init scripts and will kick off at every system startup.

To manually start type:
```
sudo /etc/init.d/dropbox start
```


Test dropbox working:
```
cd Dropbox
~/bin/dropbox.py status
~/bin/dropbox.py filestatus
```

---

