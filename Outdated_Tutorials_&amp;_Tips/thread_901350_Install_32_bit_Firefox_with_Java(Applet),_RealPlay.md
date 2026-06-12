---
title: "Install 32 bit Firefox with Java(Applet), RealPlayer, Flash and Mplayer on 64 Ubuntu."
date: 2008-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by playtowin on 2008-08-26
The following technique is a painless way to install 32bit Firefox and proprietary 32 bit binary plug-ins into your Ubuntu AMD64 bit installation. 
**[COLOR="YellowGreen"][SIZE="4"]It's works Perfect. One among the best way!![/SIZE][/COLOR]**

Install of 32 bit Firefox with Flash, Java (Applet), Realplayer (Including Plugin), Mplayer (Plugin).

This method works fine on Hardy, Gusty and Fiesty. It should work on older version also.


Before you can use the 32-bit version of Firefox **you must make sure to install** the **fundamental libraries** for 32 bit support under 64 bit native Linux. Open Synaptic Package Manager, **search and install all these**:


[COLOR="Sienna"][SIZE="5"]libraries for 32 bit support[/SIZE][/COLOR]

```
ia32-libs
gsfonts
alsa-oss
lib32gcc1
lib32stdc++6
lib32asound2
lib32ncurses5
lib32z1
libc6-i386
lib32nss-mdns
```


[COLOR="Sienna"][SIZE="5"]Installing 32 Bit Edition of Firefox[/SIZE][/COLOR]

1) Download the installation tar.bz2 from [Firefox]("http://www.mozilla.com/en-US/firefox/") or - if you want more version choices - from [[COLOR="RoyalBlue"]here[/COLOR]]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/")

2) Open a terminal, and navigate to the directory where you saved it to. Extract the file and move it (adjust the file name as needed): 

```
tar -xvf firefox-3.0.1.tar.bz2

sudo mv firefox /usr/local/firefox32
```

3) Next we must setup some minor font details.

First, create the /etc/pango32 directory if it does not already exist. 

```
sudo mkdir /etc/pango32
```

Create the environment variable file for pango32 and open it for editing:

```
gksudo gedit /etc/pango32/pangorc &
```

Then paste the script into the editor: 

```
[Pango]
ModuleFiles=/etc/pango32/pango.modules
[PangoX]
AliasFiles=/etc/pango/pangox.aliases
```

Save the file and close the editor. 

4) Finally, create a small script to setup the environment variables and launch our 32 bit version of Firefox.

```
gksudo gedit /usr/local/bin/firefox32 &
```

Copy and paste the shell script instructions below: 

```
export GTK_PATH=/usr/lib32/gtk-2.0
export PANGO_RC_FILE=/etc/pango32/pangorc
export GDK_PIXBUF_MODULE_FILE=/etc/gtk-2.0/gdk-pixbuf.loaders.32
linux32 /usr/local/firefox32/firefox "$@"
```

Save the file and close the editor. Make the file executable so that we can launch it: 

```
sudo chmod +x /usr/local/bin/firefox32
```

5) At this point, close down all instances of Firefox that you might have running. Firefox will spawn new versions of Firefox based upon any current versions you have running. This means that if you wish to load the 32 bit version, you must make certain that you have no instances of the 64 bit version running, and vice versa. Once you have closed all instances of Firefox (including the one in which you are probably reading this), test the executable with the following command in a terminal:

```
firefox32 &
```

It should load properly. Ignore any warnings that might be output to the shell. 

6) You might notice that the icons in tool bars are missing so to fix this you need to now edit /usr/local/bin/firefox32 &

Open a terminal and type the following

```
gksudo gedit /usr/local/bin/firefox32 &
```

No you see the last line as

```
linux32 /usr/local/firefox32-3/firefox $@
```

Change it to

```
/usr/local/firefox32-3/firefox $@
```

save the file.

Now everything work fine with all icon :)


[COLOR="Sienna"][SIZE="5"]32 Bit Plug-ins[/SIZE][/COLOR]

The process for installing plug-ins is relatively painless. Simply take the library file and place it into your newly created /usr/local/firefox32/plugins directory. All of these are optional, you can pick and choose from any of them that you wish to install.

[COLOR="Sienna"][SIZE="5"]Flash[/SIZE][/COLOR]

1) First off, open a Terminal (Applications - Accessories), and copy/paste these commands into it: 

```
cd Desktop

wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```

2) This will download the Flash Player on your Desktop. Then, copy/paste the following: 

```
tar -xvzf install_flash_player_9_linux.tar.gz
```

3) To extract the flash from the archive, and then just copy/paste this: 

```
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/local/firefox32/plugins/
```

To move flash into the Firefox Plug-ins folder, from where Firefox will be able to run it. Now simply restart Firefox, and your Flash will be working! 


[COLOR="Sienna"][SIZE="5"]Java with Applet[/SIZE][/COLOR]

1) To install the Java applet plugin for 32 bit Firefox, open a Terminal (Applications - Accessories), and copy/paste these commands into it: 

```
sudo aptitude install ia32-sun-java6-bin
```

2) This will download and install java. Then, copy/paste the following: 

```
sudo ln -s /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/local/firefox32/plugins/
```

This'll install a link within the Firefox 32 bit edition plugins directory and the Java applet. Now simply restart Firefox, and your Java will be working!


[COLOR="Sienna"][SIZE="5"]RealPlayer[/SIZE][/COLOR]

1) Download the installation package from the [[COLOR="RoyalBlue"]RealPlayer website[/COLOR]]("http://www.real.com/linux")

2) Next, open up a terminal and change to the directory where you saved the file you downloaded. Make the file executable and extract it: 

```
chmod +x RealPlayer11GOLD.bin

sudo ./RealPlayer11GOLD.bin
```

3) Accept the default location and extract. Move the file to the appropriate area: 

```
sudo mv /opt/real/RealPlayer /usr/local/realplayer32
```

4)Link the appropriate files to your Firefox 32 bit plug-in directory: 

```
sudo ln -s /usr/local/realplayer32/mozilla/* /usr/local/firefox32/plugins
```

5) Link the RealPlayer binary blob file to a location that your default path can find it: 

```
sudo ln -s /usr/local/realplayer32/realplay /usr/local/bin/realplay
```


[COLOR="Sienna"][SIZE="5"]Mplayer[/SIZE][/COLOR]

1) First make sure you have installed Mplayer either form Synaptic Package Manager or form their [[COLOR="RoyalBlue"]site[/COLOR]]("www.mplayerhq.hu") and then download a copy of the Mplayer plugins attached [[COLOR="RoyalBlue"]here[/COLOR]]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=AttachFile&do=view&target=firefoxmplayer.tar.bz2")

2) Open up a terminal and change to the directory where you downloaded the file. Extract the compressed file: 

```
tar -xvf firefoxmplayer.tar.bz2
```

3) Copy the Mplayer plug-in files contained in the compressed file to /usr/local/firefox32/plugins/ 

```
sudo cp firefoxmplayer/mplayerplug-in* /usr/local/firefox32/plugins/
```


**[COLOR="Red"][SIZE="4"]NOTE:[/SIZE][/COLOR]** After Installing Mplayer plugins Real Player plugin won't work(Real Player works fine), Mplayer plugin will play all real plugin files/stream. so if you want RealPlayer to play it's plugins and mplayer to play the remaining ones, open a terminal and type 

```
sudo nautilus
```

now a power user window will open

next navigate to 

```
/usr/local/firefox32/plugins
```

and Delete these

```
mplayerplug-in-rm.so

mplayerplug-in-rm.xpt
```

Now with FF32 RealPlayer plugin will work along side other Mplayer plugin.



[COLOR="Sienna"][SIZE="5"]Optional Extras[/SIZE][/COLOR]

[COLOR="Sienna"][SIZE="4"]Set 32-bit Firefox As the Default Browser[/SIZE][/COLOR]

1) Click System menu, then select Preferences > Preferred Applications.
2) Under the Internet tab, choose Custom from the drop down list under    Web Browser.
3) In the Command edit-box, type: 

```
firefox32 "%s"
```


[COLOR="Sienna"][SIZE="4"]Create a Firefox 32 Bit Menu Launcher[/SIZE][/COLOR]

1) Add a menu item or panel item. Choose a suitable icon.

2) Under the  command  entry, simply type firefox32

3) Edit the rest of the description as you like. 



[COLOR="Sienna"][SIZE="4"]Beautifying Firefox's Widgets (I haven't tested this,it should work)[/SIZE][/COLOR]

To make Firefox use much nicer buttons and other widgets, follow the instructions below.

First, grab the widgets, extract them and back up your existing set:

```
wget http://users.tkk.fi/~otsaloma/art/firefox-form-widgets.tar.gz

tar -xvzf firefox-form-widgets.tar.gz

sudo cp /usr/local/firefox32/res/forms.css /usr/lib/mozilla-firefox/res/forms.css.bak
```

Finally, set Firefox to use the new widgets: 

```
cat firefox-form-widgets/res/forms-extra.css | sudo tee --append /usr/local/firefox32/res/forms.css > /dev/null

sudo cp -r firefox-form-widgets/res/form-widgets /usr/local/firefox32/res
```


[COLOR="Sienna"][SIZE="5"]Troubleshooting[/SIZE][/COLOR]

If in case Firefox crashes while using flash or Java just simply clear the firefox's cache completely and restart the browser. It will work fine. :) ):P

---

