---
title: "Post installation checklist for Ubuntu Hardy Heron 8.04"
date: 2008-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by pterosky on 2008-05-22
Here is my checklist for setting up a new Ubuntu installation, I thought it might be of use to other Ubuntu beginners. If you decide to use this list after installing Ubuntu, please take care which commands you run and settings you change -- for example, don't disable the Printer Service if you plan on connecting a printer to your computer 8o)

For the more complicated stuff, like mounting a storage partition or defining keyboard shortcuts, I have linked to more information after the description, instead of explaining it here -- this post is already long enough as it is :) 

Three excellent guides for beginners on getting started with Ubuntu:[LIST]
[*][HowTo: Partitioning Basics]("http://ubuntuforums.org/showthread.php?t=282018")
[*][Getting started with Ubuntu Newbie (n00b) 101]("http://ubuntuforums.org/showthread.php?t=790485")
[*][The Perfect Desktop - Ubuntu 8.04]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron")
[/LIST]
My hardware: ATI graphics card, Samsung 19" LCD monitor.

My partition setup for Ubuntu installation:
/dev/sda3 - as / (root)
/dev/sda5 - as /home
/dev/sda6 - storage partition for backups, not touched during installation
/dev/sda7 - as swap

-----------------------------------------

[SIZE="4"]Setting up Ubuntu 8.04 after the installation[/SIZE]

Apply automatic updates through Update Manager and enable the proprietary ATI driver.

**Uninstall Firefox 3 and install Firefox 2** (edit: I am using Firefox 3 now) 
Open Synaptic Package Manager (System > Administration > Synaptic Package Manager)
Right click on all Firefox 3 items, select "Mark for Complete Removal" and click Apply. Navigate to /home/"Your Username", press Ctrl+H to show hidden files and folders and delete .Mozilla folder to start fresh. Restart and install Firefox 2 (firefox-2 and firefox-2-gnome-support). Correct Preferred Applications (System > Preferences > Preferred Applications), under Web browser enter "firefox-2" in the Command box.

**Firefox: Fix backspace key, single close tab button and click to select URL** 
Access Firefox preferences by entering "about:config" in the Firefox address bar: 

[LIST]
[*]Make Backspace Key Work Correctly: browser.backspace_action = 0
[*]Have a single close tab button on the right side of the tab bar: browser.tabs.closebuttons = 3
[*]Fix Ctrl+(Shift)+Arrow key behavior in address bar: layout.word_select.stop_at_punctuation = true
[*]Click to select URL in address bar: browser.urlbar.clickSelectsAll = true
[*]Disable Automatic Image Resizing: browser.enable_automatic_image_resizing = false
[*]Stop Firefox 3 from displaying bookmarks automagically in the address bar: browser.urlbar.maxRichResults = -1
[*]Prevent Firefox from stealing focus when clicking on links in Thunderbird: browser.tabs.loadDivertedInBackground = true
[/LIST]
**Larger, more readable fonts in Firefox**
Set Default Font under Content to Bitstream Vera Sans, click Advanced and set Minimum font size to 18 and Monospace to Bitstream Vera Sans. Uncheck "Allow pages to choose their own fonts, instead of my selection above". 

**Add-ons for Firefox**
Instead of installing Adblock press ESC to stop annoying animated/flashing advertisement. Right-click on image ads and select "Block images from ..." to prevent images from that domain showing up in the future.
[LIST]
[*]Flashblock
[*]Firebug
[*]UnPlug
[/LIST]
**Remove "List All Tabs Button" on the right side of Firefox and remove items from the Firefox menus**
Make a file called userChrome.css in /home/"Your Username"/.Mozilla/Firefox/Profiles/"Profile string".default/chrome with this content:
```

/* Disable Container box for "List all Tabs" Button */
.tabs-alltabs-stack {
display: none !important;
}

/* Remove Options from FireFox Drop-Down Menus */
menuitem[label="Web Search"],
menuitem[label="Web Search"] + menuseparator,
menuitem[label="Work Offline"],
menuitem[label="Bookmark All Tabs..."],
menuitem[label="Stop"],
menuitem[label="Subscribe to This Page..."],
menuitem[label="Subscribe to This Page"],
menuitem[label="Reload"],
menuitem[label="Bookmarks Toolbar Folder"],
menuitem[label="For Internet Explorer Users"],
menuitem[label="Send Link..."],
menuitem[label="Reload"] + menuseparator {
display: none !important;
}

```

**Enlarge the focus indicator in Firefox, to better highlight the cursor when navigating using the TAB-key**
Make a file called userContent.css in /home/"Your Username"/.Mozilla/Firefox/Profiles/"Profile string".default/chrome with this content:
```

*:focus { outline: 3px solid #708090 /* #10d0f0 */; outline-offset: 1px;
outline-radius: 5px; }
button:focus::-moz-focus-inner { border-color: transparent; }
button::-moz-focus-inner,
  input[type="reset"]::-moz-focus-inner,
  input[type="button"]::-moz-focus-inner,
  input[type="submit"]::-moz-focus-inner,
  input[type="file"] > input[type="button"]::-moz-focus-inner {
  border: 1px dotted transparent;
}
textarea:focus, button:focus, select:focus, input:focus {
outline-offset: -1px; }
input[type="radio"]:focus {outline-radius: 12px; outline-offset: 0px; }
a:focus { outline-offset: 0px; outline: }

```

This also works with Thunderbird: Create a folder called chrome in .mozilla-thunderbird/"Profile string".default/ and copy userContent.css to this location.

More information: [[gui-talk] Fwd: Mozilla Firefox accessibility and usability enhancement]("http://www.nfbnet.org/pipermail/gui-talk/2006-May/017563.html")

**Remove Evolution and install Thunderbird**
In a terminal window enter ```
sudo apt-get remove evolution
``` or do it through Synaptic Package Manager. Install Thunderbird (Thunderbird and Thunderbird-gnome-support) through Synaptic Package Manager. If you have a backed up Thunderbird email folder from either an old Windows or Linux installation, then copy .thunderbird folder (I keep it in my Storage partition) to /home/"Username" This should import account settings, emails and folder set up.

**Fix links not working from within Thunderbird**
Firefox starts up, but the link doesn't open up, instead it shows the home page. Edit the .mozilla-thunderbird/"Profile string".default/prefs.js file and add (or change) the following:
```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox-2");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox-2");
```

More information: [Clicking on links in Thunderbird and having them open in Firefox [Resolved]]("http://ubuntuforums.org/showthread.php?t=60427")

**Make Hotmail WebMail Add-on work**
In Tools > Add-ons > WebMail > Preferences > Servers, change POP value from 110 to 1025 and SMTP value to 1026. In Thunderbird: Edit > Account Settings > Server Settings > Port and enter 1025

**Change the default sort order in Thunderbird folders and Fix Ctrl+(Shift)+Arrow key behavior in email addresses**
Open Edit > Preferences > Advanced > Config Editor, locate and change the following:
mailnews.default_news_sort_order          2
mailnews.default_news_sort_type          22
mailnews.default_sort_order          2
mailnews.default_sort_type          18

Double click to change status to "user set": 
layout.word_select.stop_at_punctuation

More information: [Change the default sort for all Thunderbird folders, inc RSS]("http://forums.mozillazine.org/viewtopic.php?p=3075712")

**Enable Uncomplicated Firewall, open ports for Amule**
In a terminal window enter ```

sudo ufw enable
sudo ufw allow 5588/tcp
sudo ufw allow 5598/udp

```

**Change assigned IP address automatically, by changing mac address on boot**
In a terminal window enter ```

sudo apt-get install macchanger

```
Then open this file ```

sudo gedit /etc/rc.local

```
and add the following after "# By default this script does nothing."```

ifconfig eth0 down # hw ether <new_mac_addr>
macchanger --another eth0
sleep 3
ifconfig eth0 up

```

More information: [Change mac address on boot?]("http://ubuntuforums.org/showthread.php?t=451764")

**Use tor to surf anonymously**
[HOW TO surf anonymous]("http://ubuntuforums.org/showthread.php?t=95527")

**Remap ;/:, '/", [/{ keys to  æ/Æ, ø/Ø, å/Å and disable Caps Lock**
I am using a Generic 105-key US keyboard layout. For typing the danish letters æ/Æ, ø/Ø, å/Å I press ;/:, '/", [/{ by remapping these keys with xmodmap commands. To access the original keys I press Caps Lock, which has been transformed into a switch key.

Create a file called .Xmodmap in /home/"Your Username"/ and put the xmodmap commands in there. They will be run automatically on start up:
```

keycode 34 = aring Aring bracketleft braceleft
keycode 47 = ae AE semicolon colon
keycode 48 = oslash Ooblique quoteright quotedbl
keycode 66 = Mode_switch

```
More information: [HOWTO: Multimedia keys]("http://ubuntuforums.org/showthread.php?p=261714")

**Define Keyboard Shortcuts**
You can define keyboard shortcuts in System > Preferences > Keyboard Shortcuts, but I couldn't make Ubuntu recognise the Windows key, known as Super in Ubuntu, so I defined them manually, to edit them type ```
gconf-editor
``` in a terminal window and navigate to these places:

/apps/gnome_settings_daemon/keybindings/

volume_up	<Control>Page_Up - Turns the Master Volume up
volume_down	<Control>Page_Down - Turns the Master Volume down

/apps/metacity/global_keybindings
panel_main_menu		<Super>P - Show the panel menu
run_command_terminal	F12 - <Super>T is taken by Thunderbird 8o)
run_command_1		<Super>F - Firefox
run_command_2		<Super>T - Thunderbird 
run_command_3		<Super>A - Audacious
run_command_4		<Super>E - Nautilus - As in Windows Key+E
run_command_5		<Super>I - FileZilla
run_command_6		<Super>B - Baobab Disk Usage Analyzer
run_command_7		<Super>X - gedit
run_command_8		<Super>O - Opera
run_command_9		<Super>S - Gnome System Monitor
run_command_10		<Super>U - Update Manager
run_command_11		<Super>C - Calculator
run_command_12		<Super>R - Transmission
show_desktop			<Super>M - Hide all windows and focus on desktop

/apps/metacity/keybinding_commands
command_1  - firefox (*edit: I am using Firefox 3 now, to start Firefox 2: "firefox-2"*)
command_2  - thunderbird
command_3  - audacious
command_4  - nautilus /storage
command_5  - filezilla
command_6  - baobab
command_7  - gedit
command_8  - opera
command_9  - gnome-system-monitor
command_10 - update-manager
command_11 - gcalctool
command_12 - transmission

/apps/metacity/window_keybindings
close	<Control>Q  - Closes a program, since Ctrl+W closes tabs in for example Firefox and Gedit(the Text file editor). I always found Alt+F4 awkward.
toggle_maximized   F11 - Like in Firefox

The settings are saved in the files /home/"Your Username"/.gconf/apps/metacity/global_keybindings/%gconf.xml and 
/home/"Your Username"/.gconf/apps/metacity/keybinding_commands/%gconf.xml -- you can find the files at the bottom of this post.

Just paste them into the correct folders, rename the existing %gconf.xml to OLD%gconf.xml and delete [global_keybindings] or [keybinding_commands] from the filename.

More information: [Defining Keyboard Shortcuts in Gnome (Metacity)]("http://justanothertechblog.blogspot.com/2006/12/defining-keyboard-shortcuts-in-gnome.html")

**Edit Panel Menus, order of menu items and renaming them**
Under System > Preferences > Main Menu. 

**Back up or restore Panels**
Panel settings are saved in the /home/"Your Username"/.gconf/apps/panel directory, deleting it and restarting resets the panels to default.

**Change to Single Click Mouse, List View and Display**
Open the File Browser Nautilus (Places > Home Folder > Edit > Preferences)
[LIST]
[*]Views: Under Views, set View new folders using to "List View"
[*]Single Click Mouse: Under Behavior, set Behavior to "Single click to open items"
[*]Display: Under Display, set Format to "2008-05-22 3:03:01"
[/LIST]
**Remove Ctrl+T "move to trash" shortcut in Nautilus**
Open System > Preferences > Appearance > Interface, select Editable menu shortcut keys. Click on Edit in Nautilus and highlight the Empty Trash item, with the focus on that menu item, press the Delete key to remove the shortcut.
*Ubuntu can't seem to remember this though... when I restart my computer it is back:* 
More information: [Re: Change Nautilus CTRL + T "move to trash" keyboard shortcut?]("http://ubuntuforums.org/showthread.php?p=4985567")

**Change Theme, Desktop Wallpaper, Login Screen and Font Sizes**
Right click on Desktop > Change Desktop Background
[LIST]
[*]Theme: Under Theme tab Select "Custom", click Customize > Pointer and set Pointer to "DMZ-White", increase Size  
[*]Desktop Wallpaper: Under Background tab click Add and set a new Wallpaper. Click Colors and select a colour that matches the new wallpaper and copy the hexadecimal value from Color Name
[*]Login Screen: Open System > Administration > Login Window, it might take a few minutes to appear. Under Local select a new theme, click Background Color and paste the hexadecimal value in Color Name
[*]Fonts: Under Fonts select Subpixel smoothing(LCDs), click Details and set Resolution to 130 DPI[/LIST]

**Mount storage partition**
In a terminal window enter the following commands: 
Create the directory:
```
sudo mkdir /storage
```
Back up fstab file:
```
sudo cp /etc/fstab /etc/fstab_backup
```
Determine UUID for the relevant partition:
```
ls -l /dev/disk/by-uuid
```
Result: sda6 - ae51ac8f-6204-4d81-8187-98ue2f26b2c0
To be inserted into /etc/fstab:
# /dev/sda6
UUID=ae51ac8f-6204-4d81-8187-98ue2f26b2c0 /storage        ext4    defaults 0 2
```
sudo gedit /etc/fstab
```
```
sudo mount -a
sudo chown -R "Your Username":"Your Username" /storage
```
For example: sudo chown -R marie:marie /storage
```
sudo chmod -R 755 /storage
```

More information: [Mounting Linux Partitions in Ubuntu]("http://www.psychocats.net/ubuntu/mountlinux")

**Get the codecs for AVI, MP4 and other formats, DVD playback, install Java**
Follow the instructions in this excellent guide:  [[all variants] Comprehensive Multimedia & Video How-to]("http://ubuntuforums.org/showthread.php?t=766683")

**Register Java plug-in in Firefox**
To register the plug-in with Firefox-2 on 8.04 (Hardy)and get java runtime env, in terminal type: 
```
cd /usr/lib/firefox/plugins
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

More information: [[ubuntu] hardy firefox2 java problems solved]("http://ubuntuforums.org/showthread.php?t=782167")

**Fix Real Player plug-in in Firefox -- sound but no picture**
Right-click in the Firefox window > Preferences and set video output to GL.

**Get Fullscreen option in Mplayer working**
Set Preferences > video to gl X11(OpenGL) or gl2 to be able to view movies fullscreen. If not the image remains the same size and the border around the image goes black when Fullscreen is chosen.

**Set deinterlacing for movies to "blend" in VLC**
Install VLC and open Settings > Preferences > Video > Filters
Enable checkbox for deinterlacing, make sure "deinterlace" appear in the textbox below all the checkboxes. Open Settings > Preferences > Video > Filters > Deinterlace and select "Blend" for the deinterlace mode.

**Add a dictionary to Open Office Writer**
If the window is too small when using the File > Wizards > Install new dictionaries turn off visual effects by going to System > Preferences > Appearances > Visual Effects and select "None".

**Filezilla**
Install, then restore sitemanager.xml from back up in .filezilla folder

**Disable unneeded Services (System > Preferences > Preferred Applications)**
[LIST]
[*]Enable Audio Settings Management
[*]Disable Bluetooth
[*]Disable Printer service
[/LIST]

**Install XAMPP, start, stop, create public_html and link it to /opt/lampp/htdocs**
Download XAMPP from [http://www.apachefriends.org](http://www.apachefriends.org), then type in terminal:
Install: 
```
sudo tar xvfz xampp-linux-1.6.6.tar.gz -C /opt
```
Start: 
```
/opt/lampp/lampp start
```
Set up security: 
```
/opt/lampp/lampp security
```
Make public_html directory in home directory: 
```
mkdir ~/public_html
```
Link to /opt/lampp/htdocs: 
```
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
```

More information: [HOWTO: Setup easy web development environment (XAMPP)]("http://ubuntuforums.org/showthread.php?t=223410") 

**dvd::rip -- settings for ripping**
Select which Audio track to scan for volume in Rip Title
Video codec: xvid4 
Deinterlace Mode: Smart deinterlacing
MP3 bitrate: 192
Audio track: ac3 6Ch 

More information: [Backing up DVDs]("http://www.wombatnation.com/2005/01/backing-up-dvds")

**Thunar**
Installed for batch/bulk renaming files

---

### Post by ZabiGG on 2008-05-23
Great post-install, thanks ;) 

I personally kept Firefox 3, added Opera for lighter browsing, and kept Evolution, and everything works.

If you don't mind, I'll link this in my 101.

Cheers,

Z.

---

### Post by pterosky on 2008-05-23
Thank you Ma'am -- feel free to link it up!

...and thanks for making the [Ultimate nOOb Reference Post]("http://ubuntuforums.org/showthread.php?t=790485"), great initiative! :)

---

### Post by dot2kode on 2008-05-23
Very helpful thanks for taking the time to offer this. :)

---

### Post by Patch87 on 2008-05-25
Thank you very much, your info helped me solve a java problem I've been working on for a week

---

### Post by pterosky on 2008-05-25
Glad you guys found it helpful :)

If anyone did use the checklist yet for a post installation set up, feel free to post your experience.

Thanks :KS

---

### Post by a.reynolds on 2008-05-31
Thank you for your good work.  I accidentally removed the panel, your post saved my life.

---

### Post by themuddler on 2008-06-01
A useful checklist. I have the same problem with cloning onto my TV which is a higher resolution than the laptop. If I could make the laptop screen pan to the TV resolution then I'd be happy but I'm not sure how to do that (been using nvidia-settings). Sorry it's not much help but at least you know there's someone else with the same difficulty! :)

---

### Post by kartiksinghal on 2008-06-07
Thanks a lot for this gr8 list.

And hey why remove firefox 3 beta 5. Its really a great browser with added improvements from version 2.

---

### Post by NewbieNeedsHelp on 2008-06-07
Thanks for the tips for tweaking FireFox!

---

### Post by Vadi on 2008-06-07
Hm, quite personal preferences-specific there, unfortunately I didn't find anything useful. Except maybe besides enabling ufw. What's the point? All ports are covered already by default.

---

### Post by ZabiGG on 2008-06-07
> **Vadi said:**
> Hm, quite personal preferences-specific there, unfortunately I didn't find anything useful. Except maybe besides enabling ufw. What's the point? All ports are covered already by default.

well... you're kinda not a newbie ;) lol

Cheers,

Z.

---

### Post by Vadi on 2008-06-07
Yeah, and I don't think newbies should be doing this either.

---

### Post by ZabiGG on 2008-06-07
> **Vadi said:**
> Yeah, and I don't think newbies should be doing this either.

Well, this linux newbie has been around computers for at least 20 years... which is not too far off from your entire lifetime, based on your profile picture.

You'll note that most "newbies," when it comes to linux are well-read and experienced computer users who decided to switch to be able to customize their experience.

If you wish to look down on people, that's your prerogative. This post was useful to a lot of others. You should at least respect that.

Z.

---

### Post by Vadi on 2008-06-08
Oh? Show me proof that most newbies are well-experienced computer users. That's not the case with my newbies.

---

### Post by Pjotr123 on 2008-06-08
This is my checklist:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)

Hope this helps somebody.  :)

---

### Post by nooblot on 2008-06-27
excellent thread -
anyone care to explain why OP wanted to remove FF3 ?

---

### Post by pterosky on 2008-06-27
There were some problems with my internet bank, plug-ins and it occasionally hung... It was the Beta version I uninstalled though, the officially released version 3 might not have these problems.

---

### Post by nooblot on 2008-06-27
this step "Mount storage partition"

what is it for ?

---

### Post by ZabiGG on 2008-06-27
The mount step is only if you created a special partition on your disk for storage. If you installed using the full disk or dual-installed with only two partitions, it is not a necessary step.

I personally prefer to have a number of disk partitions so that I can install /home separately and not lose my configuration settings when I reinstall, and then use three other partitions respectively for storage and two dedicated spaces to play around with other distros/systems in virtualbox.

Cheers,

Z.

---

### Post by vussvillem on 2008-07-10
Well, for automatic weekly or whatever time scale backup you can use sbackup. It has very logical and easy to use GUI.

And at least in Gutsy Gibbon, I could render my screen whatever resolution while doing TV-out or VGA-out in different resolution, thanks to this how-to [http://ubuntuforums.org/showthread.php?t=641998](http://ubuntuforums.org/showthread.php?t=641998)

---

### Post by pterosky on 2008-07-15
Thanks for the suggestions. 

The TV-out solution seems a bit too cumbersome. I have made a [new thread]("http://ubuntuforums.org/showthread.php?t=859990") about what I am looking for. Maybe it isn't possible? For now I will just go to "Screen Resolution" and adjust it when I want to use TV-out.

For back-up I will just copy the pertinent folders from the /home directory, since [sbackup doesn't seem to be 100% reliable]("http://brainstorm.ubuntu.com/idea/10055/") and hard disk space isn't that expensive anymore.

---

